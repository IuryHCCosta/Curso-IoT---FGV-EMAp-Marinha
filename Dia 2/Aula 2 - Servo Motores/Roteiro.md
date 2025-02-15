
# Introdução à Eletrônica com Arduino

## Potenciômetros e Servo Motores 

### Descrição

Esse roteiro de atividades tem como objetivo introduzir o uso de potenciômetros como controladores e o uso de servo motores como atuadores em sistemas eletrônicos. Além disso, serão utilizados diferentes tipos de potenciômetros e discutidas as diferenças entre eles, bem como a linearização do comportamento de um potenciômetro não linear.

### Objetivos

- Apresentar o funcionamento de um potenciômetro e observar seu output no Serial Plotter.
- Apresentar o controle de um servo motor com uma rotina de movimento pré-programada.
- Controlar o servo motor a partir de um potenciômetro, ajustando a amplitude dos valores usando a função ```map()```.
- Comparar o comportamento de um potenciômetro do tipo A com um do tipo B e discutir as diferenças na resposta do sistema.
- Coletar dados de um transferidor graduado fixo ao servo a fim de observar a linearidade do potenciômetro do tipo A.

### Materiais Necessários
| Componente                           | Imagem                                                                                                      |
|--------------------------------------|-------------------------------------------------------------------------------------------------------------|
| 1x Placa Arduino (Uno, Mega, ou similar) | <img src="https://d229kd5ey79jzj.cloudfront.net/1338/images/1338_2_X.png?20241107090313" height="100"> |
| 1x Cabo USB para conexão com o computador | <img src="https://m.media-amazon.com/images/I/5181PDv7RbL._AC_UF894,1000_QL80_.jpg" height="100"> |
| 1x Servo motor | <img src="https://cdn.awsli.com.br/600x450/463/463999/produto/19213618/4c079f22f7.jpg" height="100"> |
| 1x Potenciômetro tipo A (10k ohms) | <img src="https://m.media-amazon.com/images/I/51WpSM+BR0L._AC_UF894,1000_QL80_.jpg" height="100"> |
| 1x Potenciômetro tipo B (10k ohms) | <img src="https://m.media-amazon.com/images/I/51WpSM+BR0L._AC_UF894,1000_QL80_.jpg" height="100"> |
| Peças graduadas impressas em 3D | <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSEhinASCRRjS-NVLtaqJ_xFPIRriMdFFM_yg&s" height="100"> |
| 1x LED branco | <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTcFawZu9wqpgrr9iK7TOXOAUY1yT7yuwyqxw&s" height="100"> |
| 1x Resistor de 300 ohms | <img src="https://http2.mlstatic.com/D_NQ_NP_988873-MLB43270980270_082020-O.webp" height="100"> |
| 1x Resistor de 10k ohms | <img src="https://www.usinainfo.com.br/1017894-thickbox_default/resistor-10k-14w-kit-com-10-unidades.jpg" height="100"> |
| 1x Botão | <img src="https://content.instructables.com/F1B/EQSU/IBL62CC3/F1BEQSUIBL62CC3.jpg?auto=webp" height="100"> |
| Breadboard | <img src="https://cdn.awsli.com.br/600x700/1665/1665980/produto/11154566064a7523ad8.jpg" height="100"> |
| Jumpers | <img src="https://res.cloudinary.com/rsc/image/upload/b_rgb:FFFFFF,c_pad,dpr_1.0,f_auto,q_auto,w_700/c_pad,w_700/R2048241-01" height="100"> |

### Palavras-chave

Arduino, Arduino IDE, Servo, Potenciômetro, Potenciômetro Linear, Potenciômetro Logarítimico, Serial Plotter, Linearização, Transferidor, Função Inversa.

---

## Metodologia

### Bloco 1: Potenciômetros

Potenciômetros são componentes eletrônicos presentes em diversos dispositivos eletrônicos, como controles de volume, brilho, entre outros. Inventados por Thomas Edison em 1872 (há controvérsias), eles são utilizados para controlar a resistência elétrica de um circuito, variando a tensão ou corrente que passa por ele. Neste bloco, vamos explorar o funcionamento de um potenciômetro e observar como ele pode ser utilizado para controlar um sistema eletrônico.

<p align="center">
  <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT5Zu9CfHnIzPHmp8j7if3I4SO-HSclugEo2Q&s" alt="Potenciômetro" height="300">
</p>

#### Passo 1: Introdução ao Circuito

Utilizando o potenciômetro do tipo B, siga os passos abaixo para montar o circuito:

1. Conecte o pino central do potenciômetro ao pino analógico A0 do Arduino.

2. Conecte um dos outros pinos do potenciômetro ao terminal de 5V do Arduino.

3. Conecte o outro pino do potenciômetro ao terminal GND do Arduino.

<p align="center">
  <img src="..\..\src\images\Aula 2\pot_circuit.png" alt="Circuito do Potenciômetro" height="300">
</p>

4. Insira o tranferidor impresso em 3D no eixo do potenciômetro para facilitar a leitura da posição.

5. Rotacione o eixo do potenciômetro até o início da escala (0 graus) e insira o knob no eixo do potenciômetro.

#### Passo 2: Programação

1. Abra o Arduino IDE e escreva o seguinte código:

```cpp
void setup() {
  Serial.begin(9600); // Inicializa a comunicação serial a 9600 bps

  pinMode(A0, INPUT); // Define o pino A0 como entrada
}

void loop() {
  int potValue = analogRead(A0); // Lê o valor do potenciômetro e armazena na variável potValue
  Serial.println(potValue);
  delay(10);
}
```

2. Selecione a placa e a porta de conexão onde o Arduino está conectado.

3. Faça o upload do código para a placa Arduino.

#### Passo 3: Observação

1. Abra o Serial Plotter no Arduino IDE.

2. Gire o potenciômetro e observe como o valor muda no Serial Plotter.

#### Passo 4: Exploração

1. Qual o valor mínimo lido pelo potenciômetro? E o máximo?

2. Qual a amplitude, em graus, do potenciômetro? (Pesquise, se necessário)

3. Qual a relação entre a posição do potenciômetro e o valor lido? parece ser linear? Experimente girar o potenciômetro lentamente e observe a saída na tela. Calcule a razão entre a variação do potenciômetro e a variação do valor lido para pelo menos 3 valores para verificar a linearidade.

4. O que acontece se inverter as conexões do potenciômetro? Inverta os fios de alimentação (5V) e terra (GND) e observe o comportamento. O que acontece ao girar o potenciômetro como antes?

5. Para compreender o funcionamento o pótenciômetro, use o multímetro para medir a resistência entre os terminais do potenciômetro. Gire o potenciômetro e observe como a resistência varia no início, meio e final do seu curso. O que você pode concluir a partir dessas medições?

---

### Bloco 2: Dimmer: PWM "raiz"

Você já ouviu falar sobre **lâmpadas dimerizáveis**? Elas permitem ajustar o brilho conforme a necessidade, seja para criar um ambiente mais aconchegante ou economizar energia. Essa tecnologia é baseada em um circuito chamado **dimmer**, que controla a potência fornecida à lâmpada. Esse conceito pode ser aplicado tanto para circuitos de corrente alternada (AC) como para circuitos de corrente contínua (DC). No caso de circuitos de corrente contínua (DC), esse controle é feito por **modulação por largura de pulso (PWM)**.

No Arduino, o **PWM** nos permite simular uma saída analógica em pinos digitais, ajustando a relação entre o tempo que um sinal permanece **ligado (HIGH)** e **desligado (LOW)** em um período fixo.

Primeiramente vamos construir um dimmer simples, usando um pino digital comum para controlar o brilho de um LED. Lembrando que o experimento que desenvolveremos agora não é a forma ideal de usar sinais PWM, porém é a forma mais simples de mostrar o fenômeno resultante de um controle por um sinal PWM.

#### Passo 1: Introdução ao Circuito

<p align="center">
  <img src="..\..\src\images\Aula 2\pot_dimmer.png" alt="Circuito do Dimmer" height="300">
</p>

#### Pàsso 2: Programação

1. Abra o Arduino IDE e escreva o seguinte código:

```cpp
const int pinoPotenciometro = A0; // pino onde o pontenciômetro está conectado
const int pinoLED = 12; // pino onde o LED está conectado
const int periodo = 1023;
int tempo_ligado, tempo_desligado ; // variável para armazenar o valor lido pelo ADC

void setup() {
  pinMode(pinoPotenciometro, INPUT); // configura o pino com potenciômetro como entrada
  pinMode(pinoLED, OUTPUT); // configura o pino com o LED como saída
  Serial.begin(9600);
}

void loop() {
  tempo_ligado = analogRead(pinoPotenciometro);// le o valor de tensão no pino do potenciômetro
  tempo_desligado = periodo - tempo_ligado; // atribui a variável tempo_desligado, quanto tempo o LED deverá permanecer desligado. 
  digitalWrite(pinoLED, HIGH); // aciona o LED
  delay(tempo_ligado); // aguarda o valor lido no pino do potenciômetro em milissegundos
  digitalWrite(pinoLED, LOW); // apaga o LED
  delay(tempo_desligado); // aguarda o valor lido no pino do potenciômetro em milissegundos
  Serial.print(tempo_ligado);
  Serial.print("\t");
  Serial.println(tempo_desligado);
    
}
```

2. Selecione a placa e a porta de conexão onde o Arduino está conectado.

3. Faça o upload do código para a placa Arduino.

#### Passo 3: Observação

1. Gire o potenciômetro e observe a variação do brilho do LED.

2. Experimente inverter as conexões do potenciômetro e veja o que acontece.

#### Passo 4: Exploração

1. O LED realmente apaga quando o potenciômetro está no mínimo? E quando está no máximo? Por que isso acontece?

2. O LED alcança o brilho máximo?

3. O efeito que vemos é suave ou notamos um 'pisca-pisca' no LED? Por que isso acontece? Experimente substituir o ```delay()``` por um ```delayMicroseconds()``` e veja o que acontece. Porque o efeito é diferente?

4. Por que a troca da função de espera de tempo influencia no brilho do LED? Qual a relação com o processo de geração de sinais por PWM?

5. Essa abordagem não é a ideal para controlar a intensidade de um LED. Como você poderia melhorar esse controle? Usando o controle de PWM que você já conhece para controlar a intensidade do LED a partir do potenciômetro? Lembre-se de usar a função ```map()```

6. Como podemos configurar um threshold para o LED acender? Por exemplo, o LED só acende quando o potenciômetro está acima de 50% do seu curso. Como você poderia fazer isso? Experimente usar condicionais para controlar o acendimento do LED.

### Bloco 3: Servo Motores

Servo motores são dispositivos capazes de girar em um ângulo específico, controlados por um sinal PWM (Pulse Width Modulation). Eles são amplamente utilizados em projetos de robótica, automação e modelismo. Neste bloco, vamos explorar o controle de um servo motor e observar seu movimento entre posições específicas, pré-definidas no código.

Seu funcionamento é baseado em um motor DC (típico de brinquedos infantis) com uma caixa de redução e um potenciômetro acoplado ao eixo, formando um sistema de feedback que permite monitorar a posição do eixo. O sinal PWM enviado ao servo motor determina a posição do eixo, variando o ângulo de rotação.

<p align="center">
  <img src="https://www.vidadesilicio.com.br/wp-content/uploads/2021/09/1848-jpg.webp" alt="Servo Motor" height="300">
</p>

#### Passo 1: Introdução ao Circuito

1. Conecte o fio de alimentação (vermelho) do servo ao terminal de 5V do Arduino.

2. Conecte o fio terra (marrom ou preto) do servo ao terminal GND do Arduino.

3. Conecte o fio de controle do servo ao pino digital 9 do Arduino.

<p align="center">
  <img src="..\..\src\images\Aula 2\servo_circuit.png" alt="Circuito do Potenciômetro" height="300">
</p>

4. Insira o transferidor impresso em 3D no eixo do servo motor para facilitar a leitura da posição

5. Insira o ponteiro no eixo do eixo do servo motor e aperte o parafuso usando a chave philips.

> ⚠: O servo motor pode consumir uma corrente maior que a fornecida pelo Arduino. Se o servo motor não estiver se movendo corretamente, considere alimentá-lo com uma fonte externa.

#### Passo 2: Programação

1. Instale a biblioteca "Servo" no Arduino IDE. Para isso, abra o Library Manager e busque por "servo".

<p align="center">
  <img src="..\..\src\images\Servo library.png" alt="Circuito do Potenciômetro" height="150">
</p>

2. Abra o Arduino IDE e escreva o seguinte código:

```cpp
#include <Servo.h> // Inclui a biblioteca Servo

Servo myServo; // Cria um objeto Servo chamado myServo

void setup() {
  myServo.attach(9); // Associa o servo ao pino digital 9
}

void loop() {
  myServo.write(0);   // Posição mínima
  delay(1000);
  myServo.write(90);  // Posição média
  delay(1000);
  myServo.write(180); // Posição máxima
  delay(1000);
}
```

3. Selecione a placa e a porta de conexão onde o Arduino está conectado.

4. Faça o upload do código para a placa Arduino.

#### Passo 3: Observação

1. Observe o movimento do servo motor entre as posições mínima (0°), média (90°) e máxima (180°). Em qual direção ele gira?

2. O ponteiro aponta para a posição correta no transferidor? Se necessário, desligue o Arduino para que o servo motor não se mova e ajuste a posição do ponteiro para a posição correta.

#### Passo 4: Exploração

1. Ele é capaz de repetir os movimentos com precisão?

2. O que acontece se alterar os valores de 0, 90 e 180 graus no código? É possível inverter a direção do servo? Experimente alterar esses valores e observe o comportamento do servo.

3. Como você poderia controlar o servo motor de forma mais sauve, com ângulos intermediários? Experimente adicionar mais posições intermediárias no código.

5. O que acontece se inserir um valor maior que 180 ou menor que 0? Experimente e observe o comportamento.


---

### Bloco 4: controle de Servo com LDR

A natureza está repleta de mecanismos fascinantes. Algumas flores, como o **girassol**, ajustam sua posição ao longo do dia para captar o máximo de luz solar possível. Outras flores, como a **dama-da-noite**, só desabrocham à noite, reagindo à ausência de luz. Podemos replicar esse comportamento na robótica, criando uma **flor robótica**, que abre ou fecha suas pétalas de acordo com a luminosidade.

Neste bloco, usaremos um **sensor de luz (LDR – Light Dependent Resistor)** para controlar um **servo motor**. Conforme a luminosidade muda, o servo se movimentará entre **0° e 180°**, simulando a abertura e o fechamento da flor.

#### Passo 1: Introdução ao Circuito

1. Com base no circuito anterior, adicione o LDR, conforme o esquemático abaixo:

<p align="center">
  <img src="..\..\src\images\Aula 1\ldr_circuit.png" height="300px" />
</p>

#### Passo 2: Programação

1. Abra o Arduino IDE e escreva o seguinte código:

```cpp
#include <Servo.h>

Servo myServo;

const int pinoLDR = A0;  // Pino do sensor de luz
const int pinoServo = 9; // Pino do servo motor

void setup() {
  myServo.attach(pinoServo);  
  Serial.begin(9600); // Inicializa o monitor serial para depuração
}

void loop() {
  int leituraLDR = analogRead(pinoLDR); // Lê o valor do LDR (0 a 1023)
  
  int angulo = map(leituraLDR, 0, 1023, 0, 180); // Mapeia o valor para o intervalo do servo

  myServo.write(angulo); // Move o servo motor para o ângulo correspondente
  
  Serial.print("LDR: "); Serial.print(leituraLDR);
  Serial.print(" - Servo: "); Serial.println(angulo);
  
  delay(100); // Pequena pausa para evitar atualizações excessivas
}
```

2. Selecione a placa e a porta de conexão onde o Arduino está conectado.

3. Faça o upload do código para a placa Arduino.

#### Passo 3: Observação

1. Abra o Serial Monitor e observe os valores lidos pelo LDR e o ângulo do servo motor.

2. Cubra o LDR com a mão e observe o movimento do servo motor. O que acontece quando a luminosidade diminui?

3. Aproxime uma lanterna ou fonte de luz ao LDR e observe o movimento do servo motor. O que acontece quando a luminosidade aumenta?

#### Passo 4: Exploração

1. O servo motor responde de forma suave às variações de luminosidade? Experimente cobrir e descobrir o LDR rapidamente e observe o comportamento do servo motor.

2. O servo se move totalmente para 0 ou 180 graus? Por quê?

3. E se quiséssemos que a flor fizesse o oposto, abrindo-se à noite e fechando-se durante o dia? Como você poderia alterar o código para inverter o comportamento do servo motor?

4. O que acontece se trocarmos o resistor de 10k ohms por um de 300 ohms? Experimente e observe o comportamento.

---

### Bloco 5: Controle do Servo com Potenciômetro Linear

Agora que já exploramos o funcionamento do potenciômetro e do servo motor, vamos combinar os dois para controlar o servo motor a partir da posição do potenciômetro. 

Neste bloco, vamos utilizar um potenciômetro linear para controlar o ângulo do servo motor, ajustando a amplitude dos valores lidos pelo potenciômetro para o intervalo de 0 a 180 graus. Para isso, utilizaremos a função `map()` do Arduino, que mapeia um valor de um intervalo para outro.

#### Passo 1: Introdução ao Circuito

Nesse bloco, combinaremos os circuitos dos blocos 1 e 2, conectando o potenciômetro e o servo motor ao Arduino.

<p align="center">
  <img src="..\..\src\images\Aula 2\pot_and_servo_circuit.png" alt="Circuito do Potenciômetro" height="300">
</p>

#### Passo 2: Programação

1. Abra o Arduino IDE e escreva o seguinte código:

```cpp
#include <Servo.h>

Servo myServo;

void setup() {
  myServo.attach(9);
  Serial.begin(9600);

  pinMode(A0, INPUT);
}

void loop() {
  int potValue = analogRead(A0);

  int angle = map(potValue, 0, 1023, 0, 180); // Mapeia o valor do potenciômetro (0 a 1023) para a amplitude do servo (0 a 180 graus)

  myServo.write(180 - angle); // Define a posição do servo motor (invertendo o ângulo de rotação)

  Serial.print("Potentiometer Value: ");
  Serial.print(potValue);
  Serial.print(" - Servo Angle: ");
  Serial.println(angle);
  delay(15);
}
```

2. Selecione a placa e a porta de conexão onde o Arduino está conectado.

3. Faça o upload do código para a placa Arduino.

#### Passo 3: Observação

1. Gire o potenciômetro e observe como o servo motor se move de acordo com a posição do potenciômetro.

2. Observe os valores no Serial Monitor para entender a relação entre a leitura do potenciômetro e o ângulo do servo.

#### Passo 4: Exploração

1. A relação entre a posição do potenciômetro e o ângulo do servo é linear? Experimente girar o potenciômetro lentamente e observe a saída na tela e na escala do servo. Calcule a razão entre a variação do potenciômetro e a variação do ângulo do servo para pelo menos 3 valores para verificar a linearidade.

2. O que acontece se inverter as conexões do potenciômetro? Inverta os fios de alimentação (5V) e terra (GND) e observe o comportamento. O que acontece ao girar o potenciômetro assim como antes?

3. O que acontece se alterar os valores de 0 e 180 graus no código? e ps valores de 0 a 1023? Experimente alterar esses valores e observe o comportamento do servo.

4. Experimente colocar um botão no circuito e, apenas atualizar a posição do servo quando o botão for pressionado. Como você poderia fazer isso?

---

### Bloco 6: Potenciômetro "Diferente"

Neste bloco, vamos substituir o potenciômetro do tipo B pelo potenciômetro do tipo A e observar as diferenças no comportamento do servo motor.

#### Passo 1: Introdução ao Circuito

Substitua o potenciômetro B10K pelo potenciômetro A10K, mantendo as mesmas conexões do bloco anterior.

#### Passo 2: Programação

Nesse bloco, usaremos o mesmo código do bloco anterior, pois a mudança no potenciômetro não afeta a programação do Arduino, apenas os valores que serão lidos e mapeados para o servo motor. 

Antes de começar as análises, confira se o código referente ao bloco anterior está carregado na placa.

#### Passo 3: Observação

1. Gire o potenciômetro e observe a resposta do servo motor.

2. Observe os valores no Serial Monitor para entender as diferenças na leitura do potenciômetro do tipo A comparado ao do tipo B.

#### Passo 4: Exploração

1. A relação entre a posição do potenciômetro e o ângulo do servo é linear? Experimente girar o potenciômetro lentamente e observe a saída na tela e na escala do servo. Calcule a razão entre a variação do potenciômetro e a variação do ângulo do servo para pelo menos 3 valores para verificar a linearidade.

2. O que acontece se inverter as conexões do potenciômetro? Inverta os fios de alimentação (5V) e terra (GND) e observe o comportamento. O que acontece ao girar o potenciômetro assim como antes?

3. Porque isso acontece? O que você pode concluir sobre o uso de potenciômetros logarítmicos em sistemas de controle? Em que cenários eles podem ser mais úteis que os lineares?

--- 

### Bloco 7: Linearidade do Potenciômetro Logarítmico

Neste bloco, vamos coletar dados de um transferidor graduado fixo ao servo motor para gerar observar o comportamento do potenciômetro logarítmico (Tipo A). A Embora estejamos realizando esse procedimento manualmente, em sistemas mais complexos, essa coleta pode ser feita por meio de algoritmos de controle, sendo úteis para calibrar até mesmo sensores lineares que possuem algum desvio ou não-linearidade.

#### Passo 1: Introdução ao Circuito

Nesse bloco, usaremos o mesmo circuito do bloco anterior, com o potenciômetro logarítmico e o servo motor conectados ao Arduino. Contudo, para facilitar a coleta de dados e produzir um volume constante de dados, vamos utilizar um botão para controlar o instante em que os dados serão coletados.

1. Adicione um botão à protoboard

2. Conecte um dos pinos ao GND.

3. Conecte um pino do mesmo lado do botão ao pino 2 do Arduino. Quando pressionado, o botão fechará o circuito entre os pinos, enviando um sinal ```LOW``` ao Arduino.

<p align="center">
  <img src="..\..\src\images\Aula 2\pot_servo_button_circuit.png" alt="Circuito do Potenciômetro" height="300">
</p>

Para mais referências sobre o circuito, consulte o [exemplo do Arduino sobre botões](https://www.arduino.cc/en/Tutorial/BuiltInExamples/Button).

#### Passo 2: Programação

1. Abra o Arduino IDE e escreva o seguinte código:

```cpp
#include <Servo.h>

Servo myServo;

int buttonPin = 2; // Define o pino do botão

void setup() {
    myServo.attach(9);
    Serial.begin(9600);
    pinMode(buttonPin, INPUT_PULLUP); // Define o pino do botão como entrada com pull-up (se não pressionado, o pino lê HIGH)
}

void loop() {


    int potValue = analogRead(A0);
    int angle = map(potValue, 0, 1023, 0, 180);
    myServo.write(180 - angle);

    if (digitalRead(buttonPin) == LOW) { // Verifica se o botão foi pressionado
    
        Serial.print("Potentiometer Value: ");
        Serial.print(potValue);
        Serial.print(" - Servo Angle: ");
        Serial.println(angle);
        
        delay(1000);
    }
}
```

2. Selecione a placa e a porta de conexão onde o Arduino está conectado.

3. Faça o upload do código para a placa Arduino.

#### Passo 3: Observação

1. Abra o Serial Monitor. Os valores do potenciômetro e do ângulo do servo motor serão exibidos apenas quando o botão for pressionado.

2. Para cada demarcação no transferidor graduado do potenciômetro, pressione o botão para coletar o valor do potenciômetro e o ângulo do servo motor.

3. Repita esse procedimento para todas as posições do potenciômetro.

4. Abra uma planilha do Excel e transfira os dados coletados, construindo uma tabela no formato mostrado abaixo. Ela será a nossa base para a linearização do potenciômetro logarítmico.


| Ângulo do Potenciômetro | Valor do Potenciômetro | Ângulo do Servo |
|------------------------|-------------------------|-----------------|
| 0                      | 0                       | 0               |
| 30                    | 27                      | 4              |
| 60                    | 63                      | 10              |
| ...                    | ...                     | ...            |
| 300                    | 1023                    | 180            |

#### Passo 4: Análise dos Dados no Excel

1. Gere um gráfico de dispersão com os dados coletados, conectando os pontos com linhas retas ou suaves. O eixo x será o ângulo do potenciômetro e o eixo y será o ângulo do servo motor. Como é o formato da curva gerada? Isso condiz com o comportamento logarítimico do potenciômetro?

2.  A curva é realmente logarítmica? Ou é uma composição de funções? Porque você acha que isso acontece?

3. Crie uma coluna ```Valor Linear do Potenciômetro```, apontando o comportamento "ideal" caso o potenciômetro fosse linear. Para isso, simularemos a função ```map```, mapeando o intervalo de 0 a 1023 para o intervalo de 0 a 300 graus, de maneira linear. Calcule a seguinte razão:

$$ = (\text{Ângulo do Pot.} / \text{Ângulo Máximo do Pot.}) * \text{Valor Máximo do Pot.} $$

onde o Ângulo Máximo do Potenciômetro é 300 graus, e o Valor Máximo do Potenciômetro é 1023.

4. Crie uma coluna ```Erro```, calculando a diferença entre o valor linear e o valor real do potenciômetro para cada ponto. Exiba os resultados num gráfico similar aos anteriores. O que você pode concluir sobre o comportamento do potenciômetro logarítmico em relação ao linear?

### Conclusão

Este experimento apresentou os potenciômetros e servo motores, começando com o uso de um potenciômetro linear, seguido pela substituição por um potenciômetro logarítmico. A coleta de dados e a visualização da linearidade da resposta do potenciômetro logarítmico proporcionaram uma compreensão prática de como um mesmo componente eletrônico, mas com especificações diferentes, podem interferir no controle de dispositivos eletrônicos.

### Referências para Consulta

- [Documentação Oficial do Arduino](https://www.arduino.cc/en/Guide/HomePage)
- [Biblioteca Servo](https://www.arduino.cc/en/Reference/Servo)
- [Função `map()`](https://www.arduino.cc/reference/en/language/functions/math/map/)
- [Exemplo do Arduino sobre botões](https://www.arduino.cc/en/Tutorial/BuiltInExamples/Button)

### Sugestões de Leitura

- [Potentiometer - Wikipedia](https://en.wikipedia.org/wiki/Potentiometer)
- [Eletronics Basics, How a Potentiometer Works - Random Nerd Tutorials](https://randomnerdtutorials.com/electronics-basics-how-a-potentiometer-works/)
- [Servo Motor - Wikipedia](https://en.wikipedia.org/wiki/Servo_motor)
- [Servos Explained - SparkFun](https://www.sparkfun.com/servos)
- [Linearization - Wikipedia](https://en.wikipedia.org/wiki/Linearization)
- [Pull-up Resistors](https://learn.sparkfun.com/tutorials/pull-up-resistors/all)

---