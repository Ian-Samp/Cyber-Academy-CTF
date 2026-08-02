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
- 2.1. [SYN - Boas Vindas](#syn---boas-vindas---20-pts)
- 2.2. [SYN/ACK - Conexão com a rede do Ficticious Bank](#synack---conexão-com-a-rede-do-ficticious-bank---20pts)
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
- 3.1. [Identificando colaboradores](#identificando-colaboradores---50-pts)
- 3.2. [Mapeando E-mails](#mapeando-e-mails---50-pts)
- 3.3. [Padrão de e-mails](#padrão-de-e-mails---50-pts)
- 3.4. [Buscando credenciais de colaboradores](#buscando-credenciais-de-colaboradores---50-pts)
- 3.5. [Reutilização de senhas - 50 pts](#reutilização-de-senhas---50-pts)
---
### Identificando colaboradores - 50 pts
Navegue por todos os links do site do Ficticious Bank (https://www.ficticiousbank.com) e identifique os dados dos colaboradores que constam no site. Quantos colaboradores (chefes, executivos, especialistas) você identificou no total? Padrão de resposta: XX (Ex. 99)
#### 🧭 Exploração
Colei o link indicado na URL e naveguei por todos os links clicáveis no site, prestando atenção em qualquer menção à colaboradores.
Em um dos links encontrei:  

![](Prints/Pasted%20image%2020260729015402.png)

Pensei em já responder "7" como Flag, mas lembrei de ter visto alguns ícones de perfil na página inicial, então voltei para verificar:  

![](Prints/Pasted%20image%2020260729020202.png)
#### 🚩 Flag
Imediatamente pensei: "É realmente necessário manter todos esses e-mail de contato à mostra no site, para qualquer um ver?". Minha intuição se demonstrou correta,
como vamos ver a seguir.  

`Flag: 11`

---
### Mapeando E-mails - 50 pts
Qual é o e-mail da consultora Alessandra Melo?  
Padrão de resposta: xxxxxx@xxxxx.xxxxx
#### 🧭 Exploração
![](Prints/Pasted%20image%2020260729020432.png)

Abaixo do perfil de cada colaborador temos um ícone de cartão de negócios. Passar o mouse por cima revela um link para o e-mail de cada um.
#### 🚩 Flag
`Flag: alessandra.melo@ficticiousbank.com`

---
### Padrão de e-mails - 50 pts
Pelos e-mails identificados, qual seria o provável e-mail do CEO do Ficticious Bank?  
Padrão de resposta: xxxxxxx@xxxxx.xxxxx
#### 🧭 Exploração
Analisando os e-mails disponíveis na página, um padrão é faciilmente identificável. Todos os caloboradores possuem o e-mail que segue a estrutura:  
`primeiro_nome.segundo_nome@ficticiousbank.com`
#### 🚩 Flag
Além de qualquer visitante do site ter acesso aos e-mails corporativos da empresa, os e-mails não divulgados podem ser deduzidos, incluindo do próprio CEO José Fernandes. Essa prática abre brecha para que um atacante faça uso de táticas de phishing mais avançadas, como o Spear Phishing, como iremos ver mais adiante. 

`Flag: jose.fernandes@ficticiousbank.com`

---
### Buscando credenciais de colaboradores - 50 pts
Recentemente, o grupo “*P3PP4 H4CK3RS*” divulgou dados de centenas de usuários. O grupo alega possuir informações de mais de 1 milhão de pessoas; entretanto, a fonte não foi identificada. Nossa equipe de Threat Intelligence (Inteligência de Ameaças) conseguiu acesso ao arquivo de demonstração publicado pelos hackers e acredita que os dados possam pertencer a algum aplicativo de entretenimento. Link dos dados: https://pastebin.com/9rm2KeXd Senha de acesso: z2iTHAcrp2 Analise os dados publicados pelos hackers e identifique se algum colaborador do Ficticious Bank teve sua credencial vazada. A resposta deverá ser a senha do usuário, conforme consta nos dados expostos. Exemplo: MinhaSenhaExposta

**Target:** https://pastebin.com/9rm2KeXd
#### 🧭 Exploração
![](Prints/Pasted%20image%2020260729021013.png)

O banco de dados divulgado pelo grupo hacker possui mais de 33.000 (trinta e três mil) linhas de dados extremamente sensíveis de milhares de pessoas (desde nome completo, e-mail e senhas, até CPF e tipo sanguíneo).  
- Para procurar optei utilizar o comando de navegador _CTRL + F_ e pesquisar o nome e sobrenome de cada colaborador;
- Após não achar nada, pesquisei por _"@ficticiousbank.com"_, pois se o e-mail vazado fosse o corporativo que encontrei no site, encontraria qualquer colaborador rapidamente, mas não funcionou, indicando que o e-mail vazado se tratava de um pessoal;
- Pensei por um tempo e percebi um erro de premissa que cometi no início da busca: havia assumido como verdade que o sobrenome no perfil site seria exatamente o
segundo sobrenome do colaborador. Mas isso poderia simplesmente ser falso;
- Voltei ao primeiro passo e pesquisei apenas o primeiro nome de cada colaborador, onde eventualmente encontrei o perfil de Martín Paulo Dias.

![](Prints/Pasted%20image%2020260729022311.png)
#### 🚩 Flag
`Flag: kRzM36SU9e`

---
### Reutilização de senhas - 50 pts
Oh nãoooo… Aparentemente, um de nossos colaboradores teve sua credencial vazada pelo grupo “P3PP4 H4CK3RS”. Sempre orientamos o uso de senhas fortes e diferentes para acesso aos sistemas do banco, então, em teoria, ele não deveria reutilizar as mesmas credenciais no e-mail corporativo… Mas será que isso realmente aconteceu? Melhor conferir. Vai que essa conta também foi comprometida. Durante a análise da caixa de entrada do usuário, foi identificado um e-mail suspeito que chama atenção pelo assunto com tom de urgência, solicitando uma verificação imediata de segurança e alertando sobre possível suspensão da conta. Seu objetivo: Acessar a conta de e-mail do usuário e identificar qual é o endereço de e-mail do remetente da mensagem cujo assunto indica uma “Ação Urgente” relacionada à segurança da conta. A resposta deve ser enviada no seguinte formato: exemplo@dominio.com

**Target:** https://webmail.ficticiousbank.com
#### 🧭 Exploração
![](Prints/Pasted%20image%2020260729022835.png)

Já possuo o endereço de e-mail corporativo de Martín Dias, então tento ele em conjunto de sua senha vazada e consigo acesso.  
`martin.dias@ficticiousbank.com`  
`Flag: kRzM36SU9e`

![](Prints/Pasted%20image%2020260729023025.png)

Identifiquei a mensagem suspeita com o assunto indicado logo no topo da caixa de e-mail. 
#### 🚩 Flag
O atacante utiliza a tática de criar sensção urgência para diminuir o senso crítico do alvo:
- "Ação Urgente"
- "imediatamente"
- "dentro de 24 horas"
- "suspensão da conta"

`Flag: seg.info@secure-auth-portal.com`

---
## 🎣 Investigando o phishing

## 🪵 Logs de um servidor web

## 🕹️ Comando e Controle (C2)

## 🚩 Conclusão
