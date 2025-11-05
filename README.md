<!DOCTYPE html>
<html>
<head>
    <title>Trivia Histórica de Bluefields - Instituto Carl Rigby Moses</title>
    <meta charset="UTF-8">
    
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
    
    <style>
        body { 
            font-family: sans-serif; 
            background-color: #f0f8ff; 
            color: #333; 
            text-align: center; 
            padding: 20px; 
        }
        .container { 
            max-width: 650px; 
            margin: 20px auto; 
            background-color: #fff; 
            padding: 30px; 
            border-radius: 10px; 
            box-shadow: 0 4px 12px rgba(0,0,0,0.15); 
        }
        .question-box { 
            margin-bottom: 25px; 
            text-align: left; 
            border-bottom: 1px solid #ddd; 
            padding-bottom: 15px; 
        }
        .question-box p { 
            font-weight: bold; 
            color: #0056b3; 
            margin-bottom: 10px;
        }
        
        /* --- ESTILOS DEL CERTIFICADO --- */
        .certificate-box { 
            display: none; 
            margin-top: 40px; 
            border: 5px solid #0056b3; 
            padding: 30px; 
            background-color: #ffffff; 
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
        }
        .certificate-box h2 { 
            color: #0056b3; 
            text-transform: uppercase;
            font-size: 1.8em;
            margin-bottom: 5px;
        }
        .certificate-box h3 {
            color: #28a745; 
            font-size: 1.4em;
            margin-top: 5px;
        }
        .certificate-name { 
            font-size: 2.2em; 
            font-weight: 900; 
            color: #d9534f; 
            margin: 20px 0; 
            display: block;
            border-bottom: 2px dashed #ccc;
            padding-bottom: 5px;
        }
        
        /* ESTILOS DEL SELLO CSS SIMPLE (Reemplazo del SVG) */
        #css-seal-container {
            width: 120px;
            height: 120px;
            background-color: #28a745; /* Verde menta */
            border-radius: 50%;
            margin: 0 auto 15px auto;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            border: 5px solid #0056b3; /* Borde azul */
            color: white;
            font-size: 10px;
            font-weight: bold;
            line-height: 1.1;
        }
        #seal-icon {
            font-size: 25px;
            margin-top: 5px;
        }
        /* --- Fin Estilos de Sello CSS --- */


        .signature-area {
            margin-top: 40px;
            text-align: center;
        }
        .signature-line {
            display: block;
            width: 70%;
            margin: 0 auto 5px auto;
            border-bottom: 1px solid #333;
        }
        .download-button {
            background-color: #d9534f;
            margin-top: 15px;
            padding: 10px 20px;
        }
        .download-button:hover {
            background-color: #c9302c;
        }
        
        /* Estilos generales */
        button { 
            padding: 12px 25px; background-color: #0056b3; color: white; border: none; border-radius: 5px; cursor: pointer; margin-top: 20px; font-size: 1.1em; transition: background-color 0.3s;
        }
        button:hover { 
            background-color: #004494; 
        }
        label { 
            display: block; margin: 8px 0; cursor: pointer;
        }
        label:hover {
            background-color: #f5f5f5;
        }
        .ranking-box {
            margin-top: 30px; padding: 15px; background-color: #f8f9fa; border: 1px solid #dee2e6; border-radius: 8px;
        }
        .ranking-box h3 {
            color: #d9534f; border-bottom: 2px solid #d9534f; padding-bottom: 5px; margin-bottom: 15px;
        }
        .ranking-box ol {
            list-style: none; padding: 0; text-align: left;
        }
        .ranking-box li {
            padding: 5px 0; border-bottom: 1px dotted #ccc; display: flex; justify-content: space-between; font-weight: 500;
        }
        .ranking-score {
            font-weight: bold; color: #0056b3;
        }
        .modal {
            display: none; position: fixed; z-index: 100; left: 0; top: 0; width: 100%; height: 100%; overflow: auto; background-color: rgba(0,0,0,0.7); 
        }
        .modal-content {
            background-color: #ffffff; margin: 15% auto; padding: 30px; border: 1px solid #888; width: 80%; max-width: 400px; border-radius: 10px; box-shadow: 0 5px 15px rgba(0,0,0,0.3); text-align: center;
        }
        #playerNameInput {
            padding: 10px; margin: 15px 0; width: 90%; border: 2px solid #ccc; border-radius: 5px; font-size: 1.1em;
        }
        #startQuizBtn {
            background-color: #28a745; 
        }
        #startQuizBtn:hover {
            background-color: #218838;
        }
    </style>
</head>
<body>

    <div id="name-modal" class="modal">
        <div class="modal-content">
            <h2>¡Bienvenido a la Trivia de Bluefields!</h2>
            <p>Por favor, ingresa tu nombre (o nickname) para empezar a jugar.</p>
            <input type="text" id="playerNameInput" placeholder="Tu nombre aquí..." maxlength="30">
            <button id="startQuizBtn" onclick="startGame()">Comenzar Trivia</button>
        </div>
    </div>
    <div class="container">
        <h1>Conocimiento de Bluefields: La Trivia</h1>
        <p>¡Hola, <span id="welcome-name">invitado</span>! Demuestra cuánto sabes sobre la historia de Bluefields.</p>
        <hr>

        <div id="quiz-container">
            </div>

        <button id="submitBtn" onclick="submitQuiz()">Finalizar y Obtener Certificado</button>
        <p id="result-message" style="margin-top: 15px; font-weight: bold;"></p>

        <div id="certificate" class="certificate-box">
            
            <div id="css-seal-container">
                INSTITUTO
                <div id="seal-icon">🎓</div>
                CARL RIGBY MOSES
            </div>
            <h3>Instituto Carl Rigby Moses</h3>

            <h2>Certificado de Reconocimiento</h2>
            <p style="font-size: 1.1em;">Otorgado a:</p>
            <span id="certified-name" class="certificate-name"></span>
            
            <p style="font-size: 1.2em; margin-top: 15px;">
                Por su *destacada participación* en la *Trivia Histórica de Bluefields* con una puntuación final de 
                <span id="final-score" style="color: #0056b3; font-weight: bold;"></span>/5.
            </p>
            
            <p style="font-size: 0.9em; margin-top: 30px;">
                Bluefields, Costa Caribe Sur, a los <span id="current-date"></span>.
            </p>
            
            <div class="signature-area">
                <span class="signature-line"></span>
                <p style="font-weight: bold; margin-bottom: 5px;">Lic. Holman Antonio López Vásquez</p>
                <p style="font-size: 0.9em; font-style: italic;">Director Instituto Carl Rigby Moses</p>
            </div>
            
            <button class="download-button" onclick="downloadCertificate()">⬇️ Descargar Certificado (PNG)</button>
        </div>

        <div id="ranking" class="ranking-box">
            <h3>🏆 Top 5 de la Historia de Bluefields 🏆</h3>
            <ol id="ranking-list">
                </ol>
        </div>
    </div>

    <script>
        // --- Variables Globales ---
        let userName = "Invitado";
        const STORAGE_KEY = 'bluefieldsTriviaRanking';

        // Definición de preguntas y respuestas
        const questions = [
            { question: "¿De qué corsario neerlandés se deriva el nombre 'Bluefields'?", options: ["Henry Morgan", "Abraham Blauvelt", "Francis Drake", "Capitán Kidd"], answer: "Abraham Blauvelt" },
            { question: "¿Qué edificio religioso emblemático en el barrio Punta Fría es conocido por ser el lugar de entierro de los primeros misioneros alemanes?", options: ["Catedral Nuestra Señora del Rosario", "Iglesia Católica del Barrio Central", "Cementerio Moravo", "Iglesia Adventista"], answer: "Cementerio Moravo" },
            { question: "¿Cuál es el nombre del centro que conserva piezas históricas, fotos y documentos sobre la cultura de la Costa Caribe?", options: ["Casa de la Cultura", "Museo Histórico Cultural BICU – CIDCA", "Centro de Artesanía Costeña", "Biblioteca Municipal"], answer: "Museo Histórico Cultural BICU – CIDCA" },
            { question: "¿En qué año Nicaragua anexó formalmente la Reserva de la Mosquitia, terminando la monarquía Miskita en Bluefields?", options: ["1920", "1894", "1850", "1903"], answer: "1894" },
            { question: "¿Cuál es el baile folclórico más representativo y emblemático de Bluefields que se celebra en Mayo?", options: ["Danza del Shauda", "Palo de Mayo (May Pole)", "El Baile del Machete", "Plot Role"], answer: "Palo de Mayo (May Pole)" }
        ];

        // --- Elementos del DOM ---
        const quizContainer = document.getElementById('quiz-container');
        const resultMessage = document.getElementById('result-message');
        const certificateBox = document.getElementById('certificate');
        const certifiedName = document.getElementById('certified-name');
        const finalScore = document.getElementById('final-score');
        const rankingList = document.getElementById('ranking-list');
        const welcomeName = document.getElementById('welcome-name');
        const currentDateElement = document.getElementById('current-date');

        // --- Funciones Adicionales ---
        function getFormattedDate() {
            const date = new Date();
            const day = date.getDate();
            const monthNames = ["Enero", "Febrero", "Marzo", "Abril", "Mayo", "Junio", "Julio", "Agosto", "Septiembre", "Octubre", "Noviembre", "Diciembre"];
            const month = monthNames[date.getMonth()];
            const year = date.getFullYear();
            return ${day} días del mes de ${month} del ${year};
        }
        
        // --- FUNCIÓN PARA DESCARGAR EL CERTIFICADO ---
        function downloadCertificate() {
            // Ocultar el botón de descarga temporalmente
            const downloadBtn = document.querySelector('.download-button');
            downloadBtn.style.display = 'none';

            // Usar html2canvas para renderizar el div del certificado en un canvas
            html2canvas(document.getElementById('certificate'), {
                scale: 2, // Aumentar la escala para mejor resolución
                useCORS: false 
            }).then(function(canvas) {
                // Restaurar el botón de descarga
                downloadBtn.style.display = 'block'; 

                // Convertir el canvas a una imagen de datos URL
                const image = canvas.toDataURL("image/png");
                
                // Crear un enlace temporal para forzar la descarga
                const link = document.createElement('a');
                link.download = Certificado_Bluefields_${userName.replace(/\s/g, '_')}.png;
                link.href = image;
                link.click();
            }).catch(error => {
                downloadBtn.style.display = 'block'; 
                alert("Hubo un error al generar la imagen. Intenta de nuevo.");
                console.error("Error al generar el canvas:", error);
            });
        }
        
        // --- Funciones de Ranking ---
        function loadRanking() {
            const rankingJson = localStorage.getItem(STORAGE_KEY);
            return rankingJson ? JSON.parse(rankingJson) : [];
        }

        function saveRanking(ranking) {
            localStorage.setItem(STORAGE_KEY, JSON.stringify(ranking));
        }

        function updateRanking(name, score) {
            let ranking = loadRanking();
            ranking.push({ name: name, score: score });
            ranking.sort((a, b) => b.score - a.score);
            ranking = ranking.slice(0, 5);
            saveRanking(ranking);
            displayRanking();
        }

        function displayRanking() {
            const ranking = loadRanking();
            rankingList.innerHTML = '';
            
            if (ranking.length === 0) {
                rankingList.innerHTML = '<li>Aún no hay puntuaciones. ¡Sé el primero!</li>';
                return;
            }

            ranking.forEach((entry, index) => {
                const li = document.createElement('li');
                li.innerHTML = <span>${index + 1}. ${entry.name}</span><span class="ranking-score">${entry.score} / ${questions.length}</span>;
                rankingList.appendChild(li);
            });
        }

        // --- Funciones de Juego ---
        function loadQuestions() {
            quizContainer.innerHTML = '';
            questions.forEach((q, index) => {
                const qBox = document.createElement('div');
                qBox.className = 'question-box';
                qBox.innerHTML = <p>${index + 1}. ${q.question}</p>;
                q.options.forEach(option => {
                    const inputId = q${index}-opt${option.replace(/\s/g, '')}; 
                    qBox.innerHTML += <label for="${inputId}"><input type="radio" id="${inputId}" name="question${index}" value="${option}">${option}</label>;
                });
                quizContainer.appendChild(qBox);
            });
        }

        function submitQuiz() {
            let score = 0;
            questions.forEach((q, index) => {
                const selector = input[name="question${index}"]:checked;
                const selected = document.querySelector(selector);
                if (selected && selected.value === q.answer) {
                    score++;
                }
            });

            const totalQuestions = questions.length;
            resultMessage.textContent = Tu puntuación es: ${score} de ${totalQuestions} respuestas correctas.;
            
            updateRanking(userName, score);

            if (score >= 3) {
                certifiedName.textContent = userName;
                finalScore.textContent = score;
                currentDateElement.textContent = getFormattedDate();
                certificateBox.style.display = 'block'; 
                document.getElementById('submitBtn').style.display = 'none'; 
                resultMessage.textContent = ¡Felicidades, ${userName}! Tu certificado ha sido generado.;
            } else {
                certificateBox.style.display = 'none';
                document.getElementById('submitBtn').style.display = 'none'; 
                resultMessage.textContent += " No has alcanzado la puntuación mínima (3/5) para el certificado. ¡Estudia la historia de Bluefields e inténtalo de nuevo!";
            }
        }

        function startGame() {
            const nameInput = document.getElementById('playerNameInput').value;
            
            if (nameInput && nameInput.trim() !== "") {
                userName = nameInput.trim();
            } else {
                userName = "Jugador Anónimo";
            }
            
            document.getElementById('name-modal').style.display = 'none';
            welcomeName.textContent = userName;
            loadQuestions();
        }

        function initializeGame() {
            document.getElementById('name-modal').style.display = 'block';
            displayRanking(); 
        }

        // Ejecutar la inicialización cuando la página cargue
        window.onload = initializeGame;
    </script>
</body>
</html>
