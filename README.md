# README - Serenatto - Cardápio Digital

## Descrição

Este projeto é um site para exibição de um **cardápio digital** de um restaurante/cafeteria chamada **Serenatto**. O cardápio é dividido em duas seções principais: opções de **Café** e **Almoço**, e os produtos são exibidos com suas imagens, descrições e preços. O site faz uso de **PHP** para recuperar os dados dos produtos a partir de um banco de dados, exibindo-os dinamicamente na interface do usuário.

## Tecnologias Utilizadas

- **PHP**: Para conectar ao banco de dados e buscar as opções de café e almoço para exibição.
- **HTML**: Estruturação da página com as seções do cardápio.
- **CSS**: Estilização da página, com links para arquivos CSS externos.
- **Banco de Dados**: O site usa o banco de dados para armazenar os produtos (café e almoço) e suas informações.

## Funcionalidades

- **Exibição Dinâmica do Cardápio**: 
  - O site se conecta a um banco de dados utilizando PHP, busca as informações de produtos do tipo "Café" e "Almoço" e as exibe na interface de forma dinâmica.
  - Cada produto possui seu nome, descrição, preço e uma imagem correspondente.
  
- **Categorias**: 
  - O cardápio está dividido em duas seções: **Café** e **Almoço**.
  - Cada seção exibe seus produtos com imagens e descrições.

## Estrutura de Arquivos

```
/Serenatto-Cardapio-Digital
    /index.php               - Arquivo principal do cardápio
    /src/conexao-bd.php       - Arquivo PHP para conexão com o banco de dados
    /css/reset.css            - Arquivo CSS para reset de estilo (normalização)
    /css/index.css            - Arquivo CSS para estilização do cardápio
    /img/logo-serenatto.png   - Logo do restaurante
    /img/ornaments-coffee.png - Ornamentação de imagens do cardápio
    /img/icone-serenatto.png  - Ícone de favicon do site
    /img/                     - Pasta para imagens dos produtos
    /src/                     - Pasta para scripts PHP e banco de dados
```

## Banco de Dados

O projeto espera que você tenha um banco de dados configurado com uma tabela `produtos` contendo as seguintes colunas:

- **id**: Identificador único do produto (int).
- **nome**: Nome do produto (varchar).
- **descriçao**: Descrição do produto (varchar).
- **preco**: Preço do produto (decimal).
- **imagem**: Caminho para a imagem do produto (varchar).
- **tipo**: Tipo do produto (varchar), podendo ser 'Café' ou 'Almoço'.

### Exemplo de tabela `produtos`:

```sql
CREATE TABLE produtos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(255) NOT NULL,
    descriçao TEXT NOT NULL,
    preco DECIMAL(10,2) NOT NULL,
    imagem VARCHAR(255) NOT NULL,
    tipo ENUM('Café', 'Almoço') NOT NULL
);
```

## Como Usar

### 1. Configuração do Banco de Dados

- Configure seu banco de dados com a tabela `produtos` conforme o exemplo acima.
- Certifique-se de que os produtos para as categorias "Café" e "Almoço" estão corretamente inseridos no banco de dados.

### 2. Arquivo `conexao-bd.php`

- No arquivo `src/conexao-bd.php`, insira as credenciais de acesso ao seu banco de dados:
  ```php
  $pdo = new PDO('mysql:host=localhost;dbname=seu_banco', 'usuario', 'senha');
  ```
  Certifique-se de que a conexão com o banco de dados esteja funcionando corretamente.

### 3. Abra o Arquivo

- Abra o arquivo `index.php` em um servidor local (ex: XAMPP, WAMP, ou qualquer servidor PHP) para visualizar o cardápio no navegador.

## Funcionalidade do Código PHP

- **Conexão com o Banco de Dados**: O arquivo `conexao-bd.php` é responsável por estabelecer a conexão com o banco de dados.
- **Consultas SQL**: 
  - As consultas SQL `SELECT * FROM produtos WHERE tipo = 'Café' ORDER BY preco` e `SELECT * FROM produtos WHERE tipo = 'Almoço' ORDER BY preco` são responsáveis por buscar os produtos de cada categoria e exibi-los em ordem de preço.
  - O `PDO::FETCH_ASSOC` é utilizado para obter os resultados como um array associativo.
- **Exibição Dinâmica no HTML**: O código PHP dentro da tag `<body>` percorre os arrays de produtos (café e almoço) e exibe as informações de cada produto, como nome, descrição, preço e imagem.

## Estilização

A página é estilizada com dois arquivos CSS:

1. **reset.css**: Arquivo para resetar os estilos padrão dos navegadores e garantir que o layout fique consistente.
2. **index.css**: Arquivo para estilizar os elementos do cardápio, como a disposição dos produtos, fontes, cores e tamanhos.

## Licença

Este projeto está sob a licença **MIT**. Você pode usar, modificar e distribuir o código conforme necessário.

## Contribuições

Se você gostaria de contribuir com melhorias ou correções, fique à vontade para criar um **fork** do repositório e enviar um **pull request**.

## Autor

Desenvolvido por Danilo Lima.
