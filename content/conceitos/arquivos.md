# Arquivos

## Edição

A leitura e edição de arquivos utilizando um código em Crystal pode ser uma ferramenta muito poderosa! Veja um exemplo para leitura de um arquivo em Crystal:

```cr
if ARGV.size != 1 # Definimos se existem argumentos passados! É necessário informar o nome do arquivo que deseja visualizar o conteúdo!
    puts "É necessário passar o nome do arquivo como parâmetro!"
    exit 1
end

file = ARGV[0]

conteudo = File.read(file) # Nesta etapa é lido o conteúdo do arquivo e passado para uma variável!

puts conteudo
```

Perceba que no exemplo acima conseguimos armazenar o conteúdo de um arquivo em uma variável!

Para adicionar texto em um arquivo podemos utilizar a função "File.write"!

```cr
if ARGV.size != 2
    puts "É necessário informar o nome do arquivo e o conteúdo a ser escrito!"
    exit 1
end

file, conteudo = ARGV

File.write(file, conteudo)
```

Inicialmente realizamos uma verificação para verificar se são passados o nome do arquivo a ser alterado seguido do conteúdo a ser adicionado! Assim, conseguimos facilmente alterar o conteúdo de um arquivo qualquer utilizando Crystal, porém, tome cuidado! Utilizando da forma apresentada no exemplo anterior realizamos uma substituição de conteúdo, ou seja, o conteúdo que havia no arquivo antes da alteração foi simplesmente excluído... Se você quiser adicionar algum conteúdo em um arquivo basta utilizar um parâmetro a mais na função "File.write":

```cr
if ARGV.size != 2
    puts "É necessário informar o nome do arquivo e o conteúdo a ser escrito!"
    exit 1
end

file, conteudo = ARGV

File.write(file, conteudo, mode: "a") # Aqui é adicionado mais um parâmetro!
```

## Propriedades

Verificar se um arquivo existe e poder visualizar suas propriedades são possibilidades poderosas de se usar com Crystal, por isso vamos dar uma olhada: 

```cr
if ARGV.size != 1
    puts "É necessário informar um nome de arquivo!"
    exit 1
end

file = ARGV[0]

if File.exists?(file)
    puts "Arquivo existe!"
else
    puts "Arquivo não existe!"
end
```

A função "File.exists?" é responsável por realizar uma verificação se um arquivo existe ou não! Agora, para quando um arquivo existir podemos ainda retornar se o arquivo está vazio ou não e seu tamanho (em caracteres)! Veja: 

```cr
if ARGV.size != 1
    puts "É necessário informar um nome de arquivo!"
    exit 1
end

file = ARGV[0]

if File.exists?(file)
    puts "Arquivo existe!"
    if (File.empty?(file) == true)
        puts "Arquivo está vazio..."
    else
        puts "Arquivo não está vazio!"
        tamanho = File.size(file)
        puts "Seu tamanho (de caracteres) é #{tamanho}"
    end
else
    puts "Arquivo não existe!"
end
```

Certo, agora que podemos verificar se um arquivo existe, retornar seu tamanho, consigo verificar quando foi a última vez que sofreu alguma modificação? Sim! Observe no exemplo abaixo: 

```cr
if ARGV.size != 1
    puts "É necessário informar um nome de arquivo!"
    exit 1
end

file = ARGV[0]

puts File.info(file).modification_time
```

---

O que achou de ver como a linguagem Crystal trabalha com arquivos? Gostou? Bora pra mais um capítulo?

<p align="right">
  <a href="https://github.com/lanjoni/crystal4noobs/blob/main/content/conceitos/diretorios.md">Próximo -> Diretórios</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/crystal4noobs#roadmap">Voltar para o menu principal</a>
</p>
