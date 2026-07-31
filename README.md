# Cyber Academy - Capture The Flag

> **Data:** 07/2026  
> **Pontuação:** 2010 pts / 0 Dicas  
> **Scoreboard:** 15º posição de 789 participantes  
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
## 🤝 Handshake!
- 2.1. [SYN - Boas Vindas](#syn-boas-vindas-20-pts)
- 2.2. [SYN/ACK - Conexão com a rede do Ficticious Bank](#syn/ack-conexão-com-a-rede-do-ficticious-bank-20pts)
---
### SYN - Boas Vindas - 20 pts
Olá! Seja bem-vindo! Esperamos que você nos ajude a encontrar as falhas que podem ter iniciado este ataque! Precisamos corrigi-las o quanto antes para restaurar nossos backups em segurança. Como sinal de boa fé, segue a sua primeira FLAG do Game: `GoHacking{BemVindoJovemPadawan}` Envie essa flag como resposta no campo abaixo.
#### 🚩 Flag
`Flag: GoHacking{BemVindoJovemPadawan}`

---
### SYN/ACK - Conexão com a rede do Ficticious Bank - 20 pts
Para validar a sua conexão com a rede do Ficticious Bank, siga as etapas a seguir: 
1 - Abra o seu navegador/browser; 
2 - Acesse a página https://www.ficticiousbank.com 
3 - A flag de resposta desse desafio estará na página inicial e no título da página
#### 🧭 Exploração
Abrindo o link da Fictious Bank, nos deparamos com a Flag na página inicial:
![](Prints/Pasted%20image%2020260729014843.png)

#### 🚩 Flag
Este primeiro grupo de desafios foram só para apresentar o CTF. Estamos apenas começando!

`Flag: GoHacking{ToNaRedeDoFicticiousBank}`

---
## 🔐 Proteja suas senhas!
- 3.1. [Identificando colaboradores](#identificando-colaboradores-50-pts)
- 3.2. [Mapeando E-mails](#mapeando-e-mails-50-pts)
- 3.3. [Padrão de e-mails](#padrão-de-e-mails-50-pts)
- 3.4. [Buscando credenciais de colaboradores](#buscando-credenciais-de-colaboradores-50-pts)
- 3.5. [Reutilização de senhas - 50 pts](#reutilização-de-senhas-50-pts)
---
### Identificando colaboradores - 50 pts
Navegue por todos os links do site do Ficticious Bank (https://www.ficticiousbank.com) e identifique os dados dos colaboradores que constam no site. Quantos colaboradores (chefes, executivos, especialistas) você identificou no total? Padrão de resposta: XX (Ex. 99)
#### 🧭 Exploração
Colei o link indicado na URL e naveguei por todos os links clicáveis no site, prestando atenção em qualquer menção à colaboradores.
Em um dos links encontrei:
![](Prints/Pasted%image%20260729015402.png)
Pensei em já responder "7" como Flag, mas lembrei de ter visto alguns ícones de perfil na página inicial, então voltei para verificar:
![](Prints/Pasted%image%20260729020202.png)
#### 🚩 Flag


### Mapeando E-mails - 50 pts
### Padrão de e-mails - 50 pts
### Buscando credenciais de colaboradores - 50 pts
### Reutilização de senhas - 50 pts
