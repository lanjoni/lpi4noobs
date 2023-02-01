# Conceitos <img align="right" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/crystal/crystal-original.svg" alt="Imagem da linguagem" width="100">

## Conceitos por trás do desenvolvimento com Crystal
- [Variáveis](https://github.com/lanjoni/crystal4noobs/blob/main/content/conceitos/README.md#variáveis)
- [Propriedades do "puts"](https://github.com/lanjoni/crystal4noobs/blob/main/content/conceitos/README.md#propriedades-do-puts)
- [Operações aritméticas](https://github.com/lanjoni/crystal4noobs/blob/main/content/conceitos/README.md#opera%C3%A7%C3%B5es-aritm%C3%A9ticas)

### Variáveis
Como já era de se esperar, existe na liguagem Crystal quatro tipos que se destacam e fazem com que seu uso possa ser possível, que são:
- String (conhecida por este nome representa uma variável que armazena um conjunto de caracteres, como letras e símbolos);
- Int32 (geralmente conhecida como tipo "Integer" ou "Inteiro", é o tipo que trata de variáveis como números inteiros);
- Float64 (geralmente conhecida como tipo "Float", é o tipo de variável que trabalha com números não inteiros - "quebrados" ou "com vírgula"-, ou seja, números com pontos flutuantes);
- Bool (geralmente conhecida como "Boolean", é o tipo de variável que define uma condição como sendo verdadeira - true - ou falsa - false);

Caso você tenha em mãos uma variável, porém, não sabe seu tipo definido, basta utilizar a função "typeof", como no exemplo abaixo:
```cr
name = "He4rt"
!p typeof(name) # Irá retornar: typeof(name) => String
```

Perceba que no exemplo acima foi utilizado o comando "!p" ao invés de "puts"! Ele é utilizado para facilitar o debug de seu código e inclui o nome da variável! Os comentários podem ser adicionados utilizando uma cerquilha (#)!

### Propriedades do "puts"

Em algumas linguagens de programação é muito comum adicionar o nome de variável para ser impresso ao invés de concatenar com alguma outra informação, e com o comando "puts" isto é possível! Veja o exemplo abaixo:
```cr
numero = 10
puts "O valor da variável é #{numero}"
```

Basicamente, conseguimos adicionar qualquer variável para ser impressa utilizando a sintaxe "#{nomedavariavel}"!

### Operações aritméticas

Inicialmente, antes de definir algumas propriedades das operações matemáticas, precisamos partir para uma análise com relação aos tipos de variáveis aceitos para operações! 

Se uma variável é do tipo String, mesmo que ela receba algum número, e somente ele, não será possível realizar nenhuma operação aritmética!

Bom, agora que já sabemos o tratamento com relação ao tipo String, podemos iniciar uma breve apresentação sobre as possíveis operações a serem realizadas:
```cr
a = 7
b = 2

puts a + b  # resultado: 9
puts a - b  # resultado: 5
puts a * b  # resultado: 14
puts a ** b # resultado: 49 (potência - elevado)
puts a / b  # resultado: 3.5
puts a // b # resultado: 3 (parte inteira)
puts a % b  # resultado: 1 (módulo)

```

---

Neste momento temos uma base para dar continuidade em nosso curso! Já conseguimos realizar operações aritméticas, retornar valores e exibir mensagens em nosso terminal! Agora, podemos nos aprofundar nos conceitos de como utilizar cada tipo de variável...

<p align="right">
  <a href="https://github.com/lanjoni/crystal4noobs/blob/main/content/conceitos/int32-float64.md">Próximo -> Int32 e Float64</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/crystal4noobs#roadmap">Voltar para o menu principal</a>
</p>
