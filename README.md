# Tutorial: Manipulação do DOM com JavaScript

> Tutorial completo para iniciantes em webdesign sobre como interagir com elementos HTML usando JavaScript

## 📚 Sumário

- [O que é o DOM?](#o-que-é-o-dom)
- [Selecionando Elementos](#selecionando-elementos)
- [Manipulando Atributos](#manipulando-atributos)
  - [getAttribute](#getattribute)
  - [setAttribute](#setattribute)
  - [classList](#classlist)
- [Criando e Removendo Elementos](#criando-e-removendo-elementos)
  - [createElement](#createelement)
  - [appendChild](#appendchild)
  - [removeChild](#removechild)
- [Desafio Prático](#desafio-prático)

---

## O que é o DOM?

**DOM** significa **Document Object Model** (Modelo de Objeto do Documento). É uma representação estruturada do documento HTML em forma de árvore de objetos, permitindo que linguagens de programação como JavaScript interajam com a página web.

### Como funciona?

Quando o navegador carrega uma página HTML, ele cria uma representação em árvore de todos os elementos da página. Cada elemento HTML se torna um **nó** (node) nessa árvore, e podemos usar JavaScript para:

- 📖 Ler conteúdo e atributos
- ✏️ Modificar elementos existentes
- ➕ Adicionar novos elementos
- ❌ Remover elementos
- 🎨 Alterar estilos e classes CSS

### Exemplo Visual da Estrutura DOM

```
document
  └── html
       ├── head
       │    ├── title
       │    └── meta
       └── body
            ├── header
            ├── main
            │    ├── section
            │    └── article
            └── footer
```

---

## Selecionando Elementos

Antes de manipular elementos, precisamos selecioná-los. Aqui estão os métodos mais comuns:

```javascript
// Selecionar por ID
const elemento = document.getElementById('meuId');

// Selecionar por classe (retorna o primeiro elemento)
const elemento = document.querySelector('.minhaClasse');

// Selecionar todos os elementos de uma classe
const elementos = document.querySelectorAll('.minhaClasse');

// Selecionar por tag
const paragrafos = document.getElementsByTagName('p');
```

---

## Manipulando Atributos

### getAttribute

O método `getAttribute()` retorna o valor de um atributo especificado de um elemento.

**Sintaxe:**
```javascript
elemento.getAttribute(nomeDoAtributo)
```

**Exemplo:**

```html
<!-- HTML -->
<img id="minhaImagem" src="foto.jpg" alt="Descrição da foto">
<a id="meuLink" href="https://www.exemplo.com">Visitar site</a>
```

```javascript
// JavaScript
const imagem = document.getElementById('minhaImagem');
const link = document.getElementById('meuLink');

// Obter o valor do atributo src
const caminhoImagem = imagem.getAttribute('src');
console.log(caminhoImagem); // "foto.jpg"

// Obter o valor do atributo href
const url = link.getAttribute('href');
console.log(url); // "https://www.exemplo.com"
```

### setAttribute

O método `setAttribute()` define um novo valor para um atributo de um elemento. Se o atributo não existir, ele será criado.

**Sintaxe:**
```javascript
elemento.setAttribute(nomeDoAtributo, valor)
```

**Exemplo:**

```html
<!-- HTML -->
<img id="minhaImagem" src="foto-antiga.jpg" alt="Foto antiga">
<button id="meuBotao">Clique aqui</button>
```

```javascript
// JavaScript
const imagem = document.getElementById('minhaImagem');
const botao = document.getElementById('meuBotao');

// Alterar o atributo src da imagem
imagem.setAttribute('src', 'foto-nova.jpg');

// Adicionar um atributo disabled ao botão
botao.setAttribute('disabled', 'true');

// Alterar múltiplos atributos
imagem.setAttribute('alt', 'Nova descrição');
imagem.setAttribute('width', '300');
```

### classList

A propriedade `classList` retorna uma coleção das classes de um elemento e fornece métodos para adicionar, remover e alternar classes CSS.

**Métodos principais:**
- `add()` - adiciona uma ou mais classes
- `remove()` - remove uma ou mais classes
- `toggle()` - adiciona a classe se não existir, remove se existir
- `contains()` - verifica se o elemento possui uma classe específica

**Exemplo:**

```html
<!-- HTML -->
<div id="caixa" class="container">
  <p>Conteúdo da caixa</p>
</div>

<style>
  .destaque {
    background-color: yellow;
    font-weight: bold;
  }
  
  .borda {
    border: 2px solid blue;
  }
  
  .escondido {
    display: none;
  }
</style>
```

```javascript
// JavaScript
const caixa = document.getElementById('caixa');

// Adicionar uma classe
caixa.classList.add('destaque');

// Adicionar múltiplas classes
caixa.classList.add('borda', 'sombra');

// Remover uma classe
caixa.classList.remove('container');

// Alternar uma classe (toggle)
caixa.classList.toggle('escondido'); // adiciona se não existir
caixa.classList.toggle('escondido'); // remove se existir

// Verificar se possui uma classe
if (caixa.classList.contains('destaque')) {
  console.log('A caixa está em destaque!');
}

// Substituir uma classe por outra
caixa.classList.replace('destaque', 'normal');
```

---

## Criando e Removendo Elementos

### createElement

O método `createElement()` cria um novo elemento HTML especificado pela tag name.

**Sintaxe:**
```javascript
document.createElement(tagName)
```

**Exemplo:**

```javascript
// Criar um novo parágrafo
const novoParagrafo = document.createElement('p');

// Adicionar texto ao parágrafo
novoParagrafo.textContent = 'Este é um novo parágrafo criado com JavaScript!';

// Criar uma nova div
const novaDiv = document.createElement('div');
novaDiv.innerHTML = '<h2>Título</h2><p>Conteúdo</p>';

// Criar um botão com atributos
const novoBotao = document.createElement('button');
novoBotao.textContent = 'Clique aqui';
novoBotao.setAttribute('id', 'btnNovo');
novoBotao.classList.add('btn', 'btn-primary');
```

### appendChild

O método `appendChild()` adiciona um elemento filho ao final da lista de filhos de um elemento pai.

**Sintaxe:**
```javascript
elementoPai.appendChild(elementoFilho)
```

**Exemplo:**

```html
<!-- HTML -->
<div id="container">
  <p>Parágrafo existente</p>
</div>
```

```javascript
// JavaScript
const container = document.getElementById('container');

// Criar um novo elemento
const novoElemento = document.createElement('p');
novoElemento.textContent = 'Novo parágrafo adicionado!';

// Adicionar o elemento ao container
container.appendChild(novoElemento);

// Exemplo mais completo: criar uma lista
const lista = document.createElement('ul');

for (let i = 1; i <= 5; i++) {
  const item = document.createElement('li');
  item.textContent = `Item ${i}`;
  lista.appendChild(item);
}

container.appendChild(lista);
```

**Resultado após execução:**
```html
<div id="container">
  <p>Parágrafo existente</p>
  <p>Novo parágrafo adicionado!</p>
  <ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
    <li>Item 4</li>
    <li>Item 5</li>
  </ul>
</div>
```

### removeChild

O método `removeChild()` remove um elemento filho de um elemento pai.

**Sintaxe:**
```javascript
elementoPai.removeChild(elementoFilho)
```

**Exemplo:**

```html
<!-- HTML -->
<div id="container">
  <p id="para1">Primeiro parágrafo</p>
  <p id="para2">Segundo parágrafo</p>
  <p id="para3">Terceiro parágrafo</p>
</div>
```

```javascript
// JavaScript
const container = document.getElementById('container');
const para2 = document.getElementById('para2');

// Remover o segundo parágrafo
container.removeChild(para2);

// Remover o primeiro filho
const primeiroFilho = container.firstChild;
container.removeChild(primeiroFilho);

// Remover todos os filhos
while (container.firstChild) {
  container.removeChild(container.firstChild);
}
```

**Método alternativo (mais moderno):**
```javascript
// Usando remove() diretamente no elemento
const elemento = document.getElementById('para2');
elemento.remove(); // Remove o próprio elemento
```

---

## Desafio Prático

Agora é sua vez! Teste seus conhecimentos criando uma **Lista de Tarefas Interativa**.

### 📋 Requisitos:

1. **HTML Base:**
   - Crie um input para digitar tarefas
   - Crie um botão "Adicionar"
   - Crie uma div/ul para exibir a lista de tarefas

2. **Funcionalidades JavaScript:**
   - ✅ Ao clicar no botão "Adicionar", criar um novo elemento `li` com o texto da tarefa
   - ✅ Adicionar um botão "Remover" em cada tarefa
   - ✅ Ao clicar em "Remover", deletar a tarefa da lista
   - ✅ Adicionar uma classe CSS que risque o texto quando a tarefa for clicada (marcar como concluída)
   - ✅ Usar `getAttribute` e `setAttribute` para manipular atributos
   - ✅ Usar `classList` para adicionar/remover classes de estilo

### 💡 Dicas:

```html
<!-- Estrutura HTML sugerida -->
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Lista de Tarefas</title>
  <style>
    .concluida {
      text-decoration: line-through;
      color: gray;
    }
    .tarefa {
      margin: 10px 0;
      padding: 10px;
      background-color: #f0f0f0;
      border-radius: 5px;
    }
  </style>
</head>
<body>
  <h1>Minha Lista de Tarefas</h1>
  <input type="text" id="inputTarefa" placeholder="Digite uma tarefa...">
  <button id="btnAdicionar">Adicionar</button>
  <ul id="listaTarefas"></ul>

  <script src="script.js"></script>
</body>
</html>
```

### 🎯 Desafio Extra:

- Impedir que tarefas vazias sejam adicionadas
- Limpar o input após adicionar uma tarefa
- Adicionar um contador mostrando quantas tarefas foram concluídas
- Salvar as tarefas no `localStorage` para persistir os dados

---

## 📚 Recursos Adicionais

- [MDN Web Docs - DOM](https://developer.mozilla.org/pt-BR/docs/Web/API/Document_Object_Model)
- [MDN - Element.classList](https://developer.mozilla.org/pt-BR/docs/Web/API/Element/classList)
- [MDN - Document.createElement](https://developer.mozilla.org/pt-BR/docs/Web/API/Document/createElement)

---

## 🤝 Contribuições

Este é um material educacional. Sugestões e melhorias são bem-vindas!

---

**Bons estudos! 🚀**
