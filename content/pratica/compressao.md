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
