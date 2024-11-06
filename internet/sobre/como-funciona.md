# Como a internet funciona?

Pode se dizer que a internet é uma rede de redes, **mas afinal o que é uma "rede"?**

## O que é uma "rede"?

Uma rede é basicamente vários computadores conectados que compartilham dados entre si. 
Os computadores se conectam dentro das redes e essas redes também se conectam entre si, assim um computador pode se comunicar com outro, trocar informações, e fazer atividades em conjunto. 
Isso acontece basicamente por meio de fios, cabos, ondas de rádio e vários outros tipos de **Infraestrututa de Rede**. 
Os dados enviados pela internet são traduzidos em **bits**, e interpretados por outro computador.

## Finalmente, como a internet funciona?

Existem dois conceitos que são super importantes para o funcionamento da internet, são eles:

### Pacotes

Um pacote é uma pequena porção de uma mensagem maior, cada pacote contém tanto dados quanto informações sobre os dados.
As informações sobre o conteúdo do pacote é chamada de cabeçalho e vai na frente do pacote para que a máquina que vai receber, saiba o que fazer com o pacote.
É praticamente um produto que vem com uma instrução de montagem, onde o produto é o pacote e o manual de montagem é o cabeçalho.

Quando os dados são enviados pra internet, primeiro eles são divididos em pacotes menores e depois traduzidos em bits. 
Os pacotes são encaminhados por vários dispositivos de rede, tipo roteadores, switches, repetidores, modem e etc.
Quando os pacotes chegam no destino, o dispositivo de rede receptor (ou seja, o moldem do computador que vai receber o dado), monta novamente os pacotes na ordem correta e então consegue utilizar ou exibir esses dados,

Os pacotes são enviados pela internet usando uma técnica chamada **Comutação de Pacotes**, que nada mais é do que o envio de uma mensagem de dados dividida em pequenas unidades (que são os pacotes).

### Protocolos

Os protocolos resolvem o problema de conectar dois computadores que tem hardwares e softwares diferentes um do outro, os protocolos servem pra padronizar e formatar os dados para que os dois computadores possam se comunicar e se entender.

Exemplos de protocolo e suas responsabilidades:

* Ethernet -> para envio de pacotes entre dispositivos na mesma rede
* IP -> para envio de pacotes de rede pra rede
* TCP -> para montar as partes dos pacotes em ordem e para manter a conexão entre o remetente e o destinatário
* HTTP -> para transferir informações entre dois dispositivos em rede, usado pra carregar páginas web usando links de hipertexto
* UDP -> para transmissões sensíveis ao tempo, como reproduções de vídeo

## Estudo feito com base nos conteúdos seguintes:

* [Como a internet funciona - Refatorando - Youtube.](https://www.youtube.com/watch?v=PaOOO2VdBoc&ab_channel=Refatorando)
* [Protocolo IP - NICbrvideos - Youtube.](https://www.youtube.com/watch?v=HNQD0qJ0TC4&ab_channel=NICbrvideos)
* [Como a internet funciona - Cloudflare - Site.](https://www.cloudflare.com/pt-br/learning/network-layer/how-does-the-internet-work/)
* [Sistemas Autônomos, BGP, PTTs - NICbrvideos - Youtube.](https://www.youtube.com/watch?v=C5qNAT_j63M&ab_channel=NICbrvideos)
