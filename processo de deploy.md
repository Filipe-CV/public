
### Gerar uma versão do projeto [^1]

#### processo manual
  
 <!--  > antes parar o tomcat -->

1. configurar o _persistence.xml_ [^2]  
   ***
   1.1. tirando a variável do prefixo `${pcr-urbanistico.data-source-prefix}`  

      [desenvolvimento (local)] **de** (linha 4):
      ```xml

         <non-jta-data-source>java:${pcr-urbanistico.data-source-prefix}${pcr-urbanistico.data-source-name}</non-jta-data-source>

      ```
      [homologação] **para**:
      ```xml

         <non-jta-data-source>java:${pcr-urbanistico.data-source-name}</non-jta-data-source>

      ```
  
   1.2. Salva a alteração  
   ***
   
1. configurar o _context.xml_ [^3]  

      > estrutura de conexão para apontar para o banco em homologação

      [desenvolvimento (local)] **de** (linha 37 a 40):
      ```xml

         url="jdbc:postgresql://127.0.0.1:5432/pcr-urbanistico"
         username="postgres"
         password="postgres"

      ```
      [homologação] **para**:
      ```xml

         url="jdbc:postgresql://carlosgomesh.recife/dbpopacote_agiles?charSet-UTF-8"
         username="agiles_purbano"
         password="emprel"

      ```
   
   ***

1. `mvn clean install`  pelo projeto pai

   > gera o .war que será enviado para o ambiente de homologação
   >> \[...]\\**pcr-urbanistico-view\target\pcr-urbanistico.war** - destino do .war gerado
   <!-- também é gerado algum .jar, exemplo o pcr-urbanistico-functions-1.0-SNAPSHOT.jar -->
   
   ***

1. Copia **pcr-urbanistico.war** para homologação e, posteriormente, para produção - via **SCP**  

    4.1.  \[...]\\**AgilesConfigs\jboss\functions\lib\pcr-urbanistico-functions-1.0-SNAPSHOT.jar**  
      >  é copiado quando têm-se uma atualização de método na function, não é de "implement", é de novos métodos acrescentados ou até excluídos para não serem mais referenciados
      >> Deste modo é feita para uma atualização "normal". Para um novo processo há passos a mais.

      > _A configuração que define seu local de criação fica no settings.xml do Maven_

1. Renomeação <nome-war>.old
    > _eventualmente renomear  .war  ->  .wardd-mm-aaaa-HHhMMmin.old_

<br></br>
##### Considerações

  > - Homologaçao e produção é o mesmo formanto de deploy. É o mesmo .war que vai para homologação e para produção.  
  > - O deploy para produção é feito pela equipe de suporte (e não pela equipe de desenvolvedores).
  


[^1]: fonte: 'repasseequipebpmagiles on 2020-12-30 00-02.mp4' tempo:21:42
[^2]: localizado no subdiretório:  \[...]\pcr-urbanistico\pcr-urbanistico-model\src\main\resources\META-INF\
[^3]: localizado no subdiretório:  \[...]\pcr-urbanistico\environment\tomcat\
<!-- só conf. local ?! C:\Users\thiagopacheco\Documents\desenvolvimento\bpm\workspace\Servers\Tomcat 6.0 jdk 1.6_26-config\context.xml -->
