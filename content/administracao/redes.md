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

## Configurações de rede

Para visualizar, gerenciar e controlar nossas interfaces de rede ativas podemos utilizar o comando `ifconfig`! Pode ser que em sua distribuição o comando já não venha por padrão mais por ter sido substituído, mas, para que possamos utilizar dele basta instalar o pacote "net-tools". Veja um exemplo abaixo:

```sh
$ ifconfig
```

Ao executar teremos uma resposta parecida com:

```sh
eth0: flags=4000<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 111.22.333.444  netmask 255.255.255.0  broadcast 111.22.333.555
        inet6 fefe::fefe:fefe:fefe:fefe  prefixlen 64  scopeid 0x20<link>
        ether 00:11:00:ff:88:ff  txqueuelen 1000  (Ethernet)
        RX packets 200  bytes 216916 (216.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 100  bytes 10000 (10 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

Os dados mostrados acima, por exemplo, mostram alguns dados de uma interface com nome "eth0", trazendo diversas informações úteis para configurações específicas em um servidor. Caso queira visualizar **todas** as interfaces de rede adicione a opção "-a" ao comando!

### ifup e ifdown

Caso tenha uma interface de rede que está inativa, mas, precisa ligar ela, utilize o seguinte comando:

```
# ifup nome_da_interface
```

Agora, caso queira desligar uma interface de rede utilize o comando:

```
# ifdown nome_da_interface
```

Tome muito cuidado ao trabalhar com as interfaces de rede!

## Rotas

Podemos dizer que as rotas são como "caminhos a se seguir em uma rede para determinado destino", assim como caminhos reais. Geralmente a troca de informação entre computadores não ocorre de forma direta, sendo necessário a existência de máquinas intermediárias, por isso traçamos as rotas para visualizar os possíveis caminhos para uma localização.

Para visualizar as rotas ativas em sua máquina podemos utilizar o seguinte comando:

```sh
$ route -n
```

O comando `route` também pode ser utilizado para se adicionar uma nova rota estática, veja o exemplo abaixo:

```sh
$ route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.1.1
```

O comando acima adiciona uma rota de comunicação do dispositivo na rede local!

## Traçar rotas

Certo, mas, como podemos visualizar todo o caminho de rotas traçadas em uma rede? Simples! Com o comando `traceroute` podemos verificar todo 
