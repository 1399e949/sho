<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Camisetas Lacoste</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      background: #f5f5f5;
    }
    header {
      background: #1a1a1a;
      color: white;
      padding: 1rem;
      text-align: center;
    }
    .container {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-around;
      padding: 2rem;
    }
    .produto {
      background: white;
      border-radius: 8px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
      width: 250px;
      margin: 1rem;
      padding: 1rem;
      text-align: center;
    }
    .produto img {
      width: 100%;
      border-radius: 6px;
    }
    .produto h3 {
      margin: 0.5rem 0;
    }
    .produto button {
      background: #007bff;
      color: white;
      border: none;
      padding: 0.5rem 1rem;
      border-radius: 4px;
      cursor: pointer;
    }
    .carrinho {
      position: fixed;
      right: 0;
      top: 0;
      background: white;
      border-left: 2px solid #ccc;
      width: 300px;
      height: 100vh;
      padding: 1rem;
      overflow-y: auto;
    }
    .carrinho h2 {
      text-align: center;
    }
    .item-carrinho {
      display: flex;
      justify-content: space-between;
      margin: 0.5rem 0;
    }
    .total {
      font-weight: bold;
      text-align: center;
      margin-top: 1rem;
    }
  </style>
</head>
<body>

  <header>
    <h1>Camisetas Lacoste Exclusivas</h1>
  </header>

  <div class="container" id="produtos">
    <!-- Produtos serão adicionados via JavaScript -->
  </div>

  <div class="carrinho" id="carrinho">
    <h2>🛒 Carrinho</h2>
    <div id="itens-carrinho"></div>
    <div class="total" id="total">Total: R$ 0,00</div>
  </div>

  <script>
    const produtos = [
      {
        nome: "Branca com Gola Azul",
        preco: 199.90,
        imagem: "https://images.unsplash.com/photo-1593032457869-e7f84d24b5e3?auto=format&fit=crop&w=400"
      },
      {
        nome: "Cinza com Logo Vermelho",
        preco: 199.90,
        imagem: "https://images.unsplash.com/photo-1618354691373-2f1ec7eec7a2?auto=format&fit=crop&w=400"
      },
      {
        nome: "Azul Céu com Detalhes Brancos",
        preco: 199.90,
        imagem: "https://images.unsplash.com/photo-1523381210434-271e8be1f52b?auto=format&fit=crop&w=400"
      },
      {
        nome: "Vinho com Logo Branco",
        preco: 199.90,
        imagem: "https://images.unsplash.com/photo-1534447677768-be436bb09401?auto=format&fit=crop&w=400"
      }
    ];

    const carrinho = [];
    const containerProdutos = document.getElementById('produtos');
    const itensCarrinho = document.getElementById('itens-carrinho');
    const total = document.getElementById('total');

    function atualizarCarrinho() {
      itensCarrinho.innerHTML = '';
      let soma = 0;
      carrinho.forEach((item, i) => {
        itensCarrinho.innerHTML += `
          <div class="item-carrinho">
            <span>${item.nome}</span>
            <span>R$ ${item.preco.toFixed(2)}</span>
          </div>
        `;
        soma += item.preco;
      });
      total.innerText = `Total: R$ ${soma.toFixed(2)}`;
    }

    function adicionarAoCarrinho(produto) {
      carrinho.push(produto);
      atualizarCarrinho();
    }

    produtos.forEach(prod => {
      const card = document.createElement('div');
      card.className = 'produto';
      card.innerHTML = `
        <img src="${prod.imagem}" alt="${prod.nome}" />
        <h3>${prod.nome}</h3>
        <p>R$ ${prod.preco.toFixed(2)}</p>
        <button onclick='adicionarAoCarrinho(${JSON.stringify(prod)})'>Adicionar ao Carrinho</button>
      `;
      containerProdutos.appendChild(card);
    });
  </script>

</body>
</html>
