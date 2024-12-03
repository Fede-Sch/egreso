<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Sorteo Egreso Claraz</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;700&display=swap" rel="stylesheet">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        body {
            font-family: 'Orbitron', sans-serif;
            background: linear-gradient(135deg, #ff1493, #000);
            color: white;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
            perspective: 1000px;
        }
        .container {
            background: rgba(0, 0, 0, 0.8);
            border-radius: 40px;
            padding: 60px;
            text-align: center;
            width: 100%;
            max-width: 800px;
            box-shadow: 
                0 30px 60px rgba(0,0,0,0.4),
                0 0 0 15px rgba(255,20,147,0.1);
            backdrop-filter: blur(20px);
            border: 4px solid rgba(255,255,255,0.2);
            transform: rotateX(15deg) scale(0.9);
            transition: all 0.6s cubic-bezier(0.23, 1, 0.32, 1);
            position: relative;
            overflow: hidden;
        }
        .container::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle at center, 
                rgba(255,20,147,0.3) 0%, 
                transparent 60%);
            animation: cosmic-rotate 30s linear infinite;
            z-index: -1;
        }
        @keyframes cosmic-rotate {
            100% { transform: rotate(360deg); }
        }
        .container:hover {
            transform: rotateX(0deg) scale(1);
            box-shadow: 
                0 40px 70px rgba(0,0,0,0.5),
                0 0 0 20px rgba(255,20,147,0.2);
        }
        .title {
            font-size: 3.5em;
            margin-bottom: 50px;
            font-weight: 700;
            background: linear-gradient(to right, #ff1493, white);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 4px 4px 8px rgba(0,0,0,0.4);
            letter-spacing: 2px;
            line-height: 1.2;
        }
        #winnersList {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 25px;
            margin-top: 40px;
        }
        .winner-card {
            background: linear-gradient(135deg, #ff1493, #8b008b);
            color: white;
            padding: 25px 35px;
            border-radius: 25px;
            font-weight: 500;
            box-shadow: 
                0 15px 30px rgba(0,0,0,0.4),
                inset 0 -5px 15px rgba(255,255,255,0.1);
            transition: all 0.5s cubic-bezier(0.23, 1, 0.32, 1);
            position: relative;
            overflow: hidden;
            perspective: 1000px;
        }
        .winner-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(
                45deg, 
                transparent, 
                rgba(255,255,255,0.15), 
                transparent
            );
            transform: rotate(45deg);
            transition: all 0.6s;
        }
        .winner-card:hover {
            transform: scale(1.05) rotateX(10deg) translateY(-15px);
            box-shadow: 
                0 20px 40px rgba(0,0,0,0.5),
                inset 0 -8px 20px rgba(255,255,255,0.2);
        }
        .winner-card:hover::before {
            transform: rotate(135deg);
        }
        #performRaffle {
            background: linear-gradient(to right, #ff1493, #8b008b);
            color: white;
            border: none;
            padding: 20px 50px;
            border-radius: 60px;
            cursor: pointer;
            font-size: 1.5em;
            font-weight: 700;
            margin-top: 40px;
            transition: all 0.5s cubic-bezier(0.23, 1, 0.32, 1);
            box-shadow: 
                0 20px 35px rgba(0,0,0,0.4),
                inset 0 -5px 15px rgba(255,255,255,0.1);
            position: relative;
            overflow: hidden;
            text-transform: uppercase;
            letter-spacing: 2px;
        }
        #performRaffle::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(
                120deg, 
                transparent, 
                rgba(255,255,255,0.3), 
                transparent
            );
            transition: all 0.6s;
        }
        #performRaffle:hover {
            transform: translateY(-15px) scale(1.05);
            box-shadow: 
                0 25px 45px rgba(0,0,0,0.5),
                inset 0 -8px 20px rgba(255,255,255,0.2);
        }
        #performRaffle:hover::before {
            left: 100%;
        }
        #participantsCount {
            font-size: 1.2em;
            margin-top: 20px;
            color: rgba(255,255,255,0.7);
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 class="title">Sorteo Egreso Claraz</h1>
        
        <button id="performRaffle">Realizar Sorteo</button>
        
        <div id="participantsCount">Participantes: 10</div>
        <div id="winnersList"></div>
    </div>

    <script>
        const participants = [
            "Lucia Fernandez",
            "Martin Rodriguez",
            "Valentina Gomez", 
            "Santiago Lopez",
            "Martina Perez",
            "Nicolas Garcia",
            "Camila Torres",
            "Joaquin Ramirez",
            "Antonella Mendez",
            "Mateo Alvarez"
        ];

        const performRaffleBtn = document.getElementById('performRaffle');
        const winnersList = document.getElementById('winnersList');

        performRaffleBtn.addEventListener('click', () => {
            // Realizar el sorteo de 5 ganadores únicos
            let winners = [];
            const shuffled = [...participants].sort(() => 0.5 - Math.random());
            winners = shuffled.slice(0, 5);

            // Mostrar los ganadores
            winnersList.innerHTML = winners.map((winner, index) => 
                `<div class="winner-card">
                    Ganador ${index + 1}: ${winner}
                </div>`
            ).join('');
        });
    </script>
</body>
</html>
