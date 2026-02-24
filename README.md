# MONAN-JEDI 2026

Repositório oficial do Plano Técnico 2026 para implementação estruturada do sistema JEDI + MONAN no CPTEC / DIMNT / GAD.

Este repositório consolida:

- Planejamento técnico
- Organização operacional
- Governança de execução
- Controle de marcos
- Evidências e relatórios formais

---

# 1. Estrutura Organizacional

O projeto está organizado em seis domínios técnicos paralelos, permitindo execução coordenada e redução de dependências críticas:

- **Infraestrutura & Spack**
- **Modelo Atmosférico (MPAS / MONAN)**
- **Observações**
- **Núcleo Variacional (JEDI)**
- **Avaliação & Métricas**
- **Documentação & Reprodutibilidade**

Cada domínio possui responsável formal e colaboradores definidos na Matriz RACI do projeto.

---

# 2. Princípios de Execução

A execução do projeto obedece aos seguintes princípios institucionais:

- Progressão por marcos verificáveis
- Execução paralela coordenada
- Critério objetivo de aceite
- Reprodutibilidade institucional
- Ausência de ajustes ad hoc
- Validação cruzada quando aplicável

Nenhuma fase avança sem evidência técnica documentada.

---

# 3. Milestones 2026

Os marcos técnicos do projeto são:

- [M1 – Consolidação de Ambiente](docs/milestones/M1.md)  
  (Milestone GitHub: https://github.com/joaogerd/monan-jedi-2026/milestone/1)
- [M2 – Baseline Determinístico MPAS](docs/milestones/M2.md)
- [M3 – Integração 3DVar FGAT](docs/milestones/M3.md)
- [M4 – Avaliação Formal MPAS-JEDI](docs/milestones/M4.md)
- [M5 – Transição Controlada MPAS → MONAN](docs/milestones/M5.md)
- [M6 – Consolidação MONAN-JEDI](docs/milestones/M6.md)
- [M7 – Hybrid 3DVar – Prova de Conceito](docs/milestones/M7.md)

Cada milestone possui:

- Objetivo formal
- Escopo técnico
- Critérios de aceite
- Evidências exigidas
- Relatório obrigatório de encerramento

---

# 4. Fluxo Operacional do Projeto

As atividades seguem o fluxo formal:

**Backlog → Pronto para Execução → Em Execução → Em Revisão Técnica → Em Validação → Concluído**

Uma tarefa só é considerada encerrada quando:

- Critérios de aceite forem cumpridos
- Evidências estiverem arquivadas
- Revisão técnica tiver sido realizada
- Registro formal estiver documentado

---

# 5. Cronograma Executivo 2026 – Execução Ajustada

O cronograma abaixo reflete o início formal das atividades em março de 2026.

As fases foram estruturadas para permitir execução paralela coordenada, minimizando dependências críticas e preservando rigor técnico.

```mermaid
gantt
    title MONAN-JEDI 2026 – Execução Ajustada
    dateFormat  YYYY-MM-DD

    section Infraestrutura
    Freeze Spack               :m1a, 2026-03-01, 30d
    Build Reprodutível         :m1b, after m1a, 15d

    section MPAS
    Definir Baseline           :m2a, 2026-03-15, 45d
    Estabilidade 7 dias        :m2b, after m2a, 30d

    section Observações
    Definir Pipeline IODA      :m1c, 2026-03-01, 45d
    Validação Ingestão         :m3a, 2026-06-01, 45d

    section Núcleo Variacional
    Configuração 3DVar         :m3b, 2026-06-01, 45d
    Teste FGAT                 :m3c, after m3b, 30d

    section Avaliação
    Definição Métricas         :m1d, 2026-03-01, 20d
    Avaliação MPAS-JEDI        :m4a, 2026-08-01, 60d

    section MONAN
    Integração MONAN           :m5a, 2026-10-01, 45d
    Consolidação MONAN-JEDI    :m6a, after m5a, 45d
````

---

# 6. Governança Técnica

O avanço entre fases depende exclusivamente de:

* Cumprimento de critérios técnicos
* Relatório formal de encerramento
* Validação institucional
* Registro no repositório

A coordenação técnica é responsável por autorizar formalmente a transição entre marcos.

---

# 7. Estrutura de Documentação

* `docs/milestones/` → Descrição detalhada de cada marco
* `docs/relatorios/` → Relatórios formais de encerramento
* `governance/` → Matriz RACI, critérios de avanço e políticas operacionais
* `spack/` → Configurações e locks oficiais

---

