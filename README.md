# Exemplo de Design de Arquitetura

<div align="center">
<sup></a>Figura 01 - Arquitetura da solução com padrão MVC
<br>
<img src = "arquiteturaSolucao.drawio.png">
<br>
</div>
<br>


# Template Readme para Arquitetura MVC em Markdown
- Nome do Projeto: TechFlex
- Descrição: O objetivo do projeto é realizar uma aplicação web que auxilie no processo da simulação de negócios internacional CESIM Global Challenge. A competição tem como principal empecilho os problemas acarretados pela dificuldade de integração entre diferentes culturas, que acarreta em dificuldades de colaboração e comunicação.
- Arquitetura: MVC (Model-View-Controller)
- Ferramenta de Diagramação: draw.io

### Modelos (Models):
*Users:* Relacionado ao gerenciamento das informações pessoais dos usuários<br>
*Comment:* Relacionado ao gerenciamento dos comentários<br>
*Forms:* Relacionado ao gerenciamento das respostas dos formulários<br>
*Files:* Relacionado ao gerenciamento dos arquivos<br>
- Users <br>
*nationality*: A nacionalidade do usuário. <br>
*name*: O nome completo do usuário. <br>
*userID*: Um identificador único para cada usuário. <br>
*timezone*: O fuso horário do usuário. <br>
*email*: O endereço de e-mail do usuário. <br>
*password*: A senha do usuário. <br>
*status*: O status do usuário. <br>
*age*: A idade do usuário. <br>
*gender*: O gênero do usuário. <br>
*curiosity*: Informações ou fatos curiosos sobre o usuário. <br>

- Comment <br>
*text*: O conteúdo do comentário. <br>
*name*: Nome do usuário que postou o comentário. <br>
*datetime*: Data e hora em que o comentário foi postado. <br>
*textID*: Um identificador único para cada comentário. <br>
*userID*: Um identificador único para cada usuário. <br>

- Forms <br>
*formID*: Um identificador único para cada formulário. <br>
*datetime*: Data e hora em que o formulário foi preenchido. <br>
*questionsCommunication*: Respostas relacionadas a questões de comunicação. <br>
*questionsCollaboration*: Respostas relacionadas a questões de colaboração. <br>
*questionsAvailability*: Respostas relacionadas a questões de disponibilidade. <br>
*questionsCriticalThinking*: Respostas relacionadas a questões de pensamento crítico. <br>
*userID*: Um identificador único para cada usuário. <br>

- Files <br>
*file*: O arquivo que será carregado ou baixado. <br>
*fileID*: Um identificador único para cada arquivo. <br>
*datetime*: Data e hora em que o arquivo foi carregado. <br>
*userID*: Um identificador único para cada usuário. <br>

<br>

&nbsp;&nbsp;&nbsp;&nbsp;A entidade users se relaciona com todas as outras pelo fato de que em forms, comment e files, é necessário o userID, o identificador do usuário, para registrar as ações realizadas por cada usuário

### Controladores (Controllers):
*Users*: Gerencia ações relacionadas aos usuários, como Cadastro, Avaliação, Modificação de Informações, Busca, Login e Logout.
<br>
*Comment*: Controla a lógica para Gravar, Deletar, Editar e Listar comentários.
<br>
*Forms*: Gerencia a gravação, exclusão, edição e listagem dos dados dos formulários.
<br>
*Files*: Relacionado às operações de Baixar, Carregar, Buscar, Exclusão e Listagem de arquivos.

- Users Controller:<br>
Register: Cadastra informações de um novo usuário.<br>
Parâmetros de entrada: (nationality, name, email, password).<br>
ModifyInformation: Atualiza as informações de um usuário existente.<br>
Parâmetros de entrada: (id, name, timezone, email, password, status, age, gender, curiosity).<br>
Search: Busca usuários baseados em nome ou nacionalidade.<br>
Parâmetros de entrada: (name, nationality).<br>
Login: Autentica um usuário.<br>
Parâmetros de entrada: (email, password)<br>
Logout: Encerra a sessão de um usuário autenticado.<br>
Parâmetros de entrada: (userID).<br>

- Comment Controller:<br>
Save: Salva um novo comentário.<br>
Parâmetros de entrada: (text, datetime)<br>
Delete: Remove um comentário.<br>
Edit: Atualiza um comentário existente.<br>
Parâmetros de entrada: (id, text).<br>
List: Lista todos os comentários.<br>
Parâmetros de entrada: Nenhum.<br>
Saída: Lista de todos os comentários.<br>

- Forms Controller:<br>
Save: Salva respostas de um formulário.<br>
Parâmetros de entrada: questionsCommunication, questionsCollaboration, questionsAvailability, questionsCriticalThinking<br>
Delete: Exclui um formulário com base no ID.<br>
Parâmetros de entrada: formID.<br>
List: Lista todos os formulários preenchidos.<br>
Parâmetros de entrada: Nenhum.<br>
Saída: Lista de formulários preenchidos.<br>

- Files Controller:<br>
Upload: Carrega um novo arquivo.<br>
Parâmetros de entrada: file.<br>
Download: Inicia o download de um arquivo com base no ID.<br>
Parâmetros de entrada: fileID.<br>
Delete: Remove um arquivo com base no ID.<br>
Parâmetros de entrada: fileID.<br>
Search: Busca usuários baseados arquivo ou usuário.<br>
Parâmetros de entrada: (fileID, name).<br>
List: Lista todos os documentos.<br>
Parâmetros de entrada: Nenhum.<br>
Saída: Lista de documentos carregados.<br>


- Interação entre controllers com models e views: Os controllers são os responsáveis pela troca de informações do views com o models, de modo que quando o usuário interage com a View, como um preenchimento de um formulário, essa informação é enviada para o controller, este interpreta a ação e envia para o model. O model executa a lógica de negócios e acessa o banco de dados, podendo enviar ou consulturar informações do banco. Após isso, com os dados recebidos do model, o controller encaminha os dados para a view e assim o usuário recebe uma resposta visual.

### Views (Views):
*Homepage*: Apresenta a página inicial com *Header*, *Form*, *Carousel* e *Footer*.
<br>
*Login*: Contém o *Form* para que os usuários façam login.
<br>
*MainPage*: Mostra a página principal, após o login, com *Header*, *Form* e *Sidebar*.
<br>
*Evaluation*: Exibe a página de avaliações com *Header*, *Form*, *Sidebar* e *Comments section*.
<br>
*Tutor's View*: Oferece uma visão específica para tutores com *Header*, *Form*, *Sidebar* e *Dropdown* para opções adicionais.

- *Header*: É a parte superior da página, que contém a logo, o menu de navegação principal e outros elementos importantes.
- *Sidebar*: Uma área na lateral superior da página que quando o usuário clicar pode ter acesso à links que levam a outras telas do site.
- *Footer*: A parte inferior da página, em que haverão links de redirecionamento para outras telas da aplicação web e créditos.
- *Form*: Áreas onde os usuários podem inserir dados, como formulários de inscrição, formulários de contato, clicar em botões de interação, etc.
- *Carousel*: Elementos de interface de usuário que permitem que o conteúdo, como imagens, seja exibido em uma sequência de slides.
- *Comments section*: Uma área interativa na página onde os usuários podem postar comentários ou feedbacks.
- *Dropdown*: Um elemento de interface que permite aos usuários escolher uma opção de uma lista pré-definida. É útil para economizar espaço na tela, pois as opções ficam ocultas até que o usuário interaja com o componente.


### Infraestrutura:

A arquitetura é sustentada por servidores web que hospedam a aplicação MVC e servidores de banco de dados que armazenam as informações dos Models. Os servidores web executam a lógica dos Controllers e renderizam as Views, enquanto os servidores de banco de dados são responsáveis por guardar e gerenciar os dados dos Models. Além disso, é utilizado o Sails.js para implementar o padrão de projeto MVC no desenvolvimento do projeto.



### Justifique as escolhas feitas e como elas impactam o projeto.
#### Implicações da Arquitetura:
A escolha do MVC se dá pela separação clara de componentes, de front-end e back-end, o que facilita a manutenção e a expansão do sistema, pois é uma estrutura organizada que possibilita que diversos desenvolvedores trabalhem simultaneamente em diferentes funções. Os Controllers agem como intermediários entre Views e Models, o que aumenta a modularidade e facilita testes individuais de componentes. A infraestrutura suporta escalabilidade, dado que a lógica de negócios e a interface do usuário podem ser escaladas de maneira independente.

### Recursos Adicionais:
- Documentação do Sails.js: https://github.com/balderdashy/sails
- Tutorial do draw.io: https://m.youtube.com/watch?v=w3zm-wbmlpc
- Exemplos de diagramas MVC: https://www.lucidchart.com/pages/templates

