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

	




Seção 2.5 fetching and pulling











 