# Non-Functional Testing: Stress Testing, Performance Testing and Fail & Recovery Testing

## 1. Introdução sobre o Tema
Os testes não funcionais representam uma dimensão crítica da engenharia de software, focada na avaliação dos atributos de qualidade do sistema, em oposição ao seu comportamento funcional específico. Enquanto os testes funcionais respondem à pergunta "O sistema faz o que foi especificado?", os testes não funcionais buscam responder "Quão bem o sistema executa essas funções?" (Pressman & Maxim, 2020). Esta categoria abrange características como desempenho, confiabilidade, usabilidade e resilência, sendo fundamental para a satisfação do usuário final e a estabilidade operacional. Teste de Performance, Teste de Estresse e Teste de Falha e Recuperação são pilares para a validação da robustez de sistemas modernos.

## 2. Histórico
A evolução dos testes não funcionais está intrinsecamente ligada ao aumento da complexidade dos sistemas. Inicialmente, o foco da teste de software era quase que exclusivamente na corretude funcional. O clássico "The Art of Software Testing" de Myers (1979) já delineava a importância de testes além da funcionalidade, mas a prática era menos difundida.

Com a revolução cliente-servidor e, posteriormente, a internet comercial, a performance tornou-se uma métrica de negócio. O livro "Performance Testing Guidance for Web Applications" (2007) da Microsoft Press marcou a formalização de práticas para lidar com a carga de usuários concorrentes. A era da computação em nuvem e das arquiteturas de microsserviços elevou a criticalidade da resiliência. Especialistas como Martin Fowler, em seus escritos sobre Arquiteturas Resilientes, e o livro "Site Reliability Engineering" (2016) do Google, consolidaram o Teste de Falha e Recuperação como uma prática essencial, promovendo uma cultura de "assumir que as falhas acontecerão" e testar proativamente a capacidade de recuperação.

## 3. O que é?
### Teste de Performance (Teste de Desempenho):
É o teste realizado para determinar o desempenho de um sistema ou componente sob uma carga de trabalho especificada (ISO/IEC 25010). Seu foco principal é medir e benchmarkar atributos como tempo de resposta, throughput (vazão) e utilização de recursos, sob condições normais e de pico esperadas (Nguyen, 2020).

### Teste de Estresse (Stress Testing):
É um tipo de teste de desempenho que visa avaliar o comportamento do sistema sob condições extremas, frequentemente além de seus limites operacionais normais, para determinar sua capacidade de se recuperar de falhas (Pressman & Maxim, 2020). O objetivo é identificar o ponto de ruptura do sistema e observar como a falha se manifesta, se de forma graciosa ou catastrófica.

### Teste de Falha e Recuperação (Fail & Recovery Testing):
Este teste valida a capacidade de um sistema de reintegrar-se com sucesso após a ocorrência de uma falha e retomar o processamento que foi interrompido (Sommerville, 2011). Envolve a injeção intencional de falhas (e.g., término de processos, indisponibilidade de rede, corrupção de dados) para verificar a eficácia dos mecanismos de redundância, rollback e procedimentos de recuperação.

## 4. Qual o Propósito?
### Propósito do Teste de Performance:

Identificar e eliminar gargalos antes do deployment em produção.
Validar se os requisitos de desempenho (SLAs - Service Level Agreements) foram atendidos.
Fornecer dados para o planejamento de capacidade e escalabilidade (Nguyen, 2020).
Garantir que a experiência do usuário não seja degradada por lentidão.

### Propósito do Teste de Estresse:

Encontrar os limites da aplicação e entender seu comportamento sob carga severa.
Garantir que o sistema não corrompa dados ou falhe de modo irreversível sob estresse.
Verificar se as mensagens de erro geradas sob condições de falha são adequadas e informativas.
Validar os mecanismos de auto-recuperação (e.g., reinício de serviços, failover) uma vez que a carga retorna a níveis normais (Jain, 1991).

### Propósito do Teste de Falha e Recuperação:

Verificar a efetividade dos procedimentos de contingência e dos planos de recuperação de desastres (DRP).
Assegurar a integridade dos dados após uma falha e durante o processo de recuperação.
Validar a confiabilidade do sistema e sua capacidade de atender a requisitos de missão crítica, onde o tempo de inatividade (downtime) deve ser mínimo (Sommerville, 2011).
Cumprir com obrigações contratuais e regulatórias que exigem altos índices de disponibilidade.

## 5. Principais Vantagens e Desvantagens (Prós e Contras)
A aplicação dessas técnicas de teste, embora crucial, apresenta um conjunto de trade-offs que devem ser considerados no planejamento do projeto.

### Teste de Performance
#### Vantagens:

Evita Problemas Críticos em Produção: Identifica gargalos de desempenho que poderiam causar lentidão generalizada ou indisponibilidade, prejudicando a receita e a reputação (Nguyen, 2020).
Base para Decisões de Capacidade: Fornece dados objetivos para o dimensionamento correto de hardware e infraestrutura, evitando tanto a subscrição (que leva a lentidão) quanto a superescalação (que gera custos desnecessários) (Jain, 1991).
Garantia de Contrato: Assegura o cumprimento de SLAs (Acordos de Nível de Serviço) estabelecidos com clientes.

#### Desvantagens:

Custo e Complexidade: Pode exigir ferramentas caras e ambientes de teste que espelhem a produção, o que é significativamente dispendioso (Pressman & Maxim, 2020).
Consumo de Tempo e Recursos: A configuração, execução e análise dos testes são processos demorados que demandam pessoal especializado.
Resultados Contextuais: Os resultados são válidos apenas para a arquitetura e carga de trabalho simuladas; mudanças no ambiente ou no padrão de uso podem invalidar as conclusões.

### Teste de Estresse
#### Vantagens:

Revela Comportamentos Inesperados: Expõe falhas de memory leaks, corrupção de dados sob carga e problemas de concorrência que não se manifestam em condições normais (Pressman & Maxim, 2020).
Define Limites Claros do Sistema: Permite que a equipe de operações saiba exatamente qual é a capacidade máxima do sistema antes de degradar.
Valida a Resiliência: Testa os mecanismos de recuperação automática, assegurando que o sistema possa se restaurar sem intervenção manual após um pico de tráfego (Sommerville, 2011).

#### Desvantagens:

Risco de Danos ao Ambiente de Teste: Pode corromper bancos de dados ou derrubar servidores em ambientes de teste mal isolados, exigindo tempo para reconstituição.
Pode Ser um "Falso Positivo": As condições simuladas podem ser tão extremas e irreais que os problemas encontrados nunca ocorreriam na prática, levando a um esforço de correção desnecessário.

### Teste de Falha e Recuperação
#### Vantagens:

Aumenta Dramaticamente a Confiabilidade: É a única maneira de verificar verdadeiramente se os planos de recuperação de desastres (DRP) e os mecanismos de alta disponibilidade (como failover) funcionam conforme o esperado (Sommerville, 2011).
Minimiza o Tempo de Inatividade (Downtime): Ao praticar e refinar os procedimentos de recuperação, as equipes podem reduzir drasticamente o MTTR (Mean Time To Recovery).
Conformidade e Auditoria: Atende a requisitos de regulamentações que exigem planos de continuidade de negócios testados.

#### Desvantagens:

Invasivo e de Alto Risco: Se realizado de forma inadequada em um ambiente próximo ao de produção, pode causar uma falha real e prolongada.
Complexidade de Configuração: Requer a configuração de ambientes redundantes e a orquestração de ferramentas de injeção de falhas, o que pode ser tecnicamente complexo.
Cultura Organizacional: Encontrar e induzir falhas intencionais pode ser visto como contra-intuitivo ou perigoso por algumas culturas de equipe, exigindo uma mudança de mentalidade para uma "Cultura de Confiabilidade" (Beyer et al., 2016).

## 6. Exemplos de Ferramentas/Frameworks
A eficácia dessas técnicas está diretamente ligada às ferramentas utilizadas para sua automação e execução.

### Para Teste de Performance e Estresse:
#### Apache JMeter (Open Source):

Descrição: Ferramenta Java de código aberto projetada para testar carga e performance funcional. Suporta uma vasta gama de protocolos de aplicação (HTTP, HTTPS, SOAP, REST, JDBC, etc.).
Aplicabilidade: Ideal para simular carga pesada em servidores web e aplicações, permitindo a criação de planos de teste complexos através de sua GUI (Nguyen, 2020). Pode ser usado para ambos os testes de performance (carga esperada) e estresse (carga extrema).

#### Gatling (Open Source):

Descrição: Também uma ferramenta de código aberto, é conhecida por seu alto desempenho e eficiência em recursos, devido à sua arquitetura assíncrona. Os scripts são desenvolvidos em Scala.
Aplicabilidade: Mais adequada para testes de carga de alto desempenho e contínuos (integrado a pipelines de CI/CD). Oferece relatórios detalhados e é frequentemente preferida para ambientes que exigem alta concorrência.

#### LoadRunner (Micro Focus - Comercial):

Descrição: Suíte comercial robusta e uma das ferramentas mais antigas e estabelecidas do mercado. Oferece suporte a uma imensa variedade de tecnologias e protocolos.
Aplicabilidade: Usada em ambientes empresariais complexos para testar aplicações de grande porte, como ERPs (SAP, Oracle) e sistemas legados, fornecendo uma análise profunda de gargalos.

### Para Teste de Falha e Recuperação:
#### Chaos Monkey (Netflix - Open Source):

Descrição: Parte do conjunto de ferramentas Simian Army da Netflix, foi uma das pioneiras na popularização do "Chaos Engineering". Ele termina aleatoriamente instâncias de servidores em produção.
Aplicabilidade: Força a equipe a garantir que seus sistemas são resilientes a falhas de instâncias, validando mecanismos de auto-recuperação e tolerância a falhas em tempo real (Beyer et al., 2016).

#### Gremlin (Comercial):

Descrição: Plataforma comercial de Chaos Engineering que vai muito além do Chaos Monkey. Permite a injeção controlada e segura de uma ampla gama de falhas, incluindo falhas de CPU, memória, rede, e até mesmo de desastres em nível de datacenter ( "Black Hole").
Aplicabilidade: Permite que equipes realizem testes de falha e recuperação de maneira sistemática e segura, mesmo em ambientes de produção, com abortos rápidos e controle de granularidade.

#### Kubernetes-specific Tools (e.g., LitmusChaos, PowerfulSeal):
Descrição: Ferramentas projetadas especificamente para injetar falhas em ambientes baseados em Kubernetes, como "matar" pods, corromper nós ou simular partições de rede.
Aplicabilidade: Essenciais para validar a resiliência e os procedimentos de auto-cura de aplicações modernas em contêineres e orquestradas por Kubernetes.

### Referências Bibliográficas
ISO/IEC 25010:2011. Systems and software engineering — Systems and software Quality Requirements and Evaluation (SQuaRE) — System and software quality models.
Jain, R. (1991). The Art of Computer Systems Performance Analysis: Techniques for Experimental Design, Measurement, Simulation, and Modeling. Wiley.
Myers, G. J., Sandler, C., & Badgett, T. (2012). The Art of Software Testing (3rd ed.). John Wiley & Sons. (Obra original publicada em 1979).
Nguyen, H. (2020). Testing Applications on the Web: Test Planning for Mobile and Internet-Based Systems (2nd ed.). Wiley.
Pressman, R. S., & Maxim, B. R. (2020). Software Engineering: A Practitioner's Approach (9th ed.). McGraw-Hill Education.
Sommerville, I. (2011). Software Engineering (9th ed.). Pearson Education.
Beyer, B., Jones, C., Petoff, J., & Murphy, N. R. (2016). Site Reliability Engineering: How Google Runs Production Systems. O'Reilly Media.
