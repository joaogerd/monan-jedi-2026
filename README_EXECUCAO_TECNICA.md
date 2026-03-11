# MONAN-JEDI 2026 - Execução Técnica

Este documento descreve como a execução técnica do projeto funciona na prática. O board do GitHub é o instrumento oficial de acompanhamento. 

>[!Warning]
> Não são utilizados controles paralelos.

## 1. Onde está o board

Repositório → Aba **Projects**
Projeto: **MONAN-JEDI 2026 – Execução Técnica**

Todas as atividades oficiais estão registradas ali.

🔗 [Link para o board do projeto](https://github.com/orgs/GAD-DIMNT-CPTEC/projects/4).

## 2. Estrutura do Projeto

O projeto está organizado em Milestones:

- [M1 - Consolidação Institucional de Ambiente e Governança de Build](https://github.com/GAD-DIMNT-CPTEC/monan-jedi-2026/milestone/1)
- [M2 - Baseline Determinístico MPAS Oficial (mpas-jedi)](https://github.com/GAD-DIMNT-CPTEC/monan-jedi-2026/milestone/2)
- [M3 - Integração 3DVar FGAT com MPAS-JEDI (Pacote Oficial)](https://github.com/GAD-DIMNT-CPTEC/monan-jedi-2026/milestone/3)
- [M4 - Avaliação Formal MPAS-JEDI (Validação Pré-Transição)](https://github.com/GAD-DIMNT-CPTEC/monan-jedi-2026/milestone/4)
- [M5 - Transição Controlada MPAS → MONAN](https://github.com/GAD-DIMNT-CPTEC/monan-jedi-2026/milestone/5)
- [M6 - Consolidação MONAN-JEDI (Estabilidade Institucional)](https://github.com/GAD-DIMNT-CPTEC/monan-jedi-2026/milestone/6)
- [M7 - Hybrid 3DVar (Prova de Conceito Controlada)](https://github.com/GAD-DIMNT-CPTEC/monan-jedi-2026/milestone/7)

Cada milestone possui issues com:

- 👤 Responsável principal
- 👥 Colaboradores
- 📋 Checklist técnico
- 🚦Critério objetivo de conclusão
- 🔁 Dependências explícitas

## 3. Fluxo obrigatório de Status

Toda issue deve seguir exatamente esta sequência:

* 📝 Todo  
* 🔵 Pronto para Execução  
* 🟢 Em Execução  
* 🟡 Em Revisão Técnica  
* 🟣 Em Validação  
* ✅ Concluído  

> [!Warning]
> Nenhuma issue pode pular etapa.

## 4. Como iniciar uma issue 🤔

1. Localizar a issue no board
2. Alterar o Status para **🟢 Em Execução**
3. Criar branch (se aplicável)
4. Iniciar organização de diretórios conforme padrão institucional
5. Registrar decisões técnicas nos comentários da issue

## 5. Evidência obrigatória antes de revisão

⚠️ Antes de mover para **🟡 Em Revisão Técnica**, é obrigatório:

- Logs arquivados em `/logs/Mx/`
- Scripts versionados
- Relatório técnico em `/docs/relatorios/`
- Checklist totalmente marcado

👉 Sem evidência, a issue não avança.

## 6. Regras de Execução

- Máximo de 2 issues simultâneas por pessoa
- Nenhuma issue de M3 inicia antes do encerramento formal de M2
- Nenhuma transição MPAS → MONAN ocorre sem relatório consolidado
- O board deve refletir o estado real do trabalho

## 7. Governança

A conclusão de uma milestone exige:

- Evidência técnica documentada
- Revisão técnica realizada
- Validação institucional registrada
- Relatório versionado

> [!Note]
> Este projeto é institucional e deve ser auditável
> A execução técnica é guiada pelo board
> Dúvidas devem ser registradas nas próprias issues para manter histórico técnico
