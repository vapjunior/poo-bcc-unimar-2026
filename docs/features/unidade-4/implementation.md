# Implementação — Unidade 4

- Papel: Coder.
- Estado: READY para QA; TASK-001 implementada, sem autoaprovação.
- Vínculos: REQ-001; AC-001, AC-002, AC-003 e AC-004.
- Base: `fb8c318`, branch `main`.

## Alterações

- `index.html`: quarto card para Herança, classes abstratas e interfaces; total atualizado para quatro unidades. Mantidos os estilos e a grade responsiva existentes.
- `Heranca_Classes_Abstratas_Interfaces_PHP84_Reveal.html`: Unidade 4 identificada no título e na capa; retorno `← Menu` com nome acessível na toolbar, ao lado de Sumário e Notas. A barra usa flex com quebra e espaçamento reduzido até 420 px; a regra preexistente de impressão oculta toda a toolbar.
- `PUBLICAR_GITHUB_PAGES.md`: nova unidade incluída na estrutura atual.
- Nenhuma dependência ou migração. Fonte original preservada em `/tmp/unidade-4-original.html` para comparação independente.

## Evidências executadas

1. Script temporário Python com `html.parser.HTMLParser`: PASS para quatro cards e destinos locais existentes, total 4, retorno acessível, identificação da unidade e 81 seções. Comparação dos slides antes/depois: conteúdo idêntico após retirar apenas a identificação `Unidade 4 ·` da capa. Todos os scripts incorporados idênticos ao original. Unidades 1–3 comparadas byte a byte com `git show HEAD:<arquivo>`: intactas. Regra de impressão inclui `.toolbar`.
2. `git diff --check`: exit 0, sem erros.
3. Tentativa inicial de servidor HTTP temporário em Python: bloqueada por `PermissionError` do sandbox ao abrir socket. Tentativas de `curl` dentro do sandbox também não alcançaram o servidor elevado.
4. `python3 -m http.server 8764 --bind 127.0.0.1` executado com permissão elevada: servidor iniciado. `curl --fail --silent --show-error --output /tmp/unidade-4-http-index.html http://127.0.0.1:8764/index.html` e consulta equivalente da apresentação executados com permissão elevada, seguidos de `cmp` com os arquivos locais: exit 0, ambas as respostas íntegras.

## Versão para QA (SHA-256)

| Arquivo | SHA-256 |
| --- | --- |
| `index.html` | `4a82af448c3d4fd9547815656088bacba09090be8f43391980ae2f1bc8f39a96` |
| `Heranca_Classes_Abstratas_Interfaces_PHP84_Reveal.html` | `c19410ca16de5135d46a56c8aa0a45a7fd6110a8dfd935ff5745b40bff7f7b4c` |
| `PUBLICAR_GITHUB_PAGES.md` | `694624f5f7347afb5d8b2c3a03c4fdb721dc28daa6772028239ed1f948098079` |

## Handoff e pendências

Próximo responsável: QA, TASK-002. Validar visualmente desktop/mobile e exercitar toolbar, navegação, demonstração e download. Coder executou verificações estruturais e HTTP; não executou testes de navegador nesta rodada. Servidor local disponível na porta 8764 durante o handoff. TASK-003 (commit/push) aguarda APPROVED independente; nenhum commit ou envio realizado.
