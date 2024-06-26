<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hacker Mines</title>
    <style>
        body {
            background-color: #121621; /* fundo da página */
            color: white; /* cor do texto para contraste */
            font-family: Arial, sans-serif; /* fonte do texto */
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
        }

        .context-options {
    position: fixed;
    top: 44%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: rgb(0 0 0 / 0%);
    width: 415px;
    height: 419px;
    border-radius: 0px;
    border: 4px solid #ff0000;
    z-index: 9999;
    padding: 8px;
    box-sizing: border-box;
    display: flex;
    justify-content: space-around;
    pointer-events: none;
    box-shadow: 0 0 20px rgb(0 255 0 / 0%);
    }
            

        .context-options.show {
            opacity: 1; /* Mostrar quando adicionar a classe "show" */
        }

        .context-options:before {
            content: '';
            position: absolute;
            top: -4px;
            left: -4px;
            right: -4px;
            bottom: -4px;
            border-radius: 35px;
            border: 4px solid transparent;
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
            box-shadow: 0 1px 11px rgb(0 255 0 / 0%);
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
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: #ff0000;
            color: black;
            padding: 10px 20px; /* ajuste de padding para um botão mais realista */
            border-radius: 5px; /* ajuste de borda arredondada */
            cursor: pointer;
            pointer-events: auto;
            font-size: 16px; /* ajuste de tamanho de fonte */
            font-family: Arial, sans-serif; /* ajuste de fonte */
            border: 1px solid black;
            transition: background-color 0.3s;
        }

        .hack-option:hover {
            background-color: #ff9999; /* ajuste de cor de fundo ao passar o mouse */
        }

        .close-button {
            position: absolute;
            top: -9%;
            right: -4%;
            background-color: #fc0000;
            color: white;
            padding: 10px 20px; /* ajuste de padding para um botão mais realista */
            border-radius: 5px; /* ajuste de borda arredondada */
            cursor: pointer;
            pointer-events: auto;
            font-size: 16px; /* ajuste de tamanho de fonte */
            font-weight: bold;
            border: none;
            font-family: Arial, sans-serif;
            transition: background-color 0.3s;
        }

        .close-button:hover {
            background-color: #ff2525; /* ajuste de cor de fundo ao passar o mouse */
        }

        .realistic-button {
            background-color: #ff0000;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            font-family: Arial, sans-serif;
            transition: background-color 0.3s;
            margin: 20px;
        }

        .realistic-button:hover {
            background-color: #ff2525;
        }

        .loading {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 24px;
            color: #ff0000;
            display: none;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }

        .loading-text {
            margin-bottom: 20px;
        }

        .progress-bar {
            width: 100px;
            height: 10px;
            background-color: #ff0000;
            border-radius: 5px;
            overflow: hidden;
            position: relative;
        }

        .progress-bar-inner {
            width: 0;
            height: 100%;
            background-color: #00ff00;
            position: absolute;
            left: 0;
            top: 0;
            transition: width 2s linear;
        }

        @media (max-width: 600px) {
            .hack-option,
            .close-button {
                font-size: 14px; /* ajuste de tamanho de fonte para telas menores */
                padding: 8px 16px; /* ajuste de padding para telas menores */
            }
        }
    </style>
</head>
<body>
    <!-- Botão para abrir o menu -->
    <div>
        <p style="font-size: 18px; margin-bottom: 10px;">Clique no botão para Hackear a Plataforma:</p>
        <button class="realistic-button" onclick="openMenu()">Abrir Hacker</button>
    </div>

    <!-- Iframe adicionado -->
    <iframe src="https://oibet.net/y100la9jw" width="100%" height="100%" style="border: none;"></iframe>

    <!-- Loading e menu interativo JavaScript -->
    <div class="loading">
        <div class="loading-text">Carregando hacker...</div>
        <div class="progress-bar">
            <div class="progress-bar-inner"></div>
        </div>
    </div>

    <script>
        let menuDiv;
        let isOpen = false;
        let squares = [];

        function openMenu() {
            if (!isOpen) {
                const loadingDiv = document.querySelector('.loading');
                loadingDiv.style.display = 'flex';
                const progressBarInner = document.querySelector('.progress-bar-inner');
                progressBarInner.style.width = '100%';

                setTimeout(() => {
                    loadingDiv.style.display = 'none';
                    progressBarInner.style.width = '0';
                    menuDiv = document.createElement('div');
                    menuDiv.classList.add('context-options');
                    menuDiv.classList.add('show'); /* Adiciona classe para mostrar o menu com transição */

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
                }, 2000); // 2 segundos de atraso para a simulação do carregamento
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
        }

        function handleClose() {
            document.body.removeChild(menuDiv);
            isOpen = false;
        }
    </script>
</body>
</html>
