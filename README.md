# AutoFeed

  Essa é um proposta de automação na alimentação de animais domésticos, através da configuração de nível da quantidade de ração dentro do pote, este pote também será usado como balança. Caso o animal doméstico se alimente de uma certa quantidade de ração, e ela passe o número configurado, depois de um determinado tempo a alavanca do molde será reaberta, permitindo o preenchimento de ração do pote, quando chegar o nivel configurado a alavanca do pote será fechada.
  
  Por se tratar de uma aplicação desenvolvida no Arduino Uno, utilizamos materiais específicos da plataforma eletrônica para a construção do suporte, segue abaixo uma lista dos elementos que serão usados e suas respectivas funções:

# Arduino UNO R3

  Placa composta por um microcontrolador, circuitos de entrada/saída e que pode ser facilmente conectada à um computador e programada via IDE (Integrated Development Environment, ou Ambiente de Desenvolvimento Integrado) utilizando uma linguagem baseada em C/C++, sem a necessidade de equipamentos extras além de um cabo USB, este hardware que vai ser utilizado para implantar a lógica do controle da ração, nele vão ser configurados os módulos, pinos, tara, etc.

Figura 1 – Arduino Uno R3

![arduinoUno](https://user-images.githubusercontent.com/48319383/85252263-c7ff0e80-b431-11ea-9a75-014a60e08873.png =250x)
 
Fonte: Site Filipeflop

# Protoboard

  Uma placa de ensaio ou matriz de contato é uma placa com furos e conexões condutoras utilizada para a montagem de protótipos e projetos em estado inicial. A grande vantagem da placa de ensaio na montagem de circuitos eletrônicos é a facilidade de inserção de componentes, uma vez que não necessita soldagem.

Figura 2 – Protoboard

![protoboard](https://user-images.githubusercontent.com/48319383/85252271-c9c8d200-b431-11ea-814d-d130a9a79599.jpg =250x)

Fonte: Site Vida de Silício

# Módulo HX711

  Se trata de um módulo conversor e amplificador, geralmente é usado para amplificar os sinais das células de carga, possibilitando a leitura através do microcontrolador, que seria o Arduino.

Figura 3 – Módulo HX711

![modulohx711](https://user-images.githubusercontent.com/48319383/85252270-c9c8d200-b431-11ea-9c62-647c77a6186b.jpg =250x)
 
Fonte: Site Filipeflop

# Ethernet Shield

  Placa que permite ao Arduino se conectar a uma rede local ou a internet, para o projeto, está placa será usada para estabelecer uma conexão via MQTT, será utilizado para controlar o nível da quantidade de ração, e passar informações a respeito da quantidade que o animal já ingeriu.

Figura 4 – Ethernet Shield

![ethernetShield](https://user-images.githubusercontent.com/48319383/85252266-c9303b80-b431-11ea-8876-a6859b1fa256.jpg =250x)
 
Fonte: Site Filipeflop

# Célula de Carga (1KG)

  Transdutor de força, medida a partir da deformação que ocorre ao materialé um transdutor de força. A força é medida de forma indireta, normalmente relacionando-a com a resposta de algum material à aplicação de carga (mudança de pressão, deformação etc.). É muito utilizada por ser muito precisa e ser muito versátil em relação ao tamanho das cargas aplicadas, será introduzido embaixo do pote de ração do animal.

Figura 5 – Célula de Carga (1KG)

![celulaCarga](https://user-images.githubusercontent.com/48319383/85252265-c897a500-b431-11ea-8800-bfa4603b3381.jpg =250x)
 
Fonte: Site Magazine Luiza

# Micro Servo Motor

  Motor na qual podemos controlar sua posição angular através de um sinal PWM, atuador eletromecânico, usado para manter e posicionar um determinado objeto, vai ser usado para controlar a alavanca do controle da ração.

Figura 6 – Micro Servo Motor

![servomotor](https://user-images.githubusercontent.com/48319383/85252273-ca616880-b431-11ea-9dcf-79a37cb01220.jpg =250x)
 
Fonte: Site Vida de Silício

# Jumpers

  Peça plástica que contém um pequeno filamento de metal responsável pela condução de eletricidade. De acordo com a disposição destas peças nos chamados pinos, o fluxo de eletricidade é desviado, ativando configurações distintas, utilizado para estabelecer a comunicação entre os elementos no Arduino.

Figura 7 - Jumpers

![jumper](https://user-images.githubusercontent.com/48319383/85252269-c9303b80-b431-11ea-8885-0981dbc33349.jpg =250x)
 
Fonte: Site Filipeflop

  Para a elaboração do software em relação ao molde, usaremos as documentações dos materiais específicos que foram selecionados, a biblioteca do módulo HX711 é capaz de tratar e medir a quantidade de ração dentro do pote, e com essa informação, identificaremos a diferença que irá gerar após o animal ingerir uma certa quantidade de ração. Utilizaremos a biblioteca Servo para controlar o servo motor, e incluir o método responsável por levantar e abaixar a alavanca quando chegar a um determinado nível de ração.
  
  Para a conexão via MQTT, através da biblioteca do Ethernet Shield e a API do MQTT para o Arduino UNO, vamos elaborar a conexão para transferir as informações que serão passadas para a web através do Arduino, informaremos a quantidade de ração que o animal ingerir, a medida que vai diminuindo essa quantidade e o jeito que estiver configurado no software para manter no nível de ração, vai ser informado no broker criado no Node-Red se a alavanca está aberta enchendo o pote com a ração, e se o pote já está no nível configurado.
  
  Então, este procedimento que o grupo elaborou segue um padrão, a medida que o pote estiver vazio, depois de um certo tempo, vai sendo preenchido com ração a quantidade que o usuário configurar, enquanto estiver enchendo ou o animal estiver se alimentando, estas informações serão passadas para o broker Node-Red pela conexão que o Arduino vai criar quando carregar a aplicação. 
