## E-commerce de produtos Apple

**Disciplina:** Prática de Programação  
**Professora:** Ludmilla Reis  
**Turma / equipe:** Grupo 2 — Carlos, Kawan, João Vitor Assunção e Natalia  
**Situação:** planejamento e implementação inicial

## 1. Objetivo
Desenvolver uma aplicação web de e-commerce simples, responsiva e totalmente funcional no navegador, utilizando HTML, CSS e JavaScript puro. O sistema permitirá navegar por produtos Apple, pesquisar, filtrar, adicionar itens ao carrinho e realizar uma finalização de pedido simulada.


## 2. Escopo funcional
### Página inicial — `index.html`
- Apresentação da loja e destaques de produtos.
- Menu de navegação para as demais páginas.
- Categorias em destaque: iPhone, iPad e acessórios (por exemplo, AirPods e Apple Watch).
- Links para acessar o catálogo.

### Catálogo — `produtos.html`
- Lista de produtos com imagem, nome, categoria e preço.
- Busca por nome.
- Filtro por categoria.
- Botão **Adicionar ao carrinho**, com retorno visual ao usuário.
- Produtos exibidos dinamicamente por JavaScript.

### Carrinho — `carrinho.html`
- Exibição dos produtos adicionados.
- Aumento ou redução de quantidade e remoção de itens.
- Cálculo automático de subtotal, frete, desconto e valor total.
- Mensagem quando o carrinho estiver vazio.
- Salvamento e recuperação dos itens pelo `localStorage`.

### Checkout — `checkout.html`
- Resumo dos itens e valor final do pedido.
- Formulário com campos básicos de identificação e contato (nome, e-mail e endereço fictício para a simulação).
- Validação de campos obrigatórios e exibição de erros compreensíveis.
- Confirmação **simulada** do pedido, sem cobrança ou envio real.
- Após confirmação válida, limpeza do carrinho.

### Regras simples para a demonstração
- Catálogo pequeno, com aproximadamente 8 a 12 produtos fictícios.
- **Frete:** R$ 29,90 para subtotal abaixo de R$ 2.000,00; grátis a partir desse valor.
- **Desconto:** 5% sobre o subtotal para compras a partir de R$ 5.000,00.
- **Total:** subtotal − desconto + frete. O pedido não pode ser concluído com o carrinho vazio.

## 3. Tecnologias e limites
**Usaremos:** HTML5, CSS3, JavaScript puro, DOM, eventos e armazenamento local do navegador (`localStorage`).
**Responsividade:** os estilos para celular e computador ficarão no mesmo arquivo `css/style.css`.
**Execução:** o projeto será testado no navegador; se necessário, usaremos o Live Server do VS Code para servir os arquivos localmente.

## 4. Organização prevista dos arquivos

```text
Projeto---Amigos-do-Peito/
├── index.html
├── produtos.html
├── carrinho.html
├── checkout.html
├── css/
│   └── style.css
├── js/
│   ├── dados.js
│   ├── utils.js
│   ├── produtos.js
│   ├── carrinho.js
│   └── checkout.js
├── img/
└── README.md
```

- `dados.js`: lista única de produtos usada em todas as páginas.
- `utils.js`: funções compartilhadas (ler, salvar e atualizar dados do carrinho; formatar preços).
- `produtos.js`: busca, filtros, exibição dinâmica e inclusão de produtos no carrinho.
- `carrinho.js`: renderização do carrinho, alterações de quantidade e cálculos.
- `checkout.js`: resumo do pedido, validações e confirmação fictícia.
- `style.css`: estilos globais, componentes e media queries.


## 5. Divisão proposta entre integrantes

| Integrante | Responsabilidade                          | Entregáveis 
| ---        | ---                                       | ---             
| Carlos     | JavaScript central e integração funcional | `js/dados.js`, `js/utils.js`, `js/produtos.js`, `js/carrinho.js`; conexão do catálogo com o carrinho; testes
| João Vitor | Interface e identidade visual             | `produtos.html`, `carrinho.html`, `css/style.css`; layout responsivo; padronização visual das quatro páginas
| Kawan      | Checkout e validação                      | `checkout.html`, `js/checkout.js`; formulário, regras de validação, exibição de erros e simulações
| Natalia    | Estrutura inicial e documentação          | `index.html` com conteúdo HTML básico e links; seleção/organização das imagens e revisão do README 


## 6. Contrato de integração (antes de programar)
Para os arquivos JavaScript funcionarem com os HTMLs criados por pessoas diferentes, acordaremos os seguintes padrões:

### Dados de produto

```js
const produtos = [
  {
    id: 1,
    nome: "iPhone - modelo demonstrativo",
    categoria: "iphone",
    preco: 3999.90,
    imagem: "img/iphone-exemplo.jpg"
  }
];
```

**Carrinho no armazenamento:** chave `carrinho` no `localStorage`, com um array de objetos no formato `{ id, quantidade }`. O catálogo de produtos será a fonte de nome, imagem e preço, evitando dados duplicados.

### Elementos que os scripts deverão encontrar
 
| Página                                | Identificadores combinados                                                  | 
| ---                                   | ---                                                                         |
| Produtos                              | `#lista-produtos`, `#busca-produtos`, `#filtro-categoria`                   |
| Carrinho                              | `#lista-carrinho`, `#subtotal`, `#frete`, `#desconto`, `#total`             |
| Checkout                              | `#form-checkout`, `#resumo-pedido`, `#mensagem-erro`, `#confirmacao-pedido` |
| Todas, quando houver contador no menu | `#contador-carrinho`                                                        |


## 7. Conteúdos da disciplina que serão demonstrados

| Conteúdo das aulas | Aplicação no projeto |
| ---                                         | ---                                                                         |
| Variáveis, operadores, tipos e condicionais | Dados dos produtos, regras de frete/desconto e validações                   |
| Estruturas de repetição e escopo            | Percorrer produtos e itens do carrinho (`for`, `forEach`)                   |
| Funções, módulos e biblioteca própria       | Funções nomeadas em cada script e funções reaproveitadas de `utils.js`      |
| Tratamento de erros                         | `try/catch/finally` e `throw` para leitura do armazenamento e/ou validações |
| Fundamentos Web e planejamento              | Mapa de navegação, organização por pastas e arquivos nomeados               |
| HTML semântico                              | `header`, `nav`, `main`, `section`, `footer` e formulário                   |
| CSS                                         | Seletores, box model, Flexbox/Grid, cores e posicionamento                  |
| Responsividade                              | Layout mobile-first, unidades relativas, media queries e menu adaptável     |
| Integração front-end / DOM                  | Seleção, criação/remoção de elementos e atualização de preços e listas      |
| Eventos e formulários                       | `click`, `input`, `change` e `submit`, com mensagens de erro                |
| Persistência de dados                       | `localStorage`, `JSON.stringify` e `JSON.parse`                             |


## 8. Cronograma da professora

| Data           | Marco                         | Meta interna do grupo                                      |
| ---            | ---                           | ---                                                        |
| **17/11/2026** | Definição de grupo e tema     | Grupo e tema definidos                                     |
| **24/11/2026** | Acompanhamento                | Escopo, divisão de tarefas e base navegável do projeto     |
| **01/12/2026** | Finalização, testes e ajustes | Quatro páginas integradas; fluxo principal funcionando     |
| **08/12/2026** | Entrega e apresentação N2     | ZIP do projeto, demonstração e apresentação de 15 minutos  |

## 9. Critérios de conclusão

- [ ] Pelo menos quatro arquivos HTML interligados.
- [ ] `index.html` na raiz com menu para as outras páginas.
- [ ] Layout funcional em computador e celular.
- [ ] Busca/filtro e adição de produtos funcionando.
- [ ] Carrinho com atualização de quantidade, remoção e total correto.
- [ ] Carrinho preservado após atualizar a página.
- [ ] Checkout validado, com erros visíveis e confirmação fictícia.
- [ ] Tratamento de erros demonstrável no código.
- [ ] Todos os conteúdos exigidos pela professora identificáveis.
- [ ] Teste do fluxo completo sem erros no console.
- [ ] Código organizado, ZIP preparado e apresentação ensaiada.

## 10. Apresentação

A apresentação terá **15 minutos no total**. Cada integrante explicará brevemente sua parte e demonstrará um trecho do código relacionado ao conteúdo ensinado em aula. Devemos mostrar a navegação completa: página inicial → catálogo → carrinho → checkout → confirmação.
