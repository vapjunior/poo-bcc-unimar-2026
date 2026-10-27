# Tarefas — Unidade 4

## TASK-001 — Integrar Unidade 4

- Estado: DONE. Implementação entregue e encaminhada ao QA; nenhum ajuste de código foi necessário durante a validação.
- Responsável: Coder.
- Dependências: plano técnico aprovado para execução pelo principal.
- Vínculos: REQ-001; AC-001, AC-002, AC-003, AC-004.
- Arquivos: `index.html`, `Heranca_Classes_Abstratas_Interfaces_PHP84_Reveal.html`, `PUBLICAR_GITHUB_PAGES.md`, `docs/features/unidade-4/implementation.md`.
- Execução: quarto card e total; identificação de Unidade 4; retorno Menu sem colisão com toolbar, responsivo e oculto na impressão; lista documental atualizada; preservar apresentação fornecida e unidades anteriores.
- Conclusão: verificações estruturais e HTTP executadas, `git diff --check` sem erros, relatório com comandos/resultados e diff pronto para QA. Não fazer commit/push antes do QA.

## TASK-002 — Validar independentemente

- Estado: DONE / APPROVED, conforme `qa-report.md`, para o diff e hashes ali registrados.
- Responsável: QA.
- Arquivo: `docs/features/unidade-4/qa-report.md`.
- Vínculos: AC-001 a AC-004 e pré-condição de AC-005.
- Execução: revisar diff atual, links e contagem de slides; validar visual desktop/mobile, card → apresentação → Menu, sumário/notas, navegação, demonstração e download. Registrar comandos reais, versão/diff, resultados e testes não executados.
- Conclusão: APPROVED aplicável ao diff atual ou CHANGES_REQUIRED com BUGs concretos para Tech Lead criar tarefas corretivas.
- Evidência encaminhada pelo principal: validação desktop/mobile concluída. Limitação preexistente no modo scroll mobile do Reveal: selecionar item do sumário fecha o overlay, mas `getIndices()` permaneceu em `h=1`; JavaScript correspondente é idêntico ao arquivo fornecido. A avaliação e os detalhes finais pertencem ao relatório QA.

## TASK-003 — Publicar no GitHub

- Estado: READY. Pré-condição APPROVED de TASK-002 atendida; publicar exatamente a implementação validada pelo QA.
- Responsável: Coder, coordenado pelo principal.
- Vínculos: REQ-002, AC-005.
- Execução: conferir estado remoto, criar commit dos arquivos autorizados e artefatos, push normal para `origin/main`, confirmar hash remoto e disponibilidade do Pages se acessível.
- Conclusão: hash, remoto, resultado do push e verificação de publicação registrados em `implementation.md`; limitações de Pages explícitas. Alteração posterior no código exige QA pertinente antes de publicar.
