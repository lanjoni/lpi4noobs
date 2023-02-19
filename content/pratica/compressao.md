# Compressão de arquivos

O ato de comprimir arquivos possibilita que grandes projetos, ou até mesmo arquivos maiores, possam ser reduzidos em um tamanho considerável. Compressão ainda vai ser muito utilizada, por isso, sabia que existem algumas ferramentas que possibilitam tal ato? Vamos conhecer algumas?

## tar

O "**t**ape-**ar**chive" é responsável por compactar arquivos e diretórios, sendo capaz de restaurar arquivos com suas devidas permissões e estado original dos dados. Seus argumentos são baseados no destino (para onde enviar o compactado) e na fonte (o que ele vai compactar), além de poder receber algumas opções para compactação, veja:

- c: Cria um arquivo novo .tar;
- t: Lista o conteúdo de um arquivo .tar;
- x: Extrai os arquivos de um arquivo .tar;
- u: Adiciona novos arquivos em um arquivo .tar apenas se forem novos ou modificados;
- r: Adiciona os arquivos ao final de um arquivo .tar;
- g: Gera um backup incremental;
- j: Utiliza o bzip2 para compactar e descompactar arquivos .tar;
- z: Utiliza o gzip para compactar e descompactar arquivos .tar;
- p: Extrai os arquivos com as mesmas permissões de criação;
- v: Lista todos os arquivos que foram processados;
- f: Indica que o destino é um arquivo em disco;
- N: Salva apenas os arquivos mais novos que uma data específica;
- C: Especifica o local na qual os arquivos serão extraídos;
- M: Habilita múltiplos volumes;
- T: Gera um pacote .tar a partir de uma lista de arquivos e diretórios;
> Um detalhe importante: podemos combinar sistemas diferentes de compactação, como é o caso com bzip2 e gzip, que recebem as opções "j" e "z" respectivamente, assim, novo arquivo final compactado consegue ser ainda menor!

Agora vamos para alguns exemplos:

### Criação de um arquivo compactado utilizando tar e gzip:
```
# tar cvzf cvzf compact.tar.gz ./compact/*
```
> Neste caso estamos criando um arquivo compactado do tipo `.tar.gz`, indicando que está sendo gravado em disco, sendo listado os arquivos que foram compactados logo após a execução do comando.

### Extração de um arquivo compactado utilizando tar e gzip:
```
# tar xvzf compact.tar.gz
```
ou
```
# tar xvzf compact.tar.gz -C .
```
> Para especificar onde será salvo o arquivo extraído, podendo alterar o ponto "." para o diretório que deseja.

## gzip e gunzip

Para uma real compressão de dados, podemos dizer que uma das ferramentas mais utilizadas é o gzip, que utiliza um algoritmo de compressão conhecido como Lempel-Ziv, encontrando caracteres duplicados nos dados de entrada e organizando as ocorrências utilizando ponteiros para a referência anterior. Para compactar um único arquivo utilizando o gzip:

```sh
$ gzip arquivo.txt
```

Para descompactar um arquivo utilize:

```sh
$ gzip -d arquivo.txt.gz
```

ou

```sh
$ gunzip arquivo.txt.gz
```
> Perceba que a ferramenta é responsável com comprimir apenas arquivos, por isso, há a necessidade de utilizar o comando tar para comprimir diretórios e o gzip para a compressão deste arquivo gerado.

## bzip2 e bunzip2

O bzip2 é utilizado para compactações utilizando o algoritmo de Burrows-Wheeler e Huffman, sendo excelente para blocos de dados grandes, na qual quanto maior for o bloco, maior será a taxa de compressão atingida, sendo considerado melhor que os compressores comuns. 

Para compactar um arquivo:

```sh
$ bzip2 arquivo.txt
```

Para descompactar um arquivo:

```sh
$ bzip2 -d arquivo.txt.bz2
```

ou 

```sh
$ bunzip2 arquivo.txt.bz2
```

## xz

O xz é outro compressor de dados, utilizando um algoritmo parecido com o do gzip, produzindo arquivos com a extensão ".xz" ou ".lzma".

Para compactar utilizando xz:

```sh
$ xz arquivo.txt
```

Para descompactar utilizando o xz:

```sh
$ xz -decompress arquivo.txt.xz
```

Caso queira estudar um pouco mais sobre compactação e compressão de arquivos no Linux, acesse o guia do site [Certificação Linux](https://www.certificacaolinux.com.br/compactadores-de-arquivos-no-linux/)!

---

Ótimo! Agora que já aprendemos como funciona a compactação e compressão de arquivos utilizando algumas ferramentas disponibilizadas no Linux, o que acha de entendermos como funciona a combinação de comandos no nosso interpretador de shell?

<p align="right">
  <a href="https://github.com/lanjoni/lpi4noobs/blob/main/content/pratica/combinacao.md">Próximo -> Combinação</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/lpi4noobs#roadmap">Voltar para o menu principal</a>
</p>
