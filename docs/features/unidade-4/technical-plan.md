# Plano técnico — Unidade 4

## Escopo e evidências

Ajuste pequeno do site estático de material didático, solicitado em 27/10/2026. Não existe aplicação Python/PHP neste checkout nem `docs/PRD.md`, PRD ou design prévios. O contrato é o padrão observável de `index.html`, das unidades 1–3 e de `PUBLICAR_GITHUB_PAGES.md`. Não há necessidade de backend, build ou nova dependência.

- Estado inspecionado: branch `main`, HEAD `fb8c318`, remoto `https://github.com/vapjunior/poo-bcc-unimar-2026.git`.
- HTML fornecido: `Heranca_Classes_Abstratas_Interfaces_PHP84_Reveal.html`, inicialmente não rastreado; 81 slides, Reveal.js incorporado, exemplos para download, sumário e notas próprios.
- O menu lista três unidades, informa total 3 e usa cards `.unit-card`; grade de três colunas acima de 860 px e uma coluna abaixo desse limite.
- As unidades publicadas possuem link `.home-link` com `href="index.html"`, rótulo acessível `Voltar ao menu inicial` e texto `← Menu`.
- A nova apresentação já usa tons azul/cinza e slides próprios. Seu toolbar ocupa `top:10px;left:20px`, portanto copiar o botão fixo existente sem ajuste causaria sobreposição.

## Requisitos e aceite proporcionais

| ID | Requisito / critério |
| --- | --- |
| REQ-001 | Integrar o arquivo fornecido como Unidade 4, mantendo o padrão do curso. |
| AC-001 | Menu exibe quatro cards em ordem 1–4, total 4, título e descrição corretos, link exato para o arquivo fornecido. |
| AC-002 | Capa e título do navegador identificam Unidade 4 e o assunto; botão `← Menu` acessível retorna ao início sem sobrepor Sumário/Notas ou conteúdo em desktop/mobile. |
| AC-003 | Preservados 81 slides, conteúdos, exemplos incorporados, downloads, navegação Reveal, sumário e notas; unidades 1–3 não sofrem alteração. |
| AC-004 | Documentação de publicação inclui a Unidade 4; arquivos estáticos e links locais funcionam servidos por HTTP. |
| REQ-002 | Publicar a versão validada no repositório GitHub existente. |
| AC-005 | QA independente aprova o diff atual antes do commit/push; commit chega a `origin/main` e a disponibilidade do Pages é verificada quando acessível. |

## Decisões técnicas

1. Manter nome do HTML, conteúdo e bibliotecas incorporadas. Alterações devem ser pontuais, sem reformatar código minificado ou substituir Reveal por CDN.
2. Acrescentar um quarto card com as classes e estrutura atuais, título `Herança, classes abstratas e interfaces`, descrição breve aderente ao conteúdo e número 4. Preservar grade responsiva existente; quarta posição em nova linha segue o padrão atual.
3. Incluir identificação `Unidade 4` no título HTML e na capa, sem alterar o assunto. Adicionar link semântico para `index.html`, com aparência baseada em `.home-link` das unidades existentes e cores compatíveis com variáveis locais.
4. Integrar o retorno ao conjunto de ferramentas superior ou deslocar a toolbar com espaço explícito para o retorno. Deve haver quebra/ajuste em telas estreitas; não sobrepor controles. Ocultar retorno na impressão como a toolbar existente.
5. Atualizar somente a lista de estrutura atual de `PUBLICAR_GITHUB_PAGES.md` para incluir o HTML; manter processo existente de publicação.
6. Preservar `.nojekyll` e histórico Git. Publicação por commit e push normal, sem force; mudanças remotas divergentes devem ser comunicadas e conciliadas antes do envio.

## Validação

Coder registra verificações estruturais com parser HTML: quatro cards/links, total, retorno, identificação da unidade, 81 seções, arquivos locais existentes; comparar conteúdo de slides antes/depois para limitar alterações à capa/integração. Executar `git diff --check` e smoke HTTP do menu e da unidade.

QA valida independentemente o diff, abre menu em desktop e mobile (por exemplo, 1366×768 e 390×844), acessa a Unidade 4 pelo card, navega entre slides, abre/fecha sumário e notas e retorna pelo Menu. Exercita ao menos uma demonstração e download para detectar regressão da integração. Registra ferramentas/comandos reais, versão/diff e limitações. Sem framework de testes novo para esta alteração estática.

Após APPROVED, Coder publica e registra hash/local remoto. A evidência de push confirma GitHub; verificar também Pages, distinguindo eventual atraso ou falha de implantação do envio ao repositório.

## Handoff

Tech Lead → Coder: TASK-001 READY. Propriedade de implementação: `index.html`, `Heranca_Classes_Abstratas_Interfaces_PHP84_Reveal.html`, `PUBLICAR_GITHUB_PAGES.md` e `implementation.md`. QA possui `qa-report.md`; principal possui `workflow.md`. Nenhum especialista deve editar artefatos de outro responsável ou criar outra equipe.
