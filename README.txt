Esse projeto foi criado para ensinar o básico da utilização do GIT.

**Texto que é o GIT?**

**Texto de configuração do GIT**

-------------> INICIANDO UM PROJETO GIT

O primeiro passo para começar um projeto git é criar uma pasta. Depois navegar via terminal até essa pasta (ou abrir o terminal a partir da pasta) e digitar o seguinte comando:

> git init

Esse comando irá criar uma pasta oculta com arquivos necessários para que software git possa gerenciar os arquivos dentro da pasta do seu projeto. Mas, ainda o projeto não está sobre gerenciamento de versão do git. O próximo passo é iniciar seu projeto com algum arquivo. Quando trata-se de código seja ele aberto ou privado é importante ter um arquivo chamado "LICENSE". Dentro desse arquivo colocamos o texto referente à qual licensa está agindo sobre o conteúdo do seu projeto . Caso seu projeto esteja em um repositório de código aberto como a versão gratuíta do GitHub e não haja nenhum arquivo LICENSE isso quer dizer que automaticamente você está aplicando os termos de licensa padrão de direito de cópia. Ou seja, ninguem tem direito de usar seu código. Logo, se seu objetivo é deixar o código aberto, então adicione um arquivo LICENSE.txt no primeiro nível da pasta do seu projeto e coloque dentro alguma licensa de uso livre, como por exemplo a licensa MIT. 
Bem, após adicionar nosso primeiro arquivo (que nesse caso foi o LICENSE mas poderia ser qualquer outro) podemos dar o primeiro commit. IMPORTANTE, só depois do commit é que o git irá gerenciar as mudanças no seu projeto. Primeiro vamos dizer para o git que estamos adicionando o primeiro arquivo modificado:

> git add LICENSE.txt

Este comando acima é de multipropósito ele serve para adicionar novos arquivos à staged area e adicionar arquivos já existentes que foram modificados à staged area. Também, quando excluimos algum arquivo precisamos "falar (adicionar)" à staged area que realmente estamos excluindo um arquivo da nossa nova versão.

Depois, vamos fazer o commit:

> git commit -m "Texto entre aspas que justifica o commit" 

Esse texto entre aspas é um texto que você escreve para que você possa identificar qual foi a mudança que vc fez, fica mais fácil depois voltar a alguma versão importante do projeto através de commits de fácil identificação.


-------------> CHECANDO O ESTADO DOS ARQUIVOS VERSIONADOS

Podemos ver o estado em que o git está através do comando

> git status

Este comando mostra se algum arquivo foi modificado e não está sendo monitorado, ou, se todos os arquivos do projeto estão monitorados. Se a cor do arquivo estiver vermelha quer dizer que não está monitorado. Se aparecer em verde quer dizer que ele foi adicionado pelo comando > git add arquivo < e podemos fazer o commit para atualizar a versão do projeto. Se nenhum arquivo aparecer quer dizer que está tudo atualizado. O comando também mostra em qual ramo do projeto vc está trabalhando, se é um ramo paralelo ou se está trabalhando no ramo principal do projeto.

Um informação importante sobre o comando > git add < : Se você faz uma alteração e adiciona o arquivo para a staged area e não executa o commit e depois altera esse arquivo e salva e faz o commit a versão do arquivo que irá ser adicionada será a com o conteúdo de quando você executou o comando git add.

Existe um comando que faz ao mesmo tempo a adição dos arquivos modificados e realiza o commit que é o comando:

> git commit -a

Ou seja, ele vai mandar os arquivos alterados para a staged area, solicitar que você digite um texto para o commit e depois de finalizar o texto e apertar enter ele vai realizar ter atualizado a versão do seu projeto.

Há um comando alternativo ao > git status < que é o > git status -s < Esse comando permite receber um informações sobre o repositório com informações mais resumidas. Os resultados em que os arquivos podem estar são:
> M  arquivo --> Refere-se a um arquivo modificado
> A  arquivo --> Adicionado para a staging area
> ?? arquivo --> novo arquivo que não está sendo monitorado
> MM arquivo --> Arquivo foi modificado, adicionado a stage area e depois modificado de novo.

Existem duas colunas onde esses valores podem aparecer como ilustrado abaixo:
> LR arquivo

O L significa Left Hand e R right hand... O valor aparecendo do lado esquerdo indica o status do arquivo referente à staging area e do lado direito referente à working tree. Exemplo:
>  M arquivo --> veja que há dois espaços em branco ali na lateral isso quer dizer que o arquivo foi alterado na working tree mas não foi adicionado à staging area.
> M  arquivo --> nesse caso o arquivo foi modificado na staging area, ou seja, está adicionado para o commit. Preste sempre atenção à distância entre o codigo do status e o nome do arquivo, isso indica em qual lado da coluna está o codigo do status. Ou simplesmente uso o > git status para obter um status mais detalhado.

-------------> FAZENDO O GIT IGNORAR ARQUIVOS DO PROJETO

Talvez em alguma situação a gente queira ignorar algum arquivo quando usamos o git status (ou seja, não adicionaremos esse arquivo ao nosso repositório). Então para isso a gente pode criar um arquivo no nosso projeto, chamado > .gitignore <. Dentro desse arquivo vamos colocar o nome e a  extensão do arquivo à ser ignorado ou *.extensãoindesejada para ignorar todos os arquivos que terminam com aquela extensão... bem podemos usar outras capacidades do bash ou shell para identificar estes arquivos, mas não iremos falar disso aqui. Caso também não queiramos que o próprio arquivo .gitignore seja adicionado no nosso repositório podemos recursivamente declarar o proprio .gitignore dentro do arquivo .gitignore. Bem, no linux é mais fácil criar esse arquivo, mas no windows isso pode ser um pouco mais dificil, vamos ver oque podemos fazer:

1° Podemos criar um arquivo .txt qualquer dentro da nossa pasta principal do repositório e escrever lá quais arquivos queremos que sejam ignorados. Depois disso, abrimos o terminal dentro desta pasta e usamos o comando para renomear o arquivo qualquer.txt, da seguinte forma

> ren qualquer.txt .gitignore

pronto nosso arquivo foi renomeado.

2° Podemos abrir o terminal dentro da pasta e usar o comando de escrita de texto dentro de um arquivo, aqui é importante saber que se o arquivo destino que a gente especificou no comando não existir ele será criado automaticamente. Ou seja, caso ela exista ele so receberá o texto na sua ultima linha não escrita e se ele não existir ele será criado com o texto que a gente escreveu. Então o comando explicado é o seguinte:

> echo "texto" > .gitignore

pronto nosso arquivo .gitignore foi criado com a palavra --> texto <-- dentro dele... perceba que essa palavra texto pode ser simplesmente a regra de exceção ou ignorar para o git. Alguns exemplos a seguir:
 
# ignore all .a files
*.a

# but do track lib.a, even though you're ignoring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in any directory named build
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in the doc/ directory and any of its subdirectories
doc/**/*.pdf

_____________________O gitignore tem uma peculiaridade complicada que pode gerar alguns problemas. Temos que ter certeza que o arquivo foi salvo com um text enconding
UTF-8. Quando usamos o PowerShell o arquivo vem pelo padrão do profile de codificação do windows que pode ser "UNICODE" para isso quando gerarmos o arquivo podemos no formato correto podemos usar o terminal assim: 

>Set-Content -encoding utf8 <nome do arquivo>

Após isso digitamos o conteúdo que queremos e apertamos enter duas vezes... Bem, depois podemos abrir o arquivo em um editor de texto só alterar o conteúdo ou adicionar novas exceções e salvar normalmente. Lembre--se de quando o ignore não estiver funcionando podem ser duas coisas::
1ª O arquivo foi salvo com um encoding diferente de ANSI ou UTF8
2ª O arquivo que adicionamos a exceção foi commitado antes de adicionarmos no .gitignore

-------------> MOVENDO E RENOMEANDO ARQUIVOS

Caso tenhamos adicionado algum arquivo por engano e queremos removelo antes de dar commit
podemos usar o seguinte comando:

> git rm --chached <nome do arquivo>

Um comando mais poderoso que pode ser utilizado para mostrar oque foi mudado dentro de um arquivo e que esteja na área de transferência é o:

> git diff --staged

Lembre-se que ele compara os seus arquivos na staged area e o que está no seu ultimo commit

Caso você mande um arquivo para a staged area e antes de dar o commit você troque alguma informação no seu working directory podemos comparar o conteudo entre estes arquivos através do comando:

> git diff

Para renomear um arquivo, podemos usar o seguinte comando:

> git mv [file_from] [file_to]

Veja que este é comando é um pouco estranho visto que na realidade você está movendo um conteúdo. Você pode movê-lo pelo git para dentro de uma pasta qualquer normalmente.

Pode também usar o comando natural do shell que é o > ren < para renomear uma pasta.

-------------> VISUALIZANDO O HISTÓRICO DE COMMITS

Para podermos ver o histórico de commit podemos usar o comando

> git log 

Ele irá mostar o histórico de commit com data e hora e quem fez o commit em ordem cronológica inversa: do mais recente para o mais antigo. Para sair desse modo de apresentação do log podemos apertar as teclas "shift + z" duas vezes. Para uma log mais detalhado do que foi feito, quais as diferenças nos arquivos em cada commit usamos o comando:

> git log -p

Bem, esse comando vai mostrar todas as diferentes de todos os arquivos entre um commit e outro... para algo mais enxuto e específico caso queira saber de um arquivo em específico podemos usar o comando:

> git log -p [arquivo_desejado]

Ainda, caso queiramos saber somente sobre uma quantidade limitada de commits, como por exemplo os últimos 3 commits podemos usar o seguinte comando:

> git log -p -x //comentário: onde "x" é um valor numérico que indica a quantidade de últimos commits que vc deseja visualizar.

Para uma visualização do log ainda mais enxuta, podemos usar o comando:

> git log --stat

Caso você esteja trabalhando em um projeto onde haja vários commits e você esteja procurando por algum em específico ou queira visualizar tudo que foi commitado de uma forma mais rápida e simplificada podemos usar o comando:

> git log --pretty=[argument] //comentário: bem há vários tipos de modelos de visualização, cada modelo tem seu valor para ser colocado onde está escrito "argument"
Algumas opções são: oneline, short, full e fuller. O "oneline" vai imprimir cada commit em uma única linha.

Bem, ainda há uma opção personalizada de como pegar seu commit. Essa versão personalizada é você quem faz, no link a seguir é possível ver uma boa explicação sobre essa opção: https://git-scm.com/docs/pretty-formats

Se pensarmos um pouco podemos perceber que gerenciar um projeto é algo bastante complicado, e projetos complexos e longos irão necessitar de muitos commits. Então o git log possui um comando muito útil para podermos filtrar qual o retorno de log que queremos, veja podemos filtar por limite de data como por exemplo tudo que foi commitado nos últimos 5 dias ou 2 semanas, horas, minutos e segundos. Também, podemos filtrar por autor... vejamos alguns exemplos à seguir:

> git log --since=1.weeks //comentário: vamos receber um log de tudo que foi commitado na última semana. Veja que é um log extenso. Podemos usar o pretty para enxugar esse log.

> git log --since=1.weeks --pretty=oneline //comentário: veja que agora é algo muito mais enxuto

> git log --since=1.days --pretty=oneline //comentário: log do último 1 dia.

> git log --since="2019-12-22" --pretty=oneline //comentário: veja que agora especificamos uma data para pegar os commites até este dia em específico.

Para poder filtar por author é importante salientar que a expressão exige que o author seja especifica log após "git log" ou pretty depois podemos usar os outros critérios de filtros, por exemplo:

> git log --pretty=oneline --author='Matheus Dias' --since=2.days //comentário: aqui vamos ver os commits do author "Matheus Dias" desde há 2 dias atrás.

Como podemos ver existem muitas opções para podermos procurar um commit em específico, pode ser muito útil tanto para restaurar o projeto para um ponto em específico. As opções são tantas que é possível estabelecer um limite superior e inferior de datas para saber oque foi commitado nestes dias.

-------------> DESFAZENDO COISAS NO GIT

Caso você tenha feito um commit no qual adicionou somente uma parte do conteúdo que queria ter adicionado naquele commit, você pode usar o comando a seguir para adicionar o conteúdo que faltou ao seu ultimo commit. Antes de usar o comando precisamos adicionar os arquivos ausentes:

> git add [arquivo]

Então assim, usamos o --amend:

> git commit --amend














 