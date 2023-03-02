# Redes

As redes de computadores nos rodeiam de diversas formas, por isso, entender como elas funcionam é uma tarefa essencial! Andrew Tanenbaum é considerado uma das maiores referências quando falamos sobre redes, com seu maravilhoso livro "Rede de Computadores", na qual aborda os principais aspectos de como é o funcionamento de uma rede.

Entender por completo o funcionamento das redes não é essencial para este guia, mas, caso tenha interesse em se aprofundar nessa área, recomendo a apostila [Linux: Administração de Redes](https://www.inf.pucrs.br/~benso/gerencia_redes/2005/manuais/Administracao%20de%20Redes.pdf).

Para nosso compreendimento, vamos esclarecer inicialmente o que é uma rede e como podemos fazer uso dela em ambiente Linux!

## O que são redes de computadores?

Uma rede é formada quando dois ou mais computadores estão conectados, de maneira a conseguir realizar troca de informações entre si. As trocas de informações podem ser feitas de diversas formas, na qual definimos questões adicionais como meios pelos quais estas trocas ocorrem e protocolos a serem compartilhados.

Cada computador possui um endereço para que possamos acessar na rede e realizar conexões, este endereço é chamado de endereço IP, podendo seguir os protocolos IPv4 ou IPv6 por exemplo. Por meio destes endereços que está a mágica de se utilizar de uma rede.

A "internet" (como conhecemos) pode ser chamada de "rede de redes", por ser uma rede internacional de computadores. Quando acessamos um site em um navegador convencional estamos utilizando o protocolo HTTP (Hypertext Transfer Protocol) acessando uma máquina que está hospedando aquele site, na qual a conexão pode ser permitida ou interrompida de acordo com as configurações do site.

Para que o site fique mais "simples e didático" de ser acessado, ao invés de utilizarmos seu endereço IP utilizamos algo chamado DNS (Domain Name System), que tem como principal tarefa "resolver nomes", isto é, dizer que um nome deve apontar para um determinado endereço IP.

Não irei entrar em muitos detalhes sobre como é o funcionamento geral de uma rede, afinal, isto poderia ser um 4noobs exclusivo! Por isso, irei explicar apenas o essencial para que possamos continuar nosso aprendizado entendendo como podemos utilizar sistemas operacionais Linux em nosso cotidiano com as redes!

## Latência

A latência é o tempo de resposta de um servidor, isto é, o tempo para enviarmos uma mensagem, o servidor escutar a mensagem, entender e depois retornar. Basicamente podemos dizer que seria o tempo completo de quando perguntamos algo para alguém e essa pessoa responda a ponto de nosso compreendimento.

Medir a latência em determinadas ocasiões é uma tarefa essencial, assim conseguimos verificar possíveis falhas de comunicação. Para isso vamos utilizar o comando `ping`:

```sh
$ ping -c 4 google.com # Neste caso podemos utilizar qualquer site ou IP
```
> A opção "-c" limita a quantidade de respostas que teremos, sendo neste caso limitado em 4. Caso não limite, o comando continuará a ser executado e pode ser cancelado apertando "CTRL + C".

Teremos uma resposta parecida com:

```sh
64 bytes from blablabla.net (111.222.333.44): icmp_seq=1 ttl=1 time=10 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
```

O retorno mostrado acima mostra o tempo de resposta de um site em "ms", mostrando também a quantidade de pacotes que foram transmitidos e recebidos, assim, analisando nossa perda de pacote também!
