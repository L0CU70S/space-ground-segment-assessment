# 2. Arquitetura do Sistema

🇧🇷 Português | [🇺🇸 English](02-system-architecture.md)

## Objetivo

Este documento descreve a arquitetura lógica do Ground Segment fictício da AuroraWatch-1 utilizado nesta avaliação educacional.

A arquitetura foi intencionalmente simplificada. Ela foi criada para apoiar a identificação de ativos, a análise de fluxos de dados, a definição de fronteiras de confiança, a modelagem de ameaças, a avaliação de riscos, o monitoramento de segurança e os testes controlados em laboratório.

Ela não reproduz a arquitetura de uma missão espacial, organização, provedor ou ambiente operacional real.

## Contexto da missão

AuroraWatch-1 é uma missão fictícia de observação da Terra em órbita baixa terrestre (LEO).

A missão coleta imagens ambientais fictícias e telemetria operacional. Os operadores utilizam o Ground Segment para monitorar o status da missão, processar telemetria, preparar comandos, trocar dados com um provedor fictício de estação terrestre e registrar eventos operacionais.

O satélite e a camada de radiofrequência são representados por um simulador. Nenhuma espaçonave real, antena, transmissão de rádio ou sistema operacional de controle de missão está conectado a este projeto.

## Componentes lógicos

### 1. Estação de trabalho do operador

A estação de trabalho do operador é utilizada por operadores autorizados para acessar aplicações de apoio à missão.

Funções esperadas:

- acessar a aplicação do MOC;
- consultar telemetria e status da missão;
- enviar ou aprovar solicitações de comandos fictícios;
- consultar alertas operacionais;
- acessar documentação aprovada;
- gerar logs de estação de trabalho e autenticação.

Considerações de segurança:

- contas individuais;
- princípio do menor privilégio;
- endurecimento do endpoint;
- autenticação multifator quando disponível;
- registro de sessões e atividades;
- acesso administrativo restrito.

### 2. Provedor de identidade

O Provedor de Identidade gerencia a autenticação e os serviços relacionados à identidade no laboratório.

Funções esperadas:

- autenticar usuários;
- fornecer informações de função e perfil;
- apoiar revisões de acesso;
- registrar eventos de autenticação bem-sucedidos e malsucedidos;
- fornecer dados de identidade ao MOC e aos fluxos de acesso privilegiado.

Considerações de segurança:

- autenticação forte;
- gestão do ciclo de vida das contas;
- controle de acesso baseado em funções;
- proteção de contas privilegiadas;
- monitoramento de eventos de autenticação;
- sincronização segura de tempo.

### 3. Gerenciamento de acesso privilegiado

O componente fictício de PAM controla o acesso privilegiado aos sistemas sensíveis de apoio à missão.

Funções esperadas:

- intermediar sessões administrativas;
- restringir o acesso a usuários aprovados;
- registrar metadados das sessões;
- apoiar acessos temporários ou baseados em tarefas;
- fornecer informações de auditoria à plataforma de monitoramento.

O componente PAM poderá ser implementado como um controle documentado ou como um serviço de laboratório, dependendo da fase do projeto.

### 4. Bastion Host

O Bastion Host é o ponto controlado de acesso administrativo aos servidores de apoio à missão.

Funções esperadas:

- fornecer um caminho controlado para administração;
- limitar o acesso administrativo direto aos sistemas protegidos;
- gerar logs de autenticação e sessão;
- apoiar revisões de acesso administrativo.

Considerações de segurança:

- acesso de rede restrito;
- contas individuais;
- chaves SSH ou mecanismo equivalente de autenticação segura;
- comandos administrativos limitados;
- registro de sessões;
- encaminhamento centralizado de logs;
- configuração endurecida.

### 5. Mission Operations Center

O Mission Operations Center é o ambiente lógico central das operações da missão.

Funções esperadas:

- exibir o status da missão;
- receber e processar telemetria;
- preparar e autorizar comandos fictícios;
- gerenciar fluxos operacionais;
- gerar eventos de missão e auditoria;
- comunicar-se com o Ground Station Gateway.

O MOC pode conter vários serviços lógicos, mesmo quando implementados em um único host de laboratório.

### 6. Servidor de controle da missão

O Servidor de Controle da Missão apoia a orquestração de comandos e o gerenciamento do estado da missão.

Funções esperadas:

- receber solicitações de comandos aprovadas;
- validar a estrutura e a autorização dos comandos;
- aplicar regras do fluxo de comandos;
- transmitir comandos aceitos ao Ground Station Gateway;
- registrar eventos de comando e administração.

Considerações de segurança:

- autenticação forte;
- autorização de comandos;
- segregação de funções;
- lista permitida de comandos;
- proteção contra replay no simulador;
- registro completo de auditoria;
- exposição de rede restrita.

### 7. Sistema de processamento de telemetria

O Sistema de Processamento de Telemetria recebe e processa telemetria simulada.

Funções esperadas:

- receber mensagens de telemetria;
- validar formato e origem das mensagens;
- normalizar dados de telemetria;
- identificar dados anormais ou ausentes;
- fornecer dados ao MOC;
- registrar eventos de processamento e validação.

Considerações de segurança:

- validação de entradas;
- autenticação da origem;
- monitoramento de integridade;
- detecção de anomalias;
- restrição de contas de serviço;
- logging centralizado.

### 8. Armazenamento de dados de missão e telemetria

O componente de armazenamento mantém dados fictícios de missão, telemetria, eventos de auditoria e evidências da avaliação.

Funções esperadas:

- armazenar telemetria;
- armazenar registros de eventos da missão;
- preservar logs de auditoria;
- apoiar investigação e análise;
- fornecer acesso controlado aos serviços autorizados.

Considerações de segurança:

- controle de acesso;
- integridade dos dados;
- backup e recuperação;
- regras de retenção;
- proteção contra exclusão ou alteração não autorizada;
- separação entre dados operacionais e evidências de segurança.

### 9. Ground Station Gateway

O Ground Station Gateway representa a interface lógica entre o Mission Operations Center e o provedor fictício terceirizado de estação terrestre.

Funções esperadas:

- receber comandos aprovados do MOC;
- validar a estrutura das mensagens e os dados de autorização;
- encaminhar comandos fictícios ao Simulador do Satélite;
- receber telemetria simulada;
- encaminhar telemetria ao Sistema de Processamento de Telemetria;
- registrar todas as transações.

Considerações de segurança:

- listas de permissão explícitas;
- comunicação autenticada entre serviços;
- validação de comandos;
- validação de sequência e timestamp;
- limitação de taxa;
- logging completo das transações;
- fronteiras de rede restritas.

### 10. Provedor terceirizado de estação terrestre

O Provedor Terceirizado de Estação Terrestre é uma dependência externa fictícia que apoia a interface com a estação terrestre.

Funções esperadas:

- fornecer uma interface lógica de estação;
- receber comandos fictícios autorizados;
- transmitir telemetria simulada;
- fornecer eventos de serviço e segurança;
- apoiar a coordenação operacional.

Considerações de segurança:

- limites contratuais e de acesso;
- menor privilégio;
- identidades individuais;
- acesso temporário;
- logging do provedor;
- gestão de mudanças;
- procedimentos de notificação de incidentes.

Nenhum provedor real, conta externa, rede externa ou estação terrestre real é utilizado.

### 11. Simulador do satélite

O Simulador do Satélite representa o segmento espacial no laboratório.

Funções esperadas:

- aceitar somente comandos fictícios e validados;
- atualizar o estado simulado da missão;
- gerar telemetria fictícia;
- retornar confirmações de comandos;
- gerar anomalias simuladas;
- registrar alterações de estado e resultados de comandos.

O simulador não modela toda a complexidade de hardware, software, órbita, radiofrequência, segurança operacional ou operação de uma espaçonave real.

### 12. Monitoramento de segurança e SIEM

O componente de Monitoramento de Segurança e SIEM coleta e analisa eventos relevantes de segurança do laboratório.

Funções esperadas:

- coletar logs de autenticação;
- coletar eventos de acesso privilegiado;
- coletar registros de auditoria do MOC e do gateway;
- detectar atividades suspeitas ou não autorizadas;
- apoiar a triagem de alertas;
- preservar evidências de investigação;
- apoiar exercícios de resposta a incidentes.

Possíveis fontes de logs:

- estação de trabalho do operador;
- Provedor de Identidade;
- PAM e Bastion Host;
- Servidor de Controle da Missão;
- Sistema de Processamento de Telemetria;
- Ground Station Gateway;
- Simulador do Satélite;
- controles de rede;
- ferramentas de monitoramento de configuração.

## Zonas lógicas de rede

O laboratório está organizado em zonas lógicas de segurança. Essas zonas são conceituais e podem ser implementadas por meio de redes virtuais, containers, controles baseados no host ou fronteiras documentadas, dependendo da fase do projeto.

### Zona de acesso dos usuários

Contém as estações de trabalho dos operadores e os caminhos de acesso voltados aos usuários.

Principais preocupações:

- comprometimento de endpoints;
- roubo de credenciais;
- acesso não autorizado;
- privilégios excessivos;
- atividade maliciosa ou acidental do operador.

### Zona corporativa ou de suporte

Representa serviços de identidade, administração e suporte compartilhado.

Principais preocupações:

- movimentação lateral;
- comprometimento de identidade;
- acesso administrativo excessivo;
- dependências inseguras.

### Zona de acesso administrativo

Contém o Bastion Host e os fluxos de acesso privilegiado.

Principais preocupações:

- comprometimento de contas privilegiadas;
- abuso de sessões;
- acesso direto a sistemas protegidos;
- trilhas de auditoria inadequadas.

### Zona de operações de missão

Contém o MOC, o Servidor de Controle da Missão, o Sistema de Processamento de Telemetria e os serviços de dados da missão.

Principais preocupações:

- comandos não autorizados;
- manipulação de dados de missão;
- perda de disponibilidade;
- segregação de funções insuficiente;
- logging incompleto.

### Zona de interface terrestre

Contém o Ground Station Gateway e sua interface lógica com o provedor fictício.

Principais preocupações:

- encaminhamento de comandos não autorizados;
- manipulação de mensagens;
- replay;
- acesso do provedor;
- interrupção do serviço.

### Zona de simulação

Contém o Simulador do Satélite e os serviços de teste controlados.

Principais preocupações:

- transições de estado inválidas;
- fragilidades na validação de comandos;
- integridade da telemetria;
- isolamento dos testes.

### Zona de monitoramento de segurança

Contém serviços de coleta, análise, alertas e preservação de evidências.

Principais preocupações:

- perda de logs;
- manipulação de logs;
- sincronização de tempo insuficiente;
- acesso excessivo às evidências de segurança;
- visibilidade incompleta.

## Principais fluxos de dados

### Fluxo F-01 — Autenticação do operador

```text
Estação de Trabalho do Operador
              ↓
       Provedor de Identidade
              ↓
          Aplicação do MOC
```

Objetivo:

- autenticar o operador;
- obter informações de função e autorização;
- registrar eventos de autenticação e acesso.

### Fluxo F-02 — Acesso administrativo privilegiado

```text
Estação de Trabalho do Operador
              ↓
       Bastion Host / PAM
              ↓
     Sistemas de Operações de Missão
```

Objetivo:

- fornecer acesso administrativo controlado;
- limitar conexões diretas;
- registrar atividades privilegiadas.

### Fluxo F-03 — Comando de missão

```text
Estação de Trabalho do Operador
              ↓
          Aplicação do MOC
              ↓
     Servidor de Controle da Missão
              ↓
      Ground Station Gateway
              ↓
       Simulador do Satélite
```

Objetivo:

- enviar um comando fictício;
- validar autorização e estrutura;
- encaminhar um comando aprovado;
- receber uma confirmação simulada;
- registrar todo o fluxo.

### Fluxo F-04 — Telemetria

```text
Simulador do Satélite
          ↓
Ground Station Gateway
          ↓
Sistema de Processamento de Telemetria
          ↓
Aplicação do MOC
          ↓
Armazenamento de Dados de Missão e Telemetria
```

Objetivo:

- transmitir telemetria simulada;
- validar e processar a telemetria;
- exibir informações da missão;
- manter dados para operação e investigação.

### Fluxo F-05 — Logging de segurança

```text
Componentes do Laboratório
              ↓
       Coletores de Logs
              ↓
  Monitoramento de Segurança / SIEM
              ↓
Alertas e Evidências de Investigação
```

Objetivo:

- centralizar eventos relevantes de segurança;
- detectar atividades anormais;
- apoiar investigação e resposta;
- preservar evidências.

## Fronteiras de confiança

As seguintes fronteiras de confiança exigem documentação e controles de segurança explícitos:

- entre a estação de trabalho do operador e o MOC;
- entre a zona de acesso dos usuários e a zona de acesso administrativo;
- entre o Bastion Host e os sistemas de apoio à missão;
- entre o MOC e o Ground Station Gateway;
- entre o Ground Station Gateway e a interface do provedor fictício;
- entre o Ground Station Gateway e o Simulador do Satélite;
- entre os sistemas operacionais e o SIEM;
- entre os dados de missão e as evidências de segurança;
- entre os serviços do laboratório e o ambiente hospedeiro.

## Princípios iniciais de segurança

A arquitetura será avaliada utilizando os seguintes princípios:

- menor privilégio;
- negar por padrão;
- autorização explícita;
- segregação de funções;
- defesa em profundidade;
- caminhos seguros de administração;
- segmentação e comunicação controlada;
- fluxos de dados autenticados e protegidos quanto à integridade;
- logging completo e centralizado;
- sincronização de tempo;
- gestão controlada de mudanças;
- recuperação e preservação de evidências;
- testes seguros em ambiente isolado.

## Limitações da arquitetura

Esta arquitetura lógica é um projeto inicial para um laboratório educacional. Ela não define:

- uma arquitetura real de espaçonave;
- um enlace real de radiofrequência;
- um projeto criptográfico real;
- um protocolo real de controle de missão;
- uma integração real com provedor;
- uma arquitetura completa de segurança operacional ou garantia de missão;
- uma implantação pronta para produção.

Tecnologias específicas, endereços de rede, protocolos, containers, máquinas virtuais e controles de segurança serão documentados somente quando forem implementados no laboratório controlado.

## Próximos passos

As próximas atividades de arquitetura são:

- [x] 1. criar um diagrama visual da arquitetura;
- [ ] 2. atribuir identificadores aos componentes e às fronteiras de confiança;
- [ ] 3. criar o inventário de ativos;
- [ ] 4. documentar as premissas dos fluxos de dados;
- [ ] 5. definir requisitos iniciais de segurança;
- [ ] 6. selecionar os primeiros casos de teste controlados;
- [ ] 7. relacionar ameaças e riscos relevantes à arquitetura.

## Status do documento

- Status: Em desenvolvimento
- Cenário: AuroraWatch-1
- Ambiente: Laboratório fictício e isolado
- Tipo de avaliação: Projeto educacional de portfólio
- Última revisão: 13 de setembro de 2026
