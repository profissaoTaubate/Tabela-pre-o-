<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Catálogo Profissional</title>
    <style>
        /* Design e Cores */
        :root {
            --cor-principal: #2c3e50;
            --cor-destaque: #e67e22;
            --cor-fundo: #f8f9fa;
        }

        body { font-family: 'Segoe UI', sans-serif; background: var(--cor-fundo); margin: 0; padding: 0; }
        
        header { background: var(--cor-principal); color: white; padding: 2rem; text-align: center; }

        /* Barra de Pesquisa */
        .search-container { text-align: center; padding: 20px; }
        #busca { padding: 10px; width: 60%; border-radius: 20px; border: 1px solid #ccc; outline: none; }

        /* Grelha de Produtos */
        .catalogo { 
            display: grid; 
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); 
            gap: 25px; 
            padding: 40px; 
            max-width: 1200px; 
            margin: auto; 
        }

        /* Cartão do Produto */
        .produto-card { 
            background: white; 
            border-radius: 12px; 
            overflow: hidden; 
            box-shadow: 0 4px 15px rgba(0,0,0,0.1); 
            transition: transform 0.3s;
            text-align: center;
        }

        .produto-card:hover { transform: translateY(-5px); }
        .produto-card img { width: 100%; height: 200px; object-fit: cover; }
        .info { padding: 15px; }
        .preco { color: var(--cor-destaque); font-size: 1.4rem; font-weight: bold; margin: 10px 0; }
        
        .btn-comprar { 
            background: #25d366; color: white; border: none; 
            padding: 10px 20px; border-radius: 5px; cursor: pointer;
            text-decoration: none; display: inline-block; font-weight: bold;
        }
    </style>
</head>
<body>

<header>
    <h1>O Meu Negócio</h1>
    <p>Qualidade e Confiança</p>
</header>

<div class="search-container">
    <input type="text" id="busca" placeholder="Pesquisar produto..." onkeyup="filtrarProdutos()">
</div>

<div class="catalogo" id="lista-produtos">
    </div>

<script>
    // DOCUMENTAÇÃO: Adiciona aqui os teus produtos reais
    const meusProdutos = [
        { id: 1, nome: "Relógio Elegance", preco: 89.90, desc: "Aço inoxidável e pulseira de couro.", img: "https://picsum.photos/400/300?random=1" },
        { id: 2, nome: "Mochila Adventure", preco: 45.00, desc: "Resistente à água e ideal para viagens.", img: "https://picsum.photos/400/300?random=2" },
        { id: 3, nome: "Auriculares Wireless", preco: 29.99, desc: "Bluetooth 5.0 com cancelamento de ruído.", img: "https://picsum.photos/400/300?random=3" },
        { id: 4, nome: "Câmara Vintage", preco: 120.00, desc: "Estilo retro com tecnologia digital.", img: "https://picsum.photos/400/300?random=4" }
    ];

    function renderizarCatálogo(lista) {
        const container = document.getElementById('lista-produtos');
        container.innerHTML = ""; // Limpa o catálogo antes de desenhar

        lista.forEach(item => {
            container.innerHTML += `
                <div class="produto-card">
                    <img src="${item.img}" alt="${item.nome}">
                    <div class="info">
                        <h3>${item.nome}</h3>
                        <p>${item.desc}</p>
                        <p class="preco">${item.preco.toFixed(2)} €</p>
                        <a href="https://wa.me/351912345678?text=Olá! Tenho interesse no ${item.nome}" class="btn-comprar">
                            Encomendar
                        </a>
                    </div>
                </div>
            `;
        });
    }

    // Função para pesquisar produtos em tempo real
    function filtrarProdutos() {
        const termo = document.getElementById('busca').value.toLowerCase();
        const filtrados = meusProdutos.filter(p => p.nome.toLowerCase().includes(termo));
        renderizarCatálogo(filtrados);
    }

    // Iniciar o app desenhando todos os produtos
    renderizarCatálogo(meusProdutos);
</script>

</body>
</html>
