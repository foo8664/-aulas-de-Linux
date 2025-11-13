# Introdução a Linux e Conceitos Relacionados

## Oque é Linux

 Linux é um Kernel, e não um sistema operacional! Mas então, o que é um kernel? Para
entender isso, é necessario entender que um sistema operacional é, na verdade, uma
serie de programas, aplicações, e camadas de abstração, como:
 * Bootloader: É o programa que boota o computador, em termos populares, ele o liga (ex: grub)
 * Kernel: É a parte mais importante do sistema operacional, ele controla os recursos de CPU, memoria, e periféricos (ex: Linux)
 * sistema de inicialização: Alavanca o sistema e o "configura" para ele funcionar corretamente (ex: systemd)
 * Aplicações: Programas usados pelo usuario no seu dia a dia (ex: Firefox)
 * Etc... (Daemons (ex: cron), Ambientes de Desktop (ex: KDE), Servidor grafico (ex: X11), ...)
 Mas então, como acessamos o sistema operacional conhecido como Linux? E como ele é chamado?
O sistema operacional Linux é chamado de GNU/Linux, isso pois diversos dos componentes além
do kernel são providenciados pelo projeto GNU (GNU's Not Unix). O GNU/Linux é distribuido no
formato de distribuições, estas, são versões diferentes do tal, feitas com intenções diferentes
para usuarios diferentes e mantidas por times e organizações diversos, existem familias de
distribuições, como a familia debian, slackware, etc, uma [arvore](https://wpollock.com/Unix/us__en_us__ibm100__linux__linux_timeline.pdf) e [lista](https://en.wikipedia.org/wiki/List_of_Linux_distributions) dessas
podem ser encontradas em varios lugares. Durante o resto da aula, os termos "Linux" e
"GNU/Linux" serão usados com o significado unico de "GNU/Linux"


## Porque Aprender e Usar GNU/Linux

 Linux esta em 500 dos 500 super computadores mais importantes, 78.5% dos desenvolvedores o usam
como sistema operacional primario ou secundario, 78.3% dos servidores webs usam Linux, e porcentagems
tão grandes quanto podem ser encontradas em diversas outras áreas, como data centers governamentais (64.9%),
missões criticas em empresas "fortune 500" (72.6%), plataformas de e-commerce (67.8%), etc.
 Além disso, existem uma serie de motivos pessoais, sejam de eficiência, preferencia, ou ética, para
se usar o Linux:
 * Segurança: O modelo de permissões é considerado extremamente seguro
 * Portabilidade: Programas para desenvolvedores quase sempre chegam primeiro - ou apenas - no Linux
 * É Software Livre: Um movimento começado por Richard Stallman, fundador do projeto GNU, argumenta-se que o Linux é mais ético que outros OSes (Operating systems)
 * Conhecimento: O Linux te permite o controle total do computador, e te força a entender como ele realmente funciona


## Diferença entre shell e terminal

 Todos conhecemos a famosa tela preta onde os comandos são digitados, este, é um terminal,
oque muitas pessoas não sabem é que este programa, na realidade, apenas renderiza o output
grafico em uma tela, o que realmente executa os comandos/programas é o shell, aquilo que
estaremos interagindo durante essas aulas. Existem diversos shells diferentes, estaremos
usando o bash (Bourne-Again SHell), o mais comum de todos.
 O shell interpreta os comandos e os organiza pelos espaços, isto é, `ls -l -a /home/diego`
sera interpretado como: "execute o programa ls com os argumentos [-l, -a, /home/diego]", esta divisão
pode ser ultrapassada com o uso de aspas duplas ou singulares (" e '), ou seja, os argumentos de
`ls -l -a /home/diego oliveira` serão [-l, -a, /home/diego, oliveira], enquanto os de
`ls -l -a "/home/diego oliveira"` serão [-l, -a, /home/diego oliveira] \(perceba que não há virgula após "diego"\).
 O bash, assim como muitos outros shells, também permite a interação modular entre comands
de forma completamente arbitraria, isto é feito por meio de diversos recursos, como variaveis, pipes,
redirecionamento de arquivos, substituição de comandos, etc, aprenderemos essas utilidades em uma aula futura


## Fontes e Referencias (em inglês):

 As fontes para esta aula estão disponiveis a seguir, aquelas precedidas com "(ler)"
têm a sua leitura deixada como um exercicio à quem lê este documento, a grande maioria são
artigos de empresas, organizações, ou programadores relevantes e experientes no assunto, cuja
leitura pode ser feita em alguns minutos, todas as fontes estão em inglẽs, mas podem ser traduzidas
com o recurso de tradução de paginas presente na maioria dos browsers modernos (Firefox, Google Chrome, etc).

 * (ler) [Visão geral do Linux e suas utilidade](https://www.ibm.com/think/topics/linux)
 * (ler) [Explicação do que é Linux](https://www.linux.com/what-is-linux/)
 * [Top 3 Razões do porque o Linux é tão usado em super-computadores](https://www.sealevel.com/linux-os)
 * (ler) [Porque aprender Linux](https://linuxhandbook.com/why-learn-linux/)
 * [Estatisticas citadas](https://sqmagazine.co.uk/linux-statistics/)
 * (ler) [Explicação sobre shells e a historia deles](https://en.wikipedia.org/wiki/Shell_(computing))
 * (ler) [Oque é Software Livre](https://www.gnu.org/philosophy/free-sw.html)

### Extra

Para as proximas aulas, será necessario acesso a uma maquina Linux, recomendo que instale
o Ubuntu em uma maquina virtual, um tutorial oficial pode ser encontrado [aqui](https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox#1-overview)
