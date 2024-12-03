
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sorteo Egreso Claraz 🎉</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600;700&display=swap');

        :root {
            --color-fucsia: #FF1493;
            --color-negro: #0a0a0a;
            --color-blanco: #FFFFFF;
            --color-accent: #8e44ad;
            --gradient-bg: linear-gradient(135deg, var(--color-fucsia), var(--color-negro));
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Montserrat', sans-serif;
            background: var(--gradient-bg);
            color: var(--color-blanco);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 20px;
            perspective: 1000px;
        }

        .container {
            background-color: rgba(255, 255, 255, 0.05);
            border-radius: 25px;
            backdrop-filter: blur(15px);
            padding: 40px;
            width: 100%;
            max-width: 700px;
            text-align: center;
            box-shadow: 0 25px 45px rgba(0,0,0,0.2);
            border: 1px solid rgba(255,255,255,0.1);
            position: relative;
        }

        .logo {
            position: absolute;
            top: -50px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 100px;
            border-radius: 50%;
            border: 4px solid var(--color-fucsia);
            overflow: hidden;
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
        }

        .logo img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        h1 {
            font-size: 2.8rem;
            margin-top: 60px;
            margin-bottom: 30px;
            background: linear-gradient(45deg, var(--color-fucsia), var(--color-blanco));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 10px 15px rgba(0,0,0,0.2);
            letter-spacing: 2px;
        }

        .sorteo-btn {
            background-color: var(--color-fucsia);
            color: var(--color-blanco);
            border: none;
            padding: 15px 30px;
            font-size: 1.1rem;
            cursor: pointer;
            border-radius: 50px;
            transition: all 0.3s ease;
            box-shadow: 0 10px 20px rgba(255,20,147,0.4);
            text-transform: uppercase;
            font-weight: 600;
            letter-spacing: 1px;
        }

        .sorteo-btn:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 15px 25px rgba(255,20,147,0.6);
            background-color: var(--color-accent);
        }

        #winners {
            display: none;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
            margin-top: 30px;
        }

        .winner-card {
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 25px;
            width: 250px;
            text-align: center;
            transition: all 0.4s ease;
            border: 1px solid rgba(255,255,255,0.1);
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
            background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, transparent 70%);
            transform: rotate(-45deg);
            opacity: 0;
            transition: opacity 0.4s ease;
        }

        .winner-card:hover::before {
            opacity: 1;
        }

        .winner-card:hover {
            transform: scale(1.05) rotateX(10deg);
            box-shadow: 0 15px 25px rgba(0,0,0,0.3);
        }

        #result {
            margin: 20px 0;
            font-size: 1.2rem;
            text-shadow: 0 2px 4px rgba(0,0,0,0.3);
        }

        @media (max-width: 600px) {
            .container {
                padding: 20px;
            }
            .logo {
                width: 80px;
                height: 80px;
                top: -40px;
            }
            h1 {
                font-size: 2rem;
                margin-top: 50px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="logoclaraz.png">
            <img src="logoclaraz.png" alt="Logoclaraz.png">
        </div>
        <h1>🎉 Sorteo Egreso Claraz 🎉</h1>
        
        <button class="sorteo-btn" onclick="realizarSorteo()">
            <i class="fas fa-dice"></i> Realizar Sorteo
        </button>
        
        <div id="result"></div>
        <div id="winners"></div>
    </div>

    <script>
        const participantes = [
            "@5849.alejandra",
            "@tomiyocuebas", 
            "@frank_bauti21",
            "@feli_corro",
            "@jackeemarcolongo",
            "@federico_sch_",
            "@torres.afra",
            "@soll_orcajo", 
            "@luudmii_basse",
            "@marianela.ibarra.188",
            "@Marianela Cuebas", 
            "@martubasse",
            "@miliaineseder",
            "@meliisantillan20",
            "@maguisuarez_",
            "@bruno.i",
            "@soljuanenea",
            "@hermida.tomas",
            "@lunii_lopepe",
            "@yami_sotuyo",
            "@cande.j24camiituarte",
            "@Camiituarte",
            "@aleexiacordoba",
            "@𝑨𝒍𝒆𝒙𝒊𝒂",
            "@yannickgerez",
            "@gerez_yannick",
            "@tomi_correa03",
            "@michaortiz22",
            "@micha",
            "@anaa_calderon1",
            "@Anahí Calderon",
            "@lautysanchez04",
            "@Lauu",
            "@juanagustinaguer",
            "@Juan Agustin Aguer",
            "@leo_larrosaa"
        ];

        function realizarSorteo() {
            const resultDiv = document.getElementById('result');
            const winnersDiv = document.getElementById('winners');

            // Limpiar resultados anteriores
            resultDiv.innerHTML = '';
            winnersDiv.innerHTML = '';

            // Seleccionar 5 ganadores al azar
            const ganadores = seleccionarGanadoresUnicos(participantes, 5);
            
            // Mostrar resultados
            resultDiv.innerHTML = `🎊 ¡Sorteo realizado con éxito! 🎊`;
            
            // Crear tarjetas de ganadores
            winnersDiv.innerHTML = ganadores.map((ganador, index) => `
                <div class="winner-card">
                    <h3>🏆 Ganador ${index + 1}</h3>
                    <p>${ganador}</p>
                </div>
            `).join('');

            // Mostrar los ganadores
            winnersDiv.style.display = 'flex';
        }

        function seleccionarGanadoresUnicos(lista, cantidadGanadores) {
            const listaModificable = [...lista];
            const ganadores = [];

            for (let i = 0; i < cantidadGanadores; i++) {
                if (listaModificable.length === 0) break;

                const indiceAleatorio = Math.floor(Math.random() * listaModificable.length);
                const ganador = listaModificable.splice(indiceAleatorio, 1)[0];
                ganadores.push(ganador);
            }

            return ganadores;
        }
    </script>
</body>
</html>
