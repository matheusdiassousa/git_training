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

Ou seja, ele vai mandar os arquivos alterados para a staged area, solicitar que voc� digite um texto para o commit e depois de finalizar o texto e apertar enter ele vai realizar ter atualizado a vers�o do seu projeto. DETALHE ESSE COMANDO S� SERVE PARA ARQUIVOS J� TRACKEADOS PELO GIT. 

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

Bem, neste momento o git vai abrir o seu gerenciador de texto configurado e ap�s isso, ele vai espera que vc altere a mensagem do commit passado. Caso voc� s� feche o arquivo, ele vai dar continuidade e adicionar seu arquivo faltante ao �ltimo commit sem alterar a mensagem.

IMPORTANTE - Para que o git consiga abrir um programa ele precisa de permiss�o de usu�rio, ent�o, voc� deve usar um PowerShell aberto como administrador... assim ao usar o GIT ele ter� permiss�es de adm para executar a��es que exijam graus de permiss�o maiores.

Agora vamos ver como retirar um arquivo em espec�fico da staged area. Isso pode ser feito com o seguinte comando:

> git reset [arquivo]

Com esse comando, podemos tirar um arquivo que foi add pelo comando > git add [arquivo] <... Bem simples n�?!

Podemos desfazer uma modifica��o local em um arquivo substituindo o arquivo alterado pela sua ultima vers�o de commit... vamos entender melhor:
Vamos supor que vc tenha um arquivo de texto com a frase "antes do restore" dentro deste arquivo. Supodondo que este seja um conte�do importante, em algum momento voc� faz alguma altera��o neste arquivo... trocou a frase para "antes do restore 1000", mas, na realidade voc� fez besteira e j� salvou este arquivo. Ent�o, voc� quer voltar para o antigo conte�do do arquivo... podemos ent�o fazer o git substituir este arquivo atual para sua vers�o do ultimo commit com o seguinte comando:

> git checkout [arquivo]

Entenda que tudo que foi commitado pode ser retornado. Voc� pode at� mandar esta vers�o do projeto que est� com este arquivo alterado para outro ramo (ou seja, o mesmo projeto em uma realidade paralela) e assim continuar no seu projeto principal com seu arquivo na fase inicial. Bem, podemos ver que o git � muito poderoso e que suas funcionalidades podem n�o fazer tanto sentido agora... mas, na realidade voc� ver� que s�o muito �teis em projetos complexos no qual voc� precisa testar e manter diferentes vers�es do mesmo projeto. Um circuito com valores e resultados diferentes: por exemplo, para quando voc� juntar com circuitos posteriores voc� possa escolher qual deles teve o melhor desempenho.

--------> TRABALHANDO COM PROJETOS REMOTOS

Bem, primeiro oque � um projeto remoto? � um projeto que est� hospedado em outro computador... como por exemplo um servidor que � acessado pela internet.
Voc� pode trabalhar em v�rios GIT ao mesmo tempo sem conflitar dados entre eles. (Se voc� n�o fizer uma besteira bem doida, tudo � poss�vel na terra.)

Um reposit�rio GIT que n�o � seu pode ser somente de Leitura onde voc� s� consegue puxar dados, como pode tamb�m ser de Leitura/Escrita no qual voc� pode enviar e receber informa��es.

**Vendo seus reposit�rios remotos

> git remote

Este comando acima vai listar os reposit�rios remotos no qual voc� configurou para ter acesso... com por exemplo deu um clone. Se n�o mostrar nada � pq voc� n�o est� trabalhando com nenhum.

Adicionar o comando "-v" mostra o endere�o url do reposit�rio:

> git remote -v

Bem agora vamos aprender como adicionar um desses reposit�rios... Ent�o, primeiro deve lembrar que a gente deve estar dentro de uma pasta (via terminal) no qual queremos hospedar localmente os arquivos deste projeto. Ent�o usamos o comando:

> git remote add <pequeno_nome_para_identificar_o_repositorio> <url_do_repositorio>

Esse pequeno nome que usamos para identificar o repo, pode ser usado no terminal no lugar de toda a URL do projeto. De agora em diante vamos chamar o nome que demos para o repositorio de de <repo_id>

Ap�s fazer essa configura��o onde voc� disse pro GIT que agora ir� trabalhar nesse reposit�rio... voc� precisa baixar para sua pasta local todos os arquivos que vc n�o tem ainda... Ent�o, para isso, usamos o comando:

> git fetch <repo_id>

Esse comando tr�s todas as informa��es do projeto, inclusive de ramos do projeto. A partir daqui voc� pode trabalhar em um ramo do projeto ou no ramo principal.

O comando >fetch< vai trazer arquivos que voc� ainda n�o tem... mesmo que sejam todos.

Se voc� clona algum projeto, voc� ter� esse reposit�rio adicionado para voc� localmente... ent�o se voc� usar o comando:

> git fetch origin

Ele vai buscar novos projetos ou arquivos a partir da vez que voc� deu o seu > git clone < perceba que origin na realidade � um id para reposit�rio clonado... ent�o quando usamos origin dentro da pasta de um projeto clonado ele na realidade est� indo atr�s do endere�o referente ao reposit�rio.
� importante salientar que o comando >fecth< somente faz o download dos arquivos para sua pasta local... voc� ainda precisa fazer manualmente a adi��o destes arquivos no seu projeto ou seja... dar um "merge" com seus arquivos versionados.

Podemos usar um comando para buscar arquivos no ramo de reposit�rio que estamos trabalhando e ainda assim fazer a fus�o desses arquivos com seus arquivos alterados localmente. Para isso podemos usar o comando:

> git pull

Ou seja, ele ir� buscar os arquivos no reposit�rio clonado e fundir com os seus arquivos... ent�o tudo � feito de uma �nica vez.

___________Enviando arquivos para um server remoto

Bem, a certo ponto do seu projeto voc� deseja disponibiliza-lo em algum reposit�rio online essa a��o chamado de "push"... se para baixar os arquivos chamamos de "pull", enviar ou "empurrar" os arquivos para a n�vem... chamamos de "push". Para isso usamos o seguinte comando, preste aten��o nos argumentos:

> git push [remote] [branch]

Bem, em remote � o endere�o que tem algum id... normalmente � o "origin" e o branch normalmente estamos trabalhando no "master"... Ent�o o comando fica assim:

> git push origin master

Ent�o estamos dizendo para o git enviar os arquivos commitados para o endere�o origem do projeto e adicionameros ou atualizaremos os arquivos no ramo "master" ou principal do reposit�rio online.

Este comando s� ir� funcionar se voc� tiver permiss�o de escrita no resposit�rio que vc est� tentando dar push... Outra coisa importante � que voc� s� poder� dar push se seu reposit�rio local tiver as ultimas atualiza��es do reposit�rio online... perceba que isso � essencial pq voc� poderia estar sobrescrevendo a ultima atualiza��o do seu projeto com uma vers�o ultrapassada. Isso pode acontecer quando se trata de um projeto com v�rias pessoas trabalhando nele. Ent�o, antes de dar o push � importante dar um pull... para ver se algo mudou e atualizar o seu projeto.

Para ver informa��es sobre seu reposit�rio online, como quais s�os os ramos, em qual ramo voc� est� trabalhando e quando voc� der pull ou push quais ser�o os ramos que ser�o baixados e atualizados. O comando �:

> git remote show origin

_________________ Renomeando e Removendo Remotes

Para mudar o id de um remote, podemos usar o comando:

> git remote rename [id_antigo] [id_novo]

Para verificar a mudan�a, podemos usar:

> git remote

Para remover algum reposit�rio remoto, por alguma raz�o como o reposit�rio n�o ser� mais disponibilizado naquele server, n�o estar� mais dispon�vel para colabora��o de algu�m... e por a� vai, podemos usar o comando:

> git remote rm [id]

Depois de usar esse comando, todas as configura��es para aquele reposit�rio remoto ser�o exclu�dos... novamente podemos checar isso pelo comando:

> git remote

Lembrando que o git remote mostra quais reposit�rios vc est� trabalhando dentro do seu projeto...

___________Tagging

Tags s�o como etiquetas que voc� usa para marcar o seu projeto... Bem, normalmente � usado para marcar a vers�o do seu projeto, vamos supor que vc lan�ou a primeira vers�o... ap�s o ultimo commit daquela vers�o voc� pode adicionar uma tag. Assim, com essa tag voc� facilmente sabe identificar um ponto importante do seu projeto.

Primeiro precisamos saber como listar tags... podemos usar o comando:

> git tag //coment�rio: podemos adicionar no final o argumento "--list" ou "-l" mas � opcional.

Esse comando vai mostrar as tags em ordem alfab�tica. Podemos tamb�m listar as tags a partir de uma espec�fica como:

> git tag -l "nome que identifica uma tag"

Ent�o essa combina��o de comandos vai mostrar tags que correspondem ao texto entre aspas.

__________Criando as tags

Existem dois tipos de tags no git s�o elas:

--> lightweight : essa tag � a mais simples, ela n�o muda e serve somente para marcar um commit.

--> annotated : essa tag � a mais completa e guarda todos os objetos referentes ao seu repositorio naquela tag... como, author, data, e salva os arquivos para serem comparados. O git recomenda taggear com esse tipo de tag. Mas, caso voc� n�o queira guardar tantas informa��es naquele momento, seja por que ainda n�o � importante ou seja por outro motivo... use a tag simples. Mas veja que a tag leve n�o guarda nem author nem hora... mas sabemos que ela aponta pra um commit que tem informa��es como author, hora e arquivos salvos para compara��o. O problema � que essas infos s�o do commit n�o de quem fez a tag.

Criando a tag annotated... � simples podemos usar o comando:

> git tag -a [nome da tag] -m "texto que fala algo sobre a tag" //coment�rio: se vc n�o colocar o argumento -m o git ir� abrir o seu editor de texto configurado para que vc escreva algo l�... ou simplesmente salve sem escrever nada.

ent�o j� sabemos que podemos listar as tags existentes com o comando:

> git tag -l

E podemos ver informa��es sobre nossa tag com o comando:

> git show [nome_da_tag]

Que ir� mostrar informa��es interessantes sobre nossa tag...

Ainda podemos usar outro argumento para resumir as infos sobre a tag, como:

> git show [nome_da_tag] -s //coment�rio: como j� usamos no "git status -s"

	

Para criar uma lightweight tag precisamos s� usar o comando de tagging sem adi��o de argumentos extras... como:

> git tag [nome da tag]

Lembrando que este tipo de tag somente adiciona uma marca��o para o commit, n�o diz quem fez a tag, que horas...etc e tal. O comando > git show < para essa tag s� vai mostrar o nome da tag e as infos do commit.

__________- Adicionando tags em commits passados.
Podemos dar um > git log --pretty=oneline < ver todos os commits e pegar o SHA-1 do commit desejado e usar o seguinte comando:

> git tag -a [nome da tag] [SHA-1 do commit]

Mas qual � o SHA-1... lembramos primeiro que quando commitamos o git gera um HASH para identificar o commit e o conte�do do projeto. O SHA-1 � essa sequ�ncia de numeros e letras que aparecem do lado esquerdo do texto do commit. Precisamos pegar no m�nimo os 7 primeiros caracteres do Hash. Esse comando acima vai exigir a abertura do editor de texto para comentar a tag... para evitar essa novela toda, podemos adicionar o argumento de adi��o de mensagem da seguinte forma:

> git tag -a [nome da tag] [SHA-1 do commit] -m "texto que a gente quer colocar"

__________________ Compartilhando Tags

Por padr�o quando realizamos um push o git n�o envia as tags que criamos no nosso versionamento local. Para isso precisamos subir a tag manualmente, ou ainda podemos subir todas as tags existentes que ainda n�o est�o no reposit�rio remoto. Podemos fazer essas duas coisas com os comandos listados respectivamente abaixo:

> git push origin [nome da tag]

> git push origin --tags

Talvez seja importante dizer que o git n�o distingue somente um tipo de tag para fazer o push. Ele ir� enviar os dois tipos. Ap�s usar estes comandos as tag estar�o aplicadas tamb�m ao reposit�rio remoto.

____________ Deletando Tags

Para deletar uma Tag localmente podemos usar o comando:

> git tag -d (ou --delete) [nome da tag]

E para fazer isso no reposit�rio online... tamb�m precisamos deletar l�

> git push origin --delete [nome da tag]

__________ Checking Out Tags
Caso queira ver a vers�o dos arquivos que a tag est� apontando podemos usar o comando:

> git checkout [nome da tag]

A quest�o aqui �, que ap�s este comando voc� vai mudar o sua vers�o de trabalho para o commit que vc escolheu... ent�o tudo vai mudar inclusive o log que voc� tinha. Nesse caso � como voltar no tempo. S� que voc� est� em um modo "des-anexado" oque quer dizer que � como vc voltar para o commit que vc selecionou no checkout e a partir da� vc pode fazer mudan�as e ir para um outro branch sem afetar o seu ramo anterior... 

----- at� aqui eu ainda n�o sei como voltar para o reposit�rio anterior.... acho que deu bosta, no sentido de ter perdido todos os meus logs...

____________ Criando apelidos para os comandos para evitar digitar todo o texto sempre
Podemos fazer apelidos para os comandos com os seguintes comandos:

> git config --global alias.[nome do apelido] 'comando que vai ser apelidado'

Por exemplo vamos fazer um apelido para o comando que mostra todos os commits de forma resumida... se para ver os commits reduzidos usamos o comando > git log --pretty=oneline < agora vamos usar
> git logres <... ent�o vamos criar esse apelido usando o comando acima citado acima:

> git config --global alias.logres 'log --pretty=oneline'

_____________ Git Branching

Aqui vamos ver como funciona a ramifica��o de projetos. O manual do git diz que esse recurso � um dos seus melhores recursos e oque realmente justifica utilizar o git ao inv�s de outro VCSs...

Para entender as ramifica��es precisamos lembrar como funciona os commits do git... quando a gente d� um commit o que git faz � criar um objeto que aponta para uma "imagem" exata do projeto antes do commit. O commit � uma esp�cia de "porta" que d� acesso exatamente � esta imagem tirada do projeto.

Ent�o cada commit � uma imagem de todo o projeto, n�o somente do arquivo mudado... mas de tudo que foi adicionado para a staged area e commitado.

Este objeto (commit) mostra quem foi que o executou, endere�o de email do author, hora e etc. Caso o commit venha a partir de uma "fus�o" de outros commits ent�o este ser� um commit Pai que mostra a uni�o de outros commits executados por outras pessoas ou vers�es de arquivos.

Quando adicionamos os arquivos � staged area o git vai criar um SHA-1 para cada arquivo que � uma sequ�ncia num�rica resultado do conte�do do arquivo... ent�o um arquivo no mesmo endere�o com mesmo nome e mesmo conte�do tem que ter o mesmo SHA-1 e assim o git consegue comparar um arquivo ele mesmo em outro momento para ver se houve modifica��es ou n�o. Bem, quando damos o commit oque git faz � guardar no reposit�rio o SHA-1 referente � cada arquivo guardado... ele chama cada SHA-1 de cada arquivo de "BLOBS". Quando realizamos o commit o reposit�rio git guarda a seguinte quantidade de arquivos:

-> X Quantidade de blobs (1 para cada arquivo adicionado)
-> 1 tree (uma arvore que lista o conte�do do diret�rio e especifica qual arquivo equivale a cada blob)
-> 1 commit (que � um objeto que aponta para arvore)

Ent�o com esses arquivos o GIT consegue remontar todo conte�do que foi salvo naquele commit.

O primeiro commit ele s� tem os arquivos citados acima... mas o segundo commit e assim sucessivamente vai apontar para o commit anterior e criar a mesma l�gica de arquivos citadas anteriormente... por exemplo:

primeiro commit de todos:


-> X Quantidade de blobs (1 para cada arquivo adicionado)
-> 1 tree (uma arvore que lista o conte�do do diret�rio e especifica qual arquivo equivale a cada blob)
-> 1 commit (que � um objeto que aponta para arvore)


Segundo commit:


-> X Quantidade de blobs (1 para cada arquivo adicionado)
-> 1 tree (uma arvore que lista o conte�do do diret�rio e especifica qual arquivo equivale a cada blob)
-> 1 commit (que � um objeto que aponta para arvore)
-> 1 objeto que aponta para o commit anterior (nesse caso o primeiro commit de todos)

Ent�o o git na realidade sempre d� um caminho para a vers�o anterior, fazendo com que tenhamos pontos tempor�is para acessar o nosso projeto.

O ramo que estamos no git � chamado de "master" � s� um nome para dizer onde estamos mesmo... mas � um ramo como qualquer outro no seu reposit�rio...

_______vamos agora criar um ramo

Para criar um ramo (outra linha temporal do projeto) podemos usar o comando:

> git branch [nome do ramo]

Esse comando s� cria um novo ramo, n�o te leva para trabalhar nesse novo ramo criado

Para saber em qual ramo estamos, quando usamos o > git log < ele mostra em qual ramos estamos ao utilizar a palavra HEAD:

HEAD -> nome do ramo

Para ver o ramo que estamos como dito anteriormente podemos usar:

> git log --oneline --decorate

Quando os ramos est�o no mesmo ponto de commits, quando vemos o log eles est�o apontando para o mesmo commit. Mas, se fizermos alguma mudan�a e commitamos somente o ramo que estamos naquele momento apontar� para aquele commit. � importante saber que quando nos movemos de branch na realidade estamos indo para o commit que aquele ramo teve por �ltimo, ou seja, estamos tamb�m andando na linha do tempo de mudan�as nos nossos arquivos.

Bem, caso usemos o comando > git log --oneline --decorate < n�s s� veremos informa��es do ramo conectado no commit que estamos no presente momento... Por exemplo se a partir de um commit no ramo "master" damos um branch para "ramo2"... e damos um checkout para "ramo2" ent�o com o log veremos os ramos que antecessores � ele mesmo... mas se autualizamos o ramo2 com um commit que s� ele tem e depois damos um checkout para o ramo "master" e usamos o log, n�o veremos o "ramo2" porque ele � uma linha do tempo que n�o existe para o "master" ele est� no futuro e ainda n�o aconteceu. Ent�o, caso queiramos ver todos os ramos e commits na linha do tempo do nosso reposit�rio... Ou seja, n�o veremos a partir da vis�o do ramo que estamos mas sim de todo o projeto podemos usar o seguinte comando:

> git log --oneline --decorate --graph --all

Com esse comando veremos inclusive um ramo des-conexo criado a partir de uma tag annotated.
Esse sim � um comando bem legal para a gente n�o ficar perdido.

No final um ramo � somente um arquivo SHA-1 que aponta para uma foto do seu projeto... isso ent�o faz com que criar ramos seja muito leve no quesito de ocupar espa�o e r�pido no quesito de processar o comando. Por isso o modo com o GIT faz um ramo � chamado de "killer feature" pq outros gerenciadores n�o fazem isso assim. Eles normalmente duplicam seus arquivos para outro diret�rio ou seja, voc� ocupa espa�o duas vezes com coisas iguais que n�o divergem de si quando comparamos um ramo com outro.

Vimos que o processo de criar um ramo e mudar para ele exige dois comandos... Mas, existe um comando que permite ao mesmo tempo criar e mudar para esse ramo, que � o seguinte:

> git checkout -b "nome do ramo"

______________ Criando ramos e depois os fundindo. (Branching and Merging)

Primeiro vamos entender em qual situa��o um Merging pode ser usado... Imagine que estamos trabalhando em um e estamos no ramo "master", o projeto trata-se de um aplicativo dispon�vel para usu�rios comuns, ent�o voc� como dev recebe um alerta do seu time de que h� um problema para efetuar a troca de conta no aplicativo. Bem, voc� precisa realizar o concerto deste bug, mas n�o ir� fazer isso no seu ramo master, pq isso pode danificar todo o seu projeto. Ent�o oque podemos fazer? Bem podemos criar um ramo a partir do ramo master, mudar para esse novo ramo que chamaremos de "bugfix" e vamos realizar neste ramo secund�rio o concerto do bug e testar se est� tudo ok nele. Depois que tivermos certeza que concertamemos esse problema, podemos ent�o fundir esse ramo "bugfix" com o ramo "master" que � o ramo principal de desenvolvimento do nosso projeto. Bem, aqui � importante saber que precisamos ter os dois ramos atualizados, ou seja, n�o pode ter nada para ser commitado seja fora ou dentro da staging area... pq se tiver em uma dessas condi��es o git n�o vai deixar realizar o branch.

Para fazer o merging n�s precisamos ir para o ramo que queremos "puxar" os arquivos do outro "ramo"... para entender melhor: n�s temos 2 ramos, um "master" e um "bugfix" que foi criado para solucionar e testar o bug... um vez solucionado queremos mandar a vers�o dos arquivos do "bugfix" para o ramo "master". Ent�o, damos um checkout para o ramo master e usamos o comando � seguir para fazer o merging:

>git merge bugfix //coment�rio: veja que depois de "merge" vem o nome do ramo que estamos puxando e fundindo os arquivos.

H� um tipo de merge chamado "fast-foward" que trata-se de quando realizamos um merge entre dois commits que est�o conectados na linha do tempo. Como assim? Se pensarmos que master � um commit no tempo 2 e bugfix � um ramo com commit na linha do tempo 3... ent�o na realidade o commit de bugfix est� logo na frente do master. Ent�o um merge fast-foward � s� o git mudando o apontador do ramo master para o mesmo commit do bugfix... em linhas grossas: os ramos master e bugfix apontam para o mesmo commit neste momento. Isso acontece somente quando um commit consegue alcan�ar o outro por estas vias. Simples n�o �?! Bem, s� tenha em mente que podemos dar um merge entre commits separados por longas linhas temporais no git.

Bem, como agora voc� j� tem o bug resolvido e n�o precisa mais do branch bugfix... podemos apagar esse branch com o comando:

> git branch -d bugfix //coment�rio: de novo, bugfix pode ser o nome de qualquer reposit�rio que vc queira apagar.

Vamos agora entender um pouco sobre o merge de commits que est�o distantes na linha temporal. Quando temos dois ramos que est�o distantes um do outro por alguns commits, o git n�o pode fazer um fast foward merge, pq os commits atuais de cada ramo possuem arquivos diferentes e n�o tem um commit ancestral direto entre eles dois. Na realidade eles tem ancestrais que tem ancestrais em comum. � como  primos que possuem os av�s como ancestrais diretos, onde seu pai � seu ancestral direto e seu tio � seu ancestral indireto. Ent�o oque o git precisa fazer � ir at� esse commit ancestral direto e reunir as informa��es e altera��es destes arquivos para que assim possa criar um novo commit um ancestral filho direto destes dois commits que est�o sendo fundidos. Assim como dito anteriormente ir� existir agora um novo commit que � a reuni�o//fus�o de informa��es dos commits anteriores.

Bem, como agora vc tem as infos desse seu branch secund�rio que foi puxado as informa��es... podemos exclui-lo como j� sabemos.

O merging nem sempre ir� ser executado t�o pacificamente assim, as vezes... ele d� alguns conflitos de informa��es e reclama. Vamos supor que voc� mudou o mesmo arquivo de forma diferente nos dois ramos... ou seja, escreveu algo l� no arquivo1 no ramo master e escreveu outra coisa no mesmo do arquivo no ramo bugfix... por exemplo... ent�o o git n�o ir� realizar o merge e vai te solicitar para solucionar o problema do conflito.

Para ver em que arquivo o conflito ocorre, podemos rodar um > git status <
Ent�o se a gnt abrir o arquivo conflituoso, l� teremos texto marcando o conflito entre os arquivos. Veja para imagens isso � mais complexo mesmo que a imagem seja um c�digo ainda assim ser� dif�cil decifrar isso. Ent�o resolver este conflito pode ser um pouco mais complicado em casos especiais de arquivos que n�o vamos abordar aqui.

Depois de resolver os conflitos precisamos somente, dar um git add nos arquivos alterados. Enviar os arquivos para a staging area faz o git entender que os arquivos est�o marcados como resolvido e para terminar o merge n�s temos que dar um commit. Vamos olhar agora nosso tree e ver com qual apar�ncia ela est� agora:

Vemos ent�o que h� agora um ancestral filho comum aos dois ramos... E se quisermos podemos excluir o ramo secund�rio ao master. Fica � seu crit�rio!

_______________BRANCH MANAGEMENT

Para ver os ramos que existem de uma forma mais simples, podemos usar o comando:

> git branch

E caso queiramos mais detalhes como o ultimo commit de cada branch podemos usar:

> git branch -v

Podemos ver quais ramos foram fundidos com o ramo no qual estamos atualmente com o commando:

> git branch --merged

E para ramos que n�o demos merge, podemos usar

> git branch --no-merged

Ramos que j� demos merged normalmente s�o seguros de serem excluidos... No entanto se tertarmos deletar um ramo que ainda n�o demos merge, o git vai nos dizer que n�o pode fazer isso pq esse conte�do n�o est� seguro para ser deletado, visto que n�o foi adicionado ao seu ramo principal.
Bem, ent�o para isso podemos fazer duas coisas:

1 - Realizar o merge
2 - Se soubermos que � seguro, podemos for�ar a exclus�o com o seguinte comando:

> git branch -D [nome_do_ramo] //coment�rio: veja que quando usamos > git branch -d [nome_do_ramo] <
o git n�o deixa a gente excluir, ent�o usar o "-D" � uma forma de dizer � ferramenta que independente do que ela acha ela executar nosso comando.

Ainda para vermos sobre ramos que n�o foram fundidos, podemos perguntar ao git quais arquivos dentro deste ramo n�o foram fundidos... ent�o, para isso podemos usar o seguinte comando:

> git branch --no-merged [nome_do_ramo]

________ Talvez seja interessante adicionar um conte�do que fale sobre modos de como projetos s�o gerenciados no git, no sentido de criar ramos para diferentes objetivos, como testar uma ideia... e por a� vai.

________ REMOTE BRANCHES

Toda vez que nos conectamos � internet o git baixa informa��es para seu reposit�rio local sobre estados dos seus ramos no reposit�rio remoto, de forma que ele sempre esteja atualizado sobre quais os estados dos ramos online. De modo que voc� n�o sobre-escreva uma vers�o do projeto que foi atualizada por algu�m que colabora com seu projeto.

Caso queira compartilhar um ramo para o servidor remoto, mas n�o queira compartilhar todos os ramos, por algum motivo... voc� pode usar o comando:

> git push [remote_name] [branch_name]

Bem, quando adicionamos um ramo para um reposit�rio online que somente n�s t�nhamos no come�o ent�o quando um colaborador usar o git pull ele s� ter� a indica��o do ramo ele ainda precisa dar merge desse ramo com o seu workflow local. Isso pode ser feito com o comando:

> git merge origin/[new_branchname]

Caso voc� d� clone em um projeto e queira trabalhar somente em um ramo espec�fico, voc� pode usar o comando:
> git checkout -b [branchname] origin/[branchname]
ou
> git checkout --track origin/[branchname]

Se voc� quiser que esse ramo remoto seja chamado por um apelido diferente do ramo online voc� pode usar o comando:

> git checkout -b [nomelocal] origin/[branchname]

Se voc� criou um ramo local e depois quer que essa ramo "monitore" os arquivos de um ramo remoto, voc� pode usar o comando:

> git branch -u origin/[branchname]

Ou seja, agora o ramo que vc est� como "head" vai monitorar os arquivos est�o no ramo "branchname" no endere�o "origin".

Para ver quais as configura��es de "monitoramento remoto" cada ramo est� seguindo, podemos usar o comando:

> git branch -vv

Quando vemos o resultado deste comando podemos ter tr�s mensagens ap�s a informa��o do endere�o remoto e o ramo remoto que o nosso ramo local est� monitorando. As mensagens s�o:

1 - ahead x - ahead quer dizer que o ramo local est� com "x" quantidades de commits na frente do ramo online... ou seja, seria legal atualizar o ramo online executando um push.
2 - behind x - behind quer dizer que o ramo local est� com "x" quantidades de commits atr�s do ramo online... ent�o, seria bom atualizar nosso ramo local executando um pull.
3 - ahead x, behind y - bem aqui a gente j� sabe ent�o, que nosso ramo local est� � frente do ramo online com "x" commits e atr�s com "y" commits. Nesse caso � melhor atualizar nosso ramo local primeiro e depois atualizar o ramo online, para que a gente n�o sobre escreva o trabalho de outra pessoa.

� importante dizer que essa informa��o mostrada pelo comando atr�s nos est� respondendo baseado nas informa��es locais que temos da ultima vez que executamos um " fetch "... ou seja, se passaram alguns minutos ou horas e h� a possibilidade das informa��es remotas terem mudado, ent�o � muito importante dar um fetch antes... como por exemplo da seguinte forma:

> git fetch --all; git branch -vv

Agora assim, temos uma informa��o atualizada. Bem, � bom lembrar que o " fetch " s� buscar informa��es atualizadas para voc�, ele n�o pega os arquivos online e altera seus arquivos locais voc� precisa fazer isso dando um merge... Mas, caso voc� execute um " git pull" ele ir� fazer as duas coisas ao mesmo tempo, no entanto, este comando n�o � t�o explicito como executar uma sequ�ncia " fetch + pull "... Fica ligado nessa parada!

Se voc� quiser deletar um ramo online, por seja qual l� for o motivo, voc� usar o seguinte comando:

> git push origin --delete [branchname]

� bom saber que o git vai apagar o apontador para aquele ramo com seu commit... mas o arquivo ainda vai ficar l� por algum tempo. O tempo de perman�ncia depende do fornecedor de reposit�rios online.


___________GIT REBASING
Esse rebase me parece bastante complicado. Mas, vamos tentar explicar. Basicamente quando a gente usa o merge, oque fazemos � pegar dois branches que em algum momento tem um ancestral comum, ir at� esse ancestral e comparar todas as diferen�as entre arquivos e depois unir estes arquivos em um s� commit. No entanto, as linhas do tempo ainda sobram. Ou seja, ainda � poss�vel acessar os ramos paralelos antes do merge. O rebase � como se esse ramo paralelo que tem seus commits espec�ficos tivessem sido feitos na linha principal do commit master que originou as ramifica��es. Imagine que temos tr�s linhas do tempo de commits, uma principal chamada master, uma lateral chamada segunda, terceira. Ent�o a linha principal continua com seus commits e do mesmo modo as outras linhas. Em algum momento terminamos as atualiza��es no ramo "segunda" e usamos o rebase da segunda dentro da linha "master". Isso quer dizer que os commits da linha segunda, ser�o movidos para uma arquivo tempor�rio e apagados da linha tempo. Ent�o ser�o criados a mesma quantidade de commits que existiam na linha segunda e estes ser�o adicionados na linha master, com o master com arquivos agora do rebase. � como se fosse um merge, mas h� uma re-organiza��o da linha do tempo. Na verdade o rebase parecer ser utilizado para manter a limpeza ou est�tica de commits do projeto, para n�o haver v�rios ramifica��es. Como usamos o rebase?

1- entramos no ramo paralelo que queremos "mover" os commits para o ramo destino

> git checkout [ramo_paralelo]

2- ent�o usamos o comando > rebase < para indicar o destino destes commits

> git rebase [ramo_destino]

Como o seu master est� em um commit agora atrasado em rela��o � sua propria linha do tempo, podemos leva-lo para o commit mais atualizado (que � a uni�o do master com os commits do ramo paralelo que foi apagado) com o seguinte comando:

> git checkout [ramo_rebased] //coment�rio: no nosso caso foi o master

> git merge [ramo_paralelo]

N�o h� diferen�a no quesito "arquivos resultantes" entre o rebase e o merge

Agora h� uma outra possibilidade que � dar rebase de um ramo que � ramifica��o de uma ramifica��o. Ou seja, vamos supor que um terceiro ramo � um sub-ramo da linha principal, ou seja, o ramo principal tem um commit que d� origem a um ramo... este ramo com seu commit inicial d� origem a outro ramo. Assim, esse terceiro ramo tem um ancestral que � ancestral da linha principal. Agora, vamos supor que queiramos mandar esse terceiro ramo para o ramo principal, mesmo que eles n�o tenha uma conex�o t�o direta assim. Deste modo, podemos usar o seguinte comando:

> git rebase --onto [ramo_destino] [ramo_pai_do_terceiro_ramo] [terceiro_ramo]

na realidade o comando assim ser� algo mais ou menos assim > git rebase --onto master segundo terceiro


Para entender melhor, o ramo_pai tem um commit no inicio da sua linha do tempo que d� origem ao terceiro_ramo e o ramo_destino tem um commit que deu origem ao commit inicial da linha do tempo do ramo_pai. Veja que o comando est� dizendo assim: "pegue os commits do terceiro_ramo que s�o diferentes do ramo_pai e mande para a linha do tempo do ramo_destino". Parece uma bagun�a mas d� certo...haha. O resultado disso � o ramo_destino agora ter� no final da sua linha do tempo os commits do terceiro_ramo, como se eles tivessem sido feitos anteriormente nessa linha tempo. N�o esque�a de dar merge entre o commit que est� o ramo_destino e o commit que est� o terceiro_ramo...assim eles estar�o no mesmo commit. Isso quer dizer que se voc� n�o fizer isso... se vc der checkout para o ramo_destino ele estar� atrasado em rela��o sua propria linha do tempo. Quem est� mais atualizado no momento � o terceiro_ramo, mas, lembre-se que isso pode ser confuso em um projeto porque o terceiro_ramo foi criado para adicionar algum recurso paralelo, e o o ramo principal normalmente � o "master". Isso quer dizer que se algum colaborador quiser ter os arquivos na posi��o oficialmente mais atualizada ele vai entar no "master", ent�o caso vc atualize oficialmente o master tem que acompanhar esse commit.

No final, quando o ramo_pai tiver pronto podemos usar o rebase normalmente (sem o --onto) para dentro do ramo_destino (master) e a� vamos dar o merge no final.
Depois para limpar a linha do tempo vamos apagar os ramos que sobraram redundantes apontando para o mesmo commit que o master.

> git branch -d terceiro

> git branch -d segundo

Bem, h� uma regra de outro em rela��o ao rebase! N�o de rebase em commits de reposit�rios que vc colabora no qual h� commits que seus parceiros est�o trabalhando, pois pode causar muita confus�o e redund�ncia de commits com mesmo autor, hora e etc...

Oque � melhor, rebase ou merge?

O rebase muda a linha temporal do projeto, deixa ela linear e mais organizada, mas n�o � fiel � hist�ria de evolu��o do seu projeto.

O merge pode ser mais bagun�ado com v�rios branchs paralelos e uni�es, mas, ele � fiel ao tempo e vers�es do seu projeto.

Fica a crit�rio da equipe de projeto adotar um ou outro. (rebase � complicado de entender)


____________GIT ON THE SERVER
Normalmente projetos s�o feitos em grupos. Neste caso, queremos que as pessoas possam afetar o projeto fazendo pulls e pushs. No entanto, ter um reposit�rio hospedado em um computador que as vezes fica offline pode n�o ser uma ideia legal, pois, voc� pode atualizar um projeto offline e seus colegas trabalharem por cima de um projeto desatualizado. A solu��o para esse problema est� em usar um resposit�rio localizado em um ponto intermedi�rio para todos os usu�rios, neste caso, ter um reposit�rio na n�vem � uma solu��o adequada para este tipo de problema. Ou seja, todos ter�o sempre que realizar um pull antes de um request, deste modo, sempre ter�o a vers�o mais atualizada do projeto minando a possibilidade de "bagun�ar" o reposit�rio online ao sobreescrever arquivos. Bem, isso ainda � poss�vel mas normalmente s� pode ser feito se for feito com o desejo prejudicial intencional.

Para configurar o git em um server, primeiro temos que configurar quais protocolos este serve ter� habilidade de lidar. Existem vantagens e desvantagens na utiliza��o de cada protocolo. Neste ponto, n�o � interesse aprender esse recurso agora. Ent�o, vamos passar para a se��o sobre Usando o git em um servirdor de terceiros como por exemplo: o famoso github.

H� um site onde � poss�vel ver uma lista atualizada de servi�os de hospedagem de reposit�rios git, como tamb�m as vantagens e desvantagens de cada um:
https://git.wiki.kernel.org/index.php/GitHosting

Ent�o agora vamos entender como criar e usar um reposit�rio no github:

________GITHUB Account Setup and Configuration

Primeira coisa a fazer � criar uma conta. Uma conta no github � gratuita:
visite https://github.com
1- Escolher um username
2- colocar um email para a conta
3- digitar uma senha para configurar a maneira segura de acesso � sua conta
4- vai haver uma p�gina perguntando sobre se vc quer fazer upgrade de conta e pagar por recursos extras. Mas aqui n�o precisamos dos rescursos de uma conta paga. Caso vc queira poder� fazer isso no futuro.
5- o GitHub vai te mandar um email para vc verificar sua conta, ent�o identifique esse email na sua caixa de entrada ou spam, e siga o procedimento apresentado l� (normalmente � clicar em um link)

A conta free do github, permite hospedar reposit�rios sem limite de tamanho. Ou seja, seja qual l� for o tamanho do seu projeto o github permite que seja hospedado. A limita��o da conta free � que reposit�rios privados, ou seja, sem acesso liberado para todos � limitado somente para 3 colaboradores. Ent�o, se voc� quiser colaboradores em uma quantidade maior que 3 ter� que de duas uma: fazer o upgrade de conta ou deixar seu reposit�rio como p�blico.

A partir do ponto que sua conta est� verificada, voc� est� pronto para usar o GitHub!

Clicando na logo do github esse "octocat" que est� na parte superior lateral esquerda voc� tem acesso � sua dashboard.

At� agora estamos permitidos � com reposit�rios atrav�s do protocolo HTTPS, autenticando com usu�rio e senha da nossa conta. Mas, para clonar um reposit�rio p�blico online para nosso diret�rio local n�o precisamos nem logar no github. A conta que criamos � �til quando realmente estamos desenvolvendo e fazemos "forks" de projetos. Por exemplo, vamos supor que tem um projeto existente por a� que vc quer come�ar a colaborar, ent�o precisa dar "fork" que � criar um clone para sua conta github e fazer uma conex�o entre oque vc est� fazendo e o reposit�rio original � como um ramo.

Alguns servidores GIT fazem a autentica��o usando SSH public keys. Bem, como pulamos a parte de protocolo voc� deve estar se perguntando oque � SSH. SSH � a abrevia��o para Secure Shell. Ele � um protocolo que permite que um computador fa�a "login" no outro e possa transferir e puxar arquivos de forma segura. Ele realiza a encripta��o da transfer�ncia de dados, permitindo que m�todos de transfer�ncia de arquivos n�o seguros (que n�o exigem protocolos de autentica��o de entrada) tornem-se seguros.

O m�todo de autentica��o pode ser feito atrav�s de chaves que podem ser p�blicas ou privadas. A chave p�blica � uma sequ�ncia de caracteres que permite qualquer um que tiver uma c�pia desses valores possa acessar um servidor (que no caso � outro computador). Bem independente de serem publicas ou privadas, essas chaves s�o chamadas de SSH Keys.

Bem, se formos acessar algum reposit�rio Remoto regido pelo protocolo SSH, precisamos configurar a SSH Key da nossa conta. N�o irei explicar como se gera essa chave, pois se voc� se encontrar nessa situa��o provavelmente saber� como gerar essas chaves para seu computador. Mas, para adicionar vc precisa ir nas configura��es da sua conta e adicionar esse valor no campo designado.

� interessante tamb�m, configurarmos informa��es pessoais como Nome de Usu�rio, Email p�blico, algum site do nosso perfil e localiza��o para que pessoas no quais est�o trabalhando conosco possam saber quem n�s somos. S�o informa��es interessantes no mundo profissional. Inclusive, sua conta no GitHub pode ser parte importante do seu curr�culo.

________Contribuindo com o um projeto
Quando queremos contribuir com um projeto existente no qual n�o temos permiss�o para pushs, n�s podemos fazer um fork. Um fork como explicado anteriormente � uma c�pia do projeto feita para voc�.
Quando voc� fizer alguma altera��o interessante ao projeto e acha que a vers�o original poderia se beneficiar disso, pode-se fazer um "pull request". Basicamente o caminho de projeto no github segue o seguinte:

1- d� fork no projeto escolhido.
2- crie um ramo para fazer suas altera��es a partir do master
3- fa�a alguns commits para aprimorar o projeto
4- fa�a um push para o seu reposit�rio online
5- abra um pull request no github.
6- discuta o seu pull request e opcionalmente continue a commitar 
7- o dono do projeto pode fazer o merge com o seu commit ou fechar seu pull request.
8- sincronize a atualiza��o do master de volta para o seu fork



___________MANDANDO UM REPO LOCAL PARA UM REPO REMOTO
Caso voc� tenha uma reposit�rio local... ou seja, tudo come�ou sendo feito na sua maquina com um >git init... e agora vc quer envia-lo para um reposit�rio online podemos fazer o seguinte
1 - deixamos o repositorio up to date com um ultimo commit.
2 - criamos o repositorio remoto l� no fornecedor que queremos usar, no meu caso vou usar o github.
//podemos checar se h� um repositorio remoto atrelado ao nosso local, com:

> git remote -v

3 - copiamos a url desse repositorio remoto e usamos o seguinte comando:

> git remote add [nome do repo] URL

> git push --set-upstream [nome do repo]





















 