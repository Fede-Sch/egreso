<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>SORTEO EGRESO CLARAZ</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        body {
            font-family: 'Poppins', sans-serif;
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
            background: rgba(0, 0, 0, 0.7);
            border-radius: 30px;
            padding: 50px;
            text-align: center;
            width: 100%;
            max-width: 700px;
            box-shadow: 
                0 25px 50px rgba(0,0,0,0.3),
                0 0 0 10px rgba(255,20,147,0.1);
            backdrop-filter: blur(15px);
            border: 3px solid rgba(255,255,255,0.2);
            transform: rotateX(15deg) scale(0.9);
            transition: all 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
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
                rgba(255,20,147,0.2) 0%, 
                transparent 60%);
            animation: rotate 20s linear infinite;
            z-index: -1;
        }
        @keyframes rotate {
            100% { transform: rotate(360deg); }
        }
        .container:hover {
            transform: rotateX(0deg) scale(1);
            box-shadow: 
                0 35px 60px rgba(0,0,0,0.4),
                0 0 0 15px rgba(255,20,147,0.2);
        }
        .logo {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            background: linear-gradient(135deg, #ff1493, #ff69b4);
            margin: 0 auto 30px;
            display: flex;
            justify-content: center;
            align-items: center;
            box-shadow: 
                0 15px 30px rgba(0,0,0,0.3),
                inset 0 -5px 15px rgba(255,255,255,0.2);
            border: 5px solid white;
            animation: float 3s ease-in-out infinite alternate;
            position: relative;
            overflow: hidden;
        }
        .logo::after {
            content: 'logoclaraz.png';
            font-size: 3em;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }
        @keyframes float {
            0% { transform: translateY(-10px); }
            100% { transform: translateY(10px); }
        }
        .title {
            font-size: 2.8em;
            margin-bottom: 40px;
            font-weight: 700;
            background: linear-gradient(to right, #ff1493, white);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 3px 3px 6px rgba(0,0,0,0.3);
            letter-spacing: 1px;
        }
        #winnersList {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
            margin-top: 30px;
        }
        .winner-card {
            background: linear-gradient(135deg, #ff1493, #8b008b);
            color: white;
            padding: 20px 30px;
            border-radius: 20px;
            font-weight: 600;
            box-shadow: 
                0 10px 20px rgba(0,0,0,0.3),
                inset 0 -3px 10px rgba(255,255,255,0.1);
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            overflow: hidden;
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
                rgba(255,255,255,0.1), 
                transparent
            );
            transform: rotate(45deg);
            transition: all 0.5s;
        }
        .winner-card:hover {
            transform: scale(1.05) translateY(-10px);
            box-shadow: 
                0 15px 30px rgba(0,0,0,0.4),
                inset 0 -5px 15px rgba(255,255,255,0.2);
        }
        .winner-card:hover::before {
            transform: rotate(135deg);
        }
        #performRaffle {
            background: linear-gradient(to right, #ff1493, #8b008b);
            color: white;
            border: none;
            padding: 15px 40px;
            border-radius: 50px;
            cursor: pointer;
            font-size: 1.3em;
            font-weight: 600;
            margin-top: 30px;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            box-shadow: 
                0 15px 25px rgba(0,0,0,0.3),
                inset 0 -3px 10px rgba(255,255,255,0.1);
            position: relative;
            overflow: hidden;
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
                rgba(255,255,255,0.2), 
                transparent
            );
            transition: all 0.5s;
        }
        #performRaffle:hover {
            transform: translateY(-10px) scale(1.05);
            box-shadow: 
                0 20px 35px rgba(0,0,0,0.4),
                inset 0 -5px 15px rgba(255,255,255,0.2);
        }
        #performRaffle:hover::before {
            left: 100%;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="logo"></div>
        <h1 class="title">SORTEO EGREO CLARAZ</h1>
        
        <button id="performRaffle">Realizar Sorteo</button>
        
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
