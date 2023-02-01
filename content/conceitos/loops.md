# Loops (laços de repetição)

Os laços de repetição, também conhecidos como loops, são muito utilizados em diversas situações em nosso cotidiano quando precisamos executar uma tarefa diversas vezes, podendo ter sua quantidade de repetições definidas ou não. 

## Loop (parecido com For)

Muito parecido com o chamado "for" em diversas linguagens, é a estrutura de loop que possui um fim pré-definido, como no exemplo abaixo:

```cr
n = 0 # Inicia uma variável como contador
loop do # Inicia a estrutura de loop
  n += 1 # A cada passo, ele aumenta de 1 em 1
  puts n # Aqui estaremos imprimindo a variável para verificar seus valores se alterando
  break if n >= 10 # Nesta etapa definimos até quando o loop se manterá funcionando, sendo neste caso até que "n" se torne maior ou igual a 10
end # Determina o fim do "loop"
```

Analisando o código acima podemos perceber que ele possui uma sintaxe um tanto quando diferente ao habitual modo que conhecemos de "for" em diversas linguagens. O "break" mostrado é responsável por definir até onde nosso código irá funcionar, sendo que nas estruturas convencionais ele é definido logo no início.

## While

O "while", com um funcionamento um pouco diferente do "loop", é um laço que se repete enquanto uma condição se caracteriza como satisfeita. Veja o exemplo:

```cr
n = 0 # Inicia uma variável como contador
while n < 10 # Enquanto "n" for menor que 0 executa o laço
  n += 1 # Aumenta de 1 em 1
  puts n # Imprime o valor da variável
end # Determina o fim do "while"
```

Neste caso, o "while" possui resposta idêntica ao exemplo com "loop" citado acima.

## Until

O "until", com sintaxe muito parecida com o "while", executa o laço até que uma condição seja satisfeita. Veja o exemplo:

```cr
n = 0 # Inicia uma variável como contador
until n >= 10 # Executa o laço até que "n" seja maior ou igual a 10
  n += 1 # Aumenta de 1 em 1
  puts n # Imprime o valor da variável
end # Determina o fim do "until"
```

A parte legal de ver o funcionamento do "until" é pensar que ele seria como um "while" ao contrário, salvando em diversas situações!

## Controles de Loop

Para controlar os loops temos tanto "break" quanto "next", responsáveis por definir a continuidade. Enquanto o break foi definido logo acima no nosso exemplo de "loop", também podemos encontrar exemplos com "next", observe:

```cr
n = 0 # Inicia uma variável como contador
while n < 5 # Executa o laço enquanto "n" for menor que 5
  n += 1 # Aumenta de 1 em 1
  if n == 3 # Se "n" for igual a 3 faz
    next # Utilizado para pular para o próximo passo do laço, cancelando o que vem a seguir (mesmo esquema de se chamar uma função novamente - recursivamente)
  end # Fim do "if"
  puts n # Imprime o valor de "n"
end # Determina o fim do "while"
```

Executando o código acima, perceba que irá ser impresso todos os números de 1 até 5, exceto o 3! Isso mesmo! O "next" é responsável por cancelar o passo do while e passar para o próximo! 

---

O que achou de aprender sobre o funcionamento de laços de repetição em Crystal? Achou interessante? Vamos dar uma olhada agora em estruturas condicionais...

<p align="right">
  <a href="https://github.com/lanjoni/crystal4noobs/blob/main/content/conceitos/condicionais.md">Próximo -> Condicionais</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/crystal4noobs#roadmap">Voltar para o menu principal</a>
</p>
