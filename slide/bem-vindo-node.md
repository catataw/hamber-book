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

Os sistemas para web desenvolvidos sobre plataforma .NET, Java, PHP, Ruby ou Python possuem uma característica em comum: eles paralisam um processamento enquanto utilizam um I/O no servidor. **Essa paralisação é conhecida como modelo bloqueante (Blocking-Thread)**. Em um servidor web podemos visualizá-lo de forma ampla e funcional. Vamos considerar que cada processo é requisição feita pelo usuário. Com o decorrer da aplicação, novos usuários vão acessando-a, gerando uma requisição no servidor. **Um sistema bloqueante enfileira cada requisição e depois as processa, uma a uma, não permitindo múltiplos processamentos delas**

---
<br><br><br><br>

.center.half[![ManieraTradicional](https://raw.githubusercontent.com/catataw/hamber-book/master/asserts/ManieraTradicional.png)]

---
<br><br><br><br>

[center-aligned image](https://raw.githubusercontent.com/catataw/hamber-book/master/asserts/ManeiraNode.png)

---

## E assim nasceu o Node.js

Foi baseado neste problema que, no final de 2009, Ryan Dahl com a ajuda inicial de 14 colaboradores criou o Node.js. Esta tecnologia possui um modelo inovador, sua  arquitetura é **totalmente non-blocking thread (não-bloqueante)**, apresentando uma boa performance com consumo de memória e utilizando ao máximo e de forma eficiente o poder de processamento dos servidores, principalmente em sistemas que produzem uma alta carga de processamento.

Usuários de sistemas Node estão livres de aguardarem por muito tempo o resultado de seus processos, **e principalmente não sofrerão de dead-locks no sistema**, porque nada bloqueia em sua plataforma e desenvolver sistemas nesse paradigma é simples e prático.

---

Node faz o I/O de forma assíncrona asynchronous para lidar com diferentes situações simultaneas.

<br><br><br><br>

.center![Right-aligned image](https://raw.githubusercontent.com/catataw/hamber-book/master/asserts/fila.jpg)

---

**Por exemplo, se você vai até um fast food e faz o pedido de um cheesebuger você tem de imadiato o pedido feito mas não o lanche, então você espara ele ficar pronto para comer. Neste meio tempo outros pedidos estão sendo feitos na lanchonete para outras pessoas. Imagine que você tenha que esperar o registro do seu cheeseburger, bloqueando outras pessoas porque o seu pedido tem que ser feito para o de outra começar enquanto preparam o seu.** 

Isso é chamado de I/O bloqueante porque todo o I/O (cozinhar cheeseburgers) acontece um a um enfileirando tudo. O Node, por sua vez é não-bloqueante, significando que os pedidos serão feitos e entregues quando estiverem prontos.

---

Quais são alguns exemplos de I/O? Bom… aqui tem um diagrama de uma aplicação que eu fiz com node e ela mostra várias fontes de I/O:

<br><br><br><br>

![Default-aligned image](https://raw.githubusercontent.com/catataw/hamber-book/master/asserts/diagrama-servidor.png)

---

## Que problema o Node pode resolver?

Node estabeleceu o objetivo número um que é **“fornecer uma maneira fácil para construir programas de rede escaláveis”**. Qual é o problema com os programas servidores atuais? Vamos fazer os cálculos. *Em linguagens como Java™ e PHP, cada conexão cria uma nova thread que potencialmente tem anexado 2 MB de memória com ela. Em um sistema que tenha 8 GB de RAM, isso põe o número máximo teórico de conexões concorrentes a cerca de 4.000 usuários*.

E quando o número de usuários aumenta, se você quer que sua aplicação web suporte mais usuários, você tem que adicionar mais e mais servidores. Somado a estes custos também podem haver possíveis problemas técnicos: um usuário pode usar diferentes servidores para cada requisição, então cada recurso compartilhado deve ser compartilhado para todos os servidores. Por todas estas rações, o gargalho em toda a arquitetura de aplicações web (incluindo velocidade de tráfego, velocidade do processador e velocidade da memória) é o número de conexões concorrentes que o servidor pode manipular.

---

Node resolve esta questão trocando a maneira como a conexão é tratada no servidor. Ao invés de criar uma nova OS thread a cada conexão (e alocar a memória anexa a ela), cada conexão dispara um evento executado dentro da engine de processos do Node. Node afirma que nunca vai dar deadlock, já que não há bloqueios permitidos, e ele não bloqueia diretamente para chamadas de I/O. Node também alega que um servidor rodando ele pode suportar dezenas de milhares de conexões simultâneas.

Então, agora que você tem um programa que pode manipular dezenas de milhares de conexões simultâneas, o que você pode realmente fazer com o Node? Seria incrível se você tivesse uma aplicação web que necessitasse desta quantidade de conexões. Este é um daqueles tipos de problema: “se você tem um problema, não é mais um problema”.

---

## O que Node definitivamente não é?

Sim, *Node é um servidor de programas*. Entretanto o produto base do Node definitivamente não é como o Apache ou o Tomcat. Estes servidores são basicamente servidores ready-to-install e estão prontos para instalar aplicativos instantâneamente.

Você pode subir e rodar um servidor em um minuto com estes produtos. Node definitivamente não é isso. Parecido com como o Apache pode adicionar um módulo PHP para permitir desenvolvedores criarem páginas da web dinâmicas, e um módulo SSL para conexões seguras,*

Node tem o conceito de módulos que podem ser adicionados no núcleo do Node. Há literalmente centenas de módulos para rodarem com o Node*, e a comunidade é bastante ativa em produzir, publicar e atualizar dezenas de módulos por dia.

---

# Instalação e Configuração

Instalando Node.js: Primeiro passo, acesse o site oficial: (http://nodejs.org) e clique em Download, para usuários do Windows e MacOSX, basta baixar os
seus instaladores e executá-los normalmente. Para quem já utiliza Linux com Package Manager instalado, acesse esse link (https://github.com/joyent/node/wiki/ Installing-Node.js-via-package-manager) que é referente as instruções sobre como instalá-lo em diferentes sistemas. Instale o Node.js de acordo com seu sistema, caso não ocorra problemas, basta abrir o seu terminal console ou prompt de comando e digitar o comando: node -v && npm -v para ver as respectivas versões do Node.js e NPM (Node Package Manager) que foram instaladas

```
  console.log("Hello World")
```

---

# NPM

Assim como o Gems do Ruby ou o Maven do Java, o Node.js também possui o seu próprio gerenciador de pacotes, ele se chama NPM (Node Package Manager). Ele
se tornou tão popular pela comunidade, que foi a partir da versão 0.6.0 do Node.js que ele se integrou no instalador do Node.js, tornando-se o gerenciador default.

 - npm install nome_do_módulo : instala um módulo no projeto. 
 - npm install -g nome_do_módulo : instala um módulo global.
 - npm install nome_do_módulo --save : instala o módulo no projeto, atualizando o package.json na lista de dependências.
 - npm list : lista todos os módulos do projeto.
 - npm list -g : lista todos os módulos globais.
 - npm remove nome_do_módulo : desinstala um módulo do projeto.

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

A diferença entre o hello.js e o human.js esta na maneira de como eles serão carregados. Em hello.js carregamos uma única função modular e em human.js é carregado um objeto com funções modulares

Para entender melhor na prática crie o código app.js para carregar esses módulos, seguindo o código abaixo:

```
  var hello = require('./hello');
  var human = require('./human');

  hello('Olá pessoal!');
  human.hello('Olá galera!');
```

Percebam o quão simples é programar com Node.js! Com base nesses pequenos trechos de código já foi possível criar um código altamente escalável e modular que utiliza as boas práticas do padrão CommonJS.

---

## Criando nossa primeira aplicação web


Node.js é multiprotocolo, ou seja, com ele será possível trabalhar com os protocolos: HTTP,HTTPS,FTP,SSH,DNS,TCP,UDP,WebSocket se também exist em outros protocolos, que são disponíveis através de módulos não-oficiais criados pela comunidade

oda aplicação web necessita de um servidor para disponibilizar todos os seus recursos. Na prática,como Node.js você desenvolve uma "aplicaçã omiddleware”, ou seja,além de programaras funcionalidades da sua aplicação, você também programa códigos de configuração de infraestrutura da sua aplicação

---

Primeiro usaremos apenas o módulo nativo HTTP, pois precisamos entender todo o conceito desse módulo, visto que todos os frameworks citados acima o utilizam como estrutura inicial em seus projetos. Abaixo mostro a vocês uma clássica aplicação Hello World. Crie o arquivo hello_server.js com o seguinte conteúdo:

````
var http = require('http');

var server = http.createServer(function(request, response){
  response.writeHead(200, {"Content-Type": "text/html"});
  response.write("<h1>Hello World!</h1>");
  response.end();
});

server.listen(3000);

````
---

O método listen também é assíncrono e você só saberá que o servidor está de pé quando o Node invocar sua função de callback.
Se você ainda está começando com JavaScript,* pode estranhar um pouco ficar passando como parâmetro uma function por todos os lados,mas isso é algo muito comum no mundo Javascript.* Como sintaxe alternativa, caso o seu código fique muito complicado em encadeamentos de diversos blocos, podemos isolá-lo em funções com nomes mais significativos, por exemplo:


```
var http = require('http');

var atendeRequisicao = function(request, response) {
  response.writeHead(200, {"Content-Type": "text/html"});
  response.write("<h1>Hello World!</h1>");
  response.end();
}
var server = http.createServer(atendeRequisicao);

var servidorLigou = function() {
  console.log('Servidor Hello World rodando!');
}

server.listen(3000, servidorLigou);

```

---

## Desafio

Desafio: Implementar um roteador de url

- Crie 3 arquivos HTML: artigos.html, contato.html e erro.html 

- Coloque qualquer conteúdo para cada página html;

- Ao digitar no browser o path: /artigos deve renderizar artigos.html;

- Ao digitar qualquer path diferente de /artigos e /contato deve renderizar
erro.html;

- A rota principal "/” deve renderizar artigos.html;

---

O resultado desse desafio se encontra na página github deste livro:
https://github.com/caio-ribeiro-pereira/livro-nodejs/tree/master/desafio-1

---

## Assincrono

É importante focar no uso das chamadas assíncronas quando trabalhamos com Node.js, assim como entender quando elas são invocadas. O código abaixo exemplifia as diferen ças entre uma fun ção síncrona e assíncrona em relação a linha do tempo que ela são executadas. Basicamente criaremos um loop de 5 itera ções, a cada itera ção será criado um arquivo texto com o mesmo conteúdo Hello Node.js! .

Primeiro vamos come çar com o código síncrono. Crie o arquivo *text_sync.js* com o código abaixo:

```
var fs = require( ' fs ' );

for(var i = 1; i <= 5; i++) {
  var file = "sync-txt" + i + ".txt";
  var out = fs.writeFileSync(file, "Hello Node.js!");
  console.log(out);
}

```

---

Agora vamos criar o arquivo text_async.js, com seu respectivo código, diferente apenas na forma de chamar a fun ção writeFileSync, que será a versãoa ssíncrona writeFile, recebendo uma função como argumento:

```
var fs = require( ' fs ' );

for(var i = 1; i <= 5; i++) {
  var file = "async-txt" + i + ".txt";
  fs.writeFile(file, "Hello Node.js!", function(err, out) {
    console.log(out);
  });
}

```

Vamos rodar? Execute os comandos: node text_sync e depois node text_async. Se for gerado 10 arquivos no mesmo diretório do código-fonte, então deu tudo certo. 


---

## Threads vs A ssincronismos

Por mais que as funções assíncronas possam executar em paralelo várias tarefas, *elas jamais serão consideradas uma Thead* (por exemplo Threads do Java). A diferença é que *Theads são manipuláveis pelo desenvolvedor*, ou seja, você pode pausar a execução de uma Thead ou fazê-la esperar o término de uma outra. *Chamadas assíncronas apenas invocam suas funções numa ordem de que você não tem controle*, e você só sabe quando uma chamada terminou quando seu callback é executado.

Pode parecer vantajoso ter o controle sobre as Theads a favor de um sistema que executa tarefas em paralelo, mas pouco domínio sobre eles pode transformar seu sistema em um caos de travamentos dead-locks, afinal *Theads são executadas de forma bloqueante*. Este é o grande diferencial das chamadas assíncronas, elas executam em paralelo suas funções sem travar processamento das outras e principalmente sem bloquear o sistema principal

Talvez você ainda não esteja convencido. A próxima se ção vai lhe mostrar como e quando utilizar bibliotecas assíncronas não-bloqueantes, tudo isso através de teste prático.

---
## A ssincronismo versus S incronismo

Para isso crie 3 arquivos: processamento.js, leitura_async.js e leitura_sync.js

leitura_async.js 

```
var fs = require( ' fs ' );

var leituraAsync = function(arquivo){
  console.log("Fazendo leitura assíncrona");
  var inicio = new Date().getTime();
  fs.readFile(arquivo)
  var fim = new Date().getTime();
  console.log("Bloqueio assíncrono: "+(fim - inicio) + "ms");
};

module.exports = leituraAsync;

```
---
Em seguida criaremos o código leitura_sync.js que faz leitura síncrona:

```
var fs = require( ' fs ' );

var leituraSync = function(arquivo){
  console.log("Fazendo leitura síncrona");
  var inicio = new Date().getTime();
  fs.readFileSync(arquivo);
  var fim = new Date().getTime();
  console.log("Bloqueio síncrono: "+(fim - inicio) + "ms");
};

module.exports = leituraSync;

```

---

Para fializar carregamos os dois tipos de leituras dentro do código processamento.js:

```
var http = require( ' http ' );
var fs = require( ' fs ' );
var leituraAsync = require( ' ./leitura_async ' );
var leituraSync = require( ' ./leitura_sync ' );
var arquivo = "./node.exe";
var stream = fs.createWriteStream(arquivo);
var download = "http://nodejs.org/dist/latest/node.exe";

http.get(download, function(res) {
  console.log("Fazendo download do Node.js");
  res.on( ' data ' , function(data){
    stream.write(data);
  });
  res.on( ' end ' , function(){
    stream.end();
    console.log("Download finalizado!");
    leituraAsync(arquivo);
    leituraSync(arquivo);
  });
});

```
---
Rode o comando node processamento.js para executar o benchmark. E agora, fiou clara a diferen ça entre o modelo bloqueante e o não-bloqueante?


Veja a pequena, porém signifiante diferen ça de tempo entre as duas funções de leitura.

Se esse teste foi com um arquivo de mais ou menos 50 MB, imagine esse teste em larga escala, lendo múltiplos arquivos de 1 GB ao mesmo tempo ou realizando múltiplos uploads em seu servidor? Esse é um dos pontos fortes do Node.js!

---

## Entendendo o Event-Loop

Isso acontece devido ao fato, de que uma chamada de I/O é considerada um tarefa muito custosa para um computador realizar. Tão custosa que chega a ser perceptível para um usuário, por exemplo, quando ele tenta abrir um arquivo de 1 GB e o sistema operacional trava alguns segundos para abri-lo. 

Vendo o contexto de um servidor, por mais potente que seja seu hardware, eles terão os mesmos bloqueios perceptíveis pelo usuário, a diferença é que um servidor estará lidando com milhares usuários requisitando I/O, com a grande probabilidade de ser ao mesmo tempo

É por isso que o Node.js trabalha com assincronismo. Ele permite que você desenvolva um sistema totalmente orientado a eventos, tudo isso graças ao Event-loop

---

![Default-aligned image](https://raw.githubusercontent.com/catataw/hamber-book/master/asserts/eventoloop.png)

Basicamente ele é um *loop infiito*, que em cada iteração verifia se existem novos eventos em sua fia de eventos. Tais eventos somente aparecem nesta fia quando são emitidos durante suas interações na aplicação.

Quando um determinado código emite um evento, o mesmo é enviado para a fia de eventos para que o Event-loop executeo, e em seguida retorne seu callback. Tal callback pode ser executado através de uma função de escuta, semanticamente conhecida pelo nome: on().

---

## Evitando Callbacks Hell

De fato, vimos o quanto é vantajoso e performático trabalhar de forma assíncrona, porém em certos momentos, inevitavelmente implementaremos diversas funções assíncronas, que serão encadeadas uma na outra através das suas funções callback.

callback_hell.js

```
var fs = require( ' fs ' );

fs.readdir(__dirname, function(erro, contents) {
  if (erro) { throw erro; }
  contents.forEach(function(content) {
    var path = ' ./ ' + content;
    fs.stat(path, function(erro, stat) {
      if (erro) { throw erro; }
      if (stat.isFile()) {
        console.log( ' %s %d bytes ' , content, stat.size);
      }
    });
  });
});

```
Reparem na quantidade de callbacks encadeados que existem em nosso código.Detalhe: ele apenas faz uma simples leitura dos arquivos de seu diretório e imprime na tela seu nome e tamanho em bytes

---

Uma boa prática de código Javascript é criar funções que expressem seu objetivo e de forma isoladas, salvando em variável e passando-as como callback. Ao invés de criar funções anônimas.

callback_heaven.js 

```
var fs = require( ' fs ' );
var lerDiretorio = function() {
  fs.readdir(__dirname, function(erro, diretorio) {
    if (erro) return erro;
    diretorio.forEach(function(arquivo) {
      ler(arquivo);
    });
  });
};

var ler = function(arquivo) {
  var path = ' ./ ' + arquivo;
  fs.stat(path, function(erro, stat) {
    if (erro) return erro;
    if (stat.isFile()) {
      console.log( ' %s %d bytes ' , arquivo, stat.size);
    }
  });
};

lerDiretorio();

```
---

https://www.youtube.com/watch?v=PDlPgalYQeM