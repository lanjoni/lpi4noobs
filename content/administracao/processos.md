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

