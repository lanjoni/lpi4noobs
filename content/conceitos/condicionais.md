# Condicionais

Nesta etapa falaremos um pouco sobre estruturas condicionais e tomadas de decisão utilizando Crystal! Eles são muito utilizados em na maior parte das linguages de programação por fornecerem etapas do nosso código na qual podemos escolher por qual caminho devemos seguir! 

## Operadores

Os operadores que serão apresentados são vistos na maior parte das linguagens de programação, então creio que não será nenhuma novidade... São eles:
- "==" (Igual a)
- "<" (Menor que)
- ">" (Maior que)
- "<=" (Menor ou igual a)
- ">=" (Maior ou igual a)
- "!=" (Diferente que)

## Spaceship operators

Utilizados para realizar comparações sobre dois valores, dizendo se o primeiro é igual ao segundo (0), menor (-1) ou maior (1) que ele. Veja um exemplo: 

```cr
puts 3 <=> 3 # retorna 0
puts 3 <=> 4 # retorna -1
puts 4 <=> 3 # retorna 1

puts "a" <=> "a" # retorna 0
puts "a" <=> "b" # retorna -1
puts "b" <=> "a" # retorna 1
```

## IF (Estrutura "se")

Acredito que se você já conhece o básico de programação, com toda certeza deve ter se deparado com a estrutura "if" (ou "se" em linguagens para aprendizado como Portugol). Ele é muito utilizado quando precisamos realizar uma verificação para dar continuidade em nosso código, assim, criando diversos caminhos pelos quais nosso código pode percorrer. Veja um exemplo:

```cr
idade = 18

if idade >= 18
  puts "A pessoa é maior de 18"
else
  puts "A pessoa não é maior de 18"
end
```

Perceba que a estrutura do "if" em Crystal é muito parecida com a estrutura de Python, que utiliza apenas a identação para organizar!

Certo, mas e se eu tiver mais de duas condições? Ou seja, eu quero utilizar um "if" encadeado? Podemos fazer de duas formas: utilizar um "if" dentro do próprio "else" ou utlizar o famoso "elsif", que em algumas linguagens pode ser "elseif" ou "else if"! Veja só:

```cr
# Com outro "if" dentro do else
idade = 18

if idade > 18
  puts "Você é maior de 18!"
else
  if idade < 18
    puts "Você não é maior de 18!"
  else
    puts "Uau! Acertei sua idade!"
  end
end

# Com "elsif"

idade = 18

if idade > 18
  puts "Você é maior de 18!"
elsif idade < 18
  puts "Você não é maior de 18!"
else
  puts "Uau! Acertei sua idade!"
end
```

Ambas as formas funcionam perfeitamente, cabe a você escolher qual é a que mais te agrada!

## Unless

A estrutura "unless" possui funcionamento contrário ao "if", ou seja, é definido qual condição não deve ser seguida para que o conjunto de código seja executado, como por exemplo:

```cr
idade = 22

unless idade >= 18
  puts "Você não é maior de 18!"
else 
  puts "Você é maior de 18!"
end
```

No exemplo acima caso a idade não seja maior ou igual a 18 ele irá executar o primeiro trecho de código, imprimindo a mensagem "Você não é maior de 18!". Interessante não é?

## Suffix

Algumas formas de tratar as estruturas "if" e "unless" é utilizando o "suffix", responsável por definir condições antes mesmo de iniciar a área do código a ser executada, como no exemplo abaixo:

```cr
x = 23

puts "SIM" if x > 20
puts "SIM" if x != 20
begin
  x = x + 1; puts x
end if x < 30
```

Será impressa a seguinte mensagem:

```sh
SIM # O x é maior que 20? Sim!
SIM # O x é diferente de 20? Sim!
23 # Imprimindo o X e finalizando se o x for menor que 30!
```

Um outro exemplo utilizando "unless" seria:

```cr
x = 23
puts "Não é 12..." unless x == 12
puts "Não é 12..." if !(x == 12)
puts "Não é 12..." if x != 12
```

Sendo impresso:

```sh
Não é 12... # A variável x não é igual a 12!
Não é 12... # A variável x não é igual a 12!
Não é 12... # A variável x é diferente de 12!
```

## Operadores lógicos

Os operadores lógicos são utilizados para realizar comparações entre diversos valores dentro de uma condicional ou não! Basicamente temos os mesmos operadores lógicos com as mesmas sintaxes da maior parte das linguagens de programação:
- "&&" ('e' ou 'AND')
- "||" ('ou' ou 'OR')
- "!" ('negando' ou 'contrário' - depende da situação)

## Case / When

Esta estrutura é dividida em casos, muito conhecida em diversas outras linguagens como "switch", na qual são definidos casos específicos para uso! Para entender melhor, veja um exemplo

```cr
numero = 10 # Iniciamos uma variável para verificação

case numero # Iremos verificar a variável com nome "numero"
  when 5 # Quando "numero" for igual a 5
    puts "O número é 5"
  when 10 # Quando "numero" for igual a 10
    puts "O número é 10"
  when 15 # Quando "numero" igual a 15
    puts "O número é 15"
  else # Quando "numero" não corresponde a nenhuma condição passada anteriormente (chamada de "default" em algumas linguagens)
    puts "Eu não sei qual é o número..."
    exit 0 # Força saída!
end # Fim do case
```

Certo, mas além de realizar verificações muito similares ao que eu poderia fazer com "if", o que mais ele pode fazer? 
Uma curiosidade é: podemos fazer verificações de tipos de variáveis! Veja só o exemplo:

```cr
x = "Isto é um texto" # A variável "x" é iniciada recebendo tipagem como "string" por ser um conjunto de caracteres

case x 
  when String # Para verificar o tipo da variável colocamos o nome do tipo iniciando com a letra maiúscula, assim sabemos que estamos falando do tipo dela e não de seu valor!
    puts "string"
    puts x.size
  when Int32
    puts "int32"
    puts x.abs
end
```

No exemplo acima será retornado a mensagem:

```sh
string # Foi impresso o texto "string"
Isto é um texto # Foi impresso o conteúdo da variável "x"!
```

## Operadores condicionais ternários

Geralmente utilizados como um "atalho" para o "if" possui uma estrutura muito similar em diversas linguagens. Veja o exemplo:

```cr
name = nil # Inicializamos uma variável chamada "name" com valor nulo

ternary_name = name ? name : "default" # Primeiro fazemos a verificação se "ternary_name" é igual a "name", se for ele retorna a variável "name", senão retorna o texto "default"
puts ternary_name

or_name = name || "default"
puts or_name
```

Neste caso teremos o seguinte retorno:

```sh
default # Como a variável "name" possui valor nulo foi retornado o texto "default"!
default
```

---

Eaí, o que achou das estruturas condicionais utilizadas em Crystal? Já está pronto para um exercício simples de código com o que aprendemos até agora? Vamos lá!

## Exercício 1 - Condicionais e Loops!

-> O código de resolução estará logo abaixo!

Utilizando seus conhecimentos com a linguagem Crystal desenvolva um código para o enunciado abaixo:

- Crie um arquivo com a extensão ".cr" com um nome de sua preferência!
- Usando o módulo para números aleatórios (chamado "Random.rand(LIMITE)"), deverá ser armazenado um número inteiro entre 1 e 20.
- O usuário deve adivinhar o número. Depois que o usuário digita o seu palpite, deverá ser informado se este foi maior ou menor do que o número gerado, ou se foi o mesmo!
- O usuário pode adivinhar várias vezes. O jogo termina quando o usuário adivinhar o número certo!

Vamos lá?

DICA: Para definir um número aleatório utilize o seguinte trecho de código:

```cr
LIMITE = 20

numeroSecreto = Random.rand(LIMIT) + 1
```

Eaí, conseguiu?

Resolução:

```cr
LIMITE = 20

numeroSecreto = Random.rand(LIMITE) + 1
# puts "Para verificar qual o número: #{numeroSecreto}" # Esta linha de código mostra a resposta direto! Descomente para ver a resposta logo no início e verificar se está tudo correto!
loop do
  print "Adivinhe um número entre 1 e #{LIMITE}: "
  guess = gets.not_nil!.to_i

  if guess == numeroSecreto
    puts "Acertou!"
    break
  elsif guess < numeroSecreto
    puts "Muito pequeno..."
  else
    puts "Muito grande..."
  end
end
```

---

O que achou das estruturas condicionais? Conseguiu resolver o exercício? Bora pra mais um desafio?

<p align="right">
  <a href="https://github.com/lanjoni/crystal4noobs/blob/main/content/conceitos/arrays.md">Próximo -> Arrays</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/crystal4noobs#roadmap">Voltar para o menu principal</a>
</p>
