# 📚 Automação de Testes de API - Hub de Leitura

Este repositório contém a suíte de testes desenvolvida para a funcionalidade **Catálogo de Livros** da API do Hub de Leitura, como parte das atividades práticas do curso da EBAC.

A estratégia cobriu requisições utilizando os principais métodos HTTP (`GET`, `POST`, `PUT`, `DELETE`), aplicando asserções de *Status Code* e validações de regras de negócio em todas as chamadas.

---

## 📁 Estrutura do Projeto

Os arquivos foram exportados diretamente do Postman e estão organizados na raiz deste repositório:
* 📄 `Hub de Leitura - Tarefa.postman_collection.json`: Contém a coleção ordenada com os cenários positivos e negativos.
* 📄 `localhost.postman_environment.json`: Contém as variáveis de ambiente necessárias (como a `baseUrl` e credenciais).

---

## Cenários Mapeados e Testados

### 🟢 Cenários Positivos (Caminho Feliz)
1. **Listar 10 livros com sucesso (`GET`)**: Valida o retorno da lista de livros com paginação (Status 200).
2. **Obter livro por ID (`GET`)**: Valida a busca de detalhes de um livro específico (Status 200).
3. **Cadastrar livro (`POST`)**: Cria um registro no acervo utilizando autenticação de admin (Status 201).
4. **Atualizar dados de um livro (`PUT`)**: Altera as informações de um livro existente no sistema (Status 200).
5. **Deletar livro (`DELETE`)**: Remove permanentemente um livro cadastrado (Status 200).

### 🔴 Cenários Negativos (Tratamento de Erros)
1. **Cadastrar livro sem permissão (`POST`)**: Garante que a API bloqueia a criação de registros caso a autenticação esteja ausente (Status 401).
2. **Buscar livro inexistente (`GET`)**: Valida se o sistema retorna o erro correto ao pesquisar por um identificador inválido ou não cadastrado (Status 404).
3. **Livro já cadastrado (`POST`)**: Valida a regra de negócio que impede a duplicação de um livro com o mesmo título e autor (Status 400).

---

## Como Executar os Testes

### Pré-requisitos
* Ter o **Postman** instalado na máquina.
* Ter o servidor local da API do Hub de Leitura rodando em ambiente local (`http://localhost:3000`).

### Passo a Passo
1. Faça o download ou clone este repositório.
2. Abra o Postman e clique em **Import** (Importar).
3. Selecione os dois arquivos JSON (`Hub de Leitura - Tarefa.postman_collection.json` e `localhost.postman_environment.json`).
4. No canto superior direito do Postman, selecione o ambiente **localhost** que foi importado.
5. Execute primeiro a requisição contida na pasta **Autenticação** (`Login com usuário administrador`) para gerar dinamicamente o Token JWT de acesso.
6. Abra o menu da Collection **Hub de Leitura - Tarefa**, clique em **Run collection** para executar todos os testes em lote e acompanhar os resultados.
