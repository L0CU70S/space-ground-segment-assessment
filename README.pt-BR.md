# Avaliação de Cibersegurança do Segmento Terrestre do AuroraWatch-1

🇧🇷 Português | [🇺🇸 English](./README.md)

Avaliação educacional e fictícia de cibersegurança do Segmento Terrestre e do Centro de Operações de Missão de uma missão simulada de observação da Terra em órbita baixa (LEO).

## Disclaimer Importante

AuroraWatch-1 é uma missão fictícia criada exclusivamente para estudos, treinamento e portfólio em cibersegurança espacial.

Este projeto não representa um satélite operacional, organização, cliente, avaliação real de segurança, teste de intrusão, auditoria de conformidade ou arquitetura de missão real.

Este projeto não possui afiliação com NIST, SPARTA, The Aerospace Corporation, CCSDS, NASA, ESA, AEB ou qualquer outra organização mencionada nas referências.

Nenhum teste é realizado contra sistemas reais, infraestrutura de terceiros ou ambientes de produção.

## Objetivo

Este projeto aplica referências públicas de cibersegurança a uma missão espacial fictícia, com foco em:

- Segmento Terrestre;
- Centro de Operações de Missão (MOC);
- estações de trabalho de operadores;
- interfaces de estações terrestres;
- controle de acesso de operadores e administradores;
- fluxos de telemetria e telecomandos;
- dependências de terceiros;
- modelagem de ameaças;
- avaliação de riscos;
- monitoramento, detecção e resposta a incidentes.

O objetivo é conectar conceitos de Blue Team, DFIR, segurança de ambientes críticos, OT/ICS e operações espaciais em um cenário seguro, reproduzível e educacional.

## Escopo Atual

O escopo atual inclui:

- estações de trabalho de operadores;
- sistemas do Centro de Operações de Missão;
- servidores de controle da missão;
- processamento de telemetria;
- armazenamento de dados da missão e telemetria;
- fluxos de telecomandos;
- gateway da estação terrestre;
- identidade, autenticação e acesso privilegiado;
- monitoramento, logging e alertas de segurança;
- interface de um provedor fictício de estação terrestre;
- simulação de satélite;
- serviços de linha de base de configuração;
- serviços de backup e recuperação;
- sincronização de tempo;
- controles de segurança de rede;
- eventos, logs, alertas e evidências sintéticas gerados no laboratório isolado.

As informações detalhadas de escopo estão documentadas em [docs/01-mission-and-scope.pt-BR.md](./docs/01-mission-and-scope.pt-BR.md).

## Visão Geral da Arquitetura

A arquitetura lógica atual está disponível em vários formatos:

- [Visão Geral da Arquitetura — PNG](./docs/architecture/architecture%20Overview.png);
- [Visão Geral da Arquitetura — SVG](./docs/architecture/Architecture%20Overview.svg);
- [Visão Geral da Arquitetura — JPG em português do Brasil](./docs/architecture/Architecture%20Overview-ptbr.jpg);
- [Fonte editável do draw.io](./docs/architecture/Architecture%20Overview.drawio).

A visão geral mostra as principais zonas, ativos, fluxos de operações de missão, caminhos de telecomandos e telemetria, coleta de eventos de segurança, monitoramento e serviços transversais.

## Documentação

### Missão e arquitetura

- [Mission and Scope — English](./docs/01-mission-and-scope.md);
- [Missão e Escopo — Português](./docs/01-mission-and-scope.pt-BR.md);
- [System Architecture — English](./docs/02-system-architecture.md);
- [Arquitetura do Sistema — Português](./docs/02-system-architecture.pt-BR.md).

### Ativos e fluxos

- [Asset Inventory — English](./docs/03-asset-inventory.md);
- [Inventário de Ativos — Português](./docs/03-asset-inventory.pt-BR.md);
- [Data Flows and Trust Boundaries — English](./docs/04-data-flows-and-trust-boundaries-en-US.md);
- [Fluxos de Dados e Limites de Confiança — Português](./docs/04-data-flows-and-trust-boundaries-pt-BR.md).

## Metodologia de Estudo

O projeto está sendo desenvolvido progressivamente:

```text
Missão e escopo
        ↓
Arquitetura do sistema
        ↓
Inventário de ativos
        ↓
Fluxos de dados e limites de confiança
        ↓
Modelagem de ameaças
        ↓
Avaliação de riscos
        ↓
Requisitos de segurança e mapeamento de controles
        ↓
Detecções e evidências
        ↓
Playbooks de resposta a incidentes
        ↓
Implementação do laboratório isolado
        ↓
Casos de teste autorizados
```

O projeto segue uma abordagem baseada em documentação. Os componentes práticos somente serão implementados depois que o escopo lógico, a arquitetura, os ativos, os fluxos e os riscos forem documentados.

## Status do Projeto

### Concluído

- missão e escopo da avaliação;
- arquitetura lógica do sistema;
- inventário de ativos;
- identificação dos fluxos de dados;
- documentação dos limites de confiança;
- diagrama da Visão Geral da Arquitetura;
- versões da documentação em inglês e português do Brasil.

### Em andamento

- modelo de ameaças;
- avaliação de riscos;
- registro inicial de riscos.

### Planejado

- requisitos de segurança;
- mapeamento de controles preventivos e detectivos;
- regras de detecção;
- playbooks de resposta a incidentes;
- implementação do laboratório isolado;
- casos de teste autorizados;
- análise de evidências sintéticas;
- descobertas, recomendações e lições aprendidas.

## Principais Referências

- SPARTA — Space Attack Research and Tactic Analysis;
- NIST IR 8270 — Cybersecurity for Commercial Satellite Operations;
- NIST IR 8401 — Satellite Ground Segment: Applying the Cybersecurity Framework to Satellite Command and Control;
- NIST SP 800-82r3 — Guide to Operational Technology Security;
- NIST SP 800-61r3 — Incident Response Recommendations and Considerations;
- NIST SP 800-30 — Guide for Conducting Risk Assessments;
- padrões e recomendações públicas do CCSDS para sistemas de dados espaciais;
- referências públicas adicionais em [references/references.md](./references/references.md).

## Estrutura do Repositório

```text
space-ground-segment-assessment/
├── README.md
├── README.pt-BR.md
├── docs/
│   ├── 01-mission-and-scope.md
│   ├── 01-mission-and-scope.pt-BR.md
│   ├── 02-system-architecture.md
│   ├── 02-system-architecture.pt-BR.md
│   ├── 03-asset-inventory.md
│   ├── 03-asset-inventory.pt-BR.md
│   ├── 04-data-flows-and-trust-boundaries-en-US.md
│   ├── 04-data-flows-and-trust-boundaries-pt-BR.md
│   └── architecture/
│       ├── Architecture Overview.drawio
│       ├── Architecture Overview.svg
│       ├── architecture Overview.png
│       └── Architecture Overview-ptbr.jpg
├── diagrams/
├── data/
├── detections/
├── playbooks/
├── lab/
└── references/
```

## Sobre o Autor

Este projeto independente é desenvolvido por Igor S. Nascimento como parte de sua jornada de estudos em Cibersegurança Espacial, com foco em Segmento Terrestre, Centro de Operações de Missão, Blue Team, DFIR e segurança de ambientes críticos.

Mais projetos e recursos:

- [CEE Orbital](https://l0cu70s.github.io/cee-orbital/);
- [Perfil e portfólio no GitHub](https://github.com/L0CU70S);
- [Guia de Estudos SPARTA PT-BR](https://github.com/L0CU70S/sparta-ptbr-study-guide).

## Licença

O código, os textos e os artefatos deste repositório são fornecidos para fins educacionais. Consulte [LICENSE](./LICENSE), quando disponível, para conhecer os termos aplicáveis.
