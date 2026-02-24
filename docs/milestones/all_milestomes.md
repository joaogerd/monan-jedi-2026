# M1 – Consolidação Institucional de Ambiente e Governança de Build

## Período
Data de início: 02/03/2026
Data de término: 30/04/2026
Duração estimada: 8 semanas

## Objetivo
Estabelecer ambiente institucionalmente reproduzível para compilação e execução do `mpas-jedi` na infraestrutura JACI, utilizando Spack como ferramenta oficial de gerenciamento de dependências, com ambiente congelado, versionado e validado via PBS.

## Justificativa Técnica
Conforme definido na Fase 1 do Plano Técnico 2026 , não existe reprodutibilidade científica sem ambiente congelado e validado. A arquitetura JEDI impõe dependências extensas (NetCDF, HDF5, Boost, ecbuild, eckit, fckit, yaml-cpp, MPI, etc.), cuja inconsistência compromete estabilidade, rastreabilidade e integração futura com MPAS/MONAN.

## Escopo

### Incluído:

* Definição formal do stack (compilador, MPI e bibliotecas científicas)
* Criação de `spack.yaml` institucional
* Concretização controlada e geração de `spack.lock`
* Padronização de build exclusivamente via PBS
* Versionamento de scripts de build
* Arquivamento estruturado de logs
* Documentação oficial do processo

### Explicitamente Excluído:

* Execução científica de experimentos
* Rodadas determinísticas do MPAS
* Integração variacional
* Ajustes físicos ou científicos

## Critérios de Pronto (Definition of Done)

* Ambiente pode ser recriado integralmente a partir do `spack.lock`
* `mpas-jedi` compila via PBS sem intervenção manual
* Executável mínimo funcional é gerado
* Logs de build estão arquivados e versionados
* Processo é reproduzido por pelo menos dois membros além do responsável principal

## Dependências Técnicas

* Acesso estável à infraestrutura JACI
* Acesso a PBS funcional
* Repositório institucional criado
* Versão oficial do `mpas-jedi` definida (ASSUNÇÃO: utilização do pacote oficial NCAR/JCSDA)

## Encadeamento Temporal

Primeira milestone estruturante.
É pré-condição obrigatória para:

* M2 – Baseline Determinístico MPAS
* M3 – Integração 3DVar FGAT

Sem congelamento de ambiente, nenhuma fase científica poderá iniciar.

## Frentes Paralelas Internas

### Infraestrutura & Spack

* Definição do stack
* Concretização do ambiente
* Testes de compilação
* Diagnóstico de conflitos

### MONAN/MPAS

* Levantamento de requisitos de compilação
* Teste de linking com bibliotecas científicas
* Validação preliminar de execução mínima

### Observações

* Definição de requisitos de IODA/UFO
* Validação de dependências necessárias para futura conversão

### Núcleo Variacional

* Validação de compilação dos módulos OOPS, SABER, UFO
* Testes de geração de binários variacionais

### Avaliação e Métricas

* Definição de estrutura de armazenamento de logs
* Padronização de coleta de métricas de build

### Documentação & Reprodutibilidade

* Manual interno de Spack
* Guia oficial de ativação
* Checklist formal de validação
* Registro formal de decisões de versão

Nenhuma área permanece ociosa: todas trabalham simultaneamente na validação estrutural do ambiente.

## Responsável Primário
Rodrigo Braz

## Colaboradores
Joao Gerd Zell de Mattos
Eder Vendrasco
Carlos Bastarz
Luiz Fernando Sapucci
Liviany Viana

## Artefatos Esperados

* `spack.yaml` versionado
* `spack.lock` congelado
* Scripts PBS versionados
* Executável `mpas-jedi` funcional
* Logs completos de build
* Documento técnico de congelamento do ambiente
* Relatório formal de validação cruzada

# M2 – Baseline Determinístico MPAS Oficial (mpas-jedi)

## Período
Data de início: 04/05/2026
Data de término: 29/05/2026
Duração estimada: 4 semanas

## Objetivo
Executar o MPAS-A determinístico utilizando exclusivamente o pacote oficial `mpas-jedi` disponibilizado pelo NCAR/JCSDA, validando estabilidade numérica, coerência de configuração e performance computacional antes da ativação do ciclo variacional.

## Justificativa Técnica
Conforme definido na Fase 2 do Plano Técnico 2026 , é necessário estabelecer um baseline determinístico formal antes da introdução da assimilação. Sem referência controlada do comportamento do modelo em ambiente congelado, não é possível avaliar impacto variacional de forma confiável.

## Escopo

### Incluído:

* Execução determinística com MPAS-A oficial
* Rodadas de 6–12h (teste curto)
* Execução contínua por 3 dias
* Execução contínua por 7 dias
* Medição sistemática de performance (CPU, memória, I/O)
* Versionamento de namelists e parâmetros físicos
* Registro formal de métricas

### Explicitamente Excluído:

* Integração variacional
* Ativação do 3DVar FGAT
* Uso do MONAN
* Ajustes científicos avançados

## Critérios de Pronto (Definition of Done)

* MPAS executa 7 dias consecutivos sem blow-up
* Logs completos versionados
* Relatório formal de performance produzido
* Namelists e configurações versionadas
* Métricas de CPU, memória e I/O documentadas
* Execução reproduzida por pelo menos dois membros

## Dependências Técnicas

* M1 concluída e ambiente congelado
* Executável `mpas-jedi` funcional
* Scripts PBS padronizados
* Dados iniciais disponíveis (ASSUNÇÃO: uso de análise GFS como condição inicial, conforme prática corrente descrita no manual )

## Encadeamento Temporal

Depende integralmente de M1.
É pré-condição obrigatória para:

* M3 – Integração 3DVar FGAT
* M4 – Avaliação Formal

Não será permitido iniciar ciclo variacional sem baseline determinístico documentado.

## Frentes Paralelas Internas

### Infraestrutura & Spack

* Ajuste fino de performance
* Diagnóstico de gargalos MPI
* Testes de filesystem
* Otimização de scripts PBS

### MONAN/MPAS

* Configuração de malha
* Ajuste de namelists
* Diagnóstico de instabilidade numérica
* Medição de escalabilidade

### Observações

* Preparação inicial de estrutura IODA (sem ativar assimilação)
* Testes de leitura de arquivos de estado
* Definição preliminar de pipeline futuro

### Núcleo Variacional

* Teste de integração mínima (sem ativar minimização)
* Validação de compatibilidade de versão
* Preparação de templates YAML

### Avaliação e Métricas

* Implementação da coleta automática de métricas
* Estruturação de scripts de análise de performance
* Registro padronizado de estatísticas de execução

### Documentação & Reprodutibilidade

* Relatório técnico do baseline
* Checklist formal de estabilidade
* Documento de referência para comparação futura

Nenhuma área permanece inativa: enquanto MPAS executa, as demais estruturam instrumentos necessários para a próxima fase.

## Responsável Primário
Eder Vendrasco

## Colaboradores
Carlos Bastarz
Rodrigo Braz
Joao Gerd Zell de Mattos
Liviany Viana

## Artefatos Esperados

* Relatório formal de baseline determinístico
* Logs completos de execução 7 dias
* Métricas de performance consolidadas
* Namelists versionadas
* Documento de estabilidade técnica

# M3 – Integração 3DVar FGAT com MPAS-JEDI (Pacote Oficial)

## Período
Data de início: 01/06/2026
Data de término: 31/07/2026
Duração estimada: 8 semanas

## Objetivo
Executar ciclo completo de assimilação 3DVar FGAT utilizando MPAS-A oficial acoplado ao JEDI, com pipeline observacional estruturado (IODA + UFO), configuração variacional versionada e execução contínua estável por 7 dias consecutivos.

## Justificativa Técnica
Conforme estabelecido na Fase 3 do Plano Técnico 2026 , a consolidação do 3DVar FGAT representa etapa crítica para validação da arquitetura modular (OOPS + UFO + IODA + SABER). A continuidade metodológica com 3DVar reduz variáveis técnicas simultâneas e permite transição controlada do GSI para o JEDI .

## Escopo

### Incluído:

* Conversão de observações convencionais para IODA (radiossondas, SYNOP, Aircraft)
* Configuração de QC via UFO
* Geração automática de relatório por ciclo (lidas, rejeitadas, assimiladas)
* Configuração YAML do ciclo 3DVar FGAT
* Definição da janela de assimilação
* Configuração inicial de SABER (background error estático)
* Execução controlada (testes curtos)
* Execução contínua por 3 dias
* Execução contínua por 7 dias
* Registro da função custo por iteração

### Explicitamente Excluído:

* Uso de MONAN
* Assimilação de radiâncias
* Hybrid 3DVar
* Ajustes científicos avançados de física

## Critérios de Pronto (Definition of Done)

* Pipeline IODA automatizado e versionado
* QC via UFO documentado e reprodutível
* Relatório automático de ingestão por ciclo
* Minimização converge consistentemente
* Função custo rastreável por iteração
* Execução contínua de 7 dias sem intervenção manual
* Métricas O–B e O–A estáveis
* Logs estruturados e versionados

## Dependências Técnicas

* M1 concluída (ambiente congelado)
* M2 concluída (baseline determinístico estável)
* Dados observacionais disponíveis (ASSUNÇÃO: disponibilidade institucional de dados convencionais já utilizados no GSI)
* Estrutura de armazenamento definida

## Encadeamento Temporal

### Depende de:

* M1 – Consolidação de Ambiente
* M2 – Baseline Determinístico

### É pré-condição obrigatória para:

* M4 – Avaliação Formal MPAS-JEDI
* M5 – Transição para MONAN

## Frentes Paralelas Internas

### Infraestrutura & Spack

* Monitoramento de estabilidade de execução
* Ajustes de escalabilidade
* Otimização de I/O
* Controle de versões do ambiente

### MONAN/MPAS

* Fornecimento consistente do estado de background
* Diagnóstico de estabilidade pós-análise
* Monitoramento de impacto variacional

### Observações

* Implementação do pipeline IODA
* Configuração de QC via UFO
* Automação de relatórios de ingestão
* Rastreabilidade completa das observações

### Núcleo Variacional

* Configuração YAML do 3DVar FGAT
* Ajuste inicial de background error
* Monitoramento da função custo
* Diagnóstico de convergência

### Avaliação e Métricas

* Cálculo sistemático de O–B e O–A
* Análise de convergência por iteração
* Monitoramento de estabilidade inter-ciclos
* Registro estatístico estruturado

### Documentação & Reprodutibilidade

* Versionamento de todos os YAML
* Manual do pipeline observacional
* Relatório técnico de estabilidade
* Registro formal de decisões variacionais

Nenhuma área permanece ociosa: Observação constrói pipeline enquanto Variacional configura ciclo, MPAS fornece estado, Infraestrutura monitora estabilidade e Avaliação estrutura métricas.

## Responsável Primário
Joao Gerd

## Colaboradores
Carlos Bastarz
Luiz Fernando Sapucci
Sergio Henrique Ferreira
Eder Vendrasco
Liviany Viana

## Artefatos Esperados

* YAML variacional versionado
* Pipeline IODA automatizado
* Relatórios de ingestão por ciclo
* Logs completos de minimização
* Métricas O–B e O–A consolidadas
* Relatório técnico formal da integração 3DVar FGAT

# M4 – Avaliação Formal MPAS-JEDI (Validação Pré-Transição)

## Período
Data de início: 03/08/2026
Data de término: 28/08/2026
Duração estimada: 4 semanas

## Objetivo
Realizar avaliação técnica formal e documentada do sistema MPAS-JEDI com 3DVar FGAT, validando estabilidade operacional, convergência variacional, comportamento estatístico e reprodutibilidade institucional antes da transição para MONAN.

## Justificativa Técnica
Conforme definido na Fase 4 do Plano Técnico 2026 , a transição para MONAN não poderá ser iniciada sem relatório técnico formal que comprove estabilidade ≥95%, convergência consistente e reprodutibilidade completa. A consolidação não é declarada por execução pontual, mas por evidência técnica mensurável .

## Escopo

### Incluído:

* Avaliação estatística sistemática (O–B, O–A, RMSE)
* Análise da função custo e termos variacionais
* Avaliação de convergência por iteração
* Verificação da taxa de sucesso dos ciclos
* Análise de estabilidade inter-ciclos
* Avaliação formal de performance computacional
* Teste de reprodutibilidade por múltiplos membros
* Produção de relatório técnico institucional

### Explicitamente Excluído:

* Alteração de física do modelo
* Introdução de novas observações
* Transição para MONAN
* Introdução de radiâncias
* Hybrid 3DVar

## Critérios de Pronto (Definition of Done)

* ≥ 95% dos ciclos executam sem falha técnica
* Função custo apresenta convergência consistente
* Estatísticas O–B e O–A estáveis temporalmente
* Nenhum ajuste ad hoc necessário entre ciclos
* Ambiente reproduzido por pelo menos dois membros
* Relatório técnico completo aprovado pelo coordenador
* Logs e métricas arquivados e versionados

## Dependências Técnicas

* M1 concluída
* M2 concluída
* M3 concluída com execução contínua validada
* Ferramentas diagnósticas estruturadas (readDiag adaptada ou equivalente)

## Encadeamento Temporal

Depende integralmente de M3.
É pré-condição obrigatória para:

* M5 – Transição Controlada MPAS → MONAN

Sem relatório técnico formal aprovado, a migração para MONAN não será autorizada.

## Frentes Paralelas Internas

### Infraestrutura & Spack

* Validação final de reprodutibilidade do ambiente
* Teste de reinstalação limpa
* Auditoria de dependências

### MONAN/MPAS

* Monitoramento de estabilidade pós-análise
* Validação de consistência física do ciclo
* Verificação de impacto variacional

### Observações

* Avaliação da taxa de assimilação
* Análise de rejeição por tipo de observação
* Verificação de rastreabilidade

### Núcleo Variacional

* Análise detalhada da função custo
* Avaliação de comportamento de termos variacionais
* Diagnóstico de convergência por iteração

### Avaliação e Métricas

* Cálculo consolidado de O–B, O–A e RMSE
* Análise temporal de estabilidade
* Estruturação de gráficos e relatórios
* Consolidação estatística formal

### Documentação & Reprodutibilidade

* Relatório técnico institucional completo
* Registro formal de decisão de transição
* Atualização do repositório com evidências
* Checklist de consolidação preenchido

Nenhuma área permanece inativa: todas participam da auditoria técnica e validação cruzada.

## Responsável Primário
Liviany Viana

## Colaboradores
Helena Azevedo
Luiz Fernando Sapucci
Caroline Viezel
Joao Gerd Zell de Mattos
Carlos Bastarz
Eder Vendrasco

## Artefatos Esperados

* Relatório técnico formal MPAS-JEDI
* Estatísticas consolidadas O–B e O–A
* Gráficos de convergência da função custo
* Auditoria de reprodutibilidade
* Documento formal de decisão de transição

# M5 – Transição Controlada MPAS → MONAN

## Período
Data de início: 31/08/2026
Data de término: 30/10/2026
Duração estimada: 8 semanas

## Objetivo
Substituir progressivamente o MPAS-A oficial pelo MONAN desenvolvido no CPTEC no ciclo 3DVar FGAT, validando compatibilidade estrutural, estabilidade numérica e impacto computacional, mantendo critérios técnicos equivalentes ao baseline previamente validado.

## Justificativa Técnica
Conforme definido na Fase 5 do Plano Técnico 2026 , a migração para MONAN só pode ocorrer após validação formal do MPAS-JEDI. A transição introduz nova malha, estrutura de I/O e possíveis diferenças de versão do MPAS-A, exigindo controle rigoroso para evitar aumento não diagnosticado de instabilidade .

## Escopo

### Incluído:

* Compilação do `monan-jedi` no ambiente congelado
* Execução determinística MONAN
* Execução 3DVar FGAT com MONAN
* Rodada contínua por 3 dias
* Rodada contínua por 7 dias
* Comparação técnica com baseline MPAS-JEDI
* Avaliação de impacto em performance
* Registro formal de diferenças estruturais

### Explicitamente Excluído:

* Introdução de radiâncias
* Alteração metodológica variacional
* Hybrid 3DVar
* Mudança de física do modelo

### Critérios de Pronto (Definition of Done)

* `monan-jedi` compila no ambiente institucional
* MONAN determinístico executa 7 dias sem blow-up
* Ciclo 3DVar FGAT executa 7 dias consecutivos
* Convergência consistente da minimização
* Estatísticas O–B comparáveis ao baseline
* Performance documentada e comparada
* Relatório formal de comparação MPAS vs MONAN produzido

### Dependências Técnicas

* M1 concluída
* M2 concluída
* M3 concluída
* M4 concluída com relatório aprovado
* Versão do MONAN compatível com suporte estrutural à assimilação (ASSUNÇÃO: compatibilidade confirmada com base ≥ 8.2.2 do MPAS-A conforme manual )

## Encadeamento Temporal

Depende de M4 (decisão formal de transição).
É pré-condição obrigatória para:

* M6 – Consolidação MONAN-JEDI

Sem estabilidade comprovada em 7 dias consecutivos, a fase não será considerada concluída.

## Frentes Paralelas Internas

### Infraestrutura & Spack

* Ajustes de linking específicos do MONAN
* Diagnóstico de dependências divergentes
* Testes de escalabilidade MPI

### MONAN/MPAS

* Integração da base MONAN com JEDI
* Ajuste de malha e namelists
* Diagnóstico de instabilidade numérica
* Controle de merges com MPAS-A

### Observações

* Validação de consistência do estado após análise
* Verificação de compatibilidade IODA com MONAN
* Monitoramento da taxa de assimilação

### Núcleo Variacional

* Validação de compatibilidade das interfaces
* Ajuste fino de background error se necessário
* Monitoramento de convergência

### Avaliação e Métricas

* Comparação estatística MPAS vs MONAN
* Análise de variação em O–B e O–A
* Avaliação de impacto computacional
* Relatório técnico comparativo

### Documentação & Reprodutibilidade

* Documento formal de transição
* Registro de diferenças estruturais
* Atualização de guias técnicos
* Versionamento da nova configuração

Nenhuma área permanece ociosa: todas atuam na validação cruzada da migração.

## Responsável Primário
Eder Vendrasco

## Colaboradores
Carlos Bastarz
Joao Gerd Zell de Mattos
Rodrigo Braz
Liviany Viana
Luiz Fernando Sapucci

## Artefatos Esperados

* Executável `monan-jedi` funcional
* Logs completos de execução 7 dias
* Relatório comparativo MPAS vs MONAN
* Métricas de performance consolidadas
* Documento formal de validação da transição

# M6 – Consolidação MONAN-JEDI (Estabilidade Institucional)

## Período
Data de início: 02/11/2026
Data de término: 31/12/2026
Duração estimada: 8 semanas

OBS: Dezembro e Janeiro são períodos de recesso e férias. Parte significativa do grupo estará integralmente disponível apenas a partir de 20/01/2027. O cronograma poderá ser ajustado formalmente mediante registro de decisão técnica.

## Objetivo
Consolidar o sistema MONAN-JEDI como arquitetura institucionalmente estável, reproduzível e operacionalmente controlada, garantindo estabilidade ≥95% dos ciclos, métricas estatísticas consistentes e ambiente plenamente reproduzível por múltiplos membros do grupo.

## Justificativa Técnica
Conforme definido na Fase 6 do Plano Técnico 2026 , a consolidação não é caracterizada por execução pontual, mas por estabilidade contínua, controle de versão e rastreabilidade completa . Esta fase transforma a integração validada em sistema institucional maduro.

## Escopo

Incluído:

* Execução contínua prolongada (mínimo 14 dias operacionais)
* Monitoramento sistemático da taxa de sucesso
* Auditoria completa de logs e rastreabilidade
* Validação formal de reprodutibilidade cruzada
* Consolidação das ferramentas diagnósticas
* Consolidação das métricas de performance
* Atualização final da documentação técnica
* Padronização de diretórios, scripts e fluxos

Explicitamente Excluído:

* Introdução de radiâncias
* Alteração do método variacional
* Hybrid 3DVar operacional
* Expansão de escopo científico

## Critérios de Pronto (Definition of Done)

* ≥ 95% dos ciclos executam sem falha técnica
* Função custo consistente e estável
* Estatísticas O–B e O–A estáveis temporalmente
* Performance documentada e controlada
* Ambiente reproduzido integralmente por pelo menos três membros
* Ferramentas diagnósticas versionadas
* Documentação institucional finalizada
* Relatório técnico institucional consolidado

## Dependências Técnicas

* M5 concluída com transição validada
* Ambiente congelado mantido ou atualizado de forma controlada
* Pipeline observacional plenamente funcional
* Ferramentas de avaliação consolidadas

Encadeamento Temporal

## Depende integralmente de M5.
É pré-condição obrigatória para:

* M7 – Hybrid 3DVar (Prova de Conceito)

Sem estabilidade comprovada nesta fase, nenhuma expansão metodológica será iniciada.

## Frentes Paralelas Internas

### Infraestrutura & Spack

* Teste de reinstalação limpa do ambiente
* Validação de consistência de dependências
* Monitoramento de performance prolongada

### MONAN/MPAS

* Monitoramento de estabilidade física
* Avaliação de comportamento inter-ciclos
* Verificação de impacto acumulativo

### Observações

* Monitoramento da consistência do pipeline IODA
* Análise de estabilidade de assimilação por tipo de observação
* Auditoria de rastreabilidade

### Núcleo Variacional

* Avaliação de estabilidade de minimização
* Monitoramento de termos variacionais
* Verificação de ausência de ajustes ad hoc

### Avaliação e Métricas

* Consolidação estatística de longo prazo
* Geração de relatório final de estabilidade
* Avaliação formal da taxa de sucesso
* Comparação com critérios institucionais

### Documentação & Reprodutibilidade

* Documento institucional consolidado MONAN-JEDI
* Guia oficial de execução operacional
* Checklist formal de maturidade técnica
* Registro formal de encerramento da fase

Nenhuma área permanece ociosa: todas participam da auditoria técnica e consolidação final.

## Responsável Primário
Joao Gerd Zell de Mattos

## Colaboradores
Rodrigo Braz
Eder Vendrasco
Carlos Bastarz
Luiz Fernando Sapucci
Liviany Viana
Helena Azevedo
Caroline Viezel

## Artefatos Esperados

* Relatório técnico institucional consolidado
* Logs completos de execução prolongada
* Métricas consolidadas de estabilidade
* Documento formal de maturidade técnica
* Ambiente validado e reproduzível

# M7 – Hybrid 3DVar (Prova de Conceito Controlada)

## Período
Data de início: 04 Janeiro 2027
Data de término: 26 Fevereiro 2027
Duração estimada: 8 semanas

OBS: Dezembro e Janeiro são períodos de recesso e férias. Parte significativa do grupo estará integralmente disponível apenas a partir de 20/01/2027. O cronograma poderá ser ajustado formalmente mediante registro de decisão técnica.

## Objetivo
Implementar e avaliar prova de conceito do Hybrid 3DVar no sistema MONAN-JEDI consolidado, utilizando ensemble reduzido (5–10 membros), janela curta de assimilação e monitoramento rigoroso de estabilidade, custo computacional e impacto estatístico.

## Justificativa Técnica
Conforme definido na Fase 7 do Plano Técnico 2026 , o Hybrid 3DVar somente pode ser iniciado após consolidação completa do sistema determinístico. A introdução prematura ampliaria o grau de liberdade do sistema e dificultaria o diagnóstico de instabilidades . Esta fase permanece exploratória e controlada.


## Escopo

### Incluído:

* Configuração híbrida via SABER
* Ensemble reduzido (5–10 membros)
* Janela curta de assimilação
* Execução controlada inicial (fase reduzida entre 04/01 e 20/01)
* Execução contínua por 3 dias (após 20/01)
* Medição de escalabilidade MPI
* Avaliação de impacto em O–B e O–A
* Avaliação de custo computacional incremental
* Relatório técnico de viabilidade

### Explicitamente Excluído:

* Operação plena híbrida
* Expansão irrestrita do ensemble
* Migração automática do sistema institucional
* Introdução simultânea de radiâncias


## Critérios de Pronto (Definition of Done)

* Hybrid compila no ambiente institucional
* Minimização híbrida converge de forma consistente
* Execução contínua por 3 dias sem falha técnica
* Impacto estatístico documentado
* Custo computacional mensurado
* Escalabilidade MPI analisada
* Relatório técnico de viabilidade produzido
* Decisão formal registrada (viável ou não viável)


## Dependências Técnicas

* M6 concluída com estabilidade institucional validada
* Representação de background error estável
* Infraestrutura computacional dimensionada
* Ferramentas diagnósticas adaptadas ao híbrido


## Encadeamento Temporal

Depende integralmente de M6.
É marco final do cronograma técnico 2026–início 2027.

O período entre 04/01 e 20/01 será destinado a:

* Configuração inicial
* Ajustes de compilação
* Testes unitários

Execuções contínuas e validações formais ocorrerão prioritariamente após 20/01.

Caso haja extensão formal do período de férias, o término poderá ser ajustado mantendo a duração técnica mínima de 8 semanas efetivas.


## Frentes Paralelas Internas

### Infraestrutura & Spack

* Avaliação de impacto de memória
* Monitoramento de escalabilidade
* Testes de uso intensivo de MPI

### MONAN/MPAS

* Monitoramento de estabilidade física sob ensemble
* Avaliação de impacto no estado inicial

### Observações

* Avaliação de impacto por tipo de observação
* Monitoramento da sensibilidade do QC

### Núcleo Variacional

* Configuração híbrida via SABER
* Ajuste de parâmetros de ponderação
* Diagnóstico detalhado da função custo híbrida

### Avaliação e Métricas

* Comparação 3DVar vs Hybrid
* Avaliação de ganho estatístico
* Análise de custo-benefício computacional

### Documentação & Reprodutibilidade

* Documento técnico da prova de conceito
* Registro formal de decisão institucional
* Versionamento completo da configuração híbrida


## Responsável Primário
Joao Gerd Zell de Mattos

## Colaboradores
Carlos Bastarz
Eder Vendrasco
Rodrigo Braz
Liviany Viana
Luiz Fernando Sapucci
Helena Azevedo
Caroline Viezel


## Artefatos Esperados

* Configuração híbrida versionada
* Logs completos de execução
* Métricas comparativas 3DVar vs Hybrid
* Relatório técnico de viabilidade
* Registro formal de decisão
