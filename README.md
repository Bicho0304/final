<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rompecabezas de Amor</title>
    <style>
        body {
            text-align: center;
            font-family: Arial, sans-serif;
            background-color: #fbe3e8;
            position: relative;
        }
        #carta-animada {
            width: 150px;
            height: 150px;
            background-image: url('carta-animada.gif');
            background-size: cover;
            margin: 20px auto;
        }
        #mensaje {
            font-size: 20px;
            background-color: #ff6b81;
            color: white;
            padding: 10px;
            cursor: pointer;
            border-radius: 5px;
            display: inline-block;
            margin-top: 20px;
        }
        #puzzle-container {
            display: grid;
            grid-template-columns: repeat(3, 100px);
            grid-template-rows: repeat(3, 100px);
            grid-gap: 5px;
            width: 315px;
            height: 315px;
            margin: 20px auto;
            display: none;
        }
        .puzzle-piece {
            width: 100px;
            height: 100px;
            background-image: url('carta.jpg');
            background-size: 300px 300px;
            opacity: 0;
            transition: opacity 0.8s ease-in-out, transform 0.8s ease-in-out;
            transform: scale(0);
        }
        #mensaje-final {
            font-size: 24px;
            font-weight: bold;
            color: #d10060;
            margin-top: 20px;
            display: none;
            opacity: 0;
            transition: opacity 2s ease-in-out;
        }
    </style>
</head>
<body>
    <audio id="musica-romantica" src="audio.mp3"></audio>
    <div id="carta-animada"></div>
    <div id="mensaje" onclick="iniciarRompecabezas()">Te llegó una carta, ábrela</div>
    <div id="puzzle-container"></div>
    <div id="mensaje-final">Gracias por llegar a mi vida<br>
    y<br>
    ser lo mejor que me ha pasado,<br>
    tu alumbras cada uno de mis dias<br>
    con tu sonrisa y tus ocurrencias,<br>
    no puedo dejar de pensar en ti<br>
    la chica mas increible del mundo,<br>
    eres mi reina hermosa<br>
    la mujer y la niña de mis ojos<br>
    <br>TE AMO DE AQUI A LA LUNA<br>A PASITOS DE TORTUGA</div>
    
    <script>
        function iniciarRompecabezas() {
            document.getElementById("carta-animada").style.display = "none";
            document.getElementById("mensaje").style.display = "none";
            document.getElementById("puzzle-container").style.display = "grid";
            
            // Iniciar música
            document.getElementById("musica-romantica").play();
            
            let puzzleContainer = document.getElementById("puzzle-container");
            puzzleContainer.innerHTML = ""; // Limpiar antes de crear
            
            let filas = 3;
            let columnas = 3;
            
            for (let y = 0; y < filas; y++) {
                for (let x = 0; x < columnas; x++) {
                    let pieza = document.createElement("div");
                    pieza.classList.add("puzzle-piece");
                    pieza.style.backgroundPosition = `${-x * 100}px ${-y * 100}px`;
                    puzzleContainer.appendChild(pieza);
                }
            }
            
            let piezas = document.querySelectorAll(".puzzle-piece");
            piezas.forEach((pieza, index) => {
                setTimeout(() => {
                    pieza.style.opacity = "1";
                    pieza.style.transform = "scale(1)";
                }, index * 500);
            });
            
            setTimeout(() => {
                let mensajeFinal = document.getElementById("mensaje-final");
                mensajeFinal.style.display = "block";
                mensajeFinal.style.opacity = "1";
            }, piezas.length * 500 + 1000);
        }
    </script>
</body>
</html>
