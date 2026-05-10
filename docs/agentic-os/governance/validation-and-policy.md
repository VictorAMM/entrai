# Governança, Validação e Policy-as-Code

## Evaluator-Optimizer
Toda saída crítica passa por duas funções:
1. Agente gerador
2. Agente avaliador com rubrica de qualidade, segurança e custo

## Policy-as-Code (OPA)
O pipeline deve bloquear automaticamente quando houver:
- violação de segurança
- violação de compliance
- estouro de orçamento de tokens
- risco operacional sem rollback validado

## Causal Interaction Graph (CIG)
Para incidentes e falhas multiagente:
- reconstruir cadeia causal
- executar Prune-Freeze-Repair na subárvore defeituosa
- registrar aprendizado no sistema de memória

## OWASP e Secure-by-Design
- Checklist OWASP desde o design.
- Threat modeling e anti-corruption layers para integrações sensíveis.

## KPIs de governança
- Change Failure Rate
- Taxa de bloqueio por policy
- MTTR
- Defect Density

## Correlação
- Fases: [`../phases/README.md`](../phases/README.md)
- Memória: [`../memory/knowledge-crystallization.md`](../memory/knowledge-crystallization.md)
