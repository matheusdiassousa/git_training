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

Ou seja, ele vai mandar os arquivos alterados para a staged area, solicitar que você digite um texto para o commit e depois de finalizar o texto e apertar enter ele vai realizar ter atualizado a versão do seu projeto. DETALHE ESSE COMANDO SÓ SERVE PARA ARQUIVOS JÁ TRACKEADOS PELO GIT. 

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

Bem, neste momento o git vai abrir o seu gerenciador de texto configurado e após isso, ele vai espera que vc altere a mensagem do commit passado. Caso você só feche o arquivo, ele vai dar continuidade e adicionar seu arquivo faltante ao último commit sem alterar a mensagem.

IMPORTANTE - Para que o git consiga abrir um programa ele precisa de permissão de usuário, então, você deve usar um PowerShell aberto como administrador... assim ao usar o GIT ele terá permissões de adm para executar ações que exijam graus de permissão maiores.

Agora vamos ver como retirar um arquivo em específico da staged area. Isso pode ser feito com o seguinte comando:

> git reset [arquivo]

Com esse comando, podemos tirar um arquivo que foi add pelo comando > git add [arquivo] <... Bem simples né?!

Podemos desfazer uma modificação local em um arquivo substituindo o arquivo alterado pela sua ultima versão de commit... vamos entender melhor:
Vamos supor que vc tenha um arquivo de texto com a frase "antes do restore" dentro deste arquivo. Supodondo que este seja um conteúdo importante, em algum momento você faz alguma alteração neste arquivo... trocou a frase para "antes do restore 1000", mas, na realidade você fez besteira e já salvou este arquivo. Então, você quer voltar para o antigo conteúdo do arquivo... podemos então fazer o git substituir este arquivo atual para sua versão do ultimo commit com o seguinte comando:

> git checkout [arquivo]

Entenda que tudo que foi commitado pode ser retornado. Você pode até mandar esta versão do projeto que está com este arquivo alterado para outro ramo (ou seja, o mesmo projeto em uma realidade paralela) e assim continuar no seu projeto principal com seu arquivo na fase inicial. Bem, podemos ver que o git é muito poderoso e que suas funcionalidades podem não fazer tanto sentido agora... mas, na realidade você verá que são muito úteis em projetos complexos no qual você precisa testar e manter diferentes versões do mesmo projeto. Um circuito com valores e resultados diferentes: por exemplo, para quando você juntar com circuitos posteriores você possa escolher qual deles teve o melhor desempenho.

--------> TRABALHANDO COM PROJETOS REMOTOS

Bem, primeiro oque é um projeto remoto? É um projeto que está hospedado em outro computador... como por exemplo um servidor que é acessado pela internet.
Você pode trabalhar em vários GIT ao mesmo tempo sem conflitar dados entre eles. (Se você não fizer uma besteira bem doida, tudo é possível na terra.)

Um repositório GIT que não é seu pode ser somente de Leitura onde você só consegue puxar dados, como pode também ser de Leitura/Escrita no qual você pode enviar e receber informações.

**Vendo seus repositórios remotos

> git remote

Este comando acima vai listar os repositórios remotos no qual você configurou para ter acesso... com por exemplo deu um clone. Se não mostrar nada é pq você não está trabalhando com nenhum.

Adicionar o comando "-v" mostra o endereço url do repositório:

> git remote -v

Bem agora vamos aprender como adicionar um desses repositórios... Então, primeiro deve lembrar que a gente deve estar dentro de uma pasta (via terminal) no qual queremos hospedar localmente os arquivos deste projeto. Então usamos o comando:

> git remote add <pequeno_nome_para_identificar_o_repositorio> <url_do_repositorio>

Esse pequeno nome que usamos para identificar o repo, pode ser usado no terminal no lugar de toda a URL do projeto. De agora em diante vamos chamar o nome que demos para o repositorio de de <repo_id>

Após fazer essa configuração onde você disse pro GIT que agora irá trabalhar nesse repositório... você precisa baixar para sua pasta local todos os arquivos que vc não tem ainda... Então, para isso, usamos o comando:

> git fetch <repo_id>

Esse comando trás todas as informações do projeto, inclusive de ramos do projeto. A partir daqui você pode trabalhar em um ramo do projeto ou no ramo principal.

O comando >fetch< vai trazer arquivos que você ainda não tem... mesmo que sejam todos.

Se você clona algum projeto, você terá esse repositório adicionado para você localmente... então se você usar o comando:

> git fetch origin

Ele vai buscar novos projetos ou arquivos a partir da vez que você deu o seu > git clone < perceba que origin na realidade é um id para repositório clonado... então quando usamos origin dentro da pasta de um projeto clonado ele na realidade está indo atrás do endereço referente ao repositório.
É importante salientar que o comando >fecth< somente faz o download dos arquivos para sua pasta local... você ainda precisa fazer manualmente a adição destes arquivos no seu projeto ou seja... dar um "merge" com seus arquivos versionados.

Podemos usar um comando para buscar arquivos no ramo de repositório que estamos trabalhando e ainda assim fazer a fusão desses arquivos com seus arquivos alterados localmente. Para isso podemos usar o comando:

> git pull

Ou seja, ele irá buscar os arquivos no repositório clonado e fundir com os seus arquivos... então tudo é feito de uma única vez.

___________Enviando arquivos para um server remoto

Bem, a certo ponto do seu projeto você deseja disponibiliza-lo em algum repositório online essa ação chamado de "push"... se para baixar os arquivos chamamos de "pull", enviar ou "empurrar" os arquivos para a núvem... chamamos de "push". Para isso usamos o seguinte comando, preste atenção nos argumentos:

> git push [remote] [branch]

Bem, em remote é o endereço que tem algum id... normalmente é o "origin" e o branch normalmente estamos trabalhando no "master"... Então o comando fica assim:

> git push origin master

Então estamos dizendo para o git enviar os arquivos commitados para o endereço origem do projeto e adicionameros ou atualizaremos os arquivos no ramo "master" ou principal do repositório online.

Este comando só irá funcionar se você tiver permissão de escrita no respositório que vc está tentando dar push... Outra coisa importante é que você só poderá dar push se seu repositório local tiver as ultimas atualizações do repositório online... perceba que isso é essencial pq você poderia estar sobrescrevendo a ultima atualização do seu projeto com uma versão ultrapassada. Isso pode acontecer quando se trata de um projeto com várias pessoas trabalhando nele. Então, antes de dar o push é importante dar um pull... para ver se algo mudou e atualizar o seu projeto.

Para ver informações sobre seu repositório online, como quais sãos os ramos, em qual ramo você está trabalhando e quando você der pull ou push quais serão os ramos que serão baixados e atualizados. O comando é:

> git remote show origin

_________________ Renomeando e Removendo Remotes

Para mudar o id de um remote, podemos usar o comando:

> git remote rename [id_antigo] [id_novo]

Para verificar a mudança, podemos usar:

> git remote

Para remover algum repositório remoto, por alguma razão como o repositório não será mais disponibilizado naquele server, não estará mais disponível para colaboração de alguém... e por aí vai, podemos usar o comando:

> git remote rm [id]

Depois de usar esse comando, todas as configurações para aquele repositório remoto serão excluídos... novamente podemos checar isso pelo comando:

> git remote

Lembrando que o git remote mostra quais repositórios vc está trabalhando dentro do seu projeto...

___________Tagging

Tags são como etiquetas que você usa para marcar o seu projeto... Bem, normalmente é usado para marcar a versão do seu projeto, vamos supor que vc lançou a primeira versão... após o ultimo commit daquela versão você pode adicionar uma tag. Assim, com essa tag você facilmente sabe identificar um ponto importante do seu projeto.

Primeiro precisamos saber como listar tags... podemos usar o comando:

> git tag //comentário: podemos adicionar no final o argumento "--list" ou "-l" mas é opcional.

Esse comando vai mostrar as tags em ordem alfabética. Podemos também listar as tags a partir de uma específica como:

> git tag -l "nome que identifica uma tag"

Então essa combinação de comandos vai mostrar tags que correspondem ao texto entre aspas.

__________Criando as tags

Existem dois tipos de tags no git são elas:

--> lightweight : essa tag é a mais simples, ela não muda e serve somente para marcar um commit.

--> annotated : essa tag é a mais completa e guarda todos os objetos referentes ao seu repositorio naquela tag... como, author, data, e salva os arquivos para serem comparados. O git recomenda taggear com esse tipo de tag. Mas, caso você não queira guardar tantas informações naquele momento, seja por que ainda não é importante ou seja por outro motivo... use a tag simples. Mas veja que a tag leve não guarda nem author nem hora... mas sabemos que ela aponta pra um commit que tem informações como author, hora e arquivos salvos para comparação. O problema é que essas infos são do commit não de quem fez a tag.

Criando a tag annotated... é simples podemos usar o comando:

> git tag -a [nome da tag] -m "texto que fala algo sobre a tag" //comentário: se vc não colocar o argumento -m o git irá abrir o seu editor de texto configurado para que vc escreva algo lá... ou simplesmente salve sem escrever nada.

então já sabemos que podemos listar as tags existentes com o comando:

> git tag -l

E podemos ver informações sobre nossa tag com o comando:

> git show [nome_da_tag]

Que irá mostrar informações interessantes sobre nossa tag...

Ainda podemos usar outro argumento para resumir as infos sobre a tag, como:

> git show [nome_da_tag] -s //comentário: como já usamos no "git status -s"

	

Para criar uma lightweight tag precisamos só usar o comando de tagging sem adição de argumentos extras... como:

> git tag [nome da tag]

Lembrando que este tipo de tag somente adiciona uma marcação para o commit, não diz quem fez a tag, que horas...etc e tal. O comando > git show < para essa tag só vai mostrar o nome da tag e as infos do commit.

__________- Adicionando tags em commits passados.
Podemos dar um > git log --pretty=oneline < ver todos os commits e pegar o SHA-1 do commit desejado e usar o seguinte comando:

> git tag -a [nome da tag] [SHA-1 do commit]

Mas qual é o SHA-1... lembramos primeiro que quando commitamos o git gera um HASH para identificar o commit e o conteúdo do projeto. O SHA-1 é essa sequência de numeros e letras que aparecem do lado esquerdo do texto do commit. Precisamos pegar no mínimo os 7 primeiros caracteres do Hash. Esse comando acima vai exigir a abertura do editor de texto para comentar a tag... para evitar essa novela toda, podemos adicionar o argumento de adição de mensagem da seguinte forma:

> git tag -a [nome da tag] [SHA-1 do commit] -m "texto que a gente quer colocar"

__________________ Compartilhando Tags

Por padrão quando realizamos um push o git não envia as tags que criamos no nosso versionamento local. Para isso precisamos subir a tag manualmente, ou ainda podemos subir todas as tags existentes que ainda não estão no repositório remoto. Podemos fazer essas duas coisas com os comandos listados respectivamente abaixo:

> git push origin [nome da tag]

> git push origin --tags

Talvez seja importante dizer que o git não distingue somente um tipo de tag para fazer o push. Ele irá enviar os dois tipos. Após usar estes comandos as tag estarão aplicadas também ao repositório remoto.

____________ Deletando Tags

Para deletar uma Tag localmente podemos usar o comando:

> git tag -d (ou --delete) [nome da tag]

E para fazer isso no repositório online... também precisamos deletar lá

> git push origin --delete [nome da tag]

__________ Checking Out Tags
Caso queira ver a versão dos arquivos que a tag está apontando podemos usar o comando:

> git checkout [nome da tag]

A questão aqui é, que após este comando você vai mudar o sua versão de trabalho para o commit que vc escolheu... então tudo vai mudar inclusive o log que você tinha. Nesse caso é como voltar no tempo. Só que você está em um modo "des-anexado" oque quer dizer que é como vc voltar para o commit que vc selecionou no checkout e a partir daí vc pode fazer mudanças e ir para um outro branch sem afetar o seu ramo anterior... 

----- até aqui eu ainda não sei como voltar para o repositório anterior.... acho que deu bosta, no sentido de ter perdido todos os meus logs...

____________ Criando apelidos para os comandos para evitar digitar todo o texto sempre
Podemos fazer apelidos para os comandos com os seguintes comandos:

> git config --global alias.[nome do apelido] 'comando que vai ser apelidado'

Por exemplo vamos fazer um apelido para o comando que mostra todos os commits de forma resumida... se para ver os commits reduzidos usamos o comando > git log --pretty=oneline < agora vamos usar
> git logres <... então vamos criar esse apelido usando o comando acima citado acima:

> git config --global alias.logres 'log --pretty=oneline'

_____________ Git Branching

Aqui vamos ver como funciona a ramificação de projetos. O manual do git diz que esse recurso é um dos seus melhores recursos e oque realmente justifica utilizar o git ao invés de outro VCSs...

Para entender as ramificações precisamos lembrar como funciona os commits do git... quando a gente dá um commit o que git faz é criar um objeto que aponta para uma "imagem" exata do projeto antes do commit. O commit é uma espécia de "porta" que dá acesso exatamente à esta imagem tirada do projeto.

Então cada commit é uma imagem de todo o projeto, não somente do arquivo mudado... mas de tudo que foi adicionado para a staged area e commitado.

Este objeto (commit) mostra quem foi que o executou, endereço de email do author, hora e etc. Caso o commit venha a partir de uma "fusão" de outros commits então este será um commit Pai que mostra a união de outros commits executados por outras pessoas ou versões de arquivos.

Quando adicionamos os arquivos à staged area o git vai criar um SHA-1 para cada arquivo que é uma sequência numérica resultado do conteúdo do arquivo... então um arquivo no mesmo endereço com mesmo nome e mesmo conteúdo tem que ter o mesmo SHA-1 e assim o git consegue comparar um arquivo ele mesmo em outro momento para ver se houve modificações ou não. Bem, quando damos o commit oque git faz é guardar no repositório o SHA-1 referente à cada arquivo guardado... ele chama cada SHA-1 de cada arquivo de "BLOBS". Quando realizamos o commit o repositório git guarda a seguinte quantidade de arquivos:

-> X Quantidade de blobs (1 para cada arquivo adicionado)
-> 1 tree (uma arvore que lista o conteúdo do diretório e especifica qual arquivo equivale a cada blob)
-> 1 commit (que é um objeto que aponta para arvore)

Então com esses arquivos o GIT consegue remontar todo conteúdo que foi salvo naquele commit.

O primeiro commit ele só tem os arquivos citados acima... mas o segundo commit e assim sucessivamente vai apontar para o commit anterior e criar a mesma lógica de arquivos citadas anteriormente... por exemplo:

primeiro commit de todos:


-> X Quantidade de blobs (1 para cada arquivo adicionado)
-> 1 tree (uma arvore que lista o conteúdo do diretório e especifica qual arquivo equivale a cada blob)
-> 1 commit (que é um objeto que aponta para arvore)


Segundo commit:


-> X Quantidade de blobs (1 para cada arquivo adicionado)
-> 1 tree (uma arvore que lista o conteúdo do diretório e especifica qual arquivo equivale a cada blob)
-> 1 commit (que é um objeto que aponta para arvore)
-> 1 objeto que aponta para o commit anterior (nesse caso o primeiro commit de todos)

Então o git na realidade sempre dá um caminho para a versão anterior, fazendo com que tenhamos pontos temporáis para acessar o nosso projeto.

O ramo que estamos no git é chamado de "master" é só um nome para dizer onde estamos mesmo... mas é um ramo como qualquer outro no seu repositório...

_______vamos agora criar um ramo

Para criar um ramo (outra linha temporal do projeto) podemos usar o comando:

> git branch [nome do ramo]

Esse comando só cria um novo ramo, não te leva para trabalhar nesse novo ramo criado

Para saber em qual ramo estamos, quando usamos o > git log < ele mostra em qual ramos estamos ao utilizar a palavra HEAD:

HEAD -> nome do ramo

Para ver o ramo que estamos como dito anteriormente podemos usar:

> git log --oneline --decorate

Quando os ramos estão no mesmo ponto de commits, quando vemos o log eles estão apontando para o mesmo commit. Mas, se fizermos alguma mudança e commitamos somente o ramo que estamos naquele momento apontará para aquele commit. É importante saber que quando nos movemos de branch na realidade estamos indo para o commit que aquele ramo teve por último, ou seja, estamos também andando na linha do tempo de mudanças nos nossos arquivos.

Bem, caso usemos o comando > git log --oneline --decorate < nós só veremos informações do ramo conectado no commit que estamos no presente momento... Por exemplo se a partir de um commit no ramo "master" damos um branch para "ramo2"... e damos um checkout para "ramo2" então com o log veremos os ramos que antecessores à ele mesmo... mas se autualizamos o ramo2 com um commit que só ele tem e depois damos um checkout para o ramo "master" e usamos o log, não veremos o "ramo2" porque ele é uma linha do tempo que não existe para o "master" ele está no futuro e ainda não aconteceu. Então, caso queiramos ver todos os ramos e commits na linha do tempo do nosso repositório... Ou seja, não veremos a partir da visão do ramo que estamos mas sim de todo o projeto podemos usar o seguinte comando:

> git log --oneline --decorate --graph --all

Com esse comando veremos inclusive um ramo des-conexo criado a partir de uma tag annotated.
Esse sim é um comando bem legal para a gente não ficar perdido.

No final um ramo é somente um arquivo SHA-1 que aponta para uma foto do seu projeto... isso então faz com que criar ramos seja muito leve no quesito de ocupar espaço e rápido no quesito de processar o comando. Por isso o modo com o GIT faz um ramo é chamado de "killer feature" pq outros gerenciadores não fazem isso assim. Eles normalmente duplicam seus arquivos para outro diretório ou seja, você ocupa espaço duas vezes com coisas iguais que não divergem de si quando comparamos um ramo com outro.

Vimos que o processo de criar um ramo e mudar para ele exige dois comandos... Mas, existe um comando que permite ao mesmo tempo criar e mudar para esse ramo, que é o seguinte:

> git checkout -b "nome do ramo"

______________ Criando ramos e depois os fundindo. (Branching and Merging)

Primeiro vamos entender em qual situação um Merging pode ser usado... Imagine que estamos trabalhando em um e estamos no ramo "master", o projeto trata-se de um aplicativo disponível para usuários comuns, então você como dev recebe um alerta do seu time de que há um problema para efetuar a troca de conta no aplicativo. Bem, você precisa realizar o concerto deste bug, mas não irá fazer isso no seu ramo master, pq isso pode danificar todo o seu projeto. Então oque podemos fazer? Bem podemos criar um ramo a partir do ramo master, mudar para esse novo ramo que chamaremos de "bugfix" e vamos realizar neste ramo secundário o concerto do bug e testar se está tudo ok nele. Depois que tivermos certeza que concertamemos esse problema, podemos então fundir esse ramo "bugfix" com o ramo "master" que é o ramo principal de desenvolvimento do nosso projeto. Bem, aqui é importante saber que precisamos ter os dois ramos atualizados, ou seja, não pode ter nada para ser commitado seja fora ou dentro da staging area... pq se tiver em uma dessas condições o git não vai deixar realizar o branch.

Para fazer o merging nós precisamos ir para o ramo que queremos "puxar" os arquivos do outro "ramo"... para entender melhor: nós temos 2 ramos, um "master" e um "bugfix" que foi criado para solucionar e testar o bug... um vez solucionado queremos mandar a versão dos arquivos do "bugfix" para o ramo "master". Então, damos um checkout para o ramo master e usamos o comando à seguir para fazer o merging:

>git merge bugfix //comentário: veja que depois de "merge" vem o nome do ramo que estamos puxando e fundindo os arquivos.

Há um tipo de merge chamado "fast-foward" que trata-se de quando realizamos um merge entre dois commits que estão conectados na linha do tempo. Como assim? Se pensarmos que master é um commit no tempo 2 e bugfix é um ramo com commit na linha do tempo 3... então na realidade o commit de bugfix está logo na frente do master. Então um merge fast-foward é só o git mudando o apontador do ramo master para o mesmo commit do bugfix... em linhas grossas: os ramos master e bugfix apontam para o mesmo commit neste momento. Isso acontece somente quando um commit consegue alcançar o outro por estas vias. Simples não é?! Bem, só tenha em mente que podemos dar um merge entre commits separados por longas linhas temporais no git.

Bem, como agora você já tem o bug resolvido e não precisa mais do branch bugfix... podemos apagar esse branch com o comando:

> git branch -d bugfix //comentário: de novo, bugfix pode ser o nome de qualquer repositório que vc queira apagar.

Vamos agora entender um pouco sobre o merge de commits que estão distantes na linha temporal. Quando temos dois ramos que estão distantes um do outro por alguns commits, o git não pode fazer um fast foward merge, pq os commits atuais de cada ramo possuem arquivos diferentes e não tem um commit ancestral direto entre eles dois. Na realidade eles tem ancestrais que tem ancestrais em comum. É como  primos que possuem os avós como ancestrais diretos, onde seu pai é seu ancestral direto e seu tio é seu ancestral indireto. Então oque o git precisa fazer é ir até esse commit ancestral direto e reunir as informações e alterações destes arquivos para que assim possa criar um novo commit um ancestral filho direto destes dois commits que estão sendo fundidos. Assim como dito anteriormente irá existir agora um novo commit que é a reunião//fusão de informações dos commits anteriores.

Bem, como agora vc tem as infos desse seu branch secundário que foi puxado as informações... podemos exclui-lo como já sabemos.

O merging nem sempre irá ser executado tão pacificamente assim, as vezes... ele dá alguns conflitos de informações e reclama. Vamos supor que você mudou o mesmo arquivo de forma diferente nos dois ramos... ou seja, escreveu algo lá no arquivo1 no ramo master e escreveu outra coisa no mesmo do arquivo no ramo bugfix... por exemplo... então o git não irá realizar o merge e vai te solicitar para solucionar o problema do conflito.

Para ver em que arquivo o conflito ocorre, podemos rodar um > git status <
Então se a gnt abrir o arquivo conflituoso, lá teremos texto marcando o conflito entre os arquivos. Veja para imagens isso é mais complexo mesmo que a imagem seja um código ainda assim será difícil decifrar isso. Então resolver este conflito pode ser um pouco mais complicado em casos especiais de arquivos que não vamos abordar aqui.

Depois de resolver os conflitos precisamos somente, dar um git add nos arquivos alterados. Enviar os arquivos para a staging area faz o git entender que os arquivos estão marcados como resolvido e para terminar o merge nós temos que dar um commit. Vamos olhar agora nosso tree e ver com qual aparência ela está agora:

Vemos então que há agora um ancestral filho comum aos dois ramos... E se quisermos podemos excluir o ramo secundário ao master. Fica à seu critério!

_______________BRANCH MANAGEMENT

Para ver os ramos que existem de uma forma mais simples, podemos usar o comando:

> git branch

E caso queiramos mais detalhes como o ultimo commit de cada branch podemos usar:

> git branch -v

Podemos ver quais ramos foram fundidos com o ramo no qual estamos atualmente com o commando:

> git branch --merged

E para ramos que não demos merge, podemos usar

> git branch --no-merged

Ramos que já demos merged normalmente são seguros de serem excluidos... No entanto se tertarmos deletar um ramo que ainda não demos merge, o git vai nos dizer que não pode fazer isso pq esse conteúdo não está seguro para ser deletado, visto que não foi adicionado ao seu ramo principal.
Bem, então para isso podemos fazer duas coisas:

1 - Realizar o merge
2 - Se soubermos que é seguro, podemos forçar a exclusão com o seguinte comando:

> git branch -D [nome_do_ramo] //comentário: veja que quando usamos > git branch -d [nome_do_ramo] <
o git não deixa a gente excluir, então usar o "-D" é uma forma de dizer à ferramenta que independente do que ela acha ela executar nosso comando.

Ainda para vermos sobre ramos que não foram fundidos, podemos perguntar ao git quais arquivos dentro deste ramo não foram fundidos... então, para isso podemos usar o seguinte comando:

> git branch --no-merged [nome_do_ramo]

________ Talvez seja interessante adicionar um conteúdo que fale sobre modos de como projetos são gerenciados no git, no sentido de criar ramos para diferentes objetivos, como testar uma ideia... e por aí vai.

________ REMOTE BRANCHES

Toda vez que nos conectamos à internet o git baixa informações para seu repositório local sobre estados dos seus ramos no repositório remoto, de forma que ele sempre esteja atualizado sobre quais os estados dos ramos online. De modo que você não sobre-escreva uma versão do projeto que foi atualizada por alguém que colabora com seu projeto.

Caso queira compartilhar um ramo para o servidor remoto, mas não queira compartilhar todos os ramos, por algum motivo... você pode usar o comando:

> git push [remote_name] [branch_name]

Bem, quando adicionamos um ramo para um repositório online que somente nós tínhamos no começo então quando um colaborador usar o git pull ele só terá a indicação do ramo ele ainda precisa dar merge desse ramo com o seu workflow local. Isso pode ser feito com o comando:

> git merge origin/[new_branchname]

Caso você dê clone em um projeto e queira trabalhar somente em um ramo específico, você pode usar o comando:
> git checkout -b [branchname] origin/[branchname]
ou
> git checkout --track origin/[branchname]

Se você quiser que esse ramo remoto seja chamado por um apelido diferente do ramo online você pode usar o comando:

> git checkout -b [nomelocal] origin/[branchname]

Se você criou um ramo local e depois quer que essa ramo "monitore" os arquivos de um ramo remoto, você pode usar o comando:

> git branch -u origin/[branchname]

Ou seja, agora o ramo que vc está como "head" vai monitorar os arquivos estão no ramo "branchname" no endereço "origin".

Para ver quais as configurações de "monitoramento remoto" cada ramo está seguindo, podemos usar o comando:

> git branch -vv

Quando vemos o resultado deste comando podemos ter três mensagens após a informação do endereço remoto e o ramo remoto que o nosso ramo local está monitorando. As mensagens são:

1 - ahead x - ahead quer dizer que o ramo local está com "x" quantidades de commits na frente do ramo online... ou seja, seria legal atualizar o ramo online executando um push.
2 - behind x - behind quer dizer que o ramo local está com "x" quantidades de commits atrás do ramo online... então, seria bom atualizar nosso ramo local executando um pull.
3 - ahead x, behind y - bem aqui a gente já sabe então, que nosso ramo local está à frente do ramo online com "x" commits e atrás com "y" commits. Nesse caso é melhor atualizar nosso ramo local primeiro e depois atualizar o ramo online, para que a gente não sobre escreva o trabalho de outra pessoa.

É importante dizer que essa informação mostrada pelo comando atrás nos está respondendo baseado nas informações locais que temos da ultima vez que executamos um " fetch "... ou seja, se passaram alguns minutos ou horas e há a possibilidade das informações remotas terem mudado, então é muito importante dar um fetch antes... como por exemplo da seguinte forma:

> git fetch --all; git branch -vv

Agora assim, temos uma informação atualizada. Bem, é bom lembrar que o " fetch " só buscar informações atualizadas para você, ele não pega os arquivos online e altera seus arquivos locais você precisa fazer isso dando um merge... Mas, caso você execute um " git pull" ele irá fazer as duas coisas ao mesmo tempo, no entanto, este comando não é tão explicito como executar uma sequência " fetch + pull "... Fica ligado nessa parada!

Se você quiser deletar um ramo online, por seja qual lá for o motivo, você usar o seguinte comando:

> git push origin --delete [branchname]

É bom saber que o git vai apagar o apontador para aquele ramo com seu commit... mas o arquivo ainda vai ficar lá por algum tempo. O tempo de permanência depende do fornecedor de repositórios online.


___________GIT REBASING
Esse rebase me parece bastante complicado. Mas, vamos tentar explicar. Basicamente quando a gente usa o merge, oque fazemos é pegar dois branches que em algum momento tem um ancestral comum, ir até esse ancestral e comparar todas as diferenças entre arquivos e depois unir estes arquivos em um só commit. No entanto, as linhas do tempo ainda sobram. Ou seja, ainda é possível acessar os ramos paralelos antes do merge. O rebase é como se esse ramo paralelo que tem seus commits específicos tivessem sido feitos na linha principal do commit master que originou as ramificações. Imagine que temos três linhas do tempo de commits, uma principal chamada master, uma lateral chamada segunda, terceira. Então a linha principal continua com seus commits e do mesmo modo as outras linhas. Em algum momento terminamos as atualizações no ramo "segunda" e usamos o rebase da segunda dentro da linha "master". Isso quer dizer que os commits da linha segunda, serão movidos para uma arquivo temporário e apagados da linha tempo. Então serão criados a mesma quantidade de commits que existiam na linha segunda e estes serão adicionados na linha master, com o master com arquivos agora do rebase. É como se fosse um merge, mas há uma re-organização da linha do tempo. Na verdade o rebase parecer ser utilizado para manter a limpeza ou estética de commits do projeto, para não haver vários ramificações. Como usamos o rebase?

1- entramos no ramo paralelo que queremos "mover" os commits para o ramo destino

> git checkout [ramo_paralelo]

2- então usamos o comando > rebase < para indicar o destino destes commits

> git rebase [ramo_destino]

Como o seu master está em um commit agora atrasado em relação à sua propria linha do tempo, podemos leva-lo para o commit mais atualizado (que é a união do master com os commits do ramo paralelo que foi apagado) com o seguinte comando:

> git checkout [ramo_rebased] //comentário: no nosso caso foi o master

> git merge [ramo_paralelo]

Não há diferença no quesito "arquivos resultantes" entre o rebase e o merge

Agora há uma outra possibilidade que é dar rebase de um ramo que é ramificação de uma ramificação. Ou seja, vamos supor que um terceiro ramo é um sub-ramo da linha principal, ou seja, o ramo principal tem um commit que dá origem a um ramo... este ramo com seu commit inicial dá origem a outro ramo. Assim, esse terceiro ramo tem um ancestral que é ancestral da linha principal. Agora, vamos supor que queiramos mandar esse terceiro ramo para o ramo principal, mesmo que eles não tenha uma conexão tão direta assim. Deste modo, podemos usar o seguinte comando:

> git rebase --onto [ramo_destino] [ramo_pai_do_terceiro_ramo] [terceiro_ramo]

na realidade o comando assim será algo mais ou menos assim > git rebase --onto master segundo terceiro


Para entender melhor, o ramo_pai tem um commit no inicio da sua linha do tempo que dá origem ao terceiro_ramo e o ramo_destino tem um commit que deu origem ao commit inicial da linha do tempo do ramo_pai. Veja que o comando está dizendo assim: "pegue os commits do terceiro_ramo que são diferentes do ramo_pai e mande para a linha do tempo do ramo_destino". Parece uma bagunça mas dá certo...haha. O resultado disso é o ramo_destino agora terá no final da sua linha do tempo os commits do terceiro_ramo, como se eles tivessem sido feitos anteriormente nessa linha tempo. Não esqueça de dar merge entre o commit que está o ramo_destino e o commit que está o terceiro_ramo...assim eles estarão no mesmo commit. Isso quer dizer que se você não fizer isso... se vc der checkout para o ramo_destino ele estará atrasado em relação sua propria linha do tempo. Quem está mais atualizado no momento é o terceiro_ramo, mas, lembre-se que isso pode ser confuso em um projeto porque o terceiro_ramo foi criado para adicionar algum recurso paralelo, e o o ramo principal normalmente é o "master". Isso quer dizer que se algum colaborador quiser ter os arquivos na posição oficialmente mais atualizada ele vai entar no "master", então caso vc atualize oficialmente o master tem que acompanhar esse commit.

No final, quando o ramo_pai tiver pronto podemos usar o rebase normalmente (sem o --onto) para dentro do ramo_destino (master) e aí vamos dar o merge no final.
Depois para limpar a linha do tempo vamos apagar os ramos que sobraram redundantes apontando para o mesmo commit que o master.

> git branch -d terceiro

> git branch -d segundo

Bem, há uma regra de outro em relação ao rebase! Não de rebase em commits de repositórios que vc colabora no qual há commits que seus parceiros estão trabalhando, pois pode causar muita confusão e redundância de commits com mesmo autor, hora e etc...

Oque é melhor, rebase ou merge?

O rebase muda a linha temporal do projeto, deixa ela linear e mais organizada, mas não é fiel à história de evolução do seu projeto.

O merge pode ser mais bagunçado com vários branchs paralelos e uniões, mas, ele é fiel ao tempo e versões do seu projeto.

Fica a critério da equipe de projeto adotar um ou outro. (rebase é complicado de entender)


____________GIT ON THE SERVER
Normalmente projetos são feitos em grupos. Neste caso, queremos que as pessoas possam afetar o projeto fazendo pulls e pushs. No entanto, ter um repositório hospedado em um computador que as vezes fica offline pode não ser uma ideia legal, pois, você pode atualizar um projeto offline e seus colegas trabalharem por cima de um projeto desatualizado. A solução para esse problema está em usar um respositório localizado em um ponto intermediário para todos os usuários, neste caso, ter um repositório na núvem é uma solução adequada para este tipo de problema. Ou seja, todos terão sempre que realizar um pull antes de um request, deste modo, sempre terão a versão mais atualizada do projeto minando a possibilidade de "bagunçar" o repositório online ao sobreescrever arquivos. Bem, isso ainda é possível mas normalmente só pode ser feito se for feito com o desejo prejudicial intencional.

Para configurar o git em um server, primeiro temos que configurar quais protocolos este serve terá habilidade de lidar. Existem vantagens e desvantagens na utilização de cada protocolo. Neste ponto, não é interesse aprender esse recurso agora. Então, vamos passar para a seção sobre Usando o git em um servirdor de terceiros como por exemplo: o famoso github.

Há um site onde é possível ver uma lista atualizada de serviços de hospedagem de repositórios git, como também as vantagens e desvantagens de cada um:
https://git.wiki.kernel.org/index.php/GitHosting

Então agora vamos entender como criar e usar um repositório no github:

________GITHUB Account Setup and Configuration

Primeira coisa a fazer é criar uma conta. Uma conta no github é gratuita:
visite https://github.com
1- Escolher um username
2- colocar um email para a conta
3- digitar uma senha para configurar a maneira segura de acesso à sua conta
4- vai haver uma página perguntando sobre se vc quer fazer upgrade de conta e pagar por recursos extras. Mas aqui não precisamos dos rescursos de uma conta paga. Caso vc queira poderá fazer isso no futuro.
5- o GitHub vai te mandar um email para vc verificar sua conta, então identifique esse email na sua caixa de entrada ou spam, e siga o procedimento apresentado lá (normalmente é clicar em um link)

A conta free do github, permite hospedar repositórios sem limite de tamanho. Ou seja, seja qual lá for o tamanho do seu projeto o github permite que seja hospedado. A limitação da conta free é que repositórios privados, ou seja, sem acesso liberado para todos é limitado somente para 3 colaboradores. Então, se você quiser colaboradores em uma quantidade maior que 3 terá que de duas uma: fazer o upgrade de conta ou deixar seu repositório como público.

A partir do ponto que sua conta está verificada, você está pronto para usar o GitHub!

Clicando na logo do github esse "octocat" que está na parte superior lateral esquerda você tem acesso à sua dashboard.

Até agora estamos permitidos à com repositórios através do protocolo HTTPS, autenticando com usuário e senha da nossa conta. Mas, para clonar um repositório público online para nosso diretório local não precisamos nem logar no github. A conta que criamos é útil quando realmente estamos desenvolvendo e fazemos "forks" de projetos. Por exemplo, vamos supor que tem um projeto existente por aí que vc quer começar a colaborar, então precisa dar "fork" que é criar um clone para sua conta github e fazer uma conexão entre oque vc está fazendo e o repositório original é como um ramo.

Alguns servidores GIT fazem a autenticação usando SSH public keys. Bem, como pulamos a parte de protocolo você deve estar se perguntando oque é SSH. SSH é a abreviação para Secure Shell. Ele é um protocolo que permite que um computador faça "login" no outro e possa transferir e puxar arquivos de forma segura. Ele realiza a encriptação da transferência de dados, permitindo que métodos de transferência de arquivos não seguros (que não exigem protocolos de autenticação de entrada) tornem-se seguros.

O método de autenticação pode ser feito através de chaves que podem ser públicas ou privadas. A chave pública é uma sequência de caracteres que permite qualquer um que tiver uma cópia desses valores possa acessar um servidor (que no caso é outro computador). Bem independente de serem publicas ou privadas, essas chaves são chamadas de SSH Keys.

Bem, se formos acessar algum repositório Remoto regido pelo protocolo SSH, precisamos configurar a SSH Key da nossa conta. Não irei explicar como se gera essa chave, pois se você se encontrar nessa situação provavelmente saberá como gerar essas chaves para seu computador. Mas, para adicionar vc precisa ir nas configurações da sua conta e adicionar esse valor no campo designado.

É interessante também, configurarmos informações pessoais como Nome de Usuário, Email público, algum site do nosso perfil e localização para que pessoas no quais estão trabalhando conosco possam saber quem nós somos. São informações interessantes no mundo profissional. Inclusive, sua conta no GitHub pode ser parte importante do seu currículo.

________Contribuindo com o um projeto
Quando queremos contribuir com um projeto existente no qual não temos permissão para pushs, nós podemos fazer um fork. Um fork como explicado anteriormente é uma cópia do projeto feita para você.
Quando você fizer alguma alteração interessante ao projeto e acha que a versão original poderia se beneficiar disso, pode-se fazer um "pull request". Basicamente o caminho de projeto no github segue o seguinte:

1- dê fork no projeto escolhido.
2- crie um ramo para fazer suas alterações a partir do master
3- faça alguns commits para aprimorar o projeto
4- faça um push para o seu repositório online
5- abra um pull request no github.
6- discuta o seu pull request e opcionalmente continue a commitar 
7- o dono do projeto pode fazer o merge com o seu commit ou fechar seu pull request.
8- sincronize a atualização do master de volta para o seu fork



___________MANDANDO UM REPO LOCAL PARA UM REPO REMOTO
Caso você tenha uma repositório local... ou seja, tudo começou sendo feito na sua maquina com um >git init... e agora vc quer envia-lo para um repositório online podemos fazer o seguinte
1 - deixamos o repositorio up to date com um ultimo commit.
2 - criamos o repositorio remoto lá no fornecedor que queremos usar, no meu caso vou usar o github.
//podemos checar se há um repositorio remoto atrelado ao nosso local, com:

> git remote -v

3 - copiamos a url desse repositorio remoto e usamos o seguinte comando:

> git remote add [nome do repo] URL

> git push --set-upstream [nome do repo]





















 