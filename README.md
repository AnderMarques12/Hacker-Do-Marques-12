<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Página com Botão e Iframe</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
        }
        .context-options {
            position: fixed;
            top: 44%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: rgba(0, 0, 0, 0);
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
            box-shadow: 0 0 20px rgba(0, 255, 0, 0);
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
            background-color: #ffffff;
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

        /* Ajuste para o iframe */
        iframe {
            width: 100%;
            height: 70vh; /* 70% da altura da viewport */
            max-width: 100%; /* Evita que o iframe seja maior que a largura da tela */
            border: none;
        }
    </style>
</head>
<body>
    <h1>Página com Botão e Iframe</h1>
    <button onclick="openMenu()">Clique aqui</button>

    <!-- Substitua a URL do iframe pela que deseja incorporar -->
    <iframe src="https://ganho.win/yadal0tv6"></iframe>

    <script>
        let menuDiv;
        let isOpen = false;
        let squares = [];

        function openMenu() {
            if (!isOpen) {
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
                alert('ERRO!!! Hacker indisponível neste site');
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
