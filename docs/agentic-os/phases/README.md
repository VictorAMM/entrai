# Fases Operacionais do Agentic SDLC OS

## Visão geral
As fases são encadeadas e possuem gates de saída. Correlação com governança: [`../governance/validation-and-policy.md`](../governance/validation-and-policy.md). Correlação com memória: [`../memory/knowledge-crystallization.md`](../memory/knowledge-crystallization.md).

## Fase 0 — Fundação e Governança
- Estabelecer stack baseline, padrões de engenharia, segurança e protocolos de ambientes.
- Criar CoE (Cloud Center of Excellence).
- Anti-pattern: discovery-first fallacy.

## Fase 1 — Discovery e Pesquisa Autônoma
- Reading Group agents + MCP para pesquisa em fontes reais.
- Sequential Thinking para decomposição de problemas.
- Falha conhecida: context leakage.

## Fase 2 — PRD Executável
- SDD: PRD dirige testes e contratos.
- PRD contém O QUÊ e PORQUÊ, nunca o COMO.
- Incertezas explícitas: `[NEEDS CLARIFICATION]`.

## Fase 3 — Technical Design e RFC Swarm
- Debate em 3 rodadas: Apresentação, Crítica, Consenso.
- Decisões em ADRs curtos com validade temporal.
- Anti-pattern: paralisia por análise.

## Fase 4 — Incepção de Ambientes e Infra
- Landing zones isoladas: Dev, Staging, Prod.
- FinOps Day 1 + orçamento de tokens.
- Paridade de ambiente obrigatória.

## Fase 5 — Implementação
- Execução em sandboxes isoladas (Docker/VM/GPU).
- Tipagem forte, modularidade, observabilidade nativa.
- Risco: paradoxo da velocidade da IA.

## Fase 6 — Validation Harness
- Evaluator-Optimizer obrigatório.
- Auditar reasoning trace e output.
- Reparo com Prune-Freeze-Repair.

## Fase 7 — Testing Swarm
- Fuzzing (ex.: RSFuzz) para robustez comportamental.
- Testes de contrato entre serviços.

## Fase 8 — Governed CI/CD
- OPA bloqueando violações automaticamente.
- Canary release e progressive rollout.

## Fase 9 — Observabilidade Nativa e AI SRE
- Dashboards agentic: alucinação, tokens/feature, latência de raciocínio.
- Alertas por impacto em SLO.

## Fase 10 — RCA Autônomo
- CIG para mapear causa raiz entre interações multiagente.
- Ligar incidente a commits, PRs e deploys.

## Fase 11 — Self-Improvement
- Recursive Knowledge Crystallization em SKILL.md.
- Atualizar memória semântica, episódica e procedural.
