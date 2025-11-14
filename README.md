# "Aulas" de GNU/Linux

 Esse repositorio contem aulas em Markdown (.md) sobre o uso do GNU/Linux (popularmente
conhecido apenas como Linux), as aulas contém conteudo sobre comandos encontrados
em distribuições diversas de Linux, assim como conteudo teorico (organização do
filesystem, permissões de arquivos, terminologia, etc).


## Minha "qualificação"

 Nenhuma. Uso Linux a alguns anos, mas não tenho nenhuma qualificação, e é extamente
por isso que todas as aulas terminarão com fontes para verificação e aprendizado,
as quais incentivo a todas as pessoas lendo as aulas a lerem.


## Para oque essas aulas foram criadas

 Essas aulas foram criadas com um unico objetivo: Ajudar e ensinar aos meus colegas
que conheci durante o processo de seleção do sprint behring no servidor não oficial
que criamos.

## Arquivos .cast em casts/

 Durante as aulas, diversas sessões de bash são mostradas para exemplificar o uso
dos comandos, essas sessões são gravadas com o [asciinema](https://github.com/asciinema/asciinema), e por isso, só
podem ser vistas de forma interativa usando o asciinema (`asciinema play <arquivo.cast>`).
 É possivel converter os arquivos para .mp4 usando o `ffmpeg` e `asciicast2gif`, mas
o [uso](https://www.vivaolinux.com.br/topico/Duvidas-em-Geral/arquivo-cast-para-mp4-ou-avi) deles está fora do escopo deste readme.
 Também é possivel ver as sessões em .txt com `asciinema convert <arquivo.cast> <arquivo.txt>`,
embora esse formato já esteja disponibilizado nas aulas, dentro dos arquivos .md

## Pré-requisitos

 É necessario uma maquina com Linux, pode ser uma maquina virtual, em hardware real,
WSL, etc. Recomendo que comece com uma maquina virtual, e, eventualmente, instale
em hardware real.
