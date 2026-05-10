# Framework Discovery-First para Stack (Greenfield)

## Ordem obrigatória de decisão
1. Contexto e intenção de negócio
2. Requisitos não-funcionais
3. Trade-offs entre ao menos 2 stacks
4. ADR temporal (valid_from, valid_until, review_trigger)

## Diretrizes base
- Python 3: descoberta, prototipagem rápida e pesquisa.
- Java + Spring: backend governado, APIs empresariais e escala.

## Matriz mínima de trade-off
- Complexidade operacional
- Segurança e compliance
- Performance e escalabilidade
- Custo total (infra + equipe)
- Velocidade de entrega
- Maturidade de ecossistema

## Saída obrigatória
- Recomendação técnica com rationale explícito.
- Alternativas descartadas e riscos residuais.
- Gatilhos objetivos para revisão da decisão.

## Correlação
- Fases: [`../phases/README.md`](../phases/README.md)
- Governança: [`../governance/validation-and-policy.md`](../governance/validation-and-policy.md)
- Templates ADR/RFC: [`../templates/README.md`](../templates/README.md)
