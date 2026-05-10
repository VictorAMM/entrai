# Memória Persistente e Knowledge Crystallization

## Princípio
Sem memória, o sistema é um “amnésico brilhante”.

## Estrutura de memória
- **Semântica**: padrões, decisões, convenções estáveis.
- **Episódica**: deploys, incidentes, regressões, correções.
- **Procedural**: runbooks, SOPs e workflows de resposta.

## Persistência local
Registrar em arquivos como SKILL.md/CLAUDE.md:
- padrões aprovados
- armadilhas conhecidas
- estratégias de mitigação
- decisões arquiteturais temporais

## Tempo semântico
Cada decisão registra:
- `valid_from`
- `valid_until` (ou evento de expiração)
- `review_trigger`

## Grafo de rastreabilidade
Feature ↔ PRD ↔ RFC ↔ ADR ↔ Commit ↔ Deploy ↔ Incidente ↔ RCA

## Correlação
- Templates: [`../templates/README.md`](../templates/README.md)
- Governança: [`../governance/validation-and-policy.md`](../governance/validation-and-policy.md)
