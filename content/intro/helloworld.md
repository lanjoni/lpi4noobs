# Hello World!

O clássico "Hello World!" não vai ficar de fora, e imprimir esta mensagem será nossa etapa de conclusão com a introdução a linguagem de programação Crystal! E para que isso seja possível: abra seu editor de textos/códigos favorito, pegue um café ou energético, acomode-se na cadeira, e vamos lá!

---

## Exibir na tela

O comando utilizado para exibir alguma mensagem na tela é chamado de "puts", e para exibir nosso primeiro "Hello World!" iremos escrever em nosso editor:
```cr
puts "Hello World!"
```

Para compilar e executar o código, primeiro iremos salvar nosso arquivo com algum nome (no meu caso irei chamá-lo de hello_world) adicionando a extensão ".cr" para o Crystal! Após salvar, iremos abrir nosso terminal no diretório em questão, e vamos executar:
```
crystal hello_world.cr
```

E assim, veremos a mensagem na tela!

Basicamente, o compilador Crystal compilou nosso arquivo e já executou, sem deixar armazenado em nosso disco rígido nenhum executável! Caso você queira compilar e salvar o executável, basta executar o comando:
```
crystal build hello_world.cr -o hello_world
```
A adição do comando "build" fará com que criemos um arquivo compilado, seguido do nome do arquivo em questão, e depois pelo parâmetro "-o" de output (saída em inglês) com o nome do nosso executável! 

Para visualizar a execução deste novo arquivo compilado criado, basta executar no diretório em questão em nosso terminal:
```
./hello_world
```

---

Pronto! Agora que você já teve seu primeiro contato com a linguagem Crystal, compilou e executou seu primeiro trecho de código, podemos avançar para outras definições da linguagem, como por exemplo o tratamento de variáveis, cadeias de caracteres, operadores lógicos, entre outras diversas possibilidades que Crystal pode oferecer! Vamos lá?

<p align="right">
  <a href="https://github.com/lanjoni/crystal4noobs/tree/main/content/conceitos">Próximo -> Conceitos</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/crystal4noobs#roadmap">Voltar para o menu principal</a>
</p>
