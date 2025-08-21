<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Site de Vendas</title>
  <style>
    /* Reset */
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: #f9f9f9;
      color: #333;
      line-height: 1.6;
    }

    /* Navbar */
    nav {
      position: fixed; top: 0; left: 0; width: 100%;
      background: #111; padding: 15px 20px;
      display: flex; justify-content: space-between; align-items: center;
      z-index: 1000; box-shadow: 0 2px 6px rgba(0,0,0,0.5);
    }
    nav .logo {
      font-size: 1.4em; font-family: 'Georgia', serif;
      background: linear-gradient(90deg, #d4af37, #f5e79e, #d4af37);
      -webkit-background-clip: text; -webkit-text-fill-color: transparent;
      font-weight: bold;
    }
    nav ul { list-style: none; display: flex; gap: 20px; }
    nav ul li a {
      color: #f9f9f9; text-decoration: none; font-weight: bold;
      transition: color 0.3s;
    }
    nav ul li a:hover { color: #d4af37; }

    /* Header */
    header {
      background: #111; padding: 100px 20px 40px;
      text-align: center; margin-top: 60px;
    }
    .luxo {
      font-family: 'Georgia', serif;
      background: linear-gradient(90deg, #d4af37, #f5e79e, #d4af37);
      -webkit-background-clip: text; -webkit-text-fill-color: transparent;
      text-shadow: 2px 2px 8px rgba(0,0,0,0.6); letter-spacing: 2px;
    }
    header h1 { font-size: 3em; }

    /* Conteúdo */
    main {
      padding: 40px 20px; max-width: 1200px; margin: auto; text-align: center;
    }
    main h2 { font-size: 2em; margin: 20px 0; }
    main p { margin-bottom: 20px; }

    /* Vitrine de produtos */
    .anuncios {
      display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 25px; margin-top: 30px;
    }
    .anuncio-item {
      background: #fff; border-radius: 12px; padding: 20px;
      box-shadow: 0 6px 14px rgba(0,0,0,0.1);
      transition: transform 0.2s, box-shadow 0.2s;
    }
    .anuncio-item:hover {
      transform: translateY(-5px); box-shadow: 0 8px 18px rgba(0,0,0,0.2);
    }
    .anuncio-item img { width: 100%; border-radius: 8px; margin-bottom: 15px; }
    .anuncio-item p { font-weight: bold; margin-bottom: 10px; font-size: 1.1em; }
    .btn-comprar {
      display: inline-block;
      background: linear-gradient(90deg, #d4af37, #f5e79e, #d4af37);
      color: #111; font-weight: bold; padding: 10px 18px;
      border-radius: 8px; text-decoration: none;
      transition: background 0.3s, transform 0.2s;
    }
    .btn-comprar:hover {
      background: linear-gradient(90deg, #f5e79e, #d4af37, #f5e79e);
      transform: scale(1.05);
    }

    /* Formulário */
    form {
      background: #fff; padding: 20px; border-radius: 12px;
      max-width: 500px; margin: 20px auto;
      box-shadow: 0 6px 14px rgba(0,0,0,0.1);
      text-align: left;
    }
    form label { display: block; margin: 10px 0 5px; font-weight: bold; }
    form input, form textarea {
      width: 100%; padding: 10px; border-radius: 6px;
      border: 1px solid #ccc; margin-bottom: 15px;
      font-size: 1em;
    }
    form button {
      background: linear-gradient(90deg, #d4af37, #f5e79e, #d4af37);
      border: none; padding: 12px 20px; font-size: 1em;
      font-weight: bold; border-radius: 8px; cursor: pointer;
      transition: transform 0.2s;
    }
    form button:hover { transform: scale(1.05); }

    /* Rodapé */
    footer {
      background: #111; color: #f9f9f9;
      padding: 20px; text-align: center; margin-top: 40px;
      font-size: 0.9em;
    }

    /* Ajuste para âncoras */
    section { scroll-margin-top: 80px; }
  </style>
</head>
<body>
  <!-- Menu fixo -->
  <nav>
    <div class="logo">✨ Minha Loja ✨</div>
    <ul>
      <li><a href="#home">Home</a></li>
      <li><a href="#produtos">Produtos</a></li>
      <li><a href="#contato">Contato</a></li>
    </ul>
  </nav>

  <!-- Header -->
  <header id="home">
    <h1 class="luxo">✨ Site de Vendas ✨</h1>
  </header>

  <main>
    <!-- Produtos -->
    <section id="produtos">
      <h2 class="luxo">Produtos em Destaque</h2>
      <p>Escolha entre os melhores produtos disponíveis no Mercado Livre com segurança e qualidade.</p>

      <div class="anuncios">
        <div class="anuncio-item">
          <img src="URL_DA_IMAGEM_DO_PRODUTO_1" alt="Produto 1 Mercado Livre">
          <p>Produto de Luxo 1</p>
          <a href="https://produto.mercadolivre.com.br/MLB-1234567890?aff_id=SEU_CODIGO" target="_blank" class="btn-comprar">Comprar Agora</a>
        </div>

        <div class="anuncio-item">
          <img src="URL_DA_IMAGEM_DO_PRODUTO_2" alt="Produto 2 Mercado Livre">
          <p>Produto de Luxo 2</p>
          <a href="https://produto.mercadolivre.com.br/MLB-0987654321?aff_id=SEU_CODIGO" target="_blank" class="btn-comprar">Comprar Agora</a>
        </div>
      </div>
    </section>

    <!-- Contato -->
    <section id="contato" style="margin-top:50px;">
      <h2 class="luxo">Entre em Contato</h2>
      <form action="https://formspree.io/f/mwkjzabc" method="POST">
        <label for="nome">Nome:</label>
        <input type="text" id="nome" name="nome" required>

        <label for="email">E-mail:</label>
        <input type="email" id="email" name="_replyto" required>

        <label for="mensagem">Mensagem:</label>
        <textarea id="mensagem" name="mensagem" rows="5" required></textarea>

        <button type="submit">Enviar Mensagem</button>
      </form>
    </section>
  </main>

  <footer>
    <p>&copy; 2025 - Minha Loja | Todos os direitos reservados</p>
  </footer>
</body>
</html>
