# 1. Missão e Escopo

🇧🇷 Português | [🇺🇸 English](01-mission-and-scope.md)

## Missão

AuroraWatch-1 é uma missão fictícia de observação da Terra em órbita baixa terrestre (LEO), criada para fins de estudo em cibersegurança e construção de portfólio.

A missão foi concebida para coletar imagens ambientais fictícias e transmitir telemetria, dados de missão e alertas operacionais para seu Segmento Terrestre (Ground Segment).

O cenário concentra-se no ambiente operacional terrestre da missão, incluindo o Mission Operations Center, os acessos dos operadores, os serviços de suporte à missão, as interfaces com a estação terrestre e determinadas dependências de terceiros.

## Dentro do escopo

Os seguintes componentes, processos e dependências fazem parte do escopo:

- Mission Operations Center (MOC);
- estações de trabalho dos operadores;
- servidores de controle da missão;
- sistemas de processamento de telemetria;
- armazenamento de dados de missão e telemetria;
- gateway da estação terrestre;
- gerenciamento de identidade e acesso;
- acesso administrativo privilegiado e remoto;
- monitoramento de segurança, registro de eventos e alertas;
- interfaces com um provedor terceirizado fictício de estação terrestre;
- fluxos de telecomando e telemetria;
- conexões de rede e fronteiras de confiança relevantes entre os componentes acima.

## Fora do escopo

Os seguintes componentes e atividades estão fora do escopo deste projeto:

- implementação física do satélite;
- testes de segurança em hardware da espaçonave e sistemas embarcados;
- testes ou transmissões reais em radiofrequência (RF);
- testes ou exploração de sistemas reais;
- acesso a satélites, estações terrestres, sistemas de controle de missão ou infraestruturas de terceiros reais;
- segurança de veículos lançadores e locais de lançamento;
- dados reais de organizações, clientes, colaboradores ou operações;
- divulgação ou coordenação de vulnerabilidades reais;
- avaliação de conformidade regulatória, contratual, de segurança operacional ou de garantia de missão;
- afirmações sobre a postura de segurança de qualquer organização, missão ou provedor real.

## Premissas

Esta avaliação é baseada nas seguintes premissas:

- AuroraWatch-1 é uma missão fictícia de observação da Terra em órbita baixa terrestre;
- o satélite, as organizações, os usuários, os sistemas e os provedores descritos no cenário são fictícios;
- os operadores acessam os sistemas da missão por meio de estações de trabalho controladas;
- o Mission Operations Center hospeda sistemas que apoiam comando, telemetria, monitoramento e operações de missão;
- um provedor terceirizado fictício opera ou apoia a interface com a estação terrestre;
- os telecomandos e a telemetria da missão são trocados por meio de interfaces lógicas definidas;
- identidades, funções e privilégios de acesso podem ser representados no laboratório;
- logs podem ser gerados e coletados a partir dos sistemas simulados;
- os controles de segurança propostos são recomendações de projeto e não foram verificados de forma independente;
- o laboratório utilizará simuladores, dados sintéticos e serviços isolados pertencentes ou controlados pelo autor.

## Objetivos da avaliação

O projeto tem como objetivos:

- documentar uma arquitetura simplificada de Ground Segment;
- identificar ativos, processos, fluxos de dados e fronteiras de confiança;
- analisar ameaças selecionadas a sistemas espaciais utilizando referências públicas;
- criar um registro de riscos para fins educacionais;
- propor controles preventivos, de detecção e de resposta;
- definir casos de teste seguros e autorizados;
- gerar e analisar eventos de segurança sintéticos;
- documentar achados, limitações e lições aprendidas;
- identificar oportunidades de melhoria e de reteste.

## Abordagem da avaliação

O projeto seguirá uma abordagem progressiva, orientada pela documentação:

1. Definir a missão e o escopo;
2. modelar a arquitetura e as fronteiras de confiança;
3. inventariar ativos e dependências;
4. documentar os fluxos de telecomando e telemetria;
5. identificar ameaças selecionadas e cenários de risco;
6. relacionar os riscos aos controles propostos;
7. implementar somente os componentes necessários do laboratório;
8. executar testes autorizados no ambiente isolado;
9. coletar e analisar evidências sintéticas;
10. documentar achados, recomendações e lições aprendidas.

O projeto não se apresenta como um teste de intrusão, uma operação de red team, uma certificação, uma avaliação de conformidade ou uma avaliação completa de cibersegurança.

## Limitações

Esta é uma avaliação educacional simplificada e não representa uma avaliação real de segurança.

O cenário não reproduz toda a complexidade técnica, operacional, física, de radiofrequência, orbital, de software, de hardware, de segurança operacional, regulatória, da cadeia de suprimentos ou de garantia de missão de um sistema espacial real.

Os resultados dependerão das premissas, da arquitetura, dos simuladores, dos dados sintéticos, dos casos de teste e dos controles implementados no laboratório. Os achados não devem ser generalizados para missões, organizações, produtos, provedores ou sistemas espaciais reais.

## Declaração sobre testes responsáveis

Todos os testes práticos associados a este projeto serão realizados somente contra serviços fictícios, dados sintéticos e sistemas pertencentes ou explicitamente controlados pelo autor.

O projeto não terá como alvo satélites reais, estações terrestres, organizações, provedores, infraestrutura pública, sistemas de produção ou serviços de terceiros.

## Status do documento

- Status: Rascunho / em desenvolvimento
- Cenário: AuroraWatch-1
- Ambiente: Laboratório fictício e isolado
- Tipo de avaliação: Projeto educacional de portfólio
- Última revisão: 13 de setembro de 2026
