# AutoFeed

  Essa é um proposta de automação na alimentação de animais domésticos, através da configuração de nível da quantidade de ração dentro do pote, que também será utilizado como balança. Caso o animal doméstico se alimente de uma certa quantidade de ração, e o nível passe o número configurado, depois de um determinado tempo a alavanca do molde será reaberta, permitindo o preenchimento de ração do pote, quando chegar o nivel configurado a alavanca do pote será fechada, em todo processo será mantido conexão com a internet via MQTT para troca de informações, abaixo segue um fluxograma do projeto:
  
<p align="center">
  <img src="https://user-images.githubusercontent.com/48025235/85958885-785b9e00-b96f-11ea-9d3f-38bc1700e5df.png" width="1000">
</p>
  
  Por se tratar de uma aplicação desenvolvida no Arduino Uno, utilizamos materiais específicos da plataforma eletrônica para a construção do suporte, segue abaixo uma lista dos elementos que serão usados e suas respectivas funções:

# Arduino UNO R3

  Placa composta por um microcontrolador, circuitos de entrada/saída e que pode ser facilmente conectada à um computador e programada via IDE (Integrated Development Environment, ou Ambiente de Desenvolvimento Integrado) utilizando uma linguagem baseada em C/C++, sem a necessidade de equipamentos extras além de um cabo USB, este hardware que vai ser utilizado para implantar a lógica do controle da ração, nele vão ser configurados os módulos, pinos, tara, etc.

<p align="center">
  Figura 1 – Arduino Uno R3
</p>
<p align="center">
  <img src="https://user-images.githubusercontent.com/48319383/85252263-c7ff0e80-b431-11ea-9a75-014a60e08873.png" width="250">
</p>
<p align="center">
  Fonte: Site Filipeflop
</p>

# Protoboard

  Uma placa de ensaio ou matriz de contato é uma placa com furos e conexões condutoras utilizada para a montagem de protótipos e projetos em estado inicial. A grande vantagem da placa de ensaio na montagem de circuitos eletrônicos é a facilidade de inserção de componentes, uma vez que não necessita soldagem.

<p align="center">
  Figura 2 – Protoboard
</p>
<p align="center">
  <img src="https://user-images.githubusercontent.com/48319383/85252271-c9c8d200-b431-11ea-814d-d130a9a79599.jpg" width="250">
</p>
<p align="center">
  Fonte: Site Vida de Silício
</p>

# Módulo HX711

  Se trata de um módulo conversor e amplificador, geralmente é usado para amplificar os sinais das células de carga, possibilitando a leitura através do microcontrolador, que seria o Arduino.

<p align="center">
  Figura 3 – Módulo HX711
</p>
<p align="center">
  <img src="https://user-images.githubusercontent.com/48319383/85252270-c9c8d200-b431-11ea-9c62-647c77a6186b.jpg" width="250">
</p>
<p align="center">
  Fonte: Site Filipeflop
</p>

# Ethernet Shield

  Placa que permite ao Arduino se conectar a uma rede local ou a internet, para o projeto, está placa será usada para estabelecer uma conexão via MQTT, será utilizado para controlar o nível da quantidade de ração, e passar informações a respeito da quantidade que o animal já ingeriu.

<p align="center">
  Figura 4 – Ethernet Shield
</p>
<p align="center">
  <img src="https://user-images.githubusercontent.com/48319383/85252266-c9303b80-b431-11ea-8876-a6859b1fa256.jpg" width="250">
</p>
<p align="center">
  Fonte: Site Filipeflop
</p>

# Célula de Carga (1KG)

  Transdutor de força, medida a partir da deformação que ocorre ao materialé um transdutor de força. A força é medida de forma indireta, normalmente relacionando-a com a resposta de algum material à aplicação de carga (mudança de pressão, deformação etc.). É muito utilizada por ser muito precisa e ser muito versátil em relação ao tamanho das cargas aplicadas, será introduzido embaixo do pote de ração do animal.
  
<p align="center">
  Figura 5 – Célula de Carga (1KG)
</p>
<p align="center">
  <img src="https://user-images.githubusercontent.com/48319383/85252265-c897a500-b431-11ea-8800-bfa4603b3381.jpg" width="250">
</p>
<p align="center">
  Fonte: Site Magazine Luiza
</p>

# Micro Servo Motor

  Motor na qual podemos controlar sua posição angular através de um sinal PWM, atuador eletromecânico, usado para manter e posicionar um determinado objeto, vai ser usado para controlar a alavanca do controle da ração.

<p align="center">
  Figura 6 – Micro Servo Motor
</p>
<p align="center">
  <img src="https://user-images.githubusercontent.com/48319383/85252273-ca616880-b431-11ea-9dcf-79a37cb01220.jpg" width="250">
</p>
<p align="center">
  Fonte: Site Vida de Silício
</p>

# Jumpers

  Peça plástica que contém um pequeno filamento de metal responsável pela condução de eletricidade. De acordo com a disposição destas peças nos chamados pinos, o fluxo de eletricidade é desviado, ativando configurações distintas, utilizado para estabelecer a comunicação entre os elementos no Arduino.

<p align="center">
  Figura 7 - Jumpers
</p>
<p align="center">
  <img src="https://user-images.githubusercontent.com/48319383/85252269-c9303b80-b431-11ea-8885-0981dbc33349.jpg" width="250">
</p>
<p align="center">
  Fonte: Site Filipeflop
</p>

# LEDs

  Componente eletrônico semicondutor, ou seja, um diodo emissor de luz (L.E.D = Light emitter diode ), mesma tecnologia utilizada nos chips dos computadores, que tem a propriedade de transformar energia elétrica em luz.

<p align="center">
  Figura 7 - LEDs
</p>
<p align="center">
  <img src="https://user-images.githubusercontent.com/48025235/85958551-abe8f900-b96c-11ea-8024-a8b09e21cb9e.png" width="250">
</p>
<p align="center">
  Fonte: Site Eagle Robotics
</p>

  Para a elaboração do software (Tópico Projeto no GitHub) em relação ao molde, usaremos as documentações dos materiais específicos que foram selecionados, a biblioteca do módulo HX711 é capaz de tratar e medir a quantidade de ração dentro do pote, e com essa informação, identificaremos a diferença que irá gerar após o animal ingerir uma certa quantidade de ração. Utilizaremos a biblioteca Servo para controlar o servo motor, e incluir o método responsável por levantar e abaixar a alavanca quando chegar a um determinado nível de ração.
  
  Para a conexão via MQTT, através da biblioteca do Ethernet Shield e a API do MQTT para o Arduino UNO, vamos elaborar a conexão em um broker público da HiveMQ (Acesso ao broker público: http://broker.mqtt-dashboard.com/index.html) para transferir os dados do Arduino, em seguida vamos configurar esse broker na ferramenta Node-Red (Acesse o link para instalação da ferramenta: https://nodered.org/docs/getting-started/local) (Arquivo do projeto para importar: flows.js), está ferramenta será utilizada no projeto para captar essas informações e realizar determinada ação, enquanto não houver conexão será aceso um LED vermelho, e quando estabilizar a conexão com o Arduino, após o Node-Red receber essa informação, será disparada uma trigger que envia uma informação de volta ao Arduino para acender o LED verde e apagar o vermelho, caso a alavanca esteja sendo aberta ou fechada, a informação também será enviada ao Node-Red, e durante todo esse processo, os dados do peso da balança serão enviados do Arduino para o Node-Red em intervalos de segundos, isto vai depender da configuração do usuário, estes dados serão utilizados para a construção de um dashboard dentro da ferramenta, este dashboard será constituído de um gráfico que apresenta a quantidade de ração em gramas a partir do tempo, além de que será necessário instalar a biblioteca node-red-dashboard para manipular o gráfico. (Para acessar o gráfico após as configurações:  http://localhost:1880/ui).
  
  Então, este procedimento que o grupo elaborou segue um padrão, a medida que o pote estiver vazio, depois de um certo tempo, vai sendo preenchido com ração a quantidade que o usuário configurar, enquanto estiver enchendo ou o animal estiver se alimentando, estas informações serão passadas para o broker, em seguida a ferramenta Node-Red vai ajustando o gráfico.

  
  Vídeo no YouTube - https://www.youtube.com/watch?v=-dr3U-8nBDw
