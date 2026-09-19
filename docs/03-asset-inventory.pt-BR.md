# 3. Inventário de Ativos

🇧🇷 Português | [🇺🇸 English](03-asset-inventory.md)

## Objetivo

Este documento define o inventário inicial de ativos do Ground Segment fictício da AuroraWatch-1.

O inventário apoia a modelagem de ameaças, a avaliação de riscos, o mapeamento de controles de segurança, o desenho do monitoramento, o planejamento de resposta a incidentes e os testes controlados em laboratório.

Os ativos listados são lógicos e fictícios. Eles não representam sistemas, produtos, organizações, provedores ou infraestruturas de missão reais.

## Escopo do inventário

O inventário abrange os componentes lógicos identificados na arquitetura de sistemas da AuroraWatch-1:

- acesso dos operadores;
- identidade e acesso privilegiado;
- Mission Operations Center;
- serviços de comando e telemetria;
- Ground Station Gateway;
- interface fictícia de provedor terceirizado;
- Simulador do Satélite;
- monitoramento de segurança;
- serviços transversais;
- evidências da avaliação.

O inventário não representa um inventário físico, de software, hardware, radiofrequência, órbita, segurança operacional ou garantia de missão completo.

## Método do inventário

Cada ativo é documentado utilizando os seguintes atributos:

- identificador do ativo;
- nome do ativo;
- segmento ou zona lógica;
- tipo de ativo;
- função principal;
- proprietário fictício;
- papel na missão ou na operação;
- criticidade;
- informação ou processo apoiado;
- dependências;
- considerações de segurança;
- status de implementação;
- evidência planejada.

## Escala de criticidade

Os valores de criticidade são classificações educacionais deste projeto:

- **Crítico:** o comprometimento ou a indisponibilidade poderia afetar diretamente a autoridade de comando, a integridade do estado da missão ou operações essenciais no cenário fictício;
- **Alto:** o comprometimento ou a indisponibilidade poderia afetar significativamente monitoramento, processamento, acesso, comunicações ou investigação;
- **Médio:** o comprometimento ou a indisponibilidade poderia afetar funções de apoio, mas talvez não interrompesse imediatamente as operações essenciais;
- **Baixo:** o comprometimento ou a indisponibilidade teria impacto limitado no cenário definido.

Essas classificações não são avaliações oficiais de risco e não devem ser aplicadas a missões reais sem critérios específicos de impacto, tolerância a risco, objetivos de recuperação e validação das partes interessadas.

## Registro de ativos

| ID | Ativo | Zona | Tipo | Função principal | Proprietário | Criticidade | Status |
|---|---|---|---|---|---|---|---|
| A-001 | Estação de Trabalho do Operador | Zona de Acesso dos Usuários | Endpoint | Acessar aplicações da missão e consultar informações operacionais | AuroraWatch Operations | Alto | Planejado |
| A-002 | Provedor de Identidade | Zona Corporativa / Suporte | Serviço de Identidade | Autenticar usuários e fornecer informações de identidade | AuroraWatch Security | Crítico | Planejado |
| A-003 | Serviço PAM | Zona de Acesso Administrativo | Serviço de Segurança | Controlar e auditar sessões privilegiadas | AuroraWatch Security | Crítico | Planejado |
| A-004 | Bastion Host | Zona de Acesso Administrativo | Sistema Administrativo | Fornecer acesso administrativo controlado | AuroraWatch Infrastructure | Alto | Planejado |
| A-005 | Aplicação do MOC | Zona de Operações de Missão | Aplicação | Apoiar monitoramento e fluxos operacionais | AuroraWatch Mission Operations | Crítico | Planejado |
| A-006 | Servidor de Controle da Missão | Zona de Operações de Missão | Servidor / Aplicação | Orquestrar e autorizar comandos fictícios | AuroraWatch Mission Operations | Crítico | Planejado |
| A-007 | Sistema de Processamento de Telemetria | Zona de Operações de Missão | Aplicação / Serviço | Validar, processar e distribuir telemetria | AuroraWatch Mission Operations | Alto | Planejado |
| A-008 | Armazenamento de Dados de Missão e Telemetria | Zona de Operações de Missão | Armazenamento | Manter dados de missão, telemetria e registros de auditoria | AuroraWatch Data Services | Alto | Planejado |
| A-009 | Ground Station Gateway | Zona de Interface Terrestre | Gateway / Serviço | Trocar comandos e telemetria com a interface da estação terrestre | AuroraWatch Communications | Crítico | Planejado |
| A-010 | Interface do Provedor Terceirizado | Zona de Interface Terrestre | Interface Externa | Representar a conexão com o provedor fictício | Fictional GroundLink Provider | Alto | Planejado |
| A-011 | Simulador do Satélite | Zona de Simulação | Simulador | Representar o segmento espacial fictício | AuroraWatch Mission Engineering | Crítico | Planejado |
| A-012 | Plataforma SIEM | Zona de Monitoramento de Segurança | Plataforma de Segurança | Coletar, correlacionar e alertar sobre eventos | AuroraWatch Security Operations | Alto | Planejado |
| A-013 | Coletor de Logs | Zona de Monitoramento de Segurança | Serviço de Logging | Receber e encaminhar logs dos componentes do laboratório | AuroraWatch Security Operations | Alto | Planejado |
| A-014 | Repositório de Baselines de Configuração | Serviços Transversais | Repositório | Armazenar baselines e alterações aprovadas | AuroraWatch Infrastructure | Médio | Planejado |
| A-015 | Armazenamento de Backup e Recuperação | Serviços Transversais | Armazenamento | Apoiar restauração de serviços e dados fictícios selecionados | AuroraWatch Infrastructure | Alto | Planejado |
| A-016 | Serviço de Sincronização de Tempo | Serviços Transversais | Serviço de Infraestrutura | Fornecer timestamps consistentes para operações e investigação | AuroraWatch Infrastructure | Alto | Planejado |
| A-017 | Controles de Segurança de Rede | Serviços Transversais | Controle de Segurança | Aplicar caminhos de comunicação permitidos | AuroraWatch Infrastructure | Crítico | Planejado |
| A-018 | Repositório de Evidências da Avaliação | Zona de Monitoramento de Segurança | Repositório de Evidências | Preservar logs sintéticos, achados e evidências de testes | AuroraWatch Security Operations | Alto | Planejado |

## Perfis detalhados dos ativos

### A-001 — Estação de Trabalho do Operador

**Objetivo:** fornece o ponto de acesso do operador às aplicações de apoio à missão.

**Processos apoiados:**

- autenticação do usuário;
- consulta de telemetria;
- solicitação e aprovação de comandos;
- consulta de alertas;
- documentação operacional;
- geração de eventos de segurança.

**Informações tratadas:** credenciais, dados de sessão, visualizações de telemetria, solicitações de comando, alertas operacionais e logs locais de segurança.

**Dependências:** Provedor de Identidade, Aplicação do MOC, controles de segurança de rede, sincronização de tempo e SIEM ou Coletor de Logs.

**Considerações de segurança:** comprometimento do endpoint, roubo de credenciais, software não autorizado, privilégio local excessivo, acesso remoto não aprovado, execução de malware e logging incompleto do endpoint.

**Evidências planejadas:** baseline de configuração do endpoint, eventos de autenticação, eventos de processos, eventos de rede e registro de acesso de usuário aprovado.

### A-002 — Provedor de Identidade

**Objetivo:** autentica usuários e fornece informações de identidade e função.

**Processos apoiados:**

- ciclo de vida de contas;
- autenticação;
- autorização;
- revisão de acessos;
- monitoramento de identidades.

**Informações tratadas:** identidades, eventos de autenticação, funções, grupos e decisões de acesso.

**Dependências:** diretório ou banco de identidades, sincronização de tempo, controles de segurança de rede e SIEM.

**Considerações de segurança:** comprometimento de identidade privilegiada, autenticação fraca, funções excessivas, persistência de contas, processos de recuperação inseguros e adulteração de logs.

**Evidências planejadas:** logs de autenticação bem-sucedida e malsucedida, atribuições de função, registro de revisão de contas e configuração de políticas de acesso.

### A-003 — Serviço PAM

**Objetivo:** controla o acesso a contas privilegiadas e sessões administrativas.

**Processos apoiados:**

- aprovação de acesso privilegiado;
- intermediação de sessões;
- proteção de credenciais;
- gravação de sessões;
- revisão de acessos.

**Informações tratadas:** identidades privilegiadas, solicitações de acesso, metadados de sessão, aprovações e registros de auditoria.

**Dependências:** Provedor de Identidade, Bastion Host, sistemas de Operações de Missão, SIEM e sincronização de tempo.

**Considerações de segurança:** bypass do caminho de acesso, contas compartilhadas, registros de sessão incompletos, privilégio permanente excessivo e recuperação de credenciais não autorizada.

**Evidências planejadas:** solicitação de acesso privilegiado, registro da sessão, trilha de aprovação e resultado da revisão de acesso.

### A-004 — Bastion Host

**Objetivo:** fornece um caminho controlado para acesso administrativo aos sistemas de apoio à missão.

**Processos apoiados:**

- administração segura;
- registro de sessões;
- restrição de acesso;
- investigação administrativa.

**Informações tratadas:** sessões administrativas, comandos, eventos de autenticação e logs do sistema.

**Dependências:** Serviço PAM, Provedor de Identidade, controles de segurança de rede, SIEM e sincronização de tempo.

**Considerações de segurança:** bypass de acesso direto, comprometimento do host, configuração SSH fraca, excesso de comandos administrativos e registro insuficiente de sessões.

**Evidências planejadas:** regras de controle de acesso, logs de autenticação, registros de sessão, baseline de configuração e histórico de comandos administrativos.

### A-005 — Aplicação do MOC

**Objetivo:** fornece a interface operacional para monitoramento da missão e gestão dos fluxos de trabalho.

**Processos apoiados:**

- exibição de telemetria;
- fluxo de comandos;
- tratamento de alertas;
- coordenação de operadores;
- geração de auditoria.

**Informações tratadas:** status da missão, visualizações de telemetria, solicitações de comandos, aprovações, alertas e eventos de auditoria.

**Dependências:** Provedor de Identidade, Servidor de Controle da Missão, Sistema de Processamento de Telemetria, armazenamento, Ground Station Gateway e SIEM.

**Considerações de segurança:** solicitações de comandos não autorizadas, falhas de autorização, comprometimento da aplicação, injeção em dados operacionais e trilhas de auditoria incompletas.

**Evidências planejadas:** logs da aplicação, decisões de acesso, registros do fluxo de comandos e eventos de auditoria.

### A-006 — Servidor de Controle da Missão

**Objetivo:** orquestra o fluxo fictício de comandos e mantém o estado da missão.

**Processos apoiados:**

- validação de comandos;
- aplicação de aprovações;
- encaminhamento de comandos;
- processamento de confirmações;
- logging de auditoria.

**Informações tratadas:** solicitações de comandos, aprovações, estado da missão, confirmações e eventos administrativos.

**Dependências:** Aplicação do MOC, Ground Station Gateway, Provedor de Identidade, armazenamento, sincronização de tempo e SIEM.

**Considerações de segurança:** execução de comandos não autorizados, replay de comandos, escalada de privilégios, manipulação de estado, comprometimento do serviço e segregação de funções insuficiente.

**Evidências planejadas:** registro de auditoria do comando, resultado da autorização, validação de sequência, registro de transição de estado e logs do serviço.

### A-007 — Sistema de Processamento de Telemetria

**Objetivo:** valida, normaliza e distribui telemetria simulada.

**Processos apoiados:**

- recebimento de mensagens;
- validação de origem e formato;
- detecção de anomalias;
- normalização;
- exibição;
- armazenamento.

**Informações tratadas:** mensagens de telemetria, resultados de validação, registros de anomalia, status de processamento e timestamps.

**Dependências:** Ground Station Gateway, Aplicação do MOC, armazenamento, sincronização de tempo e SIEM.

**Considerações de segurança:** entradas malformadas, telemetria falsa, replay de mensagens, manipulação de dados, negação de serviço e validação insuficiente da origem.

**Evidências planejadas:** registros de telemetria, eventos de validação, alertas de anomalia, metadados da origem e logs de processamento.

### A-008 — Armazenamento de Dados de Missão e Telemetria

**Objetivo:** mantém dados fictícios da missão, telemetria, eventos de auditoria e evidências selecionadas.

**Processos apoiados:**

- retenção de dados;
- recuperação;
- investigação;
- relatórios;
- recuperação operacional.

**Informações tratadas:** dados de missão, telemetria, registros de comandos, registros de auditoria e histórico operacional.

**Dependências:** Aplicação do MOC, Servidor de Controle da Missão, Sistema de Processamento de Telemetria, Armazenamento de Backup e Recuperação, gestão de acesso e SIEM.

**Considerações de segurança:** alteração não autorizada, exclusão, exposição de dados, retenção fraca, comprometimento de backups e proteção de integridade inadequada.

**Evidências planejadas:** logs de acesso, verificações de integridade, registro de backup, configuração de retenção e resultado de teste de recuperação.

### A-009 — Ground Station Gateway

**Objetivo:** aplica a troca lógica entre as operações de missão e a interface fictícia da estação terrestre.

**Processos apoiados:**

- encaminhamento de comandos;
- recebimento de telemetria;
- validação de mensagens;
- controle de taxa;
- logging de transações.

**Informações tratadas:** mensagens de comando, mensagens de telemetria, metadados de interface, dados de autorização, números de sequência e timestamps.

**Dependências:** Servidor de Controle da Missão, Sistema de Processamento de Telemetria, Interface do Provedor Terceirizado, controles de segurança de rede, sincronização de tempo e SIEM.

**Considerações de segurança:** encaminhamento não autorizado, replay, manipulação de mensagens, interfaces expostas, abuso de acesso do provedor e interrupção do serviço.

**Evidências planejadas:** log de transações do gateway, resultado da validação de mensagens, registro de conexões, evento de limitação de taxa e baseline de configuração.

### A-010 — Interface do Provedor Terceirizado

**Objetivo:** representa a dependência lógica externa utilizada para troca de comandos e telemetria.

**Processos apoiados:**

- acesso do provedor;
- troca de serviços;
- coordenação operacional;
- comunicação de eventos de segurança do provedor.

**Informações tratadas:** mensagens de interface, metadados de serviço, registros de acesso e eventos de segurança do provedor.

**Dependências:** Ground Station Gateway, premissas contratuais, controles de identidade e acesso e controles de segurança de rede.

**Considerações de segurança:** limites de responsabilidade indefinidos, acesso excessivo, autenticação fraca do provedor, logging insuficiente, risco de cadeia de suprimentos e risco de dependência de serviço.

**Evidências planejadas:** lista de acessos do provedor, requisitos de segurança, premissas de nível de serviço, logs de conexão e registro de revisão.

### A-011 — Simulador do Satélite

**Objetivo:** representa o segmento espacial fictício sem conexão com uma espaçonave ou sistema de rádio real.

**Processos apoiados:**

- aceitação de comandos;
- transições de estado simuladas;
- geração de telemetria;
- confirmações;
- anomalias simuladas.

**Informações tratadas:** comandos fictícios, estado simulado, telemetria, números de sequência, timestamps e resultados de testes.

**Dependências:** Ground Station Gateway, dados de simulação, sincronização de tempo e logging.

**Considerações de segurança:** transições de estado inválidas, validação insuficiente de comandos, replay, falha de integridade da telemetria, escape do teste e comportamento inseguro do simulador.

**Evidências planejadas:** registro do estado do simulador, comandos aceitos/rejeitados, saída de telemetria, registro de anomalias e logs de teste.

### A-012 — Plataforma SIEM

**Objetivo:** centraliza e analisa eventos relevantes de segurança.

**Processos apoiados:**

- coleta de logs;
- correlação;
- alertas;
- investigação;
- relatórios;
- apoio a evidências.

**Informações tratadas:** eventos de autenticação, eventos de endpoints, eventos de comandos, eventos de telemetria, alterações de configuração, alertas e dados de investigação.

**Dependências:** Coletor de Logs, sincronização de tempo, armazenamento, regras de detecção e acesso dos analistas.

**Considerações de segurança:** fontes de logs ausentes, parsing incorreto, fadiga de alertas, acesso não autorizado, falha de retenção e manipulação de logs.

**Evidências planejadas:** status de ingestão, regra de detecção, registro de alerta, notas do analista e linha do tempo do caso.

### A-013 — Coletor de Logs

**Objetivo:** recebe e encaminha logs dos componentes do laboratório.

**Processos apoiados:**

- transporte de logs;
- bufferização;
- normalização;
- encaminhamento;
- monitoramento de integridade.

**Informações tratadas:** logs de segurança, logs operacionais, metadados, timestamps e status de coleta.

**Dependências:** controles de segurança de rede, SIEM, sincronização de tempo e sistemas de origem.

**Considerações de segurança:** perda de logs, injeção não autorizada, transporte inseguro, esgotamento de filas e disponibilidade insuficiente.

**Evidências planejadas:** inventário de fontes, configuração de coleta, status de entrega, registro de eventos descartados e verificação de integridade.

### A-014 — Repositório de Baselines de Configuração

**Objetivo:** armazena configurações aprovadas, baselines, alterações e dados de comparação.

**Processos apoiados:**

- gestão de mudanças;
- comparação de baseline;
- monitoramento de integridade;
- apoio à reversão.

**Informações tratadas:** arquivos de configuração, hashes, registros de aprovação, histórico de versões e metadados de mudança.

**Dependências:** gestão de acesso, armazenamento, controle de versão e SIEM.

**Considerações de segurança:** alterações não autorizadas, adulteração de baseline, ausência de aprovação e incapacidade de determinar o estado esperado.

**Evidências planejadas:** baseline aprovada, solicitação de mudança, histórico de versão, comparação de integridade e registro de reversão.

### A-015 — Armazenamento de Backup e Recuperação

**Objetivo:** apoia a recuperação de serviços e dados fictícios selecionados.

**Processos apoiados:**

- backup;
- restauração;
- testes de recuperação;
- exercícios de continuidade.

**Informações tratadas:** backups de sistemas, backups de configurações, snapshots de dados e metadados de recuperação.

**Dependências:** armazenamento, gestão de acesso, agendamento e controles de segurança de rede.

**Considerações de segurança:** restauração não testada, exclusão de backups, exposição de dados de backup, separação insuficiente e pontos de recuperação desatualizados.

**Evidências planejadas:** registro do job de backup, teste de restauração, log de acesso, política de retenção e resultado da recuperação.

### A-016 — Serviço de Sincronização de Tempo

**Objetivo:** fornece timestamps consistentes aos componentes do laboratório.

**Processos apoiados:**

- correlação de eventos;
- validade de comandos;
- análise de logs;
- construção de linhas do tempo de incidentes.

**Informações tratadas:** metadados da fonte de tempo, status de sincronização, medições de offset e timestamps dos sistemas.

**Dependências:** fonte de tempo do host, controles de segurança de rede e configuração dos sistemas.

**Considerações de segurança:** desvio de relógio, alteração maliciosa de tempo, timestamps inconsistentes e linhas do tempo de investigação não confiáveis.

**Evidências planejadas:** status de sincronização, registro de offset, configuração da fonte de tempo e alerta de desvio.

### A-017 — Controles de Segurança de Rede

**Objetivo:** aplicam os caminhos de comunicação entre zonas lógicas e serviços.

**Processos apoiados:**

- segmentação;
- filtragem;
- restrição de acesso;
- monitoramento;
- contenção.

**Informações tratadas:** fluxos de rede, conjuntos de regras, tentativas de conexão, tráfego bloqueado e alterações de configuração.

**Dependências:** topologia de rede, fluxos aprovados, controles de firewall ou host, logging e sincronização de tempo.

**Considerações de segurança:** regras permissivas demais, caminhos de acesso direto, tráfego não monitorado, desvio de regras e isolamento inadequado.

**Evidências planejadas:** conjunto de regras aprovado, evento de conexão bloqueada, registro de mudança, log de fluxo e resultado de revisão.

### A-018 — Repositório de Evidências da Avaliação

**Objetivo:** preserva logs sintéticos, achados, capturas de tela, registros de teste e notas de análise.

**Processos apoiados:**

- tratamento de evidências;
- reprodutibilidade;
- relatórios;
- revisão;
- lições aprendidas.

**Informações tratadas:** evidências sintéticas, notas de investigação, capturas de tela, resultados de testes, relatórios e timestamps.

**Dependências:** gestão de acesso, armazenamento, controles de integridade, backup e sincronização de tempo.

**Considerações de segurança:** alteração de evidências, exposição acidental, procedência indefinida, ausência de timestamps e retenção inadequada.

**Evidências planejadas:** índice de evidências, registro de hash ou integridade, histórico de acesso, nota de cadeia de custódia e relatório final.

## Relações entre ativos

### Caminho operacional de comando

```text
A-001 Estação de Trabalho do Operador
              ↓
       A-005 Aplicação do MOC
              ↓
 A-006 Servidor de Controle da Missão
              ↓
      A-009 Ground Station Gateway
              ↓
       A-011 Simulador do Satélite
```

### Caminho de telemetria

```text
A-011 Simulador do Satélite
              ↓
      A-009 Ground Station Gateway
              ↓
 A-007 Sistema de Processamento de Telemetria
              ↓
       A-005 Aplicação do MOC
              ↓
A-008 Armazenamento de Dados de Missão e Telemetria
```

### Caminho de autenticação e acesso privilegiado

```text
A-001 Estação de Trabalho do Operador
              ↓
       A-002 Provedor de Identidade
              ↓
          A-005 Aplicação do MOC
```

```text
A-001 Estação de Trabalho do Operador
              ↓
          A-003 Serviço PAM
              ↓
          A-004 Bastion Host
              ↓
      Sistemas de Operações de Missão
```

### Caminho de monitoramento de segurança

```text
Componentes relevantes do laboratório
              ↓
          A-013 Coletor de Logs
              ↓
          A-012 Plataforma SIEM
              ↓
 A-018 Repositório de Evidências da Avaliação
```

## Serviços transversais

Os seguintes ativos apoiam múltiplas zonas lógicas:

- A-014 Repositório de Baselines de Configuração;
- A-015 Armazenamento de Backup e Recuperação;
- A-016 Serviço de Sincronização de Tempo;
- A-017 Controles de Segurança de Rede.

Esses ativos não devem ser interpretados como pertencentes exclusivamente a uma única zona operacional. Sua postura de segurança pode afetar diversos componentes simultaneamente.

## Considerações iniciais de criticidade

Os seguintes ativos são inicialmente considerados críticos porque influenciam autoridade de comando, integridade do estado da missão, comunicações ou controle de acesso:

- A-002 Provedor de Identidade;
- A-003 Serviço PAM;
- A-005 Aplicação do MOC;
- A-006 Servidor de Controle da Missão;
- A-009 Ground Station Gateway;
- A-011 Simulador do Satélite;
- A-017 Controles de Segurança de Rede.

Esta é uma classificação educacional inicial. O risco final de um ativo dependerá do impacto na missão, exposição a ameaças, controles existentes, dependências, objetivos de recuperação e tolerância a riscos.

## Propriedades iniciais de segurança

O projeto avaliará as seguintes propriedades de segurança para os ativos relevantes:

| Propriedade | Exemplo na AuroraWatch-1 |
|---|---|
| Confidencialidade | Proteger credenciais, dados de missão e evidências de segurança |
| Integridade | Impedir alterações não autorizadas em comandos, telemetria, configurações e logs |
| Disponibilidade | Manter acesso ao MOC, telemetria, fluxos de comandos e monitoramento |
| Autenticidade | Verificar operadores, serviços, comandos, fontes de telemetria e interfaces de provedores |
| Responsabilização | Registrar ações, aprovações, mudanças e eventos de segurança |
| Recuperabilidade | Restaurar sistemas, configurações e dados selecionados após uma interrupção |
| Segurança operacional e garantia de missão | Evitar transições inseguras simuladas e comportamento de teste não controlado |

## Limitações do inventário

Este inventário não é exaustivo. Ele se concentra nos ativos lógicos necessários para explicar a primeira fase da avaliação.

Versões futuras poderão adicionar:

- identificadores de software e serviços;
- classificação de dados;
- interfaces e portas;
- métodos de autenticação;
- objetivos de backup;
- objetivos de tempo e ponto de recuperação;
- proprietários e custodians dos ativos;
- referências a controles de segurança;
- cobertura de monitoramento;
- status de vulnerabilidades e configurações;
- dependências físicas e ambientais;
- dependências criptográficas e papéis de gerenciamento de chaves;
- responsabilidades de provedores e controles contratuais.

## Status do documento

- Status: Em desenvolvimento
- Cenário: AuroraWatch-1
- Ambiente: Laboratório fictício e isolado
- Tipo de avaliação: Projeto educacional de portfólio
- Idioma: Português brasileiro
- Última revisão: 18 de setembro de 2026
