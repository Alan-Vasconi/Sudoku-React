# Manual do Usuário - Extreme Sudoku

## Sumário
1. [Registro](#registro)
2. [Login](#login)
3. [Jogando Sudoku](#jogando-sudoku)
4. [Sair](#sair)
5. [Notas Adicionais](#notas-adicionais)
6. [Iniciando o Ambiente de Desenvolvimento](#iniciando-o-ambiente-de-desenvolvimento)
7. [Configuração do Banco de Dados](#configuração-do-banco-de-dados)
8. [Conclusão](#conclusão)

## Registro

1. **Acessar a Página de Registro**:
   - Na página inicial (`http://localhost:3000`), clique no link "Register".

2. **Preencher o Formulário de Registro**:
   - Insira um nome de usuário no campo "Username".
   - Insira uma senha no campo "Password".

3. **Confirmar Registro**:
   - Clique no botão "Register" para criar sua conta.
   - Se o nome de usuário já estiver em uso ou houver algum erro, uma mensagem de erro será exibida.

## Login

1. **Acessar a Página de Login**:
   - Na página inicial (`http://localhost:3000`), clique no link "Login".

2. **Preencher o Formulário de Login**:
   - Insira seu nome de usuário no campo "Username".
   - Insira sua senha no campo "Password".

3. **Confirmar Login**:
   - Clique no botão "Login" para acessar sua conta.
   - Se as credenciais estiverem incorretas, uma mensagem de erro será exibida.

## Jogando Sudoku

1. **Acessar a Página de Sudoku**:
   - Após o login, clique no link "Play Sudoku" na página inicial ou vá diretamente para `http://localhost:3000/sudoku`.

2. **Entendendo o Tabuleiro de Sudoku**:
   - O tabuleiro de Sudoku consiste em uma grade 9x9, dividida em nove caixas 3x3.
   - Alguns números já estarão preenchidos no tabuleiro (células originais) e não podem ser alterados.

3. **Preenchendo o Tabuleiro**:
   - Clique em uma célula vazia para selecionar e digitar um número de 1 a 9.
   - Pressione "Enter" após digitar um número para validar a entrada.

4. **Validação em Tempo Real**:
   - O tabuleiro será validado em tempo real à medida que você digita.
   - Se um número inválido for inserido (repetido na mesma linha, coluna ou caixa 3x3), a célula será destacada em vermelho.

5. **Destaques de Células**:
   - As células na mesma linha e coluna da célula selecionada serão destacadas.
   - Células com entradas válidas que foram alteradas pelo usuário serão destacadas em uma cor diferente.

6. **Pontuação e Erros**:
   - Você deve preencher todas as células corretamente para completar o tabuleiro e receber uma pontuação.
   - Se cometer 5 erros, o jogo terminará e uma mensagem será exibida.
   - Após completar o tabuleiro, um botão "Reiniciar Tabuleiro" aparecerá para você começar um novo jogo mantendo a pontuação.

## Sair

1. **Logout**:
   - Para sair da sua conta, clique no botão "Logout" localizado na página de Sudoku.
   - Você será redirecionado para a página inicial (`http://localhost:3000`).

## Notas Adicionais

- **Navegação Entre Páginas**:
  - Da página de Login, você pode navegar para a página de Registro clicando no link "Register" e vice-versa clicando no link "Login".

- **Mensagens de Erro**:
  - Durante o registro e login, mensagens de erro específicas serão exibidas caso ocorra algum problema, como usuário já existente ou credenciais inválidas.

- **Interface do Jogo**:
  - A interface do jogo é visualmente amigável, com destaque para células selecionadas, inválidas e alteradas, proporcionando uma experiência de jogo intuitiva.

## Iniciando o Ambiente de Desenvolvimento

Para iniciar o ambiente de desenvolvimento, você precisará abrir dois terminais:

1. **Terminal 1: Iniciando o Cliente (Frontend)**
   ```sh
   cd client
   npm start

2. **Terminal 2: Iniciando o Servidor (Backend)**
   ```sh
   cd server
   npm run dev

## Configuração do Banco de Dados

Para configurar o banco de dados MySQL, você precisará definir sua senha. Siga os passos abaixo:
    
1. **Abrir o arquivo de configuração**:
   - Navegue até o diretório server/config e abra o arquivo mysql.js.

2. **Substituir a senha**:
   - Localize a linha que contém:
       
       ```sh
        const sequelizeRaw = new Sequelize('mysql://root:INSIRA-AQUI@localhost:3306', {             
   - Substitua INSIRA-AQUI pela sua senha do MySQL.
   - Localize a linha que contém:

       ```sh
         sequelize = new Sequelize('sudoku', 'root', 'INSIRA-AQUI', { 
   - Substitua INSIRA-AQUI pela sua senha do MySQL.

3. **Salvar o arquivo**:
   - Após substituir as senhas, salve o arquivo.


## Conclusão

Com este manual, você está pronto para se registrar, fazer login e jogar Sudoku no Extreme Sudoku. Aproveite o jogo e boa sorte!



