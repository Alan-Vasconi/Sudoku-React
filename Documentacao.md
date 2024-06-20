# Documentação da API - Extreme Sudoku

## Sumário
- [Frontend](#frontend)
- [Backend](#backend)
- [Autenticação](#autenticação)
- [Jogo de Sudoku](#jogo-de-sudoku)
- [Observações](#observações)
- [Estado de Autenticação no Cliente](#estado-de-autenticação-no-cliente)

## Frontend
O frontend é a interface do usuário onde você interage com o jogo de Sudoku. Ele é construído usando React e pode ser acessado através da seguinte URL:

### URL do Frontend
- **URL:** `http://localhost:3000/sudoku`
  - Esta URL carrega a interface do jogo de Sudoku onde você pode jogar e interagir com o jogo.

### Páginas do Frontend

#### Página Home
- **Caminho:** `/`
- **Descrição:** Página inicial com opções de navegação para Login, Registro e jogar Sudoku.
- **Componentes:** `Home.js`
- **Estilos:** `Home.css`

#### Página de Login
- **Caminho:** `/login`
- **Descrição:** Página onde os usuários podem fazer login com seu nome de usuário e senha.
- **Componentes:** `Login.js`
- **Estilos:** `Login.css`
- **Funcionalidades Adicionais:** Exibe mensagens de erro quando as credenciais são inválidas e permite navegar para a página de registro.

#### Página de Registro
- **Caminho:** `/register`
- **Descrição:** Página onde novos usuários podem se registrar criando um nome de usuário e senha.
- **Componentes:** `Register.js`
- **Estilos:** `Register.css`
- **Funcionalidades Adicionais:** Exibe mensagens de erro quando há problemas no registro e permite navegar para a página de login.

#### Página de Sudoku
- **Caminho:** `/sudoku`
- **Descrição:** Página principal do jogo de Sudoku, onde os usuários autenticados podem jogar o jogo.
- **Componentes:** `Sudoku.js`, `SudokuGrid.js`
- **Estilos:** `Sudoku.css`, `SudokuGrid.css`
- **Funcionalidades Adicionais:** Validação em tempo real das entradas do usuário, destacando células inválidas e mostrando mensagens de erro e pontuação.

### Alterações Visuais de Acordo com o Jogo
- **Células Originais:** Estão em uma cor diferente e são somente leitura.
- **Células Inválidas:** São destacadas em vermelho quando uma entrada inválida é detectada.
- **Células Diferentes:** Destacadas em uma cor específica para mostrar que o valor foi alterado pelo usuário.
- **Destacar Células:** Quando uma célula recebe foco, todas as células na mesma linha e coluna são destacadas.

## Backend
O backend fornece os dados e lida com a lógica de negócios, como autenticação de usuários e validação do tabuleiro de Sudoku. O frontend faz requisições HTTP para o backend para obter dados e executar ações. O backend é construído usando Node.js e Express.

### Endpoints da API

#### Autenticação

##### POST /api/auth/register
Responsável por registrar um novo usuário.

- **URL:** `/api/auth/register`
- **Método:** `POST`
- **Cabeçalhos:** Nenhum
- **Parâmetros do corpo da solicitação:**
  - `username` (string) - Nome de usuário.
  - `password` (string) - Senha.
- **Respostas:**
  - **201:** Usuário registrado com sucesso.
    ```json
    {
      "message": "User registered"
    }
    ```
  - **400:** Erro na solicitação (por exemplo, usuário já existe).
    ```json
    {
      "error": "Error message"
    }
    ```

##### POST /api/auth/login
Responsável por autenticar um usuário e retornar um token JWT.

- **URL:** `/api/auth/login`
- **Método:** `POST`
- **Cabeçalhos:** Nenhum
- **Parâmetros do corpo da solicitação:**
  - `username` (string) - Nome de usuário.
  - `password` (string) - Senha.
- **Respostas:**
  - **200:** Token JWT.
    ```json
    {
      "token": "JWT token"
    }
    ```
  - **401:** Credenciais inválidas.
    ```json
    {
      "message": "Invalid credentials"
    }
    ```

### Jogo de Sudoku

#### GET /api/sudoku/puzzle
Retorna um tabuleiro de Sudoku inicial.

- **URL:** `/api/sudoku/puzzle`
- **Método:** `GET`
- **Cabeçalhos:**
  - `Authorization`: `Bearer {token}`
- **Parâmetros da solicitação:** Nenhum
- **Respostas:**
  - **200:** Tabuleiro de Sudoku.
    ```json
    {
      "board": [
        [5, 3, 0, 0, 7, 0, 0, 0, 0],
        [6, 0, 0, 1, 9, 5, 0, 0, 0],
        [0, 9, 8, 0, 0, 0, 0, 6, 0],
        [8, 0, 0, 0, 6, 0, 0, 0, 3],
        [4, 0, 0, 8, 0, 3, 0, 0, 1],
        [7, 0, 0, 0, 2, 0, 0, 0, 6],
        [0, 6, 0, 0, 0, 0, 2, 8, 0],
        [0, 0, 0, 4, 1, 9, 0, 0, 5],
        [0, 0, 0, 0, 8, 0, 0, 7, 9]
      ]
    }
    ```

#### POST /api/sudoku/validate
Responsável por validar o tabuleiro atual de Sudoku em tempo real conforme o usuário digita.

- **URL:** `/api/sudoku/validate`
- **Método:** `POST`
- **Cabeçalhos:**
  - `Authorization`: `Bearer {token}`
- **Parâmetros do corpo da solicitação:**
  - `board` (array) - Tabuleiro de Sudoku.
    ```json
    {
      "board": [
        [5, 3, 0, 0, 7, 0, 0, 0, 0],
        [6, 0, 0, 1, 9, 5, 0, 0, 0],
        [0, 9, 8, 0, 0, 0, 0, 6, 0],
        [8, 0, 0, 0, 6, 0, 0, 0, 3],
        [4, 0, 0, 8, 0, 3, 0, 0, 1],
        [7, 0, 0, 0, 2, 0, 0, 0, 6],
        [0, 6, 0, 0, 0, 0, 2, 8, 0],
        [0, 0, 0, 4, 1, 9, 0, 0, 5],
        [0, 0, 0, 0, 8, 0, 0, 7, 9]
      ]
    }
    ```
- **Respostas:**
  - **200:** Resultado da validação.
    - Se o tabuleiro for válido:
      ```json
      {
        "valid": true
      }
      ```
    - Se o tabuleiro for inválido:
      ```json
      {
        "valid": false,
        "invalidCells": [
          [0, 2],
          [1, 1]
        ]
      }
      ```

### Observações

- **Autenticação JWT**:
  - Todos os endpoints protegidos requerem o cabeçalho `Authorization` com o token JWT.
  - O formato do cabeçalho é `Authorization: Bearer {token}`.

- **Validação em Tempo Real**:
  - A validação do tabuleiro de Sudoku é realizada continuamente conforme o usuário digita, enviando o estado atual do tabuleiro para o endpoint `/api/sudoku/validate`.

- **Rota do Jogo**:
  - O jogo de Sudoku está acessível no caminho `http://localhost:3000/sudoku`.

## Estado de Autenticação no Cliente

- O cliente gerencia o estado de autenticação usando React Context API.
- O `AuthContext` é utilizado para fornecer funções de `login` e `logout`, além do estado de autenticação (`authState`).
- **Login**: Armazena o token JWT no `localStorage` e atualiza o estado de autenticação.
- **Logout**: Remove o token JWT do `localStorage` e atualiza o estado de autenticação.
