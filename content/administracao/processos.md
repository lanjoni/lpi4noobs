# Processos

Nesta etapa vamos entender um pouco sobre como é o funcionamento dos processos dentro de um sistema operacional Linux, vamos lá?

## O que é um processo?

De uma forma básica, podemos dizer que um processo é tudo que está em execução no nosso sistema operacional, englobando **tudo** mesmo, como por exemplo: abrir um terminal com vim, uma outra aba com o LibreOffice Writer, ou então até mesmo o simples ato de executar um comando. Tudo citado é um processo, estando ou não em execução no momento, é uma tarefa que nosso sitema operacional fez ou está fazendo.

De uma maneira mais sólida: um processo é toda ação executada em nosso sistema operacional, na qual podemos gerenciar e controlar.

É claro que existem "camadas" quando o assunto é processo, afinal, nem todos os processos funcionam com os mesmos graus de prioridade... Alguns são mais importantes que outros, por isso, surge a necessidade de entender o funcionamento de processos no nosso sistema operacional.

## Sinais de processo

No Linux temos mais de 30 sinais de processos definidos, sendo a maioria definidos pelo kernel, na qual possuem uma tabela de "sinal", "valor numérico" e "ação" que esse sinal vai tomar. Veja a tabela abaixo com alguns exemplos:

| Sinal | Valor numérico | Ação                                                                                                                                                                            |
|-------|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| HUP   | 1              | Utilizado automaticamente quando se é desconectado de uma sessão (fechando o terminal, por exemplo), sendo utilizado também para invocar releitura de arquivos de configuração. |
| KILL  | 9              | Finaliza o processo de forma rápida, podendo deixar arquivos corrompidos (caso estejam abertos), sendo necessária muita cautela ao se utilizar.                                 |
| TERM  | 15             | Finaliza o processo de uma forma mais "calma", permitindo que termine as execuções pendentes de um processo para que então possa finalizá-lo.                                   |
| TSTP  | 20             | Finaliza a execução para continuar depois, enviado automaticamente quando utilizamos as teclas de comando "CTRL" + "Z", para reverter modificações.                             |

## Comandos para visão específica

Agora vamos conhecer alguns comandos que são utilizados para visualizações de tipos de processo específicos, por isso essa nova área!

### jobs

Este comando é responsável por listar os processos que estão em execução em segundo plano. O comando `jobs -l` lista o PID (Process Identifier) dos processos em execução! 

### bg

Com este comando podemos colocar em segundo plano determinados processos que se encontram em execução! 

### fg

Neste comando temos um papel totalmente contrário ao comando "bg", afinal, com o "fg" colocamos a tarefa em primeiro plano, ligando-a em um terminal!

### nohup

Com o "nohup" conseguimos executar qualquer outro comando sem a necessidade de atrelá-lo a nenhum terminal, sendo imune a travamentos, quedas de conexão e desconexões propositais.

Ele pode ser útil para executar aplicações e armazenar os retornos de "logs" em um novo arquivo de texto, porque assim nenhum usuário teria "acesso" para ver seus logs em tempo real!

## Comandos para modificar prioridade de execução

Como dito anteriormente, não podemos simplesmente definir que todos os processos devam funcionar com o mesmo grau de prioridade sempre, afinal, existem "tarefas mais importantes que outras", correto? Dessa necessidade surgiram comandos que possibilitassem a modificação de prioridades de execução de maneira fácil e prática!

### nice

Com este comando podemos ajustar o tempo disponível de CPU de um processo para um nível maior ou menor de prioridade. Um exemplo prático para aumentar a prioridade de um processo seria:

```sh
$ nice -n -10 processo
```

### renice

Este comando ajusta a prioridade de execução de um processo que já se encontra em execução, recebendo por padrão o PID do processo como parâmetro. Geralmente podemos adicionar algumas opções com o comando "renice", sendo possíveis:

- **-p**: Define um PID;
- **-u**: Define um nome de usuário para alterar todos os processos em execução deste usuário;
- **-g**: Define um nome de um grupo para alterar a prioridade de todos os processos que percentem ao grupo;

Um exemplo prático seria com:

```
# renice -1 1337 -u guto root -p 32
```
> O processo de número PID 1337, com PID 32, além de todos os processos dos usuários "guto" e "root" terão maior prioridade.

O que achou de trabalhar com modificações de prioridade?

## Comandos para visão geral

Além da visão específica, temos a visão geral, que nos permite visualizar como está o funcionamento de nosso sistema operacional por completo, permitindo o gerenciamento de diversas funcionalidades, por isso, vamos dar uma olhada em mais alguns comandos!

### ps

Utilizando o comando "ps" podemos listar todos os processos que estão em execução e seus atributos, podendo ainda customizar com algumas opções, veja:

- **-a**: Mostra os processos em execução de todos os usuários;
- **-u**: Mostra uma lista de processos incluindo nome dos usuários que são donos dos processos, início das execuções, percentual de CPU utilizada e percentual de memória utilizada;
- **-x**: Mostra uma lista de processos que não possuem um terminal associado, sendo útil para visualizar processos de servidores;
- **-f**: Mostra os processos em formato de árvore, facilitando a identificação de processos pai e filho;

### pstree

Neste comando podemos visualizar uma árvore de processos, partindo do "init" até o processo mais recente em execução, sendo similar ao `ps -auxf`, podendo ainda ser combinado com mais algumas opções:

- **-a**: Mostra a linha de comando utilizada para iniciar o processo;
- **-c**: Desabilita a mescla de processos indênticos na mesma camada de hierarquia;
- **-h**: Destaca todos os processos que estão ligados ao terminal;
- **-p**: Mostra o PID de cada processo;

### top

O comando "top" mostra os processos em execução, mas, atualizando a tela em tempo real, além de servir como monitor para diversos processos do sistema por mostrar em sua interface informações sobre uso de memória e CPU, além de ordenar os processos pela quantidade de uso da CPU. Algumas opções para o comando:

- **-b**: Execução em modo batch, utilizado para direcionar a saída do comando para outro processo;
- **-d N**: Utilizado para determinar o tempo das atualizações da tela em "N" segundos, sendo cinco segundos o padrão;
- **-n N**: Utilizado para mostrar o número de atualizações dos processos em execução;
- **-q**: Ativa as atualizações em tempo real, mas, pode consumir grande quantidade da CPU;
- **-u**: Define um usuário para monitorar os processos;
- **-p**: Monitora processos determinados pelos seus PIDs;

Além das opções, podemos interagir com o comando "top" enquanto se encontra em execução! Algumas teclas podem ser ativadas para determinadas ações, veja:

- **u**: Mostra os processos de determinado usuário;
- **k**: Finaliza um processo (kill);
- **r**: Altera a prioridade de execução e um processo (renice);
- **q**: Sai do modo interativo do top;
- **Z**: Muda o esquema de cores do top (necessita de terminal que suporte ANSI);
- **F**: Adiciona colunas com algumas opções de monitoramento;
- **R**: Altera a ordem dos processos, se baseando na utilização de CPU;

Além do "top" existem algumas alternativas para utilizá-lo de forma mais interativa, com comandos que podem ser instalados em sua distribuição Linux! Dois principais deles são o "htop" e o "bashtop", permitindo uma visualização diferenciada!

### pgrep

Sendo uma mistura do comando "ps" com o comando "grep", este comando permite que procuremos por expressões nos processos em execução, retornando o PID do processo em questão! Seu uso é bem simples:

```
# pgrep expressao
```

Muito legais estas combinações de comandos, não é?

## Finalizando processos

Agora que você já sabe como monitorar processos e entendeu um pouco mais sobre seu funcionamento, o que acha de aprender a finalizar processos? Lembre-se: faça com bastante cuidado e cautela, sendo **de preferência** em uma máquina virtual para evitar possíveis quebras de processos!

### kill

O comando "kill" é utilizado para enviar sinais para os processos, sendo geralmente utilizado para finalizar a execução de processos identificados pelo PID. Sua sintaxe é bem simples:

```sh
$ kill [sinal] PID
```
> Caso o sinal não seja passado, será enviado com o sinal **TERM** (15) por padrão, para assim finalizar um processo de forma "elegante".

O comando kill é extremamente útil, mas, tome cuidado com seu uso indevido!

### killall

O comando "killall" também é utilizado para enviar sinais para os processos, mas, diferente do comando "kill" que recebe o PID de um processo, o comando "killall" recebe o nome de um processo, enviando sinais para todos que tiverem o mesmo nome. Sua sintaxe é bem simples:

```
# killall [sinal] NOME
```
> Caso o sinal não seja passado, será enviado com o sinal **TERM** (15) por padrão, para assim finalizar um processo de forma "elegante".

Tome muito cuidado com o comando "killall", afinal, ele enviará o sinal para todos os processos na fila de execução com determinado nome!

### pkill

Este comando pode enviar sinais para processos diferentes, recebendo como parâmetro uma expressão ou nome do processo, sendo geralmente utilizado para finalizar a execução de processos que possuem diversos processos filhos em execução! Sua sintaxe é bem simples:

```sh
$ pkill nome
```

Assim conseguimos manipular de uma forma mais prática os processos que tenham filhos!

Quer estudar e se aprofundar um pouco mais sobre o funcionamento de processos dentro de nosso sistema operacional? Acesse a publicação do [Certificação Linux](https://www.certificacaolinux.com.br/trabalhando-com-processos-no-linux/)!

---

Gostou de entender melhor o funcionamento de processos em nosso sistema operacional Linux? O que acha de aprendermos um pouco mais sobre a manipulação de usuários em nosso ambiente?

<p align="right">
  <a href="https://github.com/lanjoni/lpi4noobs/blob/main/content/administracao/usuarios.md">Próximo -> Usuários</a>
</p>

<p align="left">
  <a href="https://github.com/lanjoni/lpi4noobs#roadmap">Voltar para o menu principal</a>
</p>
