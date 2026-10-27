# QA — Unidade 4

- Papel: QA independente.
- Status: **APPROVED para a integração da Unidade 4** (TASK-002).
- Data: 27/10/2026.
- Base Git: `fb8c3185409367949552f55e253995c69f31a6ee`, branch `main`; implementação ainda sem commit durante a validação.
- Entradas lidas: `technical-plan.md`, `tasks.md`, `implementation.md`, `workflow.md`, diff de `index.html`/`PUBLICAR_GITHUB_PAGES.md` e comparação do novo HTML com `/tmp/unidade-4-original.html`. Não há PRD separado neste ajuste proporcional.

## Versão validada

| Arquivo | SHA-256 |
| --- | --- |
| `index.html` | `4a82af448c3d4fd9547815656088bacba09090be8f43391980ae2f1bc8f39a96` |
| `Heranca_Classes_Abstratas_Interfaces_PHP84_Reveal.html` | `c19410ca16de5135d46a56c8aa0a45a7fd6110a8dfd935ff5745b40bff7f7b4c` |
| `PUBLICAR_GITHUB_PAGES.md` | `694624f5f7347afb5d8b2c3a03c4fdb721dc28daa6772028239ed1f948098079` |

## Matriz de aceite

| AC | Cenário | Evidência e resultado |
| --- | --- | --- |
| AC-001 | Menu em 1366×768 e 390×844 | PASS: quatro cards numerados 1–4, total 4, assunto correto, quarto card abre o HTML exato; sem overflow horizontal do menu. Screenshots inspecionados. |
| AC-002 | Capa, título e retorno | PASS: identificação Unidade 4; Menu com nome acessível; clique retorna a `index.html`. Retângulos dos três controles não se sobrepõem nem ultrapassam viewport; toolbar oculta em impressão. |
| AC-003 | Preservação e interações | PASS para a integração: 81 seções antes/depois; somente primeira seção modificada; ambos os scripts idênticos ao original. Unidades 1–3 idênticas ao HEAD. Navegação, abrir/fechar Sumário e Notas, demonstração lookup, download `01_heranca.php` e retorno exercitados nos dois tamanhos, sem `pageerror`. Ver limitação preexistente abaixo. |
| AC-004 | HTTP, links e publicação documentada | PASS: menu servido com HTTP 200 e navegação real para apresentação; todos os quatro destinos locais existem. Documento lista Unidade 4; `.nojekyll` preservado. |
| AC-005 | Aprovação antes de envio | Pré-condição atendida por este relatório. Commit/push e confirmação remota são a próxima TASK-003 e devem ser registrados pelo Coder. |

## Comandos e verificações executados

- `git diff --check`: exit 0, sem erros, repetido ao concluir.
- `git diff -- index.html PUBLICAR_GITHUB_PAGES.md`: alterações limitadas a contador, quarto card e lista documental.
- Python com `html.parser.HTMLParser`, `re.findall` e `subprocess.check_output(['git','show',...])`: quatro links locais existentes; 81 seções antes/depois, mudança apenas na capa; dois scripts sem alteração; três unidades anteriores intactas.
- `git rev-parse HEAD` e `shasum -a 256 index.html Heranca_Classes_Abstratas_Interfaces_PHP84_Reveal.html PUBLICAR_GITHUB_PAGES.md`: base e hashes acima confirmados ao final.
- Chrome headless via `playwright-core` já instalado no runtime, com servidor `http://127.0.0.1:8764`: scripts temporários `/private/tmp/unidade4-qa.cjs` e `/private/tmp/unidade4-mobile-debug.cjs`. Execuções finais: desktop `PASS 1366`; mobile `PASS 390`, exit 0, nenhum erro JavaScript. Download salvo e conferido como texto PHP começando por `<?php`.
- Capturas locais inspecionadas: `/private/tmp/unidade4-menu-1366.png`, `/private/tmp/unidade4-capa-1366.png`, `/private/tmp/unidade4-menu-390.png`, `/private/tmp/unidade4-capa-390.png`; demonstrações capturadas em `/private/tmp/unidade4-demo-{1366,390}.png`.

## Limitações e diagnóstico

- Chrome não iniciou dentro da sandbox (SIGABRT/EPERM); testes de navegador foram executados com a permissão elevada do ambiente. Nenhuma dependência foi instalada no repositório.
- Duas assertivas iniciais do script precisaram de ajuste: CSS transforma a capa em maiúsculas (`textContent` usado para verificar a fonte); Reveal ativa scroll view no mobile e envolve seções em wrappers (seletor `.slides section` substitui `.slides>section`). Isso não demandou alterações no produto.
- No scroll view de 390×844, selecionar o sexto item do Sumário fechou o diálogo, mas a leitura posterior de `Reveal.getIndices()` permaneceu `h=1`; a assertiva desktop esperava `h=5`. O script funcional é byte a byte igual ao material recebido, portanto essa observação pertence ao comportamento preexistente da apresentação. A validação mobile confirmou abertura/fechamento dos diálogos e navegação por rolagem/controle nativo, além de demonstração e download; não certifica posicionamento por todos os itens do sumário nesse modo. Essa limitação não bloqueia a integração autorizada e foi comunicada ao principal.
- Não foram executados todos os exemplos PHP nem auditoria pedagógica dos 81 slides. `php -l`, Tree-sitter, ZIP, subprocessos de submissões e Docker não se aplicam: este checkout é um site estático didático, não o runtime do PHP Code Evaluator. Não foram introduzidos LLM, IA ou serviços de avaliação.
- Implantação GitHub Pages e hash remoto ainda não avaliados nesta etapa, anterior ao push.

## Handoff

QA → principal/Coder: liberar TASK-003 para publicar exatamente os hashes acima. Não há defeito introduzido identificado. Mudança posterior no código exige revalidação pertinente. O relatório aprova a integração e preservação do material fornecido dentro do escopo; publicação deve receber evidência própria.
