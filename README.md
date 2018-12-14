# Fliperama com Raspberry Pi

**Nome: Mathias Trevisan e Lucas Eduardo Pandolfo**

Decidimos que nosso projeto seria um fliperama com emulador de consoles antigos de vídeo game,
aonde optamos em utilizar a Raspberry (Figura 3) ao invés de uma Beaglebone,
em razão do seu melhor desempenho gráfico e em projetos multimídia.

Neste projeto trabalharemos com as portas GPIO para fazer as entradas do joystick que será o
controle do game, aonde iremos configurar uma compatibilização. Também estaremos utilizando a
porta HDMI da placa para enviar as imagens para um monitor.

O projeto pretende ser implementado a partir da estrutura do fliperama estragado, que pertence ao DCE.
Caso não seja possível, será montado um protótipo similar.

A intensão é de utilizarmos o monitor e o joystick com os botões inclusos no hardware que estão no DCE
(como mostra na figura 1) para implementar um novo fliperama com um Raspberry Pi 3, aonde poderemos o
deixar disponível para substituir o atual com defeito, e assim não desperdiçar o projeto.

Imagens e Videos do projeto
https://drive.google.com/drive/folders/1XPUwyRzA1HuknyGjKVIcBkT6ABPiDq3j?usp=sharing

**Funcionamento do dispositivo**

-Como havia abordado no planejamento do projeto, foi aprovado que podíamos usar os dispositivos 
que o DCE disponibilizou para consertar o fliperama.

-Já foi implementado a placa raspberry, na qual instalamos o retropie para poder rodar os jogos
no fliperama.

-Para poder fazer os testes depois de termos instalado o retropie, usamos controle USBs para ver
o comportamento do sistema se não trancava os jogos ou não rodava.

-Já que o nosso objetivo é implementar o controle por GPIO, o próximo passo seria a programação
dos botões do fliperama.


EXECUÇÃO

O emulador escolhido para o projeto foi o Emulation Station, o qual rodava em cima do sistema operacional RetroPie, permitiu emular na raspberry, diversos consoles.
sendo assim, diversos controles teriam que ser simulados com o joystick.
A vantagem em utilizar este emulador, foi de que ele mesmo gerava uma compatibilidade entre os controles dos diversos consoles, assim, foi apenas preciso configurar entradas de teclado, para que fossem correspondentes aos comendos escolhidos.
Após isso, foi pesquisado as possibilidades de linguagem de programação que seria utilizada para fazer a programação das portas GPIO
que seriam as entradas dos controles, embora o desejo fosse de fazer em linguagem C,
o projeto acabaria se tornando muito complexo e uma confiabilidade muito abaixo do esperado para um joystick de fliperama,
então, a partir desta pesquisa foi decidido por fazer uso da linguagem Python, devido a sua gama de bibliotecas específicas para Raspberry,
e também a menor complexidade do código, qual permitiu uma maior velocidade na procura e concerto dos erros cometidos no desenvolvimento.
a biblioteca utilizada para simularmos as entradas de teclado foi (https://github.com/tuomasjjrasanen/python-uinput), a qual não tivemos problemas em utilizar, pois é bem dinâmica.
A grande dificuldade no projeto foi fazer com que a inicialização do emulador estivesse sincronizada com a abertura do código de leitura das entradas da GPIO, por um descuido, houve uma duplicidade na inicialização do emulador, o qual não aceitava a inicialização do emulador com o comando "sudo"(usado para forçar execução indepentente do usuário), pois este necessitava de senha para autorizar o comando, fazendo com que "travasse" a inicialização.
Após ajuda do professor para encontrar o erro, o projeto funcionou perfeitamente.
