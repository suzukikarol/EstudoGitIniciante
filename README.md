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
             
               
     
            
         
