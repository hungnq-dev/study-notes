# Rede Neurais


# Tipos

### Perceptron
Primeiro modelo de neurônio artificial desenvolvido nas decadas de 50 e 60 por Frank Rosenblatt (inspirado no trabalho de Warren McCulloch e Walter Pitts). Atualmente é considerado "ultrapassado".
Recebe um ou mais inputs e produz um output.
[Representação Perceptron](http://neuralnetworksanddeeplearning.com/images/tikz0.png)

Para calcular o output, o perceptron utiliza pesos (_weights_) associados a cada input (w1, w2, ..., wn) que nada mais são que números reais que expressão a importância do respectivo input para o output, ou seja, basicamente pesa as evidências para tomar uma decisão.
Os inputs são valores 0 ou 1, o que o torna nem um pouco sensível.
O output do perceptron é determinado pelo resultado da soma dos inputs multiplicados pelos seus weights (denotado por _w·x_ onde _w_ e _x_ são vetores com wights e inputs respectivamente) é maior ou menor que algum valor limite (_threshold_).

Reformulando, temos: ```output = { 0 se w·x <= threshold, 1 se w·x > threshold }```
Podemos passar o threshold ara o outro lado da equação e substituí-lo pelo _bias_ do perceptron (b = -threshold).
```output = { 0 se w·x + b <= 0, 1 se w·x + b > 0 }```

O _bias_ é a medida do quão fácil é levar o perceptron para produzir como saída 1, ou seja, quão fácil atingir o threshold. Pensando em termos biológicos, o quão fácil é ativar o perceptron. Um perceptron com um valor alto no bias é muito fácil ativá-lo e um bias bem negativo torna bem difícil ativá-lo.

>Dado um perceptron que recebe 3 inputs (i1, i2 e i3) e gera um output, podemos:
>Soma = i1 * w1 + i2 * w2 + i3 * w3 ou w·x
>se Soma > threshold então output = 1 senão output = 0

Variando os weights e o threshold obtemos diferentes modelos de tomada de decisão para um perceptron e que, quandro agrupado, também varia o modelo da rede toda.

Numa rede neural temos vários perceptrons, alguns utilizam como entrada o input do usuário (primeira camada) e outros utilizam como entrada o output de outros perceptrons (camada interna - _hidden layer_).
[Representação Rede Neural com Perceptrons](http://neuralnetworksanddeeplearning.com/images/tikz1.png)

Perceptrons também são usados para calcular funções com lógicas elementares (como AND, OR e NAND).
Um perceptron com duas entradas com weights de -2 cada e um bias de 3, ao receberem entrada de 0 ou 1 conseguem efetuar o NAND das duas entradas.
> i1 = 1, i2 = 0; temos: i1 * w1 + i1 * w2 + b = 1 * -2 + 0 * -2 + 3 = 1
> i1 = 1, i2 = 1; temos: w·x + b = 1 * -2 + 1 * -2 + 3 = -1

Os perceptrons conseguem simular qualquer operação lógica ou circuitos delas. E por esses circuitos serem universais na computação, isso implica que os perceptrons também são universais.
Porém, por causas dos _weights e bias_ as soluções podem ser tunáveis, podemos alterar os valores para produzir os resultados aceitáveis. E com algoritmos de aprendizado é possível que essas variáveis sejam tunadas automaticamente conforme os treinos.



### Neurônios Sigmoid
Similares aos perceptrons, porém modificado para que pequenas mudanças nos weights e bias cause pequena mudança no output. Pois um perceptron ao sofrer uma pequena mudança no weight ou bias pode inverter completamente seu output.
Essa pequena mudança facilita e mundo o autoaprendizado, pois permite uma evolução passo a passo, se que a coisa saia do controle.
Os Sigmoids possuem a mesma estrutura dos perceptrons, porém seus inputs e outputs são valores reais entre 0 e 1.
A saída de um sigmoid é data pela função de ativação sigma: ```sigma(w·x + b)```
Onde _sigmoid_ é a função (as vezes referenciada função logística): ```sigma(z) = 1 / (1 + e ^ -z)```

Quandos o valor de _w·x + b_ é muito negativo ou muito positivo, os outputs são bem próximos de 0 e 1 respectivamente, assim como no perceptrons. Porém quando o valor tem um tamanho modestro, daí a saída é diferente pois varia entre 0 e 1, e essa pequena mundaça causa a forma em S da função quando plotada (ao contrário da função do perceptron que praticamente tem formato digital).

Essa curva suave em S permite que pequenas mudanças no weight ou no bias cause pequena mudança no output.
A variação do output é uma função linear das variações de weight e bias. Essa lineariedade facilita a escolha/descoberta dessas variações para atingir a variação desejada no output.




## Arquitetura de uma Rede Neural
A camada de neurônios mais a esquerda é chamada input layer.
A camada mais a direita é chamada output layer.
As camadas do meio são chamadas de hidden layer.
Redes neurais com várias camadas são chamadas multilayer perceptrons ou MLP, independente se forem formadas por perceptrons ou neurônios sigmoid.
O design das input e output layers são bem diretos, diretamente ligadas ao design do problema (se for para identificar se numa imagem existe o número 1, então temos a quantidade de inputs igual à resolução da imagem e um output para informar se tem ou não o número na imagem.
O design das hidden layers é uma arte e existe poucas regras de ouro. Pesquisadores tem desenvolvidos vários design heurísticos que ajudam a obter determinado comportamento (por exemplo, determinar a relação de quantidade de hidden layeres com o tempo de treino).
Modelos:

### Redes Neurais Feedforward
São redes que os outputs de uma camada são os inputs da próxima camadas.
Nelas não existe loop, ou seja, nenhuma camada produz outputs que são inputs de uma camada anterior.
Os algoritmos de aprendizado são mais poderosos que os do RNN.

### Redes Neurais Recorrente (RNN)
Possuem loops, ou seja, uma camada a frente produz output que serve de input para uma camada anterior.
A ideia neste modelo é ter neurônios que ativam somente durante um tempo limitado antes de se tornarem ociosos. Essa ativação estimula outros neurônios que também são ativados por um tempo limitado. Criando assim uma cascata de ativação assíncrona, o que não cria loops.
Os seus algoritmos de aprendizado não são tão poderosos quanto os do Feedforward porém seu modelo de funcionamento está mais próximo ao do cérebro do que o Feedforward está.



## Aprendizado

#### Função de Custo (ou perda)
Função para quantificar o quão próximo o output de uma rede neural está da inputs de treinamento.

### Gradient Descent




### Propostas para exercitar
* Desenvolver uma rede neural de perceptrons que efetuem soma, subtração e multiplicação de bits.


