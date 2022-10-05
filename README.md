# Git Flow
## O que é:
É um fluxo de trabalho utilizado por equipes de desenvolvimento para facilitar e auxiliar na organização de versionamento de códigos. Sua utilização é recomendada para projetos que existam uma grande quantidade de pessoas commitando dentro dos repositórios ou para projetos que possuem um ciclo de entrega agendado. 
## Como funciona e quais os branches do fluxo Git Flow:
No Git Flow temos dois branches principais: Master/Main e Develop e três  branches de suporte: Feature, Release e Hotfix. Cada uma com suas regras, ele define os papéis de cada branch e como eles devem interagir.

 - Main: Aqui é onde temos todo o código de produção. Todas as novas funcionalidades que estamos desenvolvendo, em algum momento, serão mescladas ou associadas a Main.
 - Develop: Aqui é onde fica o código do nosso próximo deploy. Isso significa que, como recursos ou funcionalidades, será finalizado e adicionado nesta ramificação para posteriormente passar por mais uma etapa antes de ser associado a uma Main.
 - Feature – são branches para o desenvolvimento de uma funcionalidade específica. Elas devem ter o nome iniciado por feature, por exemplo, “feature / payment-system”. É importante saber que essas features branches são criadas sempre a partir da branch Develop. Portanto, quando finalizada, ela é removida após realizar o merge com a Branch Develop.
 - Release – Serve como ponte para fazer o merge da Develop para a Main. Funciona como ambiente de homologação e é removida após realizar os testes e do merge com a Main. Caso haja alguma alteração, ela também deve ser sincronizada com a Develop.
 - Hotfix – Uma branch criada a partir da Main para realizar correções encontradas no sistema em produção. Quando concluída ela é excluída após realizar o merge com a Branch Main e Develop.
 
Na imagem a seguir, vemos a estrutura de como é o fluxo do Git Flow:

![gitflow](gitflow.jpeg)

## Principais comandos do Git Flow:

### Init

`git flow init`

É o comando inicial do Git Flow e serve para configurar o repositório com as branches do fluxo padrão. 

### Feature

Dentro desse comando temos algumas ramificações possíveis, como por exemplo:

`start nome_feature`
  
Comando que inicia uma nova feature, nela temos a criação de uma branch com a nomenclatura feature/nome_feature.

`finish nome_feature`
  
Comando para encerrar uma feature anteriormente criada, além disso será feito um merge para a branch Develop.

`publish nome_feature`
  
Se você está trabalhando em equipe e deseja compartilhar a sua nova funcionalidade, esse comando publica no servidor remoto que está configurado no seu Git local.

`pull nome_feature`
  
Ao contrário da anterior, essa serve para obter uma feature do servidor remoto.

### Release

Com a terminologia parecida, veremos os comandos referentes ao lançamento:

`start nome_release [BASE]`  

Utilize esse comando para iniciar uma versão baseada na branch de desenvolvimento, aqui você pode passar opcionalmente o código de algum commit para usar como base.

`publish nome_release`
   
É aconselhável publicar a branch de release após criá-la para permitir commits de outras pessoas desenvolvedoras. O comando é semelhante à publicação de uma nova feature.

`release track nome_release`
  
Novamente, se você quiser acompanhar alguma versão remota da release, existe esse comando.

`finish nome_release`

Com esse comando você finaliza e cria uma nova versão, logo em seguida é executada uma série de ações:

 - junta a branch na Main/Master;
 - cria uma tag com o nome da branch;
 - também junta a branch com a Develop;
 - por último, apaga a própria branch.

### Hotfix

Por fim temos os comandos da Hotfix:

`hotfix start nome_hotfix [BASENAME]` 

A partir do último commit da branch Main/Master cria-se uma branch com a nomenclatura de hotfix/nome_hotfix. É obrigatório que seja passado o nome da hotfix e opcionalmente você pode passar um BASENAME.

`hotfix finish nome_hotfix`

Temos novamente o comando para a finalização da hotfix. Quando terminado o processo final vemos que é feito uma mesclagem da hotfix nas branches main/master e develop e também temos a criação de uma etiqueta na main/master.

 ### Comentários finais:
 - O Git Flow deixa mais organizado e seguro todo o processo de criação de novas Features e Hotfixes dentro do código, evitando perder alguma informação importante.
 - Recomendado para aqueles projetos que vão ganhando corpo ou que precisam sofrer novas atualizações constantemente. Ou ainda, também, quando existe uma grande quantidade de pessoas “commitando” dentro de um repositório.

Segue abaixo link de um vídeo explicativo sobre o tema:
* [Git Flow // Dicionário do Programador](https://www.youtube.com/watch?v=oweffeS8TRc)