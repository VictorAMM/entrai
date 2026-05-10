# Mapa de Documentação do Agentic SDLC OS

Este índice organiza os documentos por função, dependência e ordem de consumo para aumentar coesão e reduzir ambiguidades entre artefatos.

## Ordem recomendada de leitura (vetorização de contexto)
1. **Visão de sistema**: [`../../AGENTIC_SDLC_OS_V3.md`](../../AGENTIC_SDLC_OS_V3.md)
2. **Fluxo operacional**: [`phases/README.md`](phases/README.md)
3. **Decisão de stack**: [`architecture/stack-discovery-first.md`](architecture/stack-discovery-first.md)
4. **Validação e políticas**: [`governance/validation-and-policy.md`](governance/validation-and-policy.md)
5. **Memória e cristalização**: [`memory/knowledge-crystallization.md`](memory/knowledge-crystallization.md)
6. **Templates executáveis**: [`templates/README.md`](templates/README.md)

## Mapa de relacionamentos
- **Fases** orquestram execução e gates de saída.
- **Arquitetura/Stack** fornece decisões técnicas para Fases 3 e 4.
- **Governança** aplica bloqueios e critérios de qualidade em Fases 6, 8 e 10.
- **Memória** fecha o ciclo de aprendizado para Fase 11 e retroalimenta as fases anteriores.
- **Templates** operacionalizam PRD/RFC/ADR/RCA usados ao longo de todas as fases.

## Matriz de inter-relações e meta-correlações
| Origem | Relaciona com | Tipo de correlação | Objetivo |
|---|---|---|---|
| Fases | Governança | Gate operacional | Bloquear avanço inseguro |
| Fases | Templates | Contrato de execução | Padronizar artefatos |
| Arquitetura | Governança | Restrição de decisão | Evitar stack sem compliance |
| Governança | Memória | Aprendizado de incidentes | Reduzir recorrência de falhas |
| Memória | Arquitetura | Meta-correlação temporal | Revalidar ADR por `review_trigger` |
| Templates | Memória | Evidência auditável | Garantir rastreabilidade |

## Checklist de coesão documental
- Cada documento deve conter seção **Correlação** com links relativos válidos.
- Toda decisão arquitetural deve explicitar validade temporal (`valid_from`, `valid_until`, `review_trigger`).
- Toda atualização de processo deve preservar o grafo: `Feature ↔ PRD ↔ RFC ↔ ADR ↔ Commit ↔ Deploy ↔ Incidente ↔ RCA`.
