Esse projeto foi criado para ensinar o b�sico da utiliza��o do GIT.

**Texto que � o GIT?**

**Texto de configura��o do GIT**

-------------> INICIANDO UM PROJETO GIT

O primeiro passo para come�ar um projeto git � criar uma pasta. Depois navegar via terminal at� essa pasta (ou abrir o terminal a partir da pasta) e digitar o seguinte comando:

> git init

Esse comando ir� criar uma pasta oculta com arquivos necess�rios para que software git possa gerenciar os arquivos dentro da pasta do seu projeto. Mas, ainda o projeto n�o est� sobre gerenciamento de vers�o do git. O pr�ximo passo � iniciar seu projeto com algum arquivo. Quando trata-se de c�digo seja ele aberto ou privado � importante ter um arquivo chamado "LICENSE". Dentro desse arquivo colocamos o texto referente � qual licensa est� agindo sobre o conte�do do seu projeto . Caso seu projeto esteja em um reposit�rio de c�digo aberto como a vers�o gratu�ta do GitHub e n�o haja nenhum arquivo LICENSE isso quer dizer que automaticamente voc� est� aplicando os termos de licensa padr�o de direito de c�pia. Ou seja, ninguem tem direito de usar seu c�digo. Logo, se seu objetivo � deixar o c�digo aberto, ent�o adicione um arquivo LICENSE.txt no primeiro n�vel da pasta do seu projeto e coloque dentro alguma licensa de uso livre, como por exemplo a licensa MIT. 
Bem, ap�s adicionar nosso primeiro arquivo (que nesse caso foi o LICENSE mas poderia ser qualquer outro) podemos dar o primeiro commit. IMPORTANTE, s� depois do commit � que o git ir� gerenciar as mudan�as no seu projeto. Primeiro vamos dizer para o git que estamos adicionando o primeiro arquivo modificado:

> git add LICENSE.txt

Este comando acima � de multiprop�sito ele serve para adicionar novos arquivos � staged area e adicionar arquivos j� existentes que foram modificados � staged area. Tamb�m, quando excluimos algum arquivo precisamos "falar (adicionar)" � staged area que realmente estamos excluindo um arquivo da nossa nova vers�o.

Depois, vamos fazer o commit:

> git commit -m "Texto entre aspas que justifica o commit" 

Esse texto entre aspas � um texto que voc� escreve para que voc� possa identificar qual foi a mudan�a que vc fez, fica mais f�cil depois voltar a alguma vers�o importante do projeto atrav�s de commits de f�cil identifica��o.


-------------> CHECANDO O ESTADO DOS ARQUIVOS VERSIONADOS

Podemos ver o estado em que o git est� atrav�s do comando

> git status

Este comando mostra se algum arquivo foi modificado e n�o est� sendo monitorado, ou, se todos os arquivos do projeto est�o monitorados. Se a cor do arquivo estiver vermelha quer dizer que n�o est� monitorado. Se aparecer em verde quer dizer que ele foi adicionado pelo comando > git add arquivo < e podemos fazer o commit para atualizar a vers�o do projeto. Se nenhum arquivo aparecer quer dizer que est� tudo atualizado. O comando tamb�m mostra em qual ramo do projeto vc est� trabalhando, se � um ramo paralelo ou se est� trabalhando no ramo principal do projeto.

Um informa��o importante sobre o comando > git add < : Se voc� faz uma altera��o e adiciona o arquivo para a staged area e n�o executa o commit e depois altera esse arquivo e salva e faz o commit a vers�o do arquivo que ir� ser adicionada ser� a com o conte�do de quando voc� executou o comando git add.

Existe um comando que faz ao mesmo tempo a adi��o dos arquivos modificados e realiza o commit que � o comando:

> git commit -a

Ou seja, ele vai mandar os arquivos alterados para a staged area, solicitar que voc� digite um texto para o commit e depois de finalizar o texto e apertar enter ele vai realizar ter atualizado a vers�o do seu projeto.

H� um comando alternativo ao > git status < que � o > git status -s < Esse comando permite receber um informa��es sobre o reposit�rio com informa��es mais resumidas. Os resultados em que os arquivos podem estar s�o:
> M  arquivo --> Refere-se a um arquivo modificado
> A  arquivo --> Adicionado para a staging area
> ?? arquivo --> novo arquivo que n�o est� sendo monitorado
> MM arquivo --> Arquivo foi modificado, adicionado a stage area e depois modificado de novo.

Existem duas colunas onde esses valores podem aparecer como ilustrado abaixo:
> LR arquivo

O L significa Left Hand e R right hand... O valor aparecendo do lado esquerdo indica o status do arquivo referente � staging area e do lado direito referente � working tree. Exemplo:
>  M arquivo --> veja que h� dois espa�os em branco ali na lateral isso quer dizer que o arquivo foi alterado na working tree mas n�o foi adicionado � staging area.
> M  arquivo --> nesse caso o arquivo foi modificado na staging area, ou seja, est� adicionado para o commit. Preste sempre aten��o � dist�ncia entre o codigo do status e o nome do arquivo, isso indica em qual lado da coluna est� o codigo do status. Ou simplesmente uso o > git status para obter um status mais detalhado.

-------------> FAZENDO O GIT IGNORAR ARQUIVOS DO PROJETO

Talvez em alguma situa��o a gente queira ignorar algum arquivo quando usamos o git status (ou seja, n�o adicionaremos esse arquivo ao nosso reposit�rio). Ent�o para isso a gente pode criar um arquivo no nosso projeto, chamado > .gitignore <. Dentro desse arquivo vamos colocar o nome e a  extens�o do arquivo � ser ignorado ou *.extens�oindesejada para ignorar todos os arquivos que terminam com aquela extens�o... bem podemos usar outras capacidades do bash ou shell para identificar estes arquivos, mas n�o iremos falar disso aqui. Caso tamb�m n�o queiramos que o pr�prio arquivo .gitignore seja adicionado no nosso reposit�rio podemos recursivamente declarar o proprio .gitignore dentro do arquivo .gitignore. Bem, no linux � mais f�cil criar esse arquivo, mas no windows isso pode ser um pouco mais dificil, vamos ver oque podemos fazer:

1� Podemos criar um arquivo .txt qualquer dentro da nossa pasta principal do reposit�rio e escrever l� quais arquivos queremos que sejam ignorados. Depois disso, abrimos o terminal dentro desta pasta e usamos o comando para renomear o arquivo qualquer.txt, da seguinte forma

> ren qualquer.txt .gitignore

pronto nosso arquivo foi renomeado.

2� Podemos abrir o terminal dentro da pasta e usar o comando de escrita de texto dentro de um arquivo, aqui � importante saber que se o arquivo destino que a gente especificou no comando n�o existir ele ser� criado automaticamente. Ou seja, caso ela exista ele so receber� o texto na sua ultima linha n�o escrita e se ele n�o existir ele ser� criado com o texto que a gente escreveu. Ent�o o comando explicado � o seguinte:

> echo "texto" > .gitignore

pronto nosso arquivo .gitignore foi criado com a palavra --> texto <-- dentro dele... perceba que essa palavra texto pode ser simplesmente a regra de exce��o ou ignorar para o git. Alguns exemplos a seguir:
 
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
UTF-8. Quando usamos o PowerShell o arquivo vem pelo padr�o do profile de codifica��o do windows que pode ser "UNICODE" para isso quando gerarmos o arquivo podemos no formato correto podemos usar o terminal assim: 

>Set-Content -encoding utf8 <nome do arquivo>

Ap�s isso digitamos o conte�do que queremos e apertamos enter duas vezes... Bem, depois podemos abrir o arquivo em um editor de texto s� alterar o conte�do ou adicionar novas exce��es e salvar normalmente. Lembre--se de quando o ignore n�o estiver funcionando podem ser duas coisas::
1� O arquivo foi salvo com um encoding diferente de ANSI ou UTF8
2� O arquivo que adicionamos a exce��o foi commitado antes de adicionarmos no .gitignore

-------------> MOVENDO E RENOMEANDO ARQUIVOS

Caso tenhamos adicionado algum arquivo por engano e queremos removelo antes de dar commit
podemos usar o seguinte comando:

> git rm --chached <nome do arquivo>

Um comando mais poderoso que pode ser utilizado para mostrar oque foi mudado dentro de um arquivo e que esteja na �rea de transfer�ncia � o:

> git diff --staged

Lembre-se que ele compara os seus arquivos na staged area e o que est� no seu ultimo commit

Caso voc� mande um arquivo para a staged area e antes de dar o commit voc� troque alguma informa��o no seu working directory podemos comparar o conteudo entre estes arquivos atrav�s do comando:

> git diff

Para renomear um arquivo, podemos usar o seguinte comando:

> git mv [file_from] [file_to]

Veja que este � comando � um pouco estranho visto que na realidade voc� est� movendo um conte�do. Voc� pode mov�-lo pelo git para dentro de uma pasta qualquer normalmente.

Pode tamb�m usar o comando natural do shell que � o > ren < para renomear uma pasta.

-------------> VISUALIZANDO O HIST�RICO DE COMMITS

Para podermos ver o hist�rico de commit podemos usar o comando

> git log 

Ele ir� mostar o hist�rico de commit com data e hora e quem fez o commit em ordem cronol�gica inversa: do mais recente para o mais antigo. Para sair desse modo de apresenta��o do log podemos apertar as teclas "shift + z" duas vezes. Para uma log mais detalhado do que foi feito, quais as diferen�as nos arquivos em cada commit usamos o comando:

> git log -p

Bem, esse comando vai mostrar todas as diferentes de todos os arquivos entre um commit e outro... para algo mais enxuto e espec�fico caso queira saber de um arquivo em espec�fico podemos usar o comando:

> git log -p [arquivo_desejado]

Ainda, caso queiramos saber somente sobre uma quantidade limitada de commits, como por exemplo os �ltimos 3 commits podemos usar o seguinte comando:

> git log -p -x //coment�rio: onde "x" � um valor num�rico que indica a quantidade de �ltimos commits que vc deseja visualizar.

Para uma visualiza��o do log ainda mais enxuta, podemos usar o comando:

> git log --stat

Caso voc� esteja trabalhando em um projeto onde haja v�rios commits e voc� esteja procurando por algum em espec�fico ou queira visualizar tudo que foi commitado de uma forma mais r�pida e simplificada podemos usar o comando:

> git log --pretty=[argument] //coment�rio: bem h� v�rios tipos de modelos de visualiza��o, cada modelo tem seu valor para ser colocado onde est� escrito "argument"
Algumas op��es s�o: oneline, short, full e fuller. O "oneline" vai imprimir cada commit em uma �nica linha.

Bem, ainda h� uma op��o personalizada de como pegar seu commit. Essa vers�o personalizada � voc� quem faz, no link a seguir � poss�vel ver uma boa explica��o sobre essa op��o: https://git-scm.com/docs/pretty-formats

Se pensarmos um pouco podemos perceber que gerenciar um projeto � algo bastante complicado, e projetos complexos e longos ir�o necessitar de muitos commits. Ent�o o git log possui um comando muito �til para podermos filtrar qual o retorno de log que queremos, veja podemos filtar por limite de data como por exemplo tudo que foi commitado nos �ltimos 5 dias ou 2 semanas, horas, minutos e segundos. Tamb�m, podemos filtrar por autor... vejamos alguns exemplos � seguir:

> git log --since=1.weeks //coment�rio: vamos receber um log de tudo que foi commitado na �ltima semana. Veja que � um log extenso. Podemos usar o pretty para enxugar esse log.

> git log --since=1.weeks --pretty=oneline //coment�rio: veja que agora � algo muito mais enxuto

> git log --since=1.days --pretty=oneline //coment�rio: log do �ltimo 1 dia.

> git log --since="2019-12-22" --pretty=oneline //coment�rio: veja que agora especificamos uma data para pegar os commites at� este dia em espec�fico.

Para poder filtar por author � importante salientar que a express�o exige que o author seja especifica log ap�s "git log" ou pretty depois podemos usar os outros crit�rios de filtros, por exemplo:

> git log --pretty=oneline --author='Matheus Dias' --since=2.days //coment�rio: aqui vamos ver os commits do author "Matheus Dias" desde h� 2 dias atr�s.

Como podemos ver existem muitas op��es para podermos procurar um commit em espec�fico, pode ser muito �til tanto para restaurar o projeto para um ponto em espec�fico. As op��es s�o tantas que � poss�vel estabelecer um limite superior e inferior de datas para saber oque foi commitado nestes dias.

-------------> DESFAZENDO COISAS NO GIT

Caso voc� tenha feito um commit no qual adicionou somente uma parte do conte�do que queria ter adicionado naquele commit, voc� pode usar o comando a seguir para adicionar o conte�do que faltou ao seu ultimo commit. Antes de usar o comando precisamos adicionar os arquivos ausentes:

> git add [arquivo]

Ent�o assim, usamos o --amend:

> git commit --amend














 