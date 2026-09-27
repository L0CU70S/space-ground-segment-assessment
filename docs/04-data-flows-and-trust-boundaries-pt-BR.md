# AuroraWatch-1
## Fluxos de Dados e Limites de Confiança

**ID do documento:** DOC-04  
**Versão:** 0.1  
**Status:** Em Desenvolvimento  
**Cenário:** Cenário educacional e fictício  
**Documentos relacionados:** DOC-01 Mission and Scope; DOC-02 System Architecture; DOC-03 Asset Inventory

**Idioma:** [English (US)](./04-data-flows-and-trust-boundaries-en-US.md)

> Este documento descreve uma arquitetura educacional e fictícia. Não representa uma espaçonave, missão, organização ou sistema de produção real.

---

## Visão Geral da Arquitetura

A arquitetura lógica descrita neste documento está disponível no repositório:

- [Visão Geral da Arquitetura — PNG](./architecture/architecture%20Overview.png)
- [Visão Geral da Arquitetura — SVG](./architecture/Architecture%20Overview.svg)
- [Visão Geral da Arquitetura — JPG, português do Brasil](./architecture/Architecture%20Overview-ptbr.jpg)
- [Fonte editável do draw.io](./architecture/Architecture%20Overview.drawio)

> A imagem JPG corresponde à versão em português do Brasil da arquitetura. A estrutura e os identificadores dos ativos são os mesmos nas duas versões linguísticas.

---

## 1. Objetivo e Escopo

Este documento identifica e descreve os fluxos lógicos de comunicação e os limites de confiança representados na Visão Geral da Arquitetura do Segmento Terrestre do AuroraWatch-1.

Ele cria rastreabilidade entre a arquitetura visual e a documentação formal da avaliação. Identificadores como F-01 e F-02 são identificadores documentais. Eles não precisam aparecer como números no diagrama.

O documento cobre:

- fluxos de autenticação e autorização;
- fluxos de administração privilegiada;
- fluxos de operação de missão e comando;
- uplink de telecomandos e downlink de telemetria;
- processamento de telemetria e fluxos de dados da missão;
- fluxos de interface com terceiros;
- coleta e monitoramento de eventos de segurança;
- serviços transversais;
- limites lógicos de confiança.

Os fluxos são representações lógicas. Eles não definem endereços IP, portas, protocolos, algoritmos criptográficos, chaves, rotas de rede ou procedimentos operacionais reais.

## 2. Convenção de Identificação dos Fluxos

Cada conexão documentada usa o seguinte formato:

```text
F-XX — Nome do fluxo
Origem → Destino
Finalidade
Considerações de segurança
```

O diagrama utiliza cores e estilos de linha para comunicar a categoria de cada fluxo. Este documento adiciona identificadores formais e descrições para que documentos posteriores de modelagem de ameaças e mapeamento de controles possam fazer referência a uma conexão específica.

Um único fluxo lógico pode representar várias conexões técnicas em uma implementação real. Da mesma forma, uma única conexão técnica pode transportar vários tipos lógicos de dados. Este documento permanece intencionalmente no nível da arquitetura lógica.

## 3. Legenda dos Fluxos

| Estilo no diagrama | Significado |
|---|---|
| Cinza pontilhado | Autenticação e autorização |
| Amarelo tracejado | Administração privilegiada |
| Ciano sólido | Operações de missão |
| Laranja sólido | Uplink de telecomandos |
| Vermelho sólido | Downlink e ingestão de telemetria |
| Rosa pontilhado | Dados da missão e telemetria processada |
| Verde pontilhado | Eventos de segurança dos ativos monitorados |
| Verde sólido | Ingestão centralizada de logs e tratamento de evidências |
| Vinho tracejado | Interface do provedor externo |
| Dourado tracejado | Serviços transversais e aplicação de políticas |

Os contêineres coloridos representam zonas lógicas. Eles não são fluxos de dados.

## 4. Inventário dos Fluxos

| ID | Origem | Destino | Rótulo no diagrama | Categoria |
|---|---|---|---|---|
| F-01 | A-001 | A-002 | Autenticação de Usuário | Autenticação |
| F-02 | A-002 | A-003 | Autorização de acesso privilegiado | Autorização |
| F-03 | A-003 | A-004 | Sessão privilegiada | Administração privilegiada |
| F-04 | A-004 | A-005 | Acesso administrativo | Administração privilegiada |
| F-05 | A-005 | A-006 | Comandos de operações de missão | Operações de missão |
| F-06 | A-006 | A-009 | Caminho do uplink de telecomando | Operações de missão |
| F-07 | A-009 | A-011 | Uplink de telecomando | TT&C |
| F-08 | A-011 | A-009 | Downlink de telemetria | TT&C |
| F-09 | A-009 | A-007 | Ingestão de telemetria | Processamento de telemetria |
| F-10 | A-007 | A-005 | Telemetria processada | Dados da missão |
| F-11 | A-007 | A-008 | Armazenamento de dados da missão | Dados da missão |
| F-12 | A-008 | A-005 | Recuperação de dados da missão | Dados da missão |
| F-13 | A-009 | A-010 | Interface do provedor terceirizado | Dependência externa |
| F-14 | A-010 | A-009 | Resposta do provedor terceirizado | Dependência externa |
| F-15 | Ativos monitorados | A-013 | Coleta de eventos de segurança | Logging |
| F-16 | A-013 | A-012 | Ingestão centralizada de logs | Monitoramento |
| F-17 | A-012 | A-018 | Retenção de evidências de segurança | Evidências |
| F-18 | A-014 | Ativos autorizados | Linha de base de configuração | Serviço transversal |
| F-19 | Ativos autorizados | A-015 | Backup e recuperação | Serviço transversal |
| F-20 | A-016 | Ativos de missão e segurança | Sincronização de tempo | Serviço transversal |
| F-21 | A-017 | Limites de zona | Aplicação de políticas | Controle transversal |

## 5. Fluxos de Autenticação e Administração

### F-01 — Autenticação de Usuário

**Origem:** A-001 Estação de Trabalho do Operador  
**Destino:** A-002 Provedor de Identidade  
**Estilo:** Cinza pontilhado  
**Finalidade:** Autenticar o operador antes de conceder acesso aos serviços protegidos.  
**Considerações de segurança:** Garantia da autenticação, MFA, proteção de credenciais, confiança no endpoint, confidencialidade, integridade, disponibilidade e responsabilização.  
**Eventos:** Autenticações bem-sucedidas e falhas, resultados de MFA, bloqueios, alterações de conta e mudanças de política.

### F-02 — Autorização de Acesso Privilegiado

**Origem:** A-002 Provedor de Identidade  
**Destino:** A-003 Serviço de PAM  
**Estilo:** Cinza pontilhado  
**Finalidade:** Fornecer informações de identidade e autorização para uma decisão de acesso privilegiado.  
**Considerações de segurança:** Avaliação de função e atributos, menor privilégio, aprovação, separação de funções e integridade da autorização.

### F-03 — Sessão Privilegiada

**Origem:** A-003 Serviço de PAM  
**Destino:** A-004 Bastion Host  
**Estilo:** Amarelo tracejado  
**Finalidade:** Estabelecer e controlar uma sessão administrativa aprovada por meio do bastion host.  
**Considerações de segurança:** Autorização da sessão, proteção de credenciais, isolamento, responsabilização por comandos e encerramento da sessão.

### F-04 — Acesso Administrativo

**Origem:** A-004 Bastion Host  
**Destino:** A-005 Aplicação do MOC e, quando explicitamente autorizado, A-006 Servidor de Controle da Missão  
**Estilo:** Amarelo tracejado  
**Finalidade:** Fornecer acesso administrativo controlado aos sistemas da missão.  
**Considerações de segurança:** Aplicação do bastion, menor privilégio, MFA, autorização administrativa, registro de sessões e aplicação de políticas de rede.

> O caminho administrativo é diferente do caminho de comandos da missão. O A-004 não faz parte do fluxo operacional normal de comandos.

## 6. Fluxos de Operação de Missão e Comandos

### F-05 — Comandos de Operações de Missão

**Origem:** A-005 Aplicação do MOC  
**Destino:** A-006 Servidor de Controle da Missão  
**Estilo:** Ciano sólido  
**Finalidade:** Enviar e coordenar comandos autorizados de operação da missão.  
**Considerações de segurança:** Autenticação, autorização, integridade dos comandos, disponibilidade, responsabilização, validação e separação de funções.

### F-06 — Caminho do Uplink de Telecomando

**Origem:** A-006 Servidor de Controle da Missão  
**Destino:** A-009 Gateway da Estação Terrestre  
**Estilo:** Ciano sólido  
**Finalidade:** Entregar comandos aprovados à interface terrestre.  
**Considerações de segurança:** Integridade dos comandos, autenticação da origem, autorização, disponibilidade, validação de entrada e aplicação de políticas no gateway.

### F-07 — Uplink de Telecomando

**Origem:** A-009 Gateway da Estação Terrestre  
**Destino:** A-011 Simulador de Satélite  
**Estilo:** Laranja sólido  
**Finalidade:** Transmitir telecomandos para o endpoint simulado do segmento espacial.  
**Considerações de segurança:** Autenticação, integridade, autorização, disponibilidade, proteção contra replay, validação de protocolo e isolamento do ambiente de testes.

> Este é um modelo lógico e fictício. Ele não define uma implementação CCSDS real, um perfil criptográfico ou um caminho de comandos qualificado para voo.

## 7. Fluxos de Telemetria e Dados da Missão

### F-08 — Downlink de Telemetria

**Origem:** A-011 Simulador de Satélite  
**Destino:** A-009 Gateway da Estação Terrestre  
**Estilo:** Vermelho sólido  
**Finalidade:** Retornar telemetria simulada e dados de status para a interface terrestre.  
**Considerações de segurança:** Integridade, autenticidade da origem quando necessária, confidencialidade quando necessária, disponibilidade, validação de entrada e responsabilização.

### F-09 — Ingestão de Telemetria

**Origem:** A-009 Gateway da Estação Terrestre  
**Destino:** A-007 Sistema de Processamento de Telemetria  
**Estilo:** Vermelho sólido  
**Finalidade:** Transferir telemetria recebida para decodificação, validação e processamento.  
**Considerações de segurança:** Integridade, disponibilidade, validação de entrada, proteção de recursos e responsabilização.

### F-10 — Telemetria Processada

**Origem:** A-007 Sistema de Processamento de Telemetria  
**Destino:** A-005 Aplicação do MOC  
**Estilo:** Rosa pontilhado  
**Finalidade:** Apresentar telemetria processada e o estado da missão aos operadores autorizados.  
**Considerações de segurança:** Integridade, disponibilidade, autorização, confidencialidade quando aplicável e responsabilização.

### F-11 — Armazenamento de Dados da Missão

**Origem:** A-007 Sistema de Processamento de Telemetria  
**Destino:** A-008 Armazenamento de Dados da Missão e Telemetria  
**Estilo:** Rosa pontilhado  
**Finalidade:** Armazenar telemetria processada, dados da missão e registros operacionais relacionados.  
**Considerações de segurança:** Confidencialidade, integridade, disponibilidade, controle de acesso, retenção e responsabilização.

### F-12 — Recuperação de Dados da Missão

**Origem:** A-008 Armazenamento de Dados da Missão e Telemetria  
**Destino:** A-005 Aplicação do MOC  
**Estilo:** Rosa pontilhado  
**Finalidade:** Fornecer acesso autorizado aos dados armazenados da missão e à telemetria histórica.  
**Considerações de segurança:** Confidencialidade, integridade, autorização, controle de exportação e responsabilização.

## 8. Fluxos do Provedor Externo

### F-13 — Interface do Provedor Terceirizado

**Origem:** A-009 Gateway da Estação Terrestre  
**Destino:** A-010 Interface do Provedor Terceirizado  
**Estilo:** Vinho tracejado  
**Finalidade:** Trocar solicitações de serviço ou dados operacionais aprovados com um provedor terceirizado.  
**Considerações de segurança:** Autenticação mútua, autorização, menor privilégio, validação de interface, confidencialidade quando necessária, integridade, risco do provedor e responsabilização.

### F-14 — Resposta do Provedor Terceirizado

**Origem:** A-010 Interface do Provedor Terceirizado  
**Destino:** A-009 Gateway da Estação Terrestre  
**Estilo:** Vinho tracejado  
**Finalidade:** Retornar respostas de serviço ou dados aprovados ao gateway.  
**Considerações de segurança:** Autenticação da origem, integridade, validação de entrada, disponibilidade e responsabilização.

> A interface do provedor externo não faz parte do caminho direto de telecomando, salvo se um projeto futuro definir e autorizar explicitamente essa dependência.

## 9. Fluxos de Monitoramento de Segurança

### F-15 — Coleta de Eventos de Segurança

**Fontes:** A-001, A-002, A-003, A-004, A-005, A-006, A-007, A-009, A-010, A-011 e A-017  
**Destino:** A-013 Coletor de Logs  
**Estilo:** Verde pontilhado  
**Finalidade:** Coletar eventos relacionados à segurança dos ativos monitorados.  
**Exemplos:** Eventos de autenticação, privilégios, administração, controle da missão, processamento de telemetria, gateway, simulador, interface externa e segurança de rede.

Mapeamento lógico das fontes:

```text
A-001 → A-013  Eventos de Segurança
A-002 → A-013  Eventos de Autenticação
A-003 → A-013  Eventos de Acesso Privilegiado
A-004 → A-013  Eventos de Sessão Administrativa
A-005 → A-013  Eventos da Aplicação da Missão
A-006 → A-013  Eventos do Controle da Missão
A-007 → A-013  Eventos do Processamento de Telemetria
A-009 → A-013  Eventos de Segurança do Gateway
A-010 → A-013  Eventos da Interface Externa
A-011 → A-013  Eventos de Segurança do Simulador
A-017 → A-013  Eventos de Segurança de Rede
```

F-15 é uma categoria lógica de monitoramento que representa várias conexões entre fontes e o coletor. Não é um caminho único de dados operacionais.

### F-16 — Ingestão Centralizada de Logs

**Origem:** A-013 Coletor de Logs  
**Destino:** A-012 Plataforma SIEM  
**Estilo:** Verde sólido  
**Finalidade:** Encaminhar eventos coletados para normalização, correlação, alertas e análise.  
**Considerações de segurança:** Integridade, disponibilidade, confidencialidade, controle de acesso e monitoramento do pipeline.

### F-17 — Retenção de Evidências de Segurança

**Origem:** A-012 Plataforma SIEM  
**Destino:** A-018 Repositório de Evidências da Avaliação  
**Estilo:** Verde sólido  
**Finalidade:** Reter logs, alertas, relatórios e evidências selecionadas para avaliação e investigação.  
**Considerações de segurança:** Confidencialidade, integridade, controle de retenção, controle de acesso, disponibilidade e cadeia de custódia.

> O A-013 não faz parte do caminho normal de comandos. Ele coleta dados de observabilidade do caminho de comandos e de outros componentes monitorados.

## 10. Fluxos de Serviços Transversais

### F-18 — Linha de Base de Configuração

**Origem:** A-014 Repositório da Linha de Base de Configuração  
**Destinos:** A-004, A-005, A-006 e A-009, quando autorizados  
**Estilo:** Dourado tracejado  
**Finalidade:** Fornecer referências de configuração aprovadas e apoiar a detecção de desvios de configuração.  
**Considerações de segurança:** Integridade, autorização, aprovação, controle de versão, responsabilização e disponibilidade.

### F-19 — Backup e Recuperação

**Fontes:** A-005, A-006, A-007, A-008, A-011, A-012, A-013 e A-018  
**Destino:** A-015 Armazenamento de Backup e Recuperação  
**Estilo:** Dourado tracejado  
**Finalidade:** Proteger dados selecionados de sistemas, configurações, missão, monitoramento e evidências para recuperação.  
**Considerações de segurança:** Confidencialidade, integridade, disponibilidade, separação, retenção, testes de restauração e controle de acesso.

### F-20 — Sincronização de Tempo

**Origem:** A-016 Serviço de Sincronização de Tempo  
**Destinos:** Ativos de missão e segurança  
**Estilo:** Dourado tracejado  
**Finalidade:** Fornecer uma referência de tempo consistente para operações, logs, correlação de eventos e investigações.  
**Considerações de segurança:** Integridade, disponibilidade, autenticação da fonte, monitoramento de desvio e comportamento de fallback.

### F-21 — Aplicação de Políticas

**Origem:** A-017 Controles de Segurança de Rede  
**Destino:** Limites de zona e caminhos de rede controlados  
**Estilo:** Dourado tracejado  
**Finalidade:** Aplicar segmentação, permitir ou negar conexões e aplicar políticas de segurança de rede.  
**Considerações de segurança:** Integridade das políticas, controle de mudanças, disponibilidade, logging e resistência a alterações não autorizadas.

## 11. Limites de Confiança

### TB-01 — Acesso do Usuário / Suporte Corporativo

Separa a Zona de Acesso do Usuário da Zona Corporativa / de Suporte. Fluxo principal: F-01.

### TB-02 — Suporte Corporativo / Acesso Administrativo

Separa a Zona Corporativa / de Suporte da Zona de Acesso Administrativo. Fluxo principal: F-02.

### TB-03 — Acesso Administrativo / Operações de Missão

Separa a Zona de Acesso Administrativo da Zona de Operações de Missão. Fluxos principais: F-03 e F-04.

### TB-04 — Operações de Missão / Interface Terrestre

Separa a Zona de Operações de Missão da Zona de Interface Terrestre. Fluxos principais: F-06, F-09, F-13 e F-14.

### TB-05 — Interface Terrestre / Simulação

Separa a Zona de Interface Terrestre da Zona de Simulação. Fluxos principais: F-07 e F-08.

### TB-06 — Operações de Missão / Monitoramento de Segurança

Separa a Zona de Operações de Missão da Zona de Monitoramento de Segurança. Fluxo principal: F-15.

### TB-07 — Interface Terrestre / Provedor Terceirizado

Separa o A-009 do A-010. Fluxos principais: F-13 e F-14.

### TB-08 — Serviços Transversais / Ativos Protegidos

Separa serviços compartilhados dos ativos que eles suportam. Fluxos principais: F-18 a F-21.

## 12. Caminhos Operacionais e de Logging

### Caminho de autenticação

```text
A-001 → A-002 → A-003
```

### Caminho de administração privilegiada

```text
A-003 → A-004 → A-005
```

### Caminho de comandos da missão

```text
A-005 → A-006 → A-009 → A-011
```

### Caminho de telemetria

```text
A-011 → A-009 → A-007 → A-005
                         └→ A-008
```

### Caminho de monitoramento de segurança

```text
Ativos monitorados → A-013 → A-012 → A-018
```

O caminho de monitoramento observa os componentes operacionais; ele não transporta comandos normais da missão.

## 13. Rastreabilidade com o Diagrama

A Visão Geral da Arquitetura não precisa exibir F-01 a F-21 ao lado de cada conexão. Os rótulos visíveis, as cores, os estilos de linha, os ativos de origem e os ativos de destino fornecem a representação visual. Este documento fornece os identificadores formais usados para rastreabilidade da avaliação.

## 14. Considerações Iniciais de Segurança

Os seguintes pontos devem ser analisados no documento de modelagem de ameaças e avaliação de riscos:

- comprometimento do A-001 e roubo de credenciais do operador;
- bypass de autenticação ou comprometimento do provedor de identidade;
- bypass das políticas do PAM ou aprovação indevida de privilégios;
- bypass do bastion ou acesso administrativo não controlado;
- criação ou transmissão não autorizada de comandos da missão;
- injeção, modificação ou replay de telecomandos;
- manipulação de telemetria, entrada malformada ou negação de serviço;
- comprometimento do A-009 Gateway da Estação Terrestre;
- comprometimento da interface do provedor terceirizado;
- perda, supressão ou manipulação de eventos de segurança;
- horário incorreto ou inconsistente nos sistemas;
- desvio de configuração ou alteração não autorizada de baseline;
- comprometimento de backup ou restauração insegura;
- alterações não autorizadas nas políticas de rede;
- isolamento insuficiente do Simulador de Satélite;
- acesso não autorizado às evidências da avaliação;
- falha das capacidades de monitoramento ou recuperação.

Esses são pontos iniciais, não um modelo de ameaças ou avaliação de riscos concluída.

## 15. Rastreabilidade para Documentos Posteriores

Este documento fornece entradas para:

### Documento 05 — Modelo de Ameaças e Avaliação de Riscos

- mapeamento de ativos para ameaças;
- identificação de ameaças baseada em fluxos;
- análise de limites de confiança;
- avaliação de impacto e probabilidade;
- registro inicial de riscos.

### Documento 06 — Requisitos de Segurança e Mapeamento de Controles

- requisitos de controle de acesso;
- requisitos de autenticação;
- requisitos de logging e monitoramento;
- requisitos de proteção de comandos e telemetria;
- requisitos de backup e recuperação;
- requisitos de gerenciamento de configuração;
- requisitos de segmentação de rede.

### Documento 07 — Procedimentos de Avaliação e Plano de Evidências

- fontes de evidência;
- logs esperados;
- evidências de configuração;
- casos de teste;
- observações da avaliação;
- procedimentos de verificação de controles.

## 16. Limitações e Disclaimer

Este documento é um artefato educacional e fictício. Ele não representa um satélite real, uma estação terrestre real, um Centro de Operações de Missão real, um provedor real, uma organização real, um sistema operacional de comandos ou uma arquitetura de cibersegurança de produção.

Os ativos, zonas, rótulos, fluxos e controles foram simplificados para uso educacional. Uma missão real exigiria engenharia de sistemas específica, engenharia de cibersegurança, análise de segurança, seleção de protocolos, projeto criptográfico, aprovação operacional, testes, validação e autorização.

A referência a NIST, CCSDS, SPARTA ou outros frameworks não implica certificação, conformidade ou aprovação.

## 17. Referências

- NIST IR 8401, *Satellite Ground Segment: Applying the Cybersecurity Framework to Satellite Command and Control*.
- NIST SP 800-30, *Guide for Conducting Risk Assessments*.
- NIST SP 800-207, *Zero Trust Architecture*.
- CCSDS 350.0-G-3, *The Application of Security to CCSDS Protocols*.
- CCSDS 355.0-B-2, *Space Data Link Security Protocol*.
- Aerospace Corporation, *Space Segment Cybersecurity Profile*.
- Aerospace Corporation, framework SPARTA.
