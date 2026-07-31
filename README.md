# Cyber Academy - Capture The Flag

> **Data:** 07/2026  
> **Scoreboard:** 15º posição de 778 participantes  
> **Categorias:** CSIRT, Web Exploitation, Log Analysis,

---

## Sumário

1. [🔍 Introdução](#-introdução)
2. [🤝 Handshake!](#-handshake)
3. [🔐 Proteja suas senhas!](#-proteja-suas-senhas)
4. [🎣 Investigando o phishing](#-investigando-o-phishing)
5. [🪵 Logs de um servidor web](#-logs-de-um-servidor-web)
6. [🕹️ Comando e Controle (C2)](#️-comando-e-controle-c2)
7. [🚩 Conclusão](#-conclusão)

---

## 🔍 Introdução

* 1.1. [Write-Up](#write-up)
* 1.2. [Contexto](#contexto)
* 1.3. [Regras](#regras)
    * 1.3.1. [Desafios](#desafios)
    * 1.3.2. [Respostas incorretas](#respostas-incorretas)
    * 1.3.3. [Dicas](#dicas)

### Write-Up
Este documento reúne o write-up do Capture The Flag (CTF) de encerramento do curso Cyber Academy 2026, promovido pela Febraban em parceria com a GoHacking.
O objetivo desta documentação é registrar a metodologia e o raciocínio analítico empregados na resolução dos desafios. Mais do que apresentar apenas as respostas finais (flags), busquei detalhar todo o processo de investigação, os percalços encontrados pelo caminho e as estratégias utilizadas para superar cada obstáculo.

### Contexto
O grupo "*P3PP4 H4CK3R5*" tem divulgado arquivos contendo dados pessoais e credenciais de clientes e funcionários do Ficticious Bank (FB), tais vazamentos coincidem com alguns incidentes de segurança identificados pelo nosso CSIRT.

Após uma investigação inicial, foi possível identificar uma estação de trabalho de um dos colaboradores do banco se comunicando com um site suspeito (provável Central de Comando e Controle - C2 do grupo de hackers), além de algumas evidências de exfiltração de dados. Acreditamos que esse foi o vetor inicial do ataque.

O Ficticious Bank é uma fintech de pequeno porte em plena expansão. Um ataque desta magnitude causaria um sério impacto à reputação do banco e consequentemente perda de clientes. Em um esforço para tentar identificar as falhas exploradas pelos hackers e evitar a paralisação de suas atividades, sua equipe recebeu a tarefa de realizar um teste de segurança nos sistemas do banco com o intuito de identificar possíveis falhas, indícios de comprometimento e artefatos maliciosos instalados pelo grupo hacker. O Ficticious Bank conta com o empenho e dedicação da sua equipe para resolver este problema!

### Regras

#### Desafios
Quando o evento for iniciado pelo instrutor, os desafios estarão disponíveis. Para demonstrar a conclusão de cada tarefa você deve fornecer a informação solicitada (Flag) no enunciado do desafio. As flags são case sensitive e podem estar no formato `GoHacking{MinhaFlagCaseSensitive}`.

#### Respostas incorretas
A partir da 2ª resposta, você perderá 1 ponto para cada tentativa incorreta e será penalizado até 5 vezes (Máx 5 pts).

#### Dicas
Serão disponibilizadas dicas para cada desafio. As dicas podem ser requisitadas para auxiliar na resolução da atividade e não serão descontados pontos por isto; entretanto, o número de dicas solicitadas será o primeiro critério de desempate entre os participantes.

---
