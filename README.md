# EstudoGitIniciante

  Este documento é apenas para consulta ou auxilio no aprendizado inicial de Git/Github

  Para começar, o git veio para ter um controle de versão, com finalidade de gerenciar diferentes versões de um mesmo documento(projeto), para que você consiga, avançar ou voltar sem maiores problemas.
  O git não verifica por diferença nos arquivos, ele guarda snapshots, ou seja a imagem deles, guardando seus estados atuais, se o arquivo não mudar, ele faz um link para que fique anexado no documento todo, assim, você consegue ter acesso e modificar partes dos projetos.
  Ele é reposnvel por versionar seus projetos automaticamentes, o git trabalha com estados dos arquivos.
 
  História do git
    Existia uma empresa chamada BitKeeper que guardava todo kernel do linux lá, porem aconteceu uma quebra entre essa empresa e a linux, que fez com que a bitkeeper que fez com ele retirasse a insenção do linux, e o criador do linux simplesmente insatisifeito por isso,e criou um pra usar com o linux, e fez o git, pensando nas melhorias que foram : - velocidade (verificação em estados e nao arquivos por arquivos), - design simples (mais fácil de add arquivos e remover), - suporte mais robusto e desenvolvimento não linear(facilitando o trabalho em equipes), - totalmente distribuido, e capaz de lidar com grandes projetos como o kernel do linux(sem problemas de lentidão e movimentar entre históricos).
    
    Mais uma curiosidade, o criador do linux e do git são a mesma pessoa, o Linus Torvalds.
    
  O que é GitHub? É um serviço de web compartilhado para quem usa o git pra versionamento, ou seja, não é o mesmo que o github, o github só é um local que você compartilha os projetos, como se fosse uma rede social open source onde você assim como você pode compartilhar seus códigos, poderá contribuir em outros projetos também.
  
  Instalando o GIT:
    1- entra no site do git (https://git-scm.com/), lá tem as informações para instalar em cada sistema operacional. No linux ja vem instalado. No Mac tambem vem com um pacote, e em outros é apenas baixar.
    
    2 - CONFIGURAR O GIT 
    - o git guarda as suas informações em 3 locais (GIT CONFIG do sistema como um todo, o GIT CONFIG do usuário(global) e o GIT CONFIG do projeto especifico daquele repositorio ). 
    Para configurar o global (git config do usuário):
      - abra o cmd (promp de comando) verifique se está na pasta desejada e dgite -->  git config --global.user.name "Seu Nome"
      -ele não vai te informar nada se der certo!
      -pra configurar o email digite -->  git config --user.email "seuEmail@email.com"
      -se der certo não aparecerá nada também!
      -pra configrua editor de text --> git config core.editor   -- se n for definido ele usara o vim por padrão.
      -pra saber qual valor da chave digitada, git config user.name(saber o nome do usuário global) ,
                                                          user.email(o email configurado para este usuário) , 
                                                          git config --list (pra listar tudo).
      
  3 - Inicializando os projetos
    - para criar uma pasta, na janela do promp digite -->  mkdir git-course(ou o nome que desejar !)
    - para acessar a pasta digite --> cd git-course(ou o nome que você escolheu) e apertar o 'enter'
    - para ser considerado parte do git, precisa inicializar o repositorio, digitando  git init e dando 'enter'
    - toda vez que o git inicializa ele cria esta pasta com várias informações, e já pode começar a trabalahr no projeto.
    
 4- Como editar os arquivos e sair sem ter problemas
    - vocÊ pode colocar 'vi' ou 'vim' e o nome do arquivo e dar 'enter', e ele mostrará o uma tela em branco para você editar o que quiser, porém você irá verifficar que está bloqueado para edição, para conseguir editar o arquivo:
    - aperte a letra i e ele entra em modo de insert
    - ao terminar aperte esc, assim ele sai do modo de edição, depois aperte a seguinte sequencia  : + w + q , feito isso ele sai do moodo de edição e volta a tela principal onde nós digitamos os comandos (tela do cmd)

5 - Estados de vida do git
    - ele possui 4 estados de vidas
      - o untracked que é quando não marcado, acabou de ser adicionado no git, ou seja o git ainda não conhece nenhuma versão deste arquivo.
      - depois de adicionar este arquivo no git ele muda para estado unmodified
      - se modificar-lo, vai para o estado modified
      - depois que você ja modificou e quer criar uma versão dele , ele fica com o estado de staged
      
      - ao final de todo o procesos ele volta a ser unmodified, pois todas as modificações foram já adicionadas e comitadas, ou seja, ele não terá mais modificações na branch.
      
      Para entender melhor, vá até o temrinal, digite ls, ele vai listar todos os arquivos que voce tem, como não tem arquivo ele nao mostrará nada.
      - digite git status e ele vai mostrar como esta seu repositorio no momento, neste caso, ele vai mostrar o seguinte:
          On branch master (você está na branch (ramo/braço) master)
          Initial Commit (Este será seu commit inicial)
          nothing to commit (Não existe nenhum commit pra ser adicionado)
       
       Essa é a mensagem inicial do git, pois no caso não houve nada além da criação deste git.
       
       Vamos cirar um arquivo através dele, digite o seguinte comando --> vim Readme.md e de 'enter' 
       , ele vai criar o arquivo, você será direcionado para uma janela como aquela de edição de texto que vimos antes, 
       basta escrever algo e sair (caso não se lembre como, o comando é :wq e tecla 'enter')
       feito isso, vamos ver qual o status que se encontra nosso repositório git?
       basta digitar novamente --> git status e teclar 'enter' , e a seguinte mensagem será exibida:
          
          On branch master
           Initial Commit
           Untracked files:
             (use "git add <file>.." to include in what will be committed)
             
                    Readme.md
             nothing added to commit but untracked files present (use "git add" to track)       
             
         Ele viu que o arquivo foi criado, porem não conhece esse arquivo ainda.
         Para isso vamos digitar o seguinte comando --> git add Readme.md  ,
         desta forma estaremos "apresentando este arquivo recem adicionado ao git".
         Verificando o status novamente dele, lembra o comando ? (se não lembra, vai uma ajudinha, git status)
         ai vai aparecer a seguinte mensagem:
         
         On branch master
          
         Initial Commit
         
         Changes to be committed:
          (use "git rm --cached <file>.." to unstage)
          
                new file:  Readme.md
                
         Pronto! Adicionamos um arquivo ao nosso repositório e o git já está ciente desta modificação no estado! Lembra dos estados? Então este momento aqui já é o momento do staged, onde já temos o arquivo adicionado e já preparado para commitar. Porém se eu editar o arquivo do Readme, e salvar, ele vai estar no estado "modified", ou seja, você precisa fazer o git add Reamd novamente para deixar ele pronto novamente para commit.
         
         O que é um commit? 
          É um momento que vc avisa o git pra ele pegar todos os arquivos e criar uma imagem(snapshot), 
          pra fazer isso basta digitar o seguinte comando --> git commit -m "mensagem condizente com o commit"
          assim que você der entrar, a seguinte mensagem será mostrado:
            
            [master (root-commit) e1458528] Add Readme.md
            traduzindo esta linha : na branch da "master", através do "cmd" foi feito um "commit" com a seguinte "hash(que é uma identificação deste commit)", sendo adicionado o seguinte arquivo "Readme.md".
            
            logo a abaixo, virá outras informações referentes aos arquivos modificados e quantas inserções ou criações teve esse commit. Neste caso, se você seguiu a risca até aqui, sua mensagem será  :  1 file changed, 3 insertions (+)
                                                                   create mode 100644 Readme.md
                                                                   
            Se for digitado o git status novamente, voce verá que não tem nada a ser commitado pois não tem modificações para adicionar na branch.
   
   6 - Log no git
    - Com o log do git é possível verificar alterações que foram criadas, e assim conseguir ver o histórico, ver o histórico do commit... Para fazer isso basta digitar --> git log, ele vai mostrar a hash do commit, quem foi  autro , email, data e o commit feito.
    Temos algumas opç~es pra passar no git log, tipo:
    --> git log --decorate , que traz informações como de qual branch pra qual branch foi, se teve merge ou não, que task foram geradas 
    --> git log --autor="Nome", ai ele procura qualquer log que o tenha comom autor este nome digiado.
    --> git shortlog , que traz um resumo de quais autores fizeram commit, quantos commmits cada um fez em ordem alfabética, e qual cada um fez, e se quiser ver apenas quantos commits cada um fez, basta digitar --> git shortlog -sn
    --> git log --graph , ele mostra em forma gráfica em como esta meus branchs e merges;
      dentro do git log temos uma hash, pelo hash conseguimos ver o que aconteceu nesse commit, pra isso:
         
         commit:207bgfaa897ertg548errv5d5f4e
         Merge: 2a2dfcg78er9f
         Date: Fri Feb 1 00:12:32 2017 -0300
         
            Merge pull request #120 from cleiton/master
            
            Update Manual.md
        
        Você vai copiar apenas o conteúdo deste campo " commit:207bgfaa897ertg548errv5d5f4e" e digitar assim 
        -->  git show 207bgfaa897ertg548errv5d5f4e  e tecle enter, ela irá mostrar várias informações que estão armazenadas neste hash!
        
 7 - Resetar os arquivos que deseja
    - digite  --> git checkout    (antes de digitar o git add!!!)
              assim ele retorna o arquivo para antes da edição.
              
              --> git reset HEAD oDocumentoQueQuiserAlterar.AextensaoQueSalvouoDoc
                ai ele vai resetar as alterações que estivirem naquele cabeçalho , pois você especificou (HEAD), logo em seguida vai
                aparecer assim abaixo desta linha:
                          
                          Unstaged changes after reset:
                          M     oDocumentoQueQuiserAlterar.AextensaoQueSalvouoDoc
             
             --> tem um comando que mostra diferenças no commit, basta estar na branch desejada,  e digitar  --> git diff
             
             --> para commitar tudo com apenas uma linha de comando, digite --> git commit -am "mensagem que quiser"
                o "-am" neste comando quer dizer, comita tudo o que tiver modified com esta mensagem.
             
             -->para desfazer o commit você tem 3 comandos diferentes:
                -- soft : vai pegar as modificações, desfaz o commit, mas o arquivo vai estar pronto para ser comitado novamente,
                          ficando novamente no estado de staged
                          
                -- mixed : defaz o commit também, volta ao estado modified 
                
                --hard : ele simplesmente ignora tudo o que foi feito no commit, como se nada estivesse acontecido.
                
                Como que faz o reset? basta digitar o comando --> git reset --o estilo de reset que quiser
                
             OBS: digamos que você queira voltar ao commit, precisa voltar um antes, ou seja, temos 3 commits, quero voltar ao 2 
             seleciono o 2, e não o 3.
             O "git reset" altera o histórico de logs que você já deu push! Então, ele deve ser usado com cuidado, e pode dar muita
             confusão nos históricos!!!
             
8 - Trabalhando com repositório remoto!
    
    Neste estudo, será feito usando o GitHub mesmo okay? 
    
    Para criar um repositório aqui no GitHub, basta criar uma conta, após isso, note que tem um sinal de + no canto superior direito da tela, lá mesmo terá a opção de "Novo Repositório", clique nela, você será direcionado para a janela onde deverá nomear este repositório, e escolher se quer que ele seja público ou privado, e escolher se quer iniciar já com o Readme.md (que pode ser útil em alguns casos, em outros nem tanto), ao finalizar só clicar em "criar repositório" (ou "create repository"), pronto, seu repositório está criado!
   
   Okay, mas como o GitHub sabe quem está fazendo os commits?
      - Ele usa um protocolo chamado SSH que serve para autenticar usuário remoto ao servidor, é baseado em chaves, sendo uma pública e outra privada, onde enviamos a chave pública pra o GitHub e a nossa máquina abre atrasvés do privado. 
      Para mais informações e como usar essa ferramente de segurança em seus repositórios, acesse esse link e saiba mais :
          https://help.github.com/en/articles/connecting-to-github-with-ssh
          

9 - Primeiros passos no Github
    Assim que você cria o repositório, ele já te dá alguns primeiros passo, mas se quiser colocar o repositório que já tem, ele te dará 
    a seguinte opção -- > 
            git remote add origin git@github.com:pessoacoder/github-course.git
            -- > E o que isso tudo quer dizer?
            -- >Ele vai adicionar um repositório remoto ("git remote add")
              , com o nome origin ("origin") (nome default, pode ser qualquer nome, até banana! rs), 
               depois passo o endereço do meu repositório do git ("git@github.com:pessoacoder/github-course.git"). 
            Pronto só dar enter!
            
            Como saber se realmente esse repositório foi criado?
            digite no terminal : 
            git remote   , e dê Enter, ele deverá aparecer algo como assim :
            origin
            
            Se quiser saber o endereço dele, digite --> git remote -v
            
            E pro fim, vamos fazer o push! O push envia os arquivos que tenho, todos os logs, tudo o que tenho para o repositório
            digite :  git push -u origin master  , ou seja ele vem do master e vai para o origin!
            pronto, só dar enter que ele envia tudo e faz a conexão.
            
10 - Enviando as mudanças para o repositório remoto
          
          Basicamente é só depois de dar o commit nas mudanças, basta digitar novamente o mesmo comando mencionado acima!
          Lembrando sempre que você deve digitar, sempre PARA ONDE VAI  e DE ONDE VEM, nesta ordem.
          Como provavelmente você está seguindo os passos, basta modificar alguma coisa no seu arquivo, ao final, commit (git commit -am "mensagem"), e após terminar de fazer isso digitar --> git push -u origin master  , pronto seu commit já está no seu repositório remoto!
          
11- Clonando os repositórios 
        
          Para isto tem um comando  -->  git clone e o link que você copiar do repositório no Github
          
         O link costuma ficar do lado direito, quando você acessa um repositório, pode reparar que do lado direito, existirá um opção de 
         clonar repositório, basta escolher se quer só clonar ele, se quer usar o ssh, e clicar em copiar link, pronto!
         
         Quando você voltar ao terminal, lembre-se de sair primeiro do repositório atual, e depois clonar este okay? Senão pode acabar
         dando alguns erros e não seria legal certo?
        
        E como funciona o clone? Ele literalmente clona tudo o que tem neste repositório para sua máquina! Incrível né? Assim você pode
        acessar seu repositório indiferente do local que for trabalhar!
        
12 - O que é Fork?
   - Fork no git, é como criar uma branch ? Não, pois no fork vc literalmente terá uma cópia de tudo o que tem naquele repositório pra você, assim você poderá contribuir para aquele projeto,mesmo que ele não seja seu, basta apenas ele estar liberado em modo público para que isso seja possivel.
   Para você forka um projeto, o git tem um "step by step" bem explicativo e ilustrativo, vou deixar o link aqui para caso queiram consultar como fazer ok? --> https://help.github.com/en/articles/fork-a-repo
  
13 - Branch
 Acima mencionei sobre criar uma branch certo? Poi bem, imagine que o repositório é uma árvore, as branchs são as ramificações dela, ou seja, quando ela foi criada, ela terá uma "cópia" daquele repositório para que você possa contribuir ,alterar e salvar, sem afetar sua master, seu principal. Mas você deve estar se questionando qual a diferença dela pra fork, é bem clara, o fork é uma copia onde só você pode mexer e contribuir depois que o "dono" da master aceitar; já o branch não, você estará contribuindo indiretamente para o projeto, outros poderão mexer na mesma branch que você sem afetar a master, e no fim, nem precisa manter a branch,pode apagar ela depois de mergiar suas alterações para as master.
       o comando para cria uma branch é --> git checkout -b NomeDaBranch e enter
       acessar a branch é --> git checkout NomeDaBranch
       deletar um branch é --> git checkout -D NomeDaBranch  , uma observação é digitar d maiúsculo mesmo okay?
       para ver as branchs que existem no repositório é --> git branch

14 - Unir as branchs
      Bom unir é fazer um merge, okay mas o que é um merge né?
      Pense no seguinte um repositorio tem um master e esse é uma linha continua, e quando criamos uma branch, fazemos uma linha em parelelo com ela, e cada qual proseguiria seu caminho em sua respectiva linha, e quando vamos unir, fazemos um merge, misturaremos as duas linhas. 
      tentarei ilustrar aqui como seria isso
      ---master-----master-------master-----MERGE----master 
                  |---branch---branch------/
                  
      o comando pra isso é, voltar para a master e digitar --> git merge NomeDaBranch
      lembrando que os commits tem que estão todos ok pra fazerem essa junção!
      
      tem outra forma de unir, através do Rebase, porém, isso deixa sua estrutura meio confusa, porem linear, mas para futuras pesquisar pra saber quem fez o que e quando ja não é tão bom.
      mas vou deixar aqui o comando, segue a ideia do merge e no final digite --> git rebase NomeDaBranch
     
15- Criar um gitgnore
    Ele já vem criado se qusier quando cria um repositório aqui no github, mas pode colocar informações para ele e dizer o que quer que ele ignore.
    acesse a branch e crie um arquivo de gitgnore, lembra do comando?
    vamos lá
    git checkout NomeDaBranch
    vi gitgnore
    coloque dentro deste arquivos extensões que quer que ele ignore, e salve, esc + w+ q + enter
    pronto, está criado o seu.
    vou deixar links de templates e collections para seguir exemplos caso queira
    https://github.com/github/gitignore
    https://git-scm.com/docs/gitignore
    
16 - GitStash
    Ele guarda comits que não foram efetivados numa pasta, para que você possa finalizar ele depois.
    comando -->  git stash
    ele volta com o status working
    e quando quiser aplicar as mudanças armazedas digite --> git stash apply
    pra saber as stash que tem digite --> git stash list
    pra apagar suas alterações guardadas --> git stash clear
    comando muito bom pra quando precisar dar um pull e voltar a fazer depois.

17 - Criar siglas de atalhos para comandos 
    Seria maravilhoso poder otimizar o tempo digitando em vez de status apenas o s não seria?
    então vamos ao step by step
    1 --> git config --global alias.s status
    aqui estou pedindo pro git criar um atalho global onde s será status
    2 pra testar só digitar --> git status e ver ele te dando o status de seu repositório.
    
18 - Tag
    Isso mesmo, para cada commit finalizado vocÊ pode colocar tags, pra identificar a versão do seu código, e facilitar pra quem for baixar as releases direto do teu github, como assim? No seu github , na aba repositorio, quando você entra num deles, é possível ver as tags, isso ajuda a identificar mais facilmente a versão que esta ou a modificação feita, alem dele armazenar também informações como quem fez o commit, quando e deixar links pra baixar seu code ali mesmo.
    o comando pra é , após dar o commit, digite --> git tag -a 1.0 -m "Mensagem que quiser"
    aqui estou mandando o git, criar a tag com o numero 1.0 (pode ser qlqr número) com a mensagem "Mensagem que quiser"
    
    pronto, se você entrar no seu repositório, e entrar na aba tag, vai ver que tem essa tag, clicando nela, voc~e poderá acessar todas aquelas informações que mencionei acima e mais algumas.
    
bom esse foi um resumo dos meus estudos, espero que tenha ajudado você de alguma forma.
