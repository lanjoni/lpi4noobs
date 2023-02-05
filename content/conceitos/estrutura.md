# Estrutura de Diretórios

Agora que já passamos pela introdução de como é o funcionamento do emulador de terminal vou lhe pedir um favor: abra seu terminal (procurando pelo terminal ou abrindo pelo atalho `CTRL + ALT + T` - nem todas as distribuições possuem este atalho como padrão) e digite o seguinte comando:
```sh
ls /
```
> Ainda vamos estudar detalhadamente sobre o funcionamento dos comandos em um interpretador de shell, mas, saiba que o comando `ls` é utilizado para **listar** todo o conteúdo dentro de um diretório, no qual nosso diretório selecionado é o **raíz** (/).

Você verá uma série de diretórios e nomes estranhos. Estes nomes compõem o que chamamos de "Hierarquia de Diretórios" ou "Filesystem Hierarchy Standard" para sistemas operacionais Linux. 

Toda a nossa estrutura é formada partindo da raíz, que seria como se fosse o "início" de nossos diretórios. Vamos entender como cada um funciona e quais são suas finalidades:

## /

Raíz do sistema de arquivos.

## /bin

Contém os binários de comandos a serem utilizados pelo usuário e pelo administrador do sistema. Basicamente falando: podemos dizer que contém os executáveis que compõem o sistema operacional.

## /boot

Contém os arquivos necessários para inicialização do sistema, como a imagem do kernel, configurações do Grub, entre outros arquivos.

## /dev

É o diretório responsável por todos os dispositivos do sistema operacional, como pendrives, discos, entre outros. Os arquivos que existem dentro deste diretório não são nada mais que descritores para facilitar o acesso aos dispositivos.

## /etc 

Aqui estão os arquivos necessários para a configuração do sistema operacional, contendo configurações de hosts, grupos, senhas, tabela de particionamento de disco, entre outras configurações, incluindo as configurações de interface de rede.

## /home

Dentro deste diretório vamos encontrar sub-diretórios que darão acesso aos arquivos pessoais para os usuários que estão cadastrados no sistema operacional, contendo scripts para configuração do interpretador de shell e outros arquivos do próprio usuário. 
> ***/home/seunome*** é o diretório "home" de seu usuário!

## /lib

Contém arquivos de bibliotecas essenciais do sistema operacional que serão utilizadas por programas e ferramentas do diretório ```/bin``` e módulos de Kernel. Normalmente encontraremos como nome ```lib64``` ou ```lib32```, sendo para arquiteturas de  64 bits e 32 bits respectivamente.

## /mnt

Um diretório vazio utilizado para ponto de montagem de discos.

## /media

Um diretório vazio utilizado para ponto de montagem de dispositivos na máquina.

## /proc

Contém informações do Kernel e de processos, sendo um pseudo-filesystem e não existindo realmente no disco. É possível realizar alterações no comportamento do Kernel modificando-se o conteúdo deste diretório.

## /opt

Aqui estão instalados todos os softwares que não são da distribuição Linux por padrão.

## /root

Diretório home do root (superusuário). Algumas distribuições podem não conter este diretório.

## /run

Possui informações do sistema desde a última inicialização, sendo apagados no início do processo de boot. Arquivos que indicam PID (basicamente o ID do processo) do processo em execução estão neste diretório.

## /sbin

Arquivos que são essenciais ao sistema, tais como utilitários para administração da máquina, na qual normalmente somente o superusuário possui acesso aos arquivos, sendo eles "mkfs", "mkswap", "reboot", entre outros.

## /tmp

Diretório para arquivos temporários. 
