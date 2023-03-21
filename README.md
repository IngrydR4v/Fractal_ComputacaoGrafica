# Computação Gráfica - Fractal ⭐

<f2 align = "left"> **O seguinte projeto possui o objetivo de construir ilustrações por meio de repetições com fractal.**</f2> 
<img src="fractal.gif" align="center"/>
<hr> </hr>

# Passo a passo
<p>Para utilizar um módulo turtle no Python, utilizamos o comando import (importar) seguido do nome do módulo que queremos importar. Após a importação, já podemos utilizar todos os objetos e funções que o módulo disponibiliza.<p>   
  
    import turtle
    
 <p> Assim, para importar o módulo de tempo, que fornece várias funções relacionadas ao tempo, usamos:</p>
 
    import time
    
<p>Defina duas constantes WIDTH e HEIGHT, com valores de 1600 e 900, respectivamente:<p>   
  
    WIDTH, HEIGHT = 1600, 900
  
<p> Cria um objeto screen a partir do módulo turtle e o atribua à variável de tela: </p>

    screen = turtle.Screen()

<p> Configura a tela com as dimensões WIDTH e HEIGHT especificadas:</p>
  
    screen.setup(WIDTH, HEIGHT)

<p> Defina o tamanho da tela para o dobro das dimensões WIDTH e HEIGHT:</p>

    screen.screensize(2*WIDTH, 2*HEIGHT)

<p> Defina a cor de fundo da tela, nesse caso escolhemos preto:</p>

    screen.bgcolor('black')

<p> Defina o tempo de atraso da tela para 0, significando que o desenho será feito sem nenhum atraso:</p>

    screen.delay(0)

<p> Crie um objeto Turtle a partir do módulo turtle e o atribui à variável trig: </p>

    trig = turtle.Turtle()

<p> Defina a largura da caneta da tartaruga para 2 pixels e a velocidade da tartaruga para 1 (sendo a mais lenta): </p>

    trig.pensize(2)
    trig.speed(1)
    
<p> Defina a posição inicial da tartaruga para ser 1/6 do caminho do canto inferior esquerdo da tela: </p>
    
    trig.setpos(-WIDTH // 6, HEIGHT // 6)
    
<p> Define a cor da tartaruga, nesse caso, para dourado: </p>

    trig.color('gold')

<p> Defina uma variável geração com valor 5, que é o número de gerações do triângulo de Sierpinski a serem gerada </p>

    generation = 5

<p> Defina um axioma de string com o padrão inicial para gerar o triângulo de Sierpinski e duas variáveis "chr_1" e "rule_1", que serão utilizadas para aplicar as regras recursivas para geração do triângulo:</p>

    axiom = 'F++F++F'
    chr_1, rule_1 = 'F', 'F-F++F-F'
    
<p> Defina uma variável de passo com valor 600, que será usada para calcular o comprimento de cada segmento de linha do triângulo e um ângulo variável com valor de 60 graus, que será utilizado para calcular o ângulo de cada volta do triângulo: </p>

    step = 600
    angle = 60
    
<p> Defina uma função apply_rules que recebe um axioma de string como entrada e retorna uma nova string com as regras recursivas aplicadas e use uma compreensão de lista para iterar sobre cada caractere no axioma, aplicando a regra recursiva rule_1 a quaisquer ocorrências de chr_1 e retornando a string resultante.: </p>

    def apply_rules(axiom):
      return ''.join([rule_1 if chr == chr_1 else chr for chr in axiom])
      
<p> Em seguida, percorra o número especificado de gerações do triângulo, definindo a cor da caneta, mova a tartaruga para as coordenadas especificadas, limpe os desenhos gerados na tela e grave o número da geração atual na tela usando a fonte, tamanho e estilo especificado:</p>

    for gen in range(generation):
      turtle.pencolor('white')
      turtle.goto(-WIDTH // 2 + 60, HEIGHT // 2 - 100)
      turtle.clear()
      turtle.write(f'Geração: {generation}', font=('Arial', 60, "normal"))
      
<p> Continuando, defina o rumo para 0 graus, mova-a para a posição inicial e limpe os desenhos gerados na tela: </p>

    trig.setheading(0)
    trig.goto(-WIDTH // 6, HEIGHT // 6)
    trig.clear()

<p> Calcule o comprimento dos movimentos para frente da tartaruga com base na geração atual: </p>

    length = step / pow(3, gen)

<p> Proporcione iteração sobre cada caractere na string do axioma, executando o comando apropriado para cada caractere. Se o caractere for 'F', a tartaruga avança pelo comprimento calculado acima. Se o caractere for '+', a tartaruga vira à direita no ângulo especificado. Se o caractere for '-', a tartaruga vira para a esquerda no ângulo especificado: </p>

    for chr in axiom:
      if chr == chr_1:
          trig.forward(length)
      elif chr == '+':
          trig.right(angle)
      elif chr == '-':
          trig.left(angle)
          
<p> Por fim, aplique a regra especificada ao axioma atual, produzindo a próxima iteração do sistema L: </p>

        axiom = apply_rules(axiom)
<p> O loop então se repete para a próxima geração até que o loop tenha concluído todas as gerações.</p>
<p> Logo, para concluir, aplique um comando que espera um clique do mouse antes de fechar a janela</p>
    
    screen.exitonclick()
