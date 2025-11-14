# Comandos basicos de linux 1 - navegação no shell

Assume-se que o leitor tem uma maquina linux funcional, com um terminal aberto,
utilizando bash (teste com "echo $SHELL"), e que a ultima aula foi assistida

## O que aprenderemos nessa aula

 Iremos ver como usar uma série de comandos para achar a nossa localização no shell,
muda-la, listar arquivos, escrever na tela, etc:

### Comandos
 * echo	- Escrever algo na tela
 * pwd	- Achar o CWD (Current Working Directory)
 * cd	- Mudar o CWD
 * ls	- Listar arquivos
 * man	- Ler paginas de manual
### Temas
 * Caminhos de arquivo absolutos e relativos
 * Arquivos escondidos
 * Flags de comandos
 * Lendo documentação offline


## Comandos e Temas:

 Vale a pena destacar, o shell apresenta um caracter de dolar (`$`) onde deve-se
digitar o comando, ao pressionar enter, uma linha é pulada graficamente e o output
(saida) do comando começa a aparecer caso haja algum


### Echo - seu primeiro comando
 Quando aprendemos a programar, nosso primeiro programa normalmente apenas escreve
uma mensagem de "Hello, World!" na tela, isto é oque faremos aqui:
```bash
diego@UbuntuBox:~/aulas-linux/exec$ echo Hello, World!
Hello, World!
```

 O comando executado é o `echo`, ele lê todos os argumentos e os escreve na tela
com um espaço entre eles, sabendo disso, qual sera o output de `echo Hello   World!`?
(pense e responda antes de seguir a leitura):
```bash
diego@UbuntuBox:~/aulas-linux/exec$ echo Hello    World!
Hello World!
diego@UbuntuBox:~/aulas-linux/exec$ echo 'Hello      World!'
Hello      World!
```
 Perceba a diferença entre os dois comandos, o primeiro, tem os argumentos `"Hello"` e
`"World!"`, o `echo` escreve eles separados com um espaço na tela e pronto! Mas no
segundo comando, as aspas fazem com que só exista o argumento `"Hello      World!"`,
que é impresso inteiro


### pwd - Se localizando no Linux
 Considere o seguinte comando:
 ```bash
 diego@UbuntuBox:~/aulas-linux/exec$ pwd
/home/diego/aulas-linux/exec
```
 O comando `pwd` significa "Print Working Directory", ele mostra o CWD ("Current Working
Directory" - "Diretório de trabalho atual"), um diretório é o nome que as pastas do windows
recebem em sistemas UNIX, o comando `pwd` mostra esse caminho em sua forma absoluta, para entender
isso melhor, é necessario entender o que são os caminhos absolutos e relativos, e usaremos o comando
`cd` para mostrar isso


### cd & Caminhos absolutos/relativos

 Considere um diretório "playground" com essa seguinte estrutura:
```bash
.
├── dir0
│   ├── dir3
│   ├── dir4
│   └── dir5
├── dir1
│   ├── dir6
│   ├── dir7
│   └── dir8
└── dir2
    ├── dir10
    ├── dir11
    └── dir9
```
 Perceba que há um diretório especial que é parente de todos, o "." - "dir0" é parente de
"dir3", "dir4", e "dir5", isto é, estes três diretórios estão dentro de "dir0" - esse nome, ".",
sai do padrão dos outros, e existe um porque, ele é o CWD. Após usar o comando `cd` ("Change Directory"),
podemos ver a estrutura novamente, começando do ".":
```bash
diego@UbuntuBox:~/aulas-linux/playground$ pwd
/home/diego/aulas-linux/playground
diego@UbuntuBox:~/aulas-linux/playground$ cd dir0
diego@UbuntuBox:~/aulas-linux/playground/dir0$ pwd
/home/diego/aulas-linux/playground/dir0
diego@UbuntuBox:~/aulas-linux/playground/dir0$ tree # Desconsidere o uso desse commando
.
├── dir3
├── dir4
└── dir5

4 directories, 0 files
diego@UbuntuBox:~/aulas-linux/playground/dir0$
```
 O comando `cd` muda o CWD para o caminho especificado, perceba que foi usado o argumento "dir0",
este é um caminho relativo, pois começa do CWD (o "."), o comando `cd /home/diego/aulas-linux/playground/dir0`
teria tido o mesmo efeito, e seria um caminho absoluto, pois começa com `/`, a pasta chamada de "root"
(raiz), ela é como o C: do windows, onde tudo começa.
 Também seria possivel voltar do dir0 usando o comando `cd ..`, pois `..` também é um nome
especial que significa o diretório anterior, existem outros nomes especiais também:
 * "`.`": 	Indica o CWD, de onde os caminhos relativos começam
 * "`..`": 	Indica o diretório anterior ao CWD
 * "`~`":	Indica o HOME, uma pasta de cada usuario para guardar seus arquivos especificos
 * "`-`":	Não é um diretório, mas é reconhecido pelo `cd` como o ultimo CWD
 * (nada):	Não é um diretório, mas é reconhecido pelo `cd` como o mesmo que `~`
 Veja o uso de alguns deles a seguir:
```bash
diego@UbuntuBox:~/aulas-linux/playground$ pwd
/home/diego/aulas-linux/playground
diego@UbuntuBox:~/aulas-linux/playground$ cd dir0
diego@UbuntuBox:~/aulas-linux/playground/dir0$ pwd
/home/diego/aulas-linux/playground/dir0
diego@UbuntuBox:~/aulas-linux/playground/dir0$ cd ..
diego@UbuntuBox:~/aulas-linux/playground$ pwd
/home/diego/aulas-linux/playground
diego@UbuntuBox:~/aulas-linux/playground$ cd
diego@UbuntuBox:~$ pwd
/home/diego
diego@UbuntuBox:~$ cd -
/home/diego/aulas-linux/playground
diego@UbuntuBox:~/aulas-linux/playground$ pwd
/home/diego/aulas-linux/playground
diego@UbuntuBox:~/aulas-linux/playground$ cd ~
diego@UbuntuBox:~$ pwd
/home/diego
diego@UbuntuBox:~$ cd -
/home/diego/aulas-linux/playground
diego@UbuntuBox:~/aulas-linux/playground$
```


###  ls - listando diretórios, flags de comandos & arquivos/diretórios escondidos

 Para saber os conteudos de um diretório, podemos usar o comando `ls`:
```bash
diego@UbuntuBox:~/aulas-linux/playground$ ls
dir0  dir1  dir2
```
 Perceba que ele lista os diretórios (e também listaria arquivos se ouvessem algum)
do CWD, o comando também aceita um diretório especifico para listar, por exemplo:
```bash
diego@UbuntuBox:~/aulas-linux/playground$ ls dir0
dir3  dir4  dir5
```
 Além disso, ele também aceita flags (bandeiras), esses são argumentos começados com `-`
ou `--` (tipicamente, as com um unico dash são apenas uma letra, e as outras, palavras)
que ativam uma funcionalidade opcional, por exemplo, a flag `-l` (long listing) mostra
diversas informações dos arquivos/diretórios listados:
```bash
diego@UbuntuBox:~/aulas-linux/playground$ ls -l
total 12
drwxrwxr-x 5 diego diego 4096 Nov 14 19:16 dir0
drwxrwxr-x 5 diego diego 4096 Nov 14 19:16 dir1
drwxrwxr-x 5 diego diego 4096 Nov 14 19:16 dir2
```
 O significado de muitos desses valores só serão explicados em aulas futuras, por
enquanto, é importante saber da existencia dessa flag. Outras duas flags muito usadas
com o `ls` é o `-a` (all) e `-A` (almost all), essas flags são baseadas no conceito de
arquivos e diretórios escondidos, qualquer arquivo ou diretório cujo o nome comece com
"." é considerado escondido, isso significa que os programas irão, em geral, evitar mostra-los
em seu output, isso é feito apenas para a organização, e NÃO É UMA MEDIDA DE SEGURANÇA, segue
o output de `ls -a` e `ls -A` no HOME de uma vm de ubuntu
```bash
diego@UbuntuBox:~$ ls -a
.            .bash_history  .cache   Documents  .lesshst  Pictures       Public  .sudo_as_admin_successful  Videos
..           .bash_logout   .config  Downloads  .local    playground.sh  snap    Templates                  .vim
aulas-linux  .bashrc        Desktop  .gnupg     Music     .profile       .ssh    test                       .viminfo
diego@UbuntuBox:~$ ls -A
aulas-linux    .bashrc  Desktop    .gnupg    Music          .profile  .ssh                       test    .viminfo
.bash_history  .cache   Documents  .lesshst  Pictures       Public    .sudo_as_admin_successful  Videos
.bash_logout   .config  Downloads  .local    playground.sh  snap      Templates                  .vim
```
 Muitos desses arquivos tem significado real, e serão explorados em aulas futuras, por exemplo,
o .bashrc permite customizar o seu shell bash, o .ssh é onde as suas chaves ssh (muito usadas
para acessar servidores, por exemplo) ficam guardadas, etc. Perceba também que a unica diferença do
`-A` para o `-a` é que ele não mostra os diretórios `.` e `..`, os quais sabemos que sempre existem
 Flags também podem ser combinadas, isso significa que `ls -la` é a mesma coisa que `ls -l -a`,
segue o output reduzido desse `ls -lA` no HOME do meu computador pessoal, com ArchLinux:
```bash
(0) [~] diego@Linux-$ ls -lA
total 420
-rw-------  1 diego diego 158952 Nov 14 19:23 .bash_history
-rw-r--r--  1 diego diego     72 Aug 14 13:37 .bash_profile
-rw-r--r--  1 diego diego   1389 Nov  5 16:57 .bashrc
drwx------ 24 diego diego   4096 Nov 13 18:52 .cache
drwxr-xr-x 17 diego diego   4096 Nov 13 15:10 .config
drwxr-xr-x  6 diego diego   4096 Nov 13 15:02 downloads
# (...) O output continua
```


 ### man - Lendo documentação (manuais) online

 As flags são extremamente comuns em todos os programas, existem dezenas, ou até centenas,
para diversos deles, e obviamente não conseguiremos decorar todas, por esse motivo, existe
o comando `man`, ele nos permite ler um manual de cada programa, basta usar 'man ls` para
ver uma explicação de como usar o `ls`. As paginas de manual são formatadas de uma forma especial,
algo que você aprenderá a interpretar melhor com o tempo, mas mesmo sem saber os significado
especial de algumas coisas (e.g. `<abc>` = "abc" é obrigatorio, `[abc]` = "abc" não é obrigatorio, etc),
apenas a descrição de todas as flags e o que o programa faz já é extremamente util. Quando
referenciamos uma pagina de manual, normalmente fazemos isso como <commando>(pagina), por exemplo,
`ls(1) (A explicação sobre paginas faz parte da leitura recomendada e exercicios), aqui, usaremos o
formato `man:<commando>(pagina)`. O output desse programa não será mostrado aqui, pois são muito grandes.


### Leitura recomendada

 * [Entendo man pages e encontrando mais documentação](https://itsfoss.com/linux-man-page-guide/)

### Exercicios

 1. Porque o comando `man printf` mostra a informação de um programa, e `man 3 printf` da função printf() da linguagem C
 2. Como você faria para listar os atributos do `ls -l` de um diretório? pense e test (consulte man:ls(1))
 2. Quais flags dos programas você achou interessante? experimenteas e veja como você pode combina-las
 3. Explore os diretórios dentro do seu HOME
 4. Explore e pesquise sobre oque há nos seguintes diretórios:
   * /
   * /home
   * /bin
   * /usr/include

### Fontes

 * man:echo(1)
 * man:pwd(1)
 * man:cd(1)
 * man:ls(1)
 * man:man(1)
 * [Artigo postado na RedHat sobre navegação do filesystem](https://www.redhat.com/en/blog/navigating-linux-filesystem)
 * [Artigo da Wikipedia sobre arquivos/diretorios escondidos](https://en.wikipedia.org/wiki/Hidden_file_and_hidden_directory)
