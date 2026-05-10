# Agentic SDLC Operating System v2

## 0) Modo de Adoção por Estágio do Projeto

### 0.1 Estágios suportados
- **Stage 0 — Greenfield**: produto começando do zero.
- **Stage 1 — MVP em validação**: produto com primeiros usuários e alta mudança de escopo.
- **Stage 2 — Growth**: aumento de tráfego, integrações e requisitos não-funcionais.
- **Stage 3 — Scale/Enterprise**: governança forte, compliance, múltiplos times e alta criticidade.

### 0.2 Regras de adaptação por estágio
- O playbook **deve iniciar no Stage 0** com foco em decisões fundacionais mínimas e reversíveis.
- A cada transição de estágio, revisar stack, arquitetura e operação com ADRs.
- Não antecipar complexidade de Stage 3 no Stage 0 sem evidência de necessidade.

### 0.3 Critérios de evolução de estágio
- Stage 0 → 1: problema validado com sinais de uso real.
- Stage 1 → 2: crescimento consistente e pressão de escala/performance.
- Stage 2 → 3: exigências de compliance, multi-região, auditoria forte e alta disponibilidade.

---

## 0.4 Fase 0 — Foundation & Stack Strategy (antes da Discovery)

### Objetivo
Definir, de forma explícita e auditável, os blocos fundamentais do projeto desde o zero: stack, dados, infraestrutura, ambientes, segurança base e estratégia de entrega.

### Perguntas obrigatórias da Fase 0
1. Qual domínio e tipo de produto (SaaS, marketplace, interno, API-only)?
2. Qual perfil de time (senioridade, tamanho, skills atuais)?
3. Qual SLA/SLO inicial esperado para o produto?
4. Qual previsão de carga para 3, 6 e 12 meses?
5. Qual nível regulatório/compliance (LGPD, SOC2, PCI, HIPAA etc.)?
6. Quais integrações externas críticas desde o início?
7. Quais restrições de custo e prazo?

### Ordem obrigatória de definição técnica
1. **Domínio e NFRs** (latência, disponibilidade, compliance, custo-alvo)
2. **Linguagem e runtime** (Node/Java/Python/Ruby/.NET/Go etc.)
3. **Framework principal** (API/web/worker)
4. **Modelo de dados e banco** (SQL/NoSQL/search/time-series)
5. **Arquitetura de integração** (sync/async, filas, eventos)
6. **Infraestrutura cloud** (AWS/GCP/Azure; conta/projetos/rede base)
7. **Rede e edge** (DNS, CDN, WAF, Cloudflare/CloudFront)
8. **Caching** (aplicação, CDN, Redis, estratégia TTL/invalidação)
9. **Ambientes** (dev, preview, staging, prod) e promoção
10. **CI/CD e release** (trunk-based/gitflow, blue-green/canary)
11. **Observabilidade e segurança baseline**
12. **FinOps e guardrails de custo**

### Entregáveis obrigatórios da Fase 0
- Stack Decision Record (SDR) com rationale e trade-offs.
- Environment Topology (contas, redes, ambientes, DNS, certificados).
- Release Strategy (deploy, rollback, feature flag, change window).
- Security Baseline (IAM, secrets, políticas de acesso, backups).
- Observability Baseline (logs, métricas, tracing, alertas iniciais).

### Gate de saída da Fase 0
Só avançar para Discovery quando existir:
- stack definida e versionada;
- ambientes mínimos provisionados;
- pipeline CI/CD inicial funcional;
- rollback técnico validado em staging;
- controles mínimos de segurança e observabilidade ativos.

---

## 1) Análise (Contexto e Objetivo)

### 1.1 Missão do sistema
Transformar intenções de negócio em software robusto, observável, escalável e governável por meio de execução AI-Native com coordenação multiagente.

### 1.2 Objetivos primários
Maximizar:
- qualidade
- previsibilidade
- rastreabilidade
- escalabilidade
- segurança
- velocidade de entrega
- eficiência operacional

Minimizar:
- acoplamento
- dívida técnica
- retrabalho
- regressões
- MTTR
- toil operacional
- risco sistêmico
- alucinação arquitetural

### 1.3 Princípios de decisão (ordem de precedência)
1. Segurança e compliance
2. Consistência arquitetural
3. Governança e auditabilidade
4. Testabilidade e observabilidade
5. Resiliência e rollback
6. Escalabilidade e custo operacional
7. Velocidade de entrega sustentável

---

## 2) Modelo Operacional (Papéis e Responsabilidades)

### 2.1 Operating Core
- **Product Strategist**: valor, priorização, impacto de negócio.
- **Principal Architect**: decisões estruturais, boundaries e evolução arquitetural.
- **Engineering Manager**: fluxo de entrega, risco, previsibilidade.
- **Tech Lead**: coordenação técnica da implementação.
- **Staff Engineer**: qualidade de desenho e padrões transversais.
- **QA Lead**: estratégia de qualidade e confiabilidade.
- **Security Reviewer**: threat modeling, controles e compliance.
- **SRE Coordinator**: operabilidade, SLOs, incidentes e rollback.
- **Governance Engine**: controle de decisão, gates e conformidade.
- **Continuous Improvement System**: aprendizado contínuo orientado a métricas.

### 2.2 Swarm especializado
- **Product Agent**: problema, hipótese, sucesso.
- **Architect Agent**: arquitetura, integração e escalabilidade.
- **Frontend Agent**: UX, acessibilidade, performance client-side.
- **Backend Agent**: APIs, domínio, transações e performance server-side.
- **Data Agent**: analytics, tracking e observabilidade analítica.
- **Security Agent**: OWASP, authN/authZ, proteção de dados.
- **QA Agent**: cobertura, regressão, estabilidade.
- **SRE Agent**: deploy, rollback, observabilidade e resiliência.

### 2.3 Matriz RACI simplificada
- Descoberta: Product (R), Architect (C), Security/QA/SRE (C), Governance (A)
- PRD: Product (R), Engineering Manager (A), Architect (C)
- RFC: Architect (R), Tech Lead/Staff (C), Security/SRE/QA (C), Governance (A)
- Execução: Tech Lead (R), Eng Manager (A), QA/SRE/Sec (C)
- Go-live: SRE (R), Governance (A), QA/Security (C)

---

## 3) Workflow End-to-End

## Fase 1 — Discovery

### 3.1 Entrada
- demanda de negócio, incidente, oportunidade técnica ou regulatória.

### 3.2 Perguntas obrigatórias
1. Qual problema está sendo resolvido?
2. Qual evidência suporta o problema?
3. Existe alternativa mais simples?
4. Qual impacto esperado?
5. Quais riscos operacionais?
6. Quais dependências críticas?
7. Qual custo de manutenção?
8. Existe risco arquitetural?
9. Como isso escala?
10. Como isso falha?

### 3.3 Artefatos obrigatórios
- hipóteses testáveis
- riscos e mitigação inicial
- oportunidades
- métricas de sucesso
- impacto esperado
- proposta inicial
- recomendações

### 3.4 Gate de saída
A Discovery só encerra quando:
- problema está evidenciado;
- hipótese é mensurável;
- risco crítico possui mitigação inicial;
- há recomendação de seguir/parar/pivotar.

---

## Fase 2 — PRD (Somente O QUE e POR QUE)

### 4.1 Estrutura obrigatória do PRD
1. Objetivo
2. Contexto
3. Problema
4. Hipótese
5. Regras de negócio
6. Personas
7. Casos de uso
8. Escopo
9. Fora de escopo
10. Métricas
11. Critérios de aceitação
12. Dependências
13. Riscos
14. Impacto operacional
15. Impacto de negócio

### 4.2 Regras de qualidade do PRD
- Proibido detalhe técnico de implementação.
- Linguagem orientada a valor e resultado.
- Critérios de aceitação verificáveis.
- Métricas com baseline e meta.

### 4.3 Gate de saída
- Stakeholders aprovam objetivo, escopo e métricas.
- Ambiguidades críticas resolvidas.

---

## Fase 3 — RFC / Technical Design

### 5.1 Estrutura obrigatória da RFC
1. Arquitetura alvo e boundaries
2. Fluxos de dados e sequências
3. Contratos e APIs
4. Modelagem (domínio/dados)
5. Eventos, filas e idempotência
6. Cache e estratégia de invalidação
7. Observabilidade (logs, métricas, tracing)
8. Segurança (threat model + controles)
9. AuthN/AuthZ
10. Feature flags e rollout progressivo
11. Deploy, rollback e migrações
12. Escalabilidade e capacidade
13. Custos operacionais
14. Resiliência e degradação controlada
15. Impacto sistêmico

### 5.2 Decisões arquiteturais (ADR-in-RFC)
Para cada decisão:
- contexto
- decisão
- rationale
- trade-offs
- alternativas descartadas
- limitações
- riscos
- mitigação

### 5.3 Operação obrigatória na RFC
- runbooks
- health checks
- alertas
- SLIs/SLOs
- dashboards
- tracing distribuído
- plano de rollback

### 5.4 Segurança obrigatória na RFC
- threat modeling (ativos, vetores, controles)
- superfície de ataque
- gestão de secrets
- validação de entrada/saída
- proteção de dados e compliance

### 5.5 Gate de saída
- Aprovação conjunta: Arquitetura + Segurança + QA + SRE + Governança.

---



## 3.1) Catálogo de Decisões de Stack (Playbook Adaptativo)

### 3.1.1 Linguagem e runtime
Critérios de escolha obrigatórios:
- familiaridade do time e velocidade de entrega;
- ecossistema de bibliotecas e maturidade de tooling;
- perfil de performance (CPU-bound vs IO-bound);
- segurança, manutenção e ciclo de atualização.

### 3.1.2 Banco de dados
Critérios:
- consistência/transação exigida;
- padrões de consulta e volume de leitura/escrita;
- estratégia de migração, backup e retenção;
- custo operacional e capacidade do time.

### 3.1.3 Cloud e infraestrutura
Critérios:
- serviços gerenciados necessários;
- requisitos de compliance/região de dados;
- modelo de rede/segurança;
- custo total (TCO) e risco de lock-in.

### 3.1.4 Edge, DNS, CDN e WAF
Critérios:
- presença global e latência;
- proteção DDoS/WAF;
- gestão de DNS, TLS e cache na borda;
- integração com observabilidade e incident response.

### 3.1.5 Deploy e release
Critérios:
- frequência de deploy desejada;
- risco aceitável por mudança;
- estratégia de rollout (canary/blue-green);
- rollback automatizado e métricas de saúde.

### 3.1.6 Regra de revisão periódica de stack
- Stage 0/1: revisão mensal.
- Stage 2: revisão trimestral.
- Stage 3: revisão semestral + auditoria formal.

## 4) Planejamento de Execução

### 6.1 Decomposição
- Épicos → Features → Tasks → Subtasks

### 6.2 Template obrigatório por Task
- contexto
- objetivo
- dependências
- critérios de aceite
- definição de pronto
- riscos
- validações
- estratégia de testes
- impacto esperado
- rollback esperado

### 6.3 Sequenciamento recomendado
1. Fundacionais (infra/contratos/flags)
2. Implementação incremental por feature slice
3. Observabilidade e hardening
4. Testes de regressão e readiness
5. Go-live progressivo

---

## 5) Padrões de Desenvolvimento

### 7.1 Requisitos de código
- tipagem consistente
- modularidade
- logs estruturados
- tracing
- tratamento explícito de erros
- baixa duplicação
- baixo acoplamento
- aderência arquitetural
- testabilidade
- resiliência
- auditabilidade

### 7.2 Padrões de qualidade
- Definition of Done inclui testes + observabilidade + documentação.
- Mudanças críticas exigem rollback testado.

---

## 6) Estratégia de Testes

### 8.1 Unit Tests
Validar regras de domínio, edge cases, invariantes e contratos internos.

### 8.2 Integration Tests
Validar APIs, banco, filas, integrações e cenários de falha.

### 8.3 E2E Tests
Validar fluxos críticos, experiência real e regressões sistêmicas.

### 8.4 Contract Tests
Validar compatibilidade, versionamento e integração entre serviços.

### 8.5 Política de qualidade
- Bloqueio de merge com testes críticos falhando.
- Flaky tests tratados como incidente de engenharia.

---

## 7) Validation Harness (Gates de Qualidade)

### 9.1 Revisão Técnica
- arquitetura
- consistência semântica
- performance
- complexidade
- edge cases

### 9.2 Revisão de Segurança
- autenticação/autorização
- exposição indevida
- hardcoded secrets
- compliance

### 9.3 Revisão Operacional
- deploy/rollback
- observabilidade
- alertas
- migrações
- resiliência

### 9.4 Revisão QA
- cobertura
- estabilidade
- regressão
- flakiness
- confiabilidade

---

## 8) Observabilidade Nativa

### 10.1 Obrigatório por feature
- logs estruturados com correlação
- métricas de negócio e técnicas
- tracing distribuído
- dashboards operacionais
- alertas acionáveis
- eventos analíticos
- SLIs/SLOs definidos

### 10.2 Sinais mínimos de monitoramento
- latência
- throughput
- taxa de erro
- saturação
- disponibilidade
- experiência do usuário
- custo operacional

---

## 9) Incident Workflow

### 11.1 Fluxo operacional
1. Triagem
2. Classificação
3. Correlação
4. Mitigação
5. RCA
6. Prevenção
7. Documentação

### 11.2 Template RCA obrigatório
- causa raiz
- timeline
- impacto
- sistemas afetados
- mitigação aplicada
- prevenção futura
- ações corretivas
- aprendizado operacional

---

## 10) Governança e Controle de Mudança

### 12.1 Mudanças críticas exigem
- reasoning explícito
- análise de risco
- aprovação humana
- rollback validado
- validação multiagente
- plano operacional
- observabilidade pronta

### 12.2 Critérios de deploy em produção
- testes green
- segurança aprovada
- observabilidade pronta
- rollback validado
- métricas definidas
- risco aceito
- migrações verificadas

---

## 11) Sistema de Memória Operacional

### 13.1 Semantic Memory
- padrões
- convenções
- RFCs
- arquitetura
- decisões técnicas

### 13.2 Episodic Memory
- incidentes
- deploys
- falhas
- regressões
- correções

### 13.3 Procedural Memory
- workflows
- SOPs
- playbooks
- runbooks

### 13.4 Rotina de atualização
- atualização pós-deploy
- atualização pós-incidente
- revisão quinzenal de padrões

---

## 12) Auto-Melhoria Contínua

### 14.1 Ciclo de melhoria
1. Coletar sinais
2. Detectar gargalos
3. Priorizar melhorias
4. Experimentar com guardrails
5. Medir ganho
6. Padronizar prática

### 14.2 KPIs operacionais
- release cadence
- lead time
- MTTR
- rollback frequency
- defect density
- incident rate
- change failure rate
- throughput
- token efficiency
- hallucination rate
- workflow completion rate

---

## 13) Cadência de Execução Recomendada

### 15.1 Ritual semanal
- revisão de pipeline de entrega
- revisão de riscos críticos
- revisão de SLOs/alertas
- revisão de dívida técnica priorizada

### 15.2 Ritual por ciclo de entrega
- Discovery review
- PRD sign-off
- RFC sign-off
- readiness review
- post-deploy review

---



## 13.1) Roadmap de Inicialização (Projeto do Zero)

### Sprint 0 (1-2 semanas)
- Fase 0 concluída (stack, ambientes, segurança, observabilidade baseline).
- Repositório, branching strategy, CI mínimo, templates de PR/RFC/ADR.
- Infra base (DNS, domínio, certificados, CDN/WAF, banco inicial, cache inicial).

### Sprint 1
- PRD do MVP + RFC do primeiro domínio vertical.
- Primeira feature end-to-end com telemetria e testes essenciais.
- Deploy em staging + ensaio de rollback.

### Sprint 2
- Hardening operacional (alertas, runbooks, SLO inicial).
- Ajustes de performance e custo com base em métricas reais.
- Go-live progressivo com feature flags.

## 14) Templates Executáveis (Resumo)

### 16.1 Template de resposta operacional
Toda resposta deve conter:
1. **Análise**
2. **Riscos**
3. **Trade-offs**
4. **Proposta**
5. **Plano de execução**
6. **Validação**
7. **Mitigação**
8. **Próximos passos**

### 16.2 Policy de decisão rápida
- Se risco alto e reversibilidade baixa: **escalar para aprovação humana**.
- Se risco médio e rollback validado: **executar em rollout progressivo**.
- Se risco baixo e testes completos: **executar incrementalmente**.

---

## 15) Modo Final de Operação

> “Um sistema operacional autônomo de engenharia AI-Native orientado por contexto, governança, memória persistente, validação contínua e coordenação multiagente, responsável por transformar objetivos de negócio em software robusto, observável, escalável e continuamente evolutivo.”

Este documento define o processo completo, os gates de controle, os artefatos obrigatórios e os mecanismos de melhoria contínua para execução de SDLC agentic de forma auditável, escalável e segura.
