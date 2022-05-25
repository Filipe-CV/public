 ## [Jenkins](http://jenkins.recife)

  - [ ] 1. implementar a integração de código
    - [ ] 1.1. especificação do repositório SVN;
    - [ ] 1.2. configuração Maven do repositório (remoto) de depedências específicas do projeto - Archiva;
    - [ ] 1.3. configurações relacionadas ao banco de dados;  
    - [ ] 1.4. *.properties ?
      - [ ] 1.4.1. <!-- C:\Users\thiagopacheco\Documents\desenvolvimento\bpm\ --> AgilesConfigs\jboss\config\urbanistico.properties
      - [ ] 1.4.2. <nomedoprocesso>.properties
        > Cada processo tem um arquivo properties correspondente.
        >> para facilitar no momento de modificar.  
     <br>
  
    |sistemas\servidores|configuração|homologação|produção|
    |--|:--:|:--:|:--:|
    |[Archiva](http://capibaribe.recife:8090/repository/internal)|settings.xml [^ 1]| - | - |
    |de Processos| - | root@pradoh.recife | jboss@prado.recife | <--! sanchod.recife -->
    |do Ágiles| - | root@joqueihl.recife | joqueihl.recife |
    <!-- |do BD| - | carlosgomesh.recife || -->
    <!-- |ass. digi.| - | root@coleiro.recife || -->
  
  
  - [ ] 2. testar
  - [ ] 3. relatar resultado / relatar o caminho encontrado
  <br></br>
    > - [ ] vê se é necessário configurar notificações por email
    
    
    [^1]: localizado no subdiretório: ...\apache-maven-3.0.1\conf
<!-- + //informações login e senha (e está fora do workspace) C:\Users\thiagopacheco\Documents\desenvolvimento\bpm\settings.xml -->
