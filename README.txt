Esse projeto foi criado para ensinar o básico da utilização do GIT.

**Texto de configuração do GIT**

O primeiro passo para começar um projeto git é criar uma pasta. Depois navegar via terminal até essa pasta (ou abrir o terminal a partir da pasta) e digitar o seguinte comando:

> git init

Esse comando irá criar uma pasta oculta com arquivos necessários para que software git possa gerenciar os arquivos dentro da pasta do seu projeto. Mas, ainda o projeto não está sobre gerenciamento de versão do git. O próximo passo é iniciar seu projeto com algum arquivo. Quando trata-se de código seja ele aberto ou privado é importante ter um arquivo chamado "LICENSE". Dentro desse arquivo colocamos o texto referente à qual licensa está agindo sobre o conteúdo do seu projeto . Caso seu projeto esteja em um repositório de código aberto como a versão gratuíta do GitHub e não haja nenhum arquivo LICENSE isso quer dizer que automaticamente você está aplicando os termos de licensa padrão de direito de cópia. Ou seja, ninguem tem direito de usar seu código. Logo, se seu objetivo é deixar o código aberto, então adicione um arquivo LICENSE.txt no primeiro nível da pasta do seu projeto e coloque dentro alguma licensa de uso livre, como por exemplo a licensa MIT. 
Bem, após adicionar nosso primeiro arquivo (que nesse caso foi o LICENSE mas poderia ser qualquer outro) podemos dar o primeiro commit. IMPORTANTE, só depois do commit é que o git irá gerenciar as mudanças no seu projeto. Primeiro vamos dizer para o git que estamos adicionando o primeiro arquivo modificado:

> git add LICENSE.txt

Depois, vamos fazer o commit:

> git commit -m "Texto entre aspas que justifica o commit" 

Esse texto entre aspas é um texto que você escreve para que você possa identificar qual foi a mudança que vc fez, fica mais fácil depois voltar a alguma versão importante do projeto através de commits de fácil identificação.

Podemos ver o estado em que o git está através do comando

> git status

Este comando mostra se algum arquivo foi modificado e não está sendo monitorado, ou, se todos os arquivos do projeto estão monitorados. Se a cor do arquivo estiver vermelha quer dizer que não está monitorado. Se aparecer em verde quer dizer que ele foi adicionado pelo comando > git add arquivo < e podemos fazer o commit para atualizar a versão do projeto. Se nenhum arquivo aparecer quer dizer que está tudo atualizado. O comando também mostra em qual ramo do projeto vc está trabalhando, se é um ramo paralelo ou se está trabalhando no ramo principal do projeto.
 