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

![Default-aligned image](ManieraTradicional.png)

---

![Default-aligned image](https://raw.githubusercontent.com/catataw/hamber-book/master/asserts/ManeiraNode.png)

## E assim nasceu o Node.js

Foi baseado neste problema que, no final de 2009, Ryan Dahl com a ajuda inicial de 14 colaboradores criou o Node.js. Esta tecnologia possui um modelo inovador, sua  arquitetura é totalmente non-blocking thread (não-bloqueante), apresentando uma boa performance com consumo de memória e utilizando ao máximo e de forma eficiente o poder de processamento dos servidores, principalmente em sistemas que produzem uma alta carga de processamento. Usuários de sistemas Node estão livres de aguardarem por muito tempo o resultado de seus processos, e principalmente não sofrerão de dead-locks no sistema, porque nada bloqueia em sua plataforma e desenvolver sistemas nesse paradigma é simples e prático.

---

Quais são alguns exemplos de I/O? Bom… aqui tem um diagrama de uma aplicação que eu fiz com node e ela mostra várias fontes de I/O:

![Default-aligned image](diagrama-servidor.png)

Node faz o I/O de forma assíncrona asynchronous para lidar com diferentes situações simultaneas. Por exemplo, se você vai até um fast food e faz o pedido de um cheesebuger você tem de imadiato o pedido feito mas não o lanche, então você espara ele ficar pronto para comer. Neste meio tempo outros pedidos estão sendo feitos na lanchonete para outras pessoas. Imagine que você tenha que esperar o registro do seu cheeseburger, bloqueando outras pessoas porque o seu pedido tem que ser feito para o de outra começar enquanto preparam o seu. Isso é chamado de I/O bloqueante porque todo o I/O (cozinhar cheeseburgers) acontece um a um enfileirando tudo. O Node, por sua vez é não-bloqueante, significando que os pedidos serão feitos e entregues quando estiverem prontos.

---

## Que problema o Node pode resolver?

Node estabeleceu o objetivo número um que é “fornecer uma maneira fácil para construir programas de rede escaláveis”. Qual é o problema com os programas servidores atuais? Vamos fazer os cálculos. Em linguagens como Java™ e PHP, cada conexão cria uma nova thread que potencialmente tem anexado 2 MB de memória com ela. Em um sistema que tenha 8 GB de RAM, isso põe o número máximo teórico de conexões concorrentes a cerca de 4.000 usuários. E quando o número de usuários aumenta, se você quer que sua aplicação web suporte mais usuários, você tem que adicionar mais e mais servidores. Somado a estes custos também podem haver possíveis problemas técnicos: um usuário pode usar diferentes servidores para cada requisição, então cada recurso compartilhado deve ser compartilhado para todos os servidores. Por todas estas rações, o gargalho em toda a arquitetura de aplicações web (incluindo velocidade de tráfego, velocidade do processador e velocidade da memória) é o número de conexões concorrentes que o servidor pode manipular.

Node resolve esta questão trocando a maneira como a conexão é tratada no servidor. Ao invés de criar uma nova OS thread a cada conexão (e alocar a memória anexa a ela), cada conexão dispara um evento executado dentro da engine de processos do Node. Node afirma que nunca vai dar deadlock, já que não há bloqueios permitidos, e ele não bloqueia diretamente para chamadas de I/O. Node também alega que um servidor rodando ele pode suportar dezenas de milhares de conexões simultâneas.

Então, agora que você tem um programa que pode manipular dezenas de milhares de conexões simultâneas, o que você pode realmente fazer com o Node? Seria incrível se você tivesse uma aplicação web que necessitasse desta quantidade de conexões. Este é um daqueles tipos de problema: “se você tem um problema, não é mais um problema”.

---

### O que Node definitivamente não é?
Sim, Node é um servidor de programas. Entretanto o produto base do Node definitivamente não é como o Apache ou o Tomcat. Estes servidores são basicamente servidores ready-to-install e estão prontos para instalar aplicativos instantâneamente. Você pode subir e rodar um servidor em um minuto com estes produtos. Node definitivamente não é isso. Parecido com como o Apache pode adicionar um módulo PHP para permitir desenvolvedores criarem páginas da web dinâmicas, e um módulo SSL para conexões seguras, Node tem o conceito de módulos que podem ser adicionados no núcleo do Node. Há literalmente centenas de módulos para rodarem com o Node, e a comunidade é bastante ativa em produzir, publicar e atualizar dezenas de módulos por dia.
