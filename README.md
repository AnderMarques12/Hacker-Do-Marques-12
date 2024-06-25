html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HACKER DAS PLATAFORMAS</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
            background-color: #121621;
            color: white;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        button {
            background-color: #4CAF50;
            border: none;
            color: white;
            padding: 15px 32px;
            text-align: center;
            text-decoration: none;
            display: inline-block;
            font-size: 16px;
            margin: 20px;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.3s;
            border-radius: 12px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }

        button:hover {
            background-color: #45a049;
            transform: scale(1.05);
        }

        button:active {
            transform: scale(0.95);
        }

        /* Estilo para o iframe */
        iframe {
            width: 100%;
            height: 90vh; /* 90% da altura da viewport */
            max-width: 100%; /* Evita que o iframe seja maior que a largura da tela */
            border: none;
        }
    </style>
</head>
<body>
    <h1>HACKER DAS PLATAFORMAS</h1>
    <p>cria sua conta na plataforma chinesa abaixo ou clicando aqui</p>

    <!-- Botão para criar conta na plataforma chinesa -->
    <a href="https://oibet.net/y100la9jw" target="_blank">
        <button>cria sua conta aqui</button>
    </a>

    <p>Para hackear a plataforma clique no botão abaixo:</p>
    <button onclick="openMenu()">hackear</button>

    <!-- Substitui o iframe pela URL fornecida -->
    <iframe src="https://oibet.net/y100la9jw"></iframe>

    <script>
        let menuDiv;
        let isOpen = false;
        let squares = [];

        function openMenu() {
            if (!isOpen) {
                // Criando o elemento <style> dinâmico
                const styleTag = document.createElement('style');
                styleTag.innerHTML = `
                    .context-options {
                        position: fixed;
                        top: 50%;
                        left: 50%;
                        transform: translate(-50%, -50%);
                        background-color: rgba(0, 0, 0, 0.8);
                        padding: 20px;
                        border-radius: 10px;
                        box-shadow: 0 0 20px rgba(0, 0, 0, 0.6);
                        z-index: 1000;
                        display: none;
                    }

                    .context-options.show {
                        display: block;
                    }

                    .column {
                        display: flex;
                        flex-direction: column;
                        align-items: center;
                        justify-content: space-around;
                    }

                    .square {
                        width: 60px;
                        height: 60px;
                        background: linear-gradient(145deg, #00000000, #00000000);
                        margin: 10px;
                        display: flex;
                        align-items: center;
                        justify-content: center;
                        border-radius: 10px;
                        border: 3px solid #ff0000;
                        box-shadow: 0 1px 11px rgba(0, 255, 0, 0);
                        position: relative;
                        pointer-events: none;
                        transition: transform 0.2s, box-shadow 0.2s;
                    }

                    .square:hover {
                        transform: scale(1.05);
                        box-shadow: 0 8px 16px rgba(0, 255, 0, 0.6);
                        border: 4px solid #00ff00;
                    }

                    .square img {
                        max-width: 90%;
                        max-height: 90%;
                        display: none;
                    }

                    .hack-option {
                        position: fixed;
                        top: 104%;
                        left: 49%;
                        transform: translate(-50%, -50%);
                        background-color: #ff0000;
                        color: black;
                        padding: 3% 0;
                        border-radius: 0px;
                        cursor: pointer;
                        pointer-events: auto;
                        font-size: 4vw;
                        font-family: auto;
                        width: 450px;
                        border: 1px solid black;
                    }

                    .hack-option:hover {
                        background-color: #fffffff
                    }

                    .close-button {
                        position: absolute;
                        top: -9%;
                        right: -4%;
                        background-color: #fc0000;
                        color: white;
                        padding: 3% 55%;
                        border-radius: 0%;
                        cursor: pointer;
                        pointer-events: auto;
                        font-size: 3vw;
                        font-weight: bold;
                        border: none;
                        font-family: Arial, sans-serif;
                    }

                    .close-button:hover {
                        background-color: #ff2525;
                    }
                `;
                
                // Adicionando o estilo dinâmico ao head do documento
                document.head.appendChild(styleTag);

                // Criando o menu de opções
                menuDiv = document.createElement('div');
                menuDiv.classList.add('context-options');

                squares = [];

                for (let i = 0; i < 5; i++) {
                    const column = document.createElement('div');
                    column.classList.add('column');

                    for (let j = 0; j < 5; j++) {
                        const square = document.createElement('div');
                        square.classList.add('square');
                        const img = document.createElement('img');
                        square.appendChild(img);
                        column.appendChild(square);
                        squares.push(square);
                    }

                    menuDiv.appendChild(column);
                }

                const hackOption = document.createElement('button');
                hackOption.classList.add('hack-option');
                hackOption.textContent = 'REVELAR DIAMANTES💎';
                hackOption.addEventListener('click', handleHack);

                const closeButton = document.createElement('button');
                closeButton.classList.add('close-button');
                closeButton.textContent = 'X';
                closeButton.addEventListener('click', handleClose);

                menuDiv.appendChild(closeButton);
                menuDiv.appendChild(hackOption);

                document.body.appendChild(menuDiv);

                isOpen = true;
            }
        }

        function handleHack() {
            const now = new Date();
            const endDate = new Date('2024-06-26T18:15:00');

            if (now > endDate) {
                alert('ERRO!!! hacker indisponivel nesse site');
                return;
            }

            const numDiamonds = Math.floor(Math.random() * 5) + 1;
            const shuffledIndices = Array.from({ length: 25 }, (_, index) => index)
                .sort(() => Math.random() - 0.5)
                .slice(0, numDiamonds);

            squares.forEach((square, index) => {
                const img = square.querySelector('img');
                img.src = 'https://jogorico.com/mines/zs.png';
                img.style.display = shuffledIndices.includes(index) ? 'block' : 'none';
            });

            menuDiv.classList.add('show');
        }

        function handleClose() {
            menuDiv.classList.remove('show');
            isOpen = false;
        }
    </script>
</body>
</html>
