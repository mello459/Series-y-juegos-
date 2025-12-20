            height: 450px; /* Altura ideal para video HD */
            border: 2px solid #333; /* Borde negro para ver el área del reproductor */
            border-radius: 8px; /* Esquinas redondeadas */
        }
        .mensaje {
            margin-top: 15px;
            padding: 10px;
            border-radius: 4px;
        }
        .exito { color: green; background: #d4edda; }
        .error { color: red; background: #f8d7da; }
    </style>
</head>
<body>
    <h1>Reproductor de Intensa Mente 2</h1> <!-- Título de la página -->
    
    <!-- Área donde se va a mostrar el reproductor -->
    <div id="player"></div>

    <!-- Mensaje para informar si funciona o no -->
    <div id="mensaje" class="mensaje"></div>

    <!-- 1. Cargamos la librería PlayerJS (versión estable y confiable) -->
    <script src="https://cdn.jsdelivr.net/npm/playerjs@1.0.28/dist/playerjs.min.js"></script>

    <!-- 2. Código para configurar el reproductor -->
    <script>
        // URL del video que te diste (comprobada)
        const urlVideo = "https://ia600900.us.archive.org/28/items/1.-riesgo-de-vuelo-2025-espanol_202506/Intensa%20Mente%202.mp4";
        
        // Área donde se pondrá el reproductor
        const playerContainer = document.getElementById("player");
        const mensajeDiv = document.getElementById("mensaje");

        try {
            // Creamos el reproductor con configuraciones extras
            const player = new Playerjs({
                id: "player", // ID del div donde se muestra
                file: urlVideo, // URL del video
                autoplay: false, // No se reproduce automáticamente (mejor para navegadores)
                controls: true, // Muestra los controles (play, pause, volumen, etc.)
                poster: "https://via.placeholder.com/800x450?text=Intensa+Mente+2", // Imagen de portada temporal
                muted: false, // No está silenciado por defecto
                loop: false // No se repite automáticamente
            });

            // Mensaje de éxito si se crea el reproductor
            mensajeDiv.textContent = "Reproductor cargado correctamente! Presiona 'Play' para ver el video.";
            mensajeDiv.className = "mensaje exito";

            // Comprobamos si hay error al cargar el video
            player.on("error", function(error) {
                mensajeDiv.textContent = `Error al cargar el video: ${error.message}. Intenta recargar la página o revisa la URL.`;
                mensajeDiv.className = "mensaje error";
                console.log("Error detallado:", error); // Para ver más info en la consola del navegador
            });

        } catch (error) {
            // Mensaje si hay un error en el código
            mensajeDiv.textContent = `Error al crear el reproductor: ${error.message}`;
            mensajeDiv.className = "mensaje error";
            console.log("Error detallado:", error);
        }
    </script>
</body>
</html>
