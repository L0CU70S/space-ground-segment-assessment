# AuroraWatch-1 Ground Segment Cybersecurity Assessment

🇧🇷 Português | [🇺🇸 English](../README.md)

Avaliação educacional e fictícia de cibersegurança para o Ground Segment e o Mission Operations Center de uma missão espacial simulada.

## Aviso importante

AuroraWatch-1 é uma missão fictícia criada exclusivamente para fins de estudo, treinamento e portfólio em cibersegurança espacial.

Este projeto não representa um satélite operacional, uma organização, um cliente, uma avaliação real de segurança, um teste de intrusão, uma auditoria de conformidade ou uma arquitetura real de missão.

O projeto não possui afiliação com NIST, SPARTA, The Aerospace Corporation, CCSDS, NASA, ESA, AEB ou qualquer outra organização mencionada nas referências.

Nenhum teste é realizado contra sistemas reais, infraestruturas de terceiros ou ambientes de produção.

## Objetivo

Este projeto aplica referências públicas de cibersegurança a uma missão espacial fictícia, com foco em:

- Ground Segment;
- Mission Operations Center (MOC);
- estações de operação;
- interfaces com estações terrestres;
- controle de acesso de operadores e administradores;
- fluxos de telemetria e telecomando;
- dependências de terceiros;
- modelagem de ameaças;
- avaliação de riscos;
- monitoramento, detecção e resposta a incidentes.

O objetivo é conectar conceitos de Blue Team, DFIR, segurança de ambientes críticos, OT/ICS e operações espaciais em um cenário reproduzível e seguro.

## Escopo inicial

O escopo inicial contempla:

- Estações de trabalho de operadores;
- sistemas do Mission Operations Center;
- processamento de telemetria;
- fluxo de telecomandos;
- gateway de estação terrestre;
- identidade, autenticação e acesso privilegiado;
- monitoramento e registros de segurança;
- dependências de um provedor fictício de estação terrestre;
- simulador de satélite.

Os detalhes do escopo estão documentados em [`docs/01-mission-and-scope.md`](docs/01-mission-and-scope.md).

## Metodologia de estudo

O assessment será desenvolvido progressivamente:

1. Definição da missão e do escopo;
2. modelagem da arquitetura;
3. inventário de ativos;
4. identificação de fluxos de dados e fronteiras de confiança;
5. seleção de ameaças relevantes;
6. registro e priorização de riscos;
7. mapeamento de controles preventivos e de detecção;
8. criação de casos de teste autorizados;
9. análise de logs e evidências;
10. documentação de resposta e lições aprendidas.

Os testes práticos, quando implementados, ocorrerão somente em ambiente próprio, isolado e controlado, usando simuladores e serviços fictícios.

## Referências principais

- SPARTA — Space Attack Research and Tactic Analysis;
- NIST IR 8270 — Cybersecurity for Commercial Satellite Operations;
- NIST IR 8401 — Satellite Ground Segment: Applying the Cybersecurity Framework to Satellite Command and Control;
- NIST SP 800-82r3 — Guide to Operational Technology (OT) Security;
- NIST SP 800-61r3 — Incident Response Recommendations and Considerations;
- NIST SP 800-30 — Guide for Conducting Risk Assessments;
- CCSDS — padrões e recomendações públicas para sistemas de dados espaciais;
- outras referências públicas identificadas em [`references/references.md`](references/references.md).

## Estrutura do projeto

```text
space-ground-segment-assessment/
├── README.md
├── README.pt-BR.md
├── docs/
│   ├── 01-mission-and-scope.md
│   └── 02-system-architecture.md
├── diagrams/
├── data/
├── detections/
├── playbooks/
├── lab/
└── references/
```

A estrutura será ampliada conforme novos artefatos forem desenvolvidos.

## Status

🚧 Em desenvolvimento.

A primeira etapa do projeto consiste em definir a missão, o escopo e a arquitetura do cenário fictício antes da implementação dos simuladores e dos casos de teste.

## Sobre o autor

Este é um projeto independente desenvolvido por Igor S. Nascimento como parte de sua jornada de estudos em cibersegurança espacial, com foco em Ground Segment, Mission Operations Center, Blue Team, DFIR e segurança de ambientes críticos.

Mais projetos e materiais:

- [CEE Orbital](https://l0cu70s.github.io/cee-orbital/)
- [Perfil e portfólio no GitHub](https://github.com/L0CU70S)
- [Guia de estudos SPARTA PT-BR](https://github.com/L0CU70S/sparta-ptbr-study-guide)

## Licença

O código, os textos e os artefatos deste repositório são disponibilizados para fins educacionais. Consulte o arquivo [`LICENSE`](../LICENSE), quando disponível, para obter os termos aplicáveis.

> Aprender, modelar, testar com responsabilidade, documentar e compartilhar.
