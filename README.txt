Esse projeto foi criado para ensinar o b�sico da utiliza��o do GIT.

**Texto de configura��o do GIT**

O primeiro passo para come�ar um projeto git � criar uma pasta. Depois navegar via terminal at� essa pasta (ou abrir o terminal a partir da pasta) e digitar o seguinte comando:

> git init

Esse comando ir� criar uma pasta oculta com arquivos necess�rios para que software git possa gerenciar os arquivos dentro da pasta do seu projeto. Mas, ainda o projeto n�o est� sobre gerenciamento de vers�o do git. O pr�ximo passo � iniciar seu projeto com algum arquivo. Quando trata-se de c�digo seja ele aberto ou privado � importante ter um arquivo chamado "LICENSE". Dentro desse arquivo colocamos o texto referente � qual licensa est� agindo sobre o conte�do do seu projeto . Caso seu projeto esteja em um reposit�rio de c�digo aberto como a vers�o gratu�ta do GitHub e n�o haja nenhum arquivo LICENSE isso quer dizer que automaticamente voc� est� aplicando os termos de licensa padr�o de direito de c�pia. Ou seja, ninguem tem direito de usar seu c�digo. Logo, se seu objetivo � deixar o c�digo aberto, ent�o adicione um arquivo LICENSE.txt no primeiro n�vel da pasta do seu projeto e coloque dentro alguma licensa de uso livre, como por exemplo a licensa MIT. 
Bem, ap�s adicionar nosso primeiro arquivo (que nesse caso foi o LICENSE mas poderia ser qualquer outro) podemos dar o primeiro commit. IMPORTANTE, s� depois do commit � que o git ir� gerenciar as mudan�as no seu projeto. Primeiro vamos dizer para o git que estamos adicionando o primeiro arquivo modificado:

> git add LICENSE.txt

Este comando acima � de multiprop�sito ele serve para adicionar novos arquivos � staged area e adicionar arquivos j� existentes que foram modificados � staged area. Tamb�m, quando excluimos algum arquivo precisamos "falar (adicionar)" � staged area que realmente estamos excluindo um arquivo da nossa nova vers�o.

Depois, vamos fazer o commit:

> git commit -m "Texto entre aspas que justifica o commit" 

Esse texto entre aspas � um texto que voc� escreve para que voc� possa identificar qual foi a mudan�a que vc fez, fica mais f�cil depois voltar a alguma vers�o importante do projeto atrav�s de commits de f�cil identifica��o.

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

------ Usando o GIT Ignore no Windows -------
Talvez em alguma situa��o a gente queira ignorar algum arquivo quando usamos o git status (ou seja, n�o adicionaremos esse arquivo ao nosso reposit�rio). Ent�o para isso a gente pode criar um arquivo no nosso projeto, chamado > .gitignore <. Dentro desse arquivo vamos colocar o nome e a  extens�o do arquivo � ser ignorado ou *.extens�oindesejada para ignorar todos os arquivos que terminam com aquela extens�o... bem podemos usar outras capacidades do bash ou shell para identificar estes arquivos, mas n�o iremos falar disso aqui. Caso tamb�m n�o queiramos que o pr�prio arquivo .gitignore seja adicionado no nosso reposit�rio podemos recursivamente declarar o proprio .gitignore dentro do arquivo .gitignore. Bem, no linux � mais f�cil criar esse arquivo, mas no windows isso pode ser um pouco mais dificil, vamos ver oque podemos fazer:

1� Podemos criar um arquivo .txt qualquer dentro da nossa pasta principal do reposit�rio e escrever l� quais arquivos queremos que sejam ignorados. Depois disso, abrimos o terminal dentro desta pasta e usamos o comando para renomear o arquivo qualquer.txt, da seguinte forma

> ren qualquer.txt .gitignore

pronto nosso arquivo foi renomeado.

2� Podemos abrir o terminal dentro da pasta e usar o comando de escrita de texto dentro de um arquivo, aqui � importante saber que se o arquivo destino que a gente especificou no comando n�o existir ele ser� criado automaticamente. Ou seja, caso ela exista ele so receber� o texto na sua ultima linha n�o escrita e se ele n�o existir ele ser� criado com o texto que a gente escreveu. Ent�o o comando explicado � o seguinte:

> echo "texto" > .gitignore

pronto nosso arquivo .gitignore foi criado com a palavra --> texto <-- dentro dele... perceba que essa palavra texto pode ser simplesmente a regra de exce��o ou ignorar para o git.

 