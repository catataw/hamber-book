# Bem-vindo ao mundo Node.js

---

# Agenda

- Arquitetura
- Instalação e Configuração
- NPM
- Hello Word
- Desafio
- Assincrono

---

# Arquitetura

Os sistemas para web desenvolvidos sobre plataforma .NET, Java, PHP, Ruby ou Python possuem uma característica em comum: eles paralisam um processamento enquanto utilizam um I/O no servidor. Essa paralisação é conhecida como modelo bloqueante (Blocking-Thread). Em um servidor web podemos visualizá-lo de forma ampla e funcional. Vamos considerar que cada processo é requisição feita pelo usuário. Com o decorrer da aplicação, novos usuários vão acessando-a, gerando uma requisição no servidor. Um sistema bloqueante enfileira cada requisição e depois as processa, uma a uma, não permitindo múltiplos processamentos delas

---

![Default-aligned image](https://raw.githubusercontent.com/catataw/hamber-book/master/asserts/ManieraTradicional.png)

---

![Default-aligned image](https://raw.githubusercontent.com/catataw/hamber-book/master/asserts/ManeiraNode.png)

---

## E assim nasceu o Node.js

Foi baseado neste problema que, no final de 2009, Ryan Dahl com a ajuda inicial de 14 colaboradores criou o Node.js. Esta tecnologia possui um modelo inovador, sua  arquitetura é totalmente non-blocking thread (não-bloqueante), apresentando uma boa performance com consumo de memória e utilizando ao máximo e de forma eficiente o poder de processamento dos servidores, principalmente em sistemas que produzem uma alta carga de processamento. Usuários de sistemas Node estão livres de aguardarem por muito tempo o resultado de seus processos, e principalmente não sofrerão de dead-locks no sistema, porque nada bloqueia em sua plataforma e desenvolver sistemas nesse paradigma é simples e prático.

---

Quais são alguns exemplos de I/O? Bom… aqui tem um diagrama de uma aplicação que eu fiz com node e ela mostra várias fontes de I/O:

![Default-aligned image](https://raw.githubusercontent.com/catataw/hamber-book/master/asserts/diagrama-servidor.png)

---

Node faz o I/O de forma assíncrona asynchronous para lidar com diferentes situações simultaneas. Por exemplo, se você vai até um fast food e faz o pedido de um cheesebuger você tem de imadiato o pedido feito mas não o lanche, então você espara ele ficar pronto para comer. Neste meio tempo outros pedidos estão sendo feitos na lanchonete para outras pessoas. Imagine que você tenha que esperar o registro do seu cheeseburger, bloqueando outras pessoas porque o seu pedido tem que ser feito para o de outra começar enquanto preparam o seu. Isso é chamado de I/O bloqueante porque todo o I/O (cozinhar cheeseburgers) acontece um a um enfileirando tudo. O Node, por sua vez é não-bloqueante, significando que os pedidos serão feitos e entregues quando estiverem prontos.

---

## Que problema o Node pode resolver?

Node estabeleceu o objetivo número um que é “fornecer uma maneira fácil para construir programas de rede escaláveis”. Qual é o problema com os programas servidores atuais? Vamos fazer os cálculos. *Em linguagens como Java™ e PHP, cada conexão cria uma nova thread que potencialmente tem anexado 2 MB de memória com ela. Em um sistema que tenha 8 GB de RAM, isso põe o número máximo teórico de conexões concorrentes a cerca de 4.000 usuários*.

E quando o número de usuários aumenta, se você quer que sua aplicação web suporte mais usuários, você tem que adicionar mais e mais servidores. Somado a estes custos também podem haver possíveis problemas técnicos: um usuário pode usar diferentes servidores para cada requisição, então cada recurso compartilhado deve ser compartilhado para todos os servidores. Por todas estas rações, o gargalho em toda a arquitetura de aplicações web (incluindo velocidade de tráfego, velocidade do processador e velocidade da memória) é o número de conexões concorrentes que o servidor pode manipular.

---

Node resolve esta questão trocando a maneira como a conexão é tratada no servidor. Ao invés de criar uma nova OS thread a cada conexão (e alocar a memória anexa a ela), cada conexão dispara um evento executado dentro da engine de processos do Node. Node afirma que nunca vai dar deadlock, já que não há bloqueios permitidos, e ele não bloqueia diretamente para chamadas de I/O. Node também alega que um servidor rodando ele pode suportar dezenas de milhares de conexões simultâneas.

Então, agora que você tem um programa que pode manipular dezenas de milhares de conexões simultâneas, o que você pode realmente fazer com o Node? Seria incrível se você tivesse uma aplicação web que necessitasse desta quantidade de conexões. Este é um daqueles tipos de problema: “se você tem um problema, não é mais um problema”.

---

## O que Node definitivamente não é?

Sim, Node é um servidor de programas. Entretanto o produto base do Node definitivamente não é como o Apache ou o Tomcat. Estes servidores são basicamente servidores ready-to-install e estão prontos para instalar aplicativos instantâneamente. Você pode subir e rodar um servidor em um minuto com estes produtos. Node definitivamente não é isso. Parecido com como o Apache pode adicionar um módulo PHP para permitir desenvolvedores criarem páginas da web dinâmicas, e um módulo SSL para conexões seguras,* Node tem o conceito de módulos que podem ser adicionados no núcleo do Node. Há literalmente centenas de módulos para rodarem com o Node*, e a comunidade é bastante ativa em produzir, publicar e atualizar dezenas de módulos por dia.

---

# Instalação e Configuração

Instalando Node.js: Primeiro passo, acesse o site oficial: (http://nodejs.org) e clique em Download, para usuários do Windows e MacOSX, basta baixar os
seus instaladores e executá-los normalmente. Para quem já utiliza Linux com Package Manager instalado, acesse esse link (https://github.com/joyent/node/wiki/ Installing-Node.js-via-package-manager) que é referente as instruções sobre como instalá-lo em diferentes sistemas. Instale o Node.js de acordo com seu sistema, caso não ocorra problemas, basta abrir o seu terminal console ou prompt de comando e digitar o comando: node -v && npm -v para ver as respectivas versões do Node.js e NPM (Node Package Manager) que foram instaladas

code
  console.log("Hello World")
code

---

# NPM

Assim como o Gems do Ruby ou o Maven do Java, o Node.js também possui o seu próprio gerenciador de pacotes, ele se chama NPM (Node Package Manager). Ele
se tornou tão popular pela comunidade, que foi a partir da versão 0.6.0 do Node.js que ele se integrou no instalador do Node.js, tornando-se o gerenciador default.

 - npm install nome_do_módulo : instala um módulo no projeto. 
 - npm install -g nome_do_módulo : instala um módulo global.
 - npm install nome_do_módulo --save : instala o módulo no projeto, atualizando o package.json na lista de dependências.
• npm list : lista todos os módulos do projeto.
• npm list -g : lista todos os módulos globais.
• npm remove nome_do_módulo : desinstala um módulo do projeto.

---

## Entendendo o package.json

Todo projeto Node.js é chamado de módulo, mas o que é um módulo? => módulo, biblioteca e framework

O termo módulo surgiu do conceito de que a arquitetura do Node.js é modular. E todo módulo é acompanhado de um arquivo descritor, conhecido pelo nome de package.json 

Este arquivo é essencial para um projeto Node.js. Um package.json mal escrito pode causar bugs ou impedir o funcionamento correto do seu módulo, pois ele possui alguns atributos chaves que são compreendidos pelo Node.js e NPM.


Os módulos no Node.js trabalham com 3 níveis de versionamento. Por exemplo,a versão 1.2.3 estadivididanosníveis: Major (1),Minor (2)ePatch(3).
---

# Hello Word

---

## CommonJS, Como ele funciona?

O Node.js utiliza nativamente o padrão CommonJS para organização e carregamento de módulos. Na prática, diversas funções deste padrão será utilizada com frequência em um projeto Node.js. A função require('nome-do-modulo') é um exemplo disso, ela carrega um módulo

Abaixo apresento-lhe dois exemplos de códigos que utilizam esse padrão do CommonJS, primeiro crie o código hello.js 

```
module.exports = function(msg) {
  console.log(msg);
};
```

E também crie o código human.js com o seguinte código:

```
exports.hello = function(msg) {
  console.log(msg);
};
```

---
A diferença entre o hello.js e o human.js esta na maneira de como eles serão carregados. Em hello.js carregamos uma única função modular e em
human.js é carregado um objeto com funções modulares

Para entender melhor na prática crie o código app.js para carregar esses módulos, seguindo o código abaixo:

```
  var hello = require('./hello');
  var human = require('./human');

  hello('Olá pessoal!');
  human.hello('Olá galera!');
```

---

Percebam o quão simples é programar com Node.js! Com base nesses pequenos trechos de código já foi possível criar um código altamente escalável e modular que utiliza as boas práticas do padrão CommonJS.

----