# Projeto MVC em PHP

Este é um projeto PHP que utiliza o padrão de projeto MVC (Model-View-Controller) para criar um aplicativo simples de cadastro de estudantes e professores.

## Estrutura do Projeto

O projeto está organizado da seguinte forma:

- `controller`: Contém os controladores PHP para lidar com as solicitações do usuário.
- `model`: Contém os modelos PHP que interagem com o banco de dados.
- `view`: Contém as visualizações HTML para a interface do usuário.
- `database`: Contém a classe `Database` para conexão com o banco de dados.
- `public`: Contém arquivos públicos, como CSS e JavaScript.
- `index.php`: O arquivo principal que direciona as solicitações com base nas URLs.

## Roteamento

O arquivo `index.php` é responsável pelo roteamento das solicitações com base nos parâmetros `controller` e `acao` da URL. Aqui está um exemplo de como as URLs são roteadas:

- `/index.php?controller=Estudante&acao=listar`: Lista todos os estudantes.
- `/index.php?controller=Estudante&acao=salvar`: Exibe um formulário para salvar um novo estudante.
- `/index.php?controller=Estudante&acao=editar&id=1`: Exibe um formulário para editar um estudante com ID 1.

## Uso

Para usar o aplicativo, você pode acessar as URLs correspondentes aos controladores e ações desejados. Certifique-se de configurar corretamente o ambiente de desenvolvimento, incluindo um servidor web e um banco de dados.

## Tecnologias Utilizadas

- PHP
- MySQL (ou outro banco de dados de sua escolha)
- Bootstrap (para a interface do usuário)
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Estudante Controller

Este é um controlador  para gerenciar operações relacionadas a estudantes. Ele se conecta ao modelo `EstudanteModel` para realizar ações como listar, salvar, editar e excluir estudantes.

## Uso
- Para listar todos os estudantes:

  ```php
  http://localhost:8081/estudante/?controller=Estudante&acao=listar
  
Para criar um novo estudante, vá para:
http://localhost:8081/estudante/?controller=Estudante&acao=salvar

Para editar um estudante existente, vá para:
http://localhost:8081/estudante/?controller=Estudante&acao=editar&id=<ID_DO_ESTUDANTE>

Para excluir um estudante existente, vá para:
http://localhost:8081/estudante/?controller=Estudante&acao=excluir&id=<ID_DO_ESTUDANTE>

Lembre-se de substituir `<ID_DO_ESTUDANTE>` pelos identificadores reais. 

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Professor Controller

Este é um controlador para gerenciar operações relacionadas a professores. Ele se conecta ao modelo `ProfessorModel` para realizar ações como listar, salvar, editar e excluir professores.

## Uso

- Para listar todos os professores:
http://localhost:8081/professor/?controller=Professor&acao=listar

- Para criar um novo professor, vá para:
http://localhost:8081/professor/?controller=Professor&acao=salvar

- Para editar um professor existente, vá para:
http://localhost:8081/professor/?controller=Professor&acao=editar&id=<ID_DO_PROFESSOR>

- Para excluir um professor existente, vá para:
http://localhost:8081/professor/?controller=Professor&acao=excluir&id=<ID_DO_PROFESSOR>

**Lembre-se de substituir <ID_DO_PROFESSOR> pelos identificadores reais dos professores**

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Classe de Banco de Dados (Database)

Esta é uma classe  para lidar com conexões e operações em um banco de dados MySQL. Ela encapsula a funcionalidade de abrir e fechar conexões, executar consultas SELECT e realizar inserções.

## Uso

```php
// Criando uma instância da classe Database
$database = new Database();

// Abrindo uma conexão com o banco de dados
$database->openConnection();

// Executando uma consulta SELECT
$sql = "SELECT * FROM tabela";
$resultados = $database->executeSelect($sql);

// Inserindo dados no banco de dados
$sql = "INSERT INTO tabela (campo1, campo2) VALUES ('valor1', 'valor2')";
$database->insert($sql);

// Fechando a conexão com o banco de dados
$database->closeConnection();
Construtor
A classe Database possui um construtor que define os parâmetros de conexão com o banco de dados, como servidor, nome de usuário, senha e nome do banco de dados. Lembre-se de ajustar esses valores de acordo com a sua configuração específica.

Métodos Principais
openConnection(): Este método abre uma conexão com o banco de dados MySQL usando as informações fornecidas no construtor.

closeConnection(): Este método fecha a conexão com o banco de dados.

executeSelect(string $sql): Este método executa uma consulta SELECT no banco de dados e retorna os resultados em um array associativo.

insert(string $sql): Este método executa uma inserção de dados no banco de dados.

Exemplo de Uso

$database = new Database();
$database->openConnection();

$sql = "SELECT * FROM alunos";
$resultados = $database->executeSelect($sql);

foreach ($resultados as $aluno) {
    echo "Nome: " . $aluno['nome'] . "<br>";
}

$database->closeConnection();



Lembre-se de substituir as informações específicas, como o nome da tabela, os campos e os valores, de acordo com o seu projeto. Este é um formato de README.md que você pode usar para documentar sua classe `Database` no GitHub.```

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Classe EstudanteModel

Esta é uma classe  que representa o modelo para a entidade "Estudante". Ela lida com operações relacionadas a estudantes, como salvar, listar, editar e excluir.

## Uso

Primeiro, crie uma instância da classe `EstudanteModel`:

```php
$estudante = new EstudanteModel();
Listar Estudantes


$estudantes = $estudante->listarModel();
Salvar um Novo Estudante


$nome = "Nome do Estudante";
$idade = 20;
$estudante->salvarModel($nome, $idade);
Buscar Estudante pelo ID


$id = 1;
$estudanteEncontrado = $estudante->buscarPeloId($id);
Atualizar um Estudante


$id = 1;
$novoNome = "Novo Nome";
$novaIdade = 25;
$estudante->atualizarModel($id, $novoNome, $novaIdade);
Excluir um Estudante


$id = 1;
$estudante->excluirModel($id);

Construtor
A classe EstudanteModel possui um construtor que cria uma instância da classe Database para interagir com o banco de dados. Certifique-se de que a configuração da classe Database esteja correta.

Métodos Principais
listarModel(): Retorna um array com todos os estudantes no banco de dados.

salvarModel(string $nome, int $idade): Insere um novo estudante no banco de dados.

buscarPeloId(int $id): Busca um estudante pelo ID no banco de dados e retorna um array associativo com os dados do estudante.

atualizarModel(int $id, string $nome, int $idade): Atualiza os dados de um estudante no banco de dados com base no ID.

excluirModel(int $id): Exclui um estudante do banco de dados com base no ID.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Classe ProfessorModel

Esta é uma classe  que representa o modelo para a entidade "Professor". Ela lida com operações relacionadas a professores, como salvar, listar, editar e excluir.

## Uso

Primeiro, crie uma instância da classe `ProfessorModel`:

```php
$professor = new ProfessorModel();
Listar Professores


$professores = $professor->listarModel();
Salvar um Novo Professor


$nome = "Nome do Professor";
$idade = 30;
$professor->salvarModel($nome, $idade);
Buscar Professor pelo ID


$id = 1;
$professorEncontrado = $professor->buscarPeloId($id);
Atualizar um Professor


$id = 1;
$novoNome = "Novo Nome";
$novaIdade = 35;
$professor->atualizarModel($id, $novoNome, $novaIdade);
Excluir um Professor


$id = 1;
$professor->excluirModel($id);
Construtor
A classe ProfessorModel possui um construtor que cria uma instância da classe Database para interagir com o banco de dados. Certifique-se de que a configuração da classe Database esteja correta.

Métodos Principais
listarModel(): Retorna um array com todos os professores no banco de dados.

salvarModel(string $nome, int $idade): Insere um novo professor no banco de dados.

buscarPeloId(int $id): Busca um professor pelo ID no banco de dados e retorna um array associativo com os dados do professor.

atualizarModel(int $id, string $nome, int $idade): Atualiza os dados de um professor no banco de dados com base no ID.

excluirModel(int $id): Exclui um professor do banco de dados com base no ID.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Formulário de Cadastro de Estudante

Este é um formulário HTML simples para o cadastro de estudantes. Ele permite inserir o nome e a idade de um estudante e salvar os dados.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Formulário de Edição de Estudante

Este é um formulário HTML simples para a edição de dados de um estudante. Ele permite editar o nome e a idade de um estudante e salvar as alterações.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Lista de Estudantes

Esta é uma página HTML que exibe uma lista de estudantes. Ela inclui informações como nome, idade e ações para editar ou excluir estudantes.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Formulário de Cadastro de Professor

Este é um formulário HTML simples para cadastrar informações de um professor. Ele permite inserir o nome e a idade do professor e salvar os dados.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Formulário de Edição de Professor

Este é um formulário HTML simples para editar as informações de um professor. Ele permite editar o nome e a idade do professor e salvar as alterações.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Lista de Professores

Esta é uma página HTML que exibe uma lista de professores. Você pode ver os detalhes de cada professor, como nome, idade e realizar ações como editar ou excluir.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Página HTML Básica

Esta é uma página HTML simples criada com Bootstrap. Ela inclui um navbar na parte superior.

# Barra de Navegação

Esta é uma barra de navegação responsiva que pode ser usada para navegar em diferentes partes do aplicativo. Ela inclui links para as páginas "Home", "Estudantes" e "Professores", bem como um campo de pesquisa.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

O arquivo index.php é o ponto de entrada principal de um aplicativo web simples em PHP. Ele desempenha um papel fundamental no roteamento das solicitações e na inicialização dos controladores e visualizações apropriados com base nos parâmetros fornecidos na URL.

Constante FOLDER
Descrição: A constante FOLDER é usada para definir o nome da pasta do projeto. Ela é essencial para construir caminhos para os controladores e visualizações.

Utilização: Certifique-se de definir o valor dessa constante de acordo com a estrutura do seu projeto. Por exemplo, se o seu projeto estiver em uma pasta chamada "aula3", defina-a como 'aula3'.

Roteamento de Solicitações
O código a seguir lida com o roteamento das solicitações com base nos parâmetros controller e acao passados pela URL:

if(isset($_GET['controller']) && isset($_GET['acao'])){
    $controller = $_GET['controller'];
    $metodo = $_GET['acao'];
    $controller .= "Controller";

    require_once $_SERVER['DOCUMENT_ROOT'] . '/' . FOLDER . '/controller/'. $controller . '.php';

    $objeto = new $controller();
    $objeto->$metodo();
} else {
    require_once $_SERVER['DOCUMENT_ROOT'] . '/' . FOLDER . '/view/home.php';
}
Verificação de Parâmetros: O código verifica se os parâmetros controller e acao estão definidos na URL.

Construção do Nome do Controlador: Com base nos parâmetros recebidos, o nome do controlador é construído adicionando "Controller" ao final do nome fornecido na URL.

Requerimento do Controlador: O controlador apropriado é requerido com base no nome construído. Certifique-se de que seus controladores estejam localizados na pasta controller do seu projeto.

Criação de uma Instância do Controlador: Uma instância do controlador apropriado é criada com base no nome fornecido na URL.

Chamada da Ação no Controlador: A ação apropriada no controlador é chamada com base no valor do parâmetro acao da URL.

Visualização Padrão: Se os parâmetros controller e acao não estiverem definidos na URL, a visualização home.php é requerida. Certifique-se de que suas visualizações estejam localizadas na pasta view do seu projeto.

Este arquivo principal atua como um roteador simples para direcionar solicitações para os controladores apropriados e exibir as visualizações correspondentes com base nos parâmetros da URL. 

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Requisitos
 7.x
Um servidor web (por exemplo, Apache)
O modelo EstudanteModel deve estar configurado corretamente.
Contribuição
Sinta-se à vontade para contribuir com este projeto. Para colaborar, siga estas etapas:

Faça um fork do repositório.
Clone o repositório forkado para o seu ambiente local.
Crie uma nova branch para a sua contribuição: git checkout -b minha-contribuicao
Faça as alterações desejadas.
Faça commit das suas alterações: git commit -m "Minha contribuição"
Faça push das alterações para a sua branch: git push origin minha-contribuicao
Crie um pull request no repositório original.

Autor
Henrique Valim Ribas

**O README.md serve como uma introdução e guia de uso para este projeto no GitHub.**

