<!-- CÓDIGO HTML COMPLETO COM O NOME NO RODAPÉ -->
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Protocolo de Cartas</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/flatpickr/dist/flatpickr.min.css">
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f9f9f9;
      max-width: 900px;
      margin: 20px auto;
      padding: 0 15px 40px;
      color: #222;
    }
    header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      background-color: #002060;
      color: white;
      padding: 15px 20px;
      border-radius: 8px;
      margin-bottom: 30px;
      position: sticky;
      top: 0;
      z-index: 10;
    }
    header h1 {
      margin: 0;
      font-size: 1.6rem;
    }
    header button {
      background-color: white;
      color: #002060;
      border: none;
      padding: 8px 18px;
      font-size: 1rem;
      border-radius: 6px;
      cursor: pointer;
      font-weight: bold;
    }
    header button:hover {
      background-color: #f0f0f0;
    }
    #inputBusca {
      width: 100%;
      padding: 12px 15px;
      font-size: 1rem;
      border: 2px solid #ccc;
      border-radius: 8px;
      margin-bottom: 25px;
      box-sizing: border-box;
      transition: border-color 0.3s;
    }
    #inputBusca:focus {
      border-color: #002060;
      outline: none;
    }
    .form-container {
      background: white;
      padding: 20px 25px;
      border-radius: 8px;
      box-shadow: 0 3px 12px rgba(0,0,0,0.1);
      margin-bottom: 40px;
    }
    .form-container h2 {
      margin-top: 0;
      color: #002060;
      text-align: center;
      margin-bottom: 15px;
    }
    .form-container input, .form-container select {
      width: 100%;
      padding: 10px 14px;
      margin-bottom: 15px;
      font-size: 1rem;
      border: 1.8px solid #ccc;
      border-radius: 6px;
      box-sizing: border-box;
    }
    .form-container button {
      background-color: #002060;
      color: white;
      border: none;
      padding: 12px 25px;
      font-size: 1.1rem;
      border-radius: 6px;
      cursor: pointer;
      width: 100%;
      font-weight: 700;
    }
    .form-container button:hover {
      background-color: #001640;
    }
    .card {
      background: white;
      border-radius: 8px;
      padding: 15px 20px;
      box-shadow: 0 1.5px 6px rgba(0,0,0,0.1);
      margin-bottom: 18px;
      position: relative;
    }
    .card p {
      margin: 6px 0;
      font-size: 1rem;
      line-height: 1.3;
    }
    .btn-excluir {
      position: absolute;
      top: 15px;
      right: 15px;
      background-color: #666;
      color: white;
      border: none;
      padding: 5px 12px;
      font-size: 0.9rem;
      border-radius: 5px;
      cursor: pointer;
    }
    .btn-excluir:hover {
      background-color: #444;
    }
    .erro {
      text-align: center;
      font-weight: 700;
      color: #002060;
      font-size: 1.1rem;
    }
    .setores-container {
      margin-top: 10px;
    }
    .setor-titulo {
      background-color: #002060;
      color: white;
      cursor: pointer;
      padding: 12px 20px;
      font-weight: 700;
      border-radius: 8px;
      margin-bottom: 8px;
      user-select: none;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 1.1rem;
    }
    .setor-titulo:hover {
      background-color: #001640;
    }
    .setor-conteudo {
      background-color: white;
      border-radius: 0 0 8px 8px;
      padding: 15px 20px;
      display: none;
      margin-bottom: 15px;
    }
    .card-list {
      max-height: 300px;
      overflow-y: auto;
    }
    .setor-titulo .icon {
      font-size: 1.4rem;
      transition: transform 0.3s ease;
    }
    .setor-titulo.active .icon {
      transform: rotate(90deg);
    }
    footer {
      text-align: center;
      font-size: 0.75rem;
      color: #888;
      margin-top: 40px;
    }
  </style>
</head>
<body>

  <header>
    <h1>Protocolo de Cartas</h1>
    <button onclick="resetBusca()">Início</button>
  </header>

  <input type="text" id="inputBusca" placeholder="Buscar por protocolo, nome ou setor..." oninput="buscarCartas()">

  <div id="resultadoBusca"></div>

  <div class="form-container">
    <h2>Adicionar Nova Carta</h2>
    <input type="text" id="novoProtocolo" placeholder="Número do Protocolo" />
    <input type="text" id="novoNome" placeholder="Nome de quem fez o protocolo" />
    <input type="text" id="novaData" placeholder="DD/MM/AAAA" />
    <select id="novoSetor"></select>
    <button onclick="adicionarCarta()">Adicionar Carta</button>
  </div>

  <section class="setores-container" id="setoresContainer"></section>

  <footer>Desenvolvido por Jonoel Pereira</footer>

  <script src="https://cdn.jsdelivr.net/npm/flatpickr"></script>
  <script>
    flatpickr("#novaData", {
      dateFormat: "d/m/Y",
      allowInput: true
    });

    const setores = ['NUPAT', 'SEPOL', 'DIPOL', 'GABIN SRRF', 'DIREP', 'AGU', 'SECOP', 'DRJ', 'DRF', 'ESCOR05', 'DIFIS'];

    const selectSetor = document.getElementById("novoSetor");
    selectSetor.innerHTML = '<option value="">Selecione o Setor</option>' + setores.map(s => `<option value="${s}">${s}</option>`).join('');

    let cartas = JSON.parse(localStorage.getItem('cartas')) || [];

    function salvarCartas() {
      localStorage.setItem('cartas', JSON.stringify(cartas));
    }

    function formatarData(dataStr) {
      return dataStr;
    }

    function renderSetores() {
      const container = document.getElementById('setoresContainer');
      container.innerHTML = '';

      setores.forEach(setor => {
        const cartasSetor = cartas.filter(c => c.setor === setor);
        const div = document.createElement('div');

        div.innerHTML = `
          <div class="setor-titulo">
            ${setor} <span class="icon">&#9656;</span>
          </div>
          <div class="setor-conteudo">
            ${cartasSetor.length
              ? cartasSetor.map(c => `
                  <div class="card">
                    <p><strong>Protocolo:</strong> ${c.protocolo}</p>
                    <p><strong>Nome:</strong> ${c.nome}</p>
                    <p><strong>Data:</strong> ${formatarData(c.data)}</p>
                    <button class="btn-excluir" onclick="excluirCarta('${c.protocolo}')">Excluir</button>
                  </div>
                `).join('')
              : '<p>Nenhuma carta cadastrada neste setor.</p>'
            }
          </div>
        `;
        container.appendChild(div);
      });

      document.querySelectorAll('.setor-titulo').forEach(title => {
        title.onclick = () => {
          title.classList.toggle('active');
          const content = title.nextElementSibling;
          content.style.display = content.style.display === 'block' ? 'none' : 'block';
        };
      });
    }

    function adicionarCarta() {
      const protocolo = document.getElementById('novoProtocolo').value.trim();
      const nome = document.getElementById('novoNome').value.trim();
      const data = document.getElementById('novaData').value.trim();
      const setor = document.getElementById('novoSetor').value;

      if (!protocolo || !nome || !data || !setor) {
        alert("Preencha todos os campos.");
        return;
      }
      if (cartas.some(c => c.protocolo === protocolo)) {
        alert("Protocolo já existe!");
        return;
      }

      cartas.push({ protocolo, nome, data, setor });
      salvarCartas();
      document.getElementById('novoProtocolo').value = '';
      document.getElementById('novoNome').value = '';
      document.getElementById('novaData').value = '';
      document.getElementById('novoSetor').value = '';

      renderSetores();
      document.getElementById('resultadoBusca').innerHTML = '';
      document.getElementById('inputBusca').value = '';
    }

    function excluirCarta(protocolo) {
      if (!confirm("Tem certeza que deseja excluir esta carta?")) return;
      cartas = cartas.filter(c => c.protocolo !== protocolo);
      salvarCartas();
      renderSetores();
      buscarCartas();
    }

    function buscarCartas() {
      const termo = document.getElementById('inputBusca').value.trim().toLowerCase();
      const resultado = document.getElementById('resultadoBusca');
      resultado.innerHTML = '';

      if (!termo) {
        renderSetores();
        return;
      }

      const filt = cartas.filter(c =>
        c.protocolo.toLowerCase().includes(termo) ||
        c.nome.toLowerCase().includes(termo) ||
        c.setor.toLowerCase().includes(termo)
      );

      if (filt.length === 0) {
        resultado.innerHTML = `<p class="erro">Nenhuma carta encontrada.</p>`;
        return;
      }

      resultado.innerHTML = filt.map(c => `
        <div class="card">
          <p><strong>Protocolo:</strong> ${c.protocolo}</p>
          <p><strong>Nome:</strong> ${c.nome}</p>
          <p><strong>Data:</strong> ${c.data}</p>
          <p><strong>Setor:</strong> ${c.setor}</p>
          <button class="btn-excluir" onclick="excluirCarta('${c.protocolo}')">Excluir</button>
        </div>
      `).join('');
    }

    function resetBusca() {
      document.getElementById('inputBusca').value = '';
      document.getElementById('resultadoBusca').innerHTML = '';
      renderSetores();
    }

    renderSetores();
  </script>
</body>
</html>
