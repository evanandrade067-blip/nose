<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Evan-10: Terminal v74</title>
    <style>
        * { margin: 0; padding: 0; overflow: hidden; background: #000; color: #00ff00; font-family: 'Courier New', monospace; }
        body, html { height: 100%; width: 100%; display: flex; flex-direction: column; }

        /* Pantalla de Inicio con Instrucciones */
        #intro-screen {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: #000; z-index: 10000; display: flex; 
            flex-direction: column; align-items: center; justify-content: center;
            cursor: pointer; text-align: center; padding: 20px;
        }
        #identity-msg { font-size: 22px; color: #0f0; margin-bottom: 20px; text-shadow: 0 0 10px #0f0; }
        #manual { 
            border: 1px solid #004400; background: #050505; padding: 15px; 
            font-size: 11px; text-align: left; max-width: 450px; margin-bottom: 20px;
            color: #0f0;
        }
        .blink { animation: blinker 1.5s linear infinite; color: #ff0; }
        @keyframes blinker { 50% { opacity: 0; } }

        /* Interfaz Samsumg */
        #nav-bar { background: #050505; border-bottom: 1px solid #00ff00; padding: 10px; display: flex; gap: 10px; align-items: center; z-index: 500; }
        button, .file-label { background: #000; color: #0f0; border: 1px solid #00ff00; padding: 6px 12px; cursor: pointer; font-size: 10px; }
        input[type="file"] { display: none; }
        
        #viewport { flex-grow: 1; width: 100%; background: #000; }
        iframe { width: 100%; height: 100%; border: none; background: #fff; }
        
        .status { position: fixed; bottom: 5px; right: 10px; font-size: 9px; color: #004400; }
    </style>
</head>
<body>

    <audio id="bg-music" loop></audio>

    <div id="intro-screen" onclick="entrarBalsa()">
        <div id="identity-msg">Hello, my name is protect... :]</div>
        
        <div id="manual">
            <p style="color: #ff0; border-bottom: 1px solid #ff0; margin-bottom: 5px;">[ MANUAL DE LA BALSA v74 ]</p>
            1. Toca para iniciar el sistema limpio.<br>
            2. Usa <b>"ELEGIR MP3"</b> para cargar <i>Rainy Day Reflections</i>.<br>
            3. El sistema cargará Shuttle Math directamente.<br>
            4. <b>Protect</b> vigila la seguridad de la terminal.<br>
            5. <b>Carbón</b> está en modo espera en la barra inferior.<br>
            <br>
            <span style="color: #444;">ID: EVAN-10 // TERM: SAMSUMG // PET: CARBÓN 🐾</span>
        </div>

        <p class="blink">[ EJECUTAR PROTOCOLO ]</p>
    </div>

    <div id="nav-bar">
        <label for="mp3-input" class="file-label">🎵 ELEGIR MP3</label>
        <input type="file" id="mp3-input" accept="audio/mpeg">
        
        <button onclick="execGame('https://shuttlemath.com/')">🚀 SHUTTLE MATH</button>
        
        <button id="m-btn" onclick="toggleAudio()" style="color: #ff0;">⏯️ AUDIO: OFF</button>
    </div>

    <div id="viewport">
        <iframe id="engine" src="about:blank"></iframe>
    </div>

    <div class="status">EVAN-10 // SAMSUMG // CARBÓN 🐾</div>

    <script>
        const music = document.getElementById('bg-music');
        const mBtn = document.getElementById('m-btn');
        const fileIn = document.getElementById('mp3-input');
        const intro = document.getElementById('intro-screen');

        fileIn.onchange = function(e) {
            const file = e.target.files[0];
            if(file) {
                music.src = URL.createObjectURL(file);
                music.play();
                mBtn.innerText = "🎵 AUDIO: ON";
            }
        };

        function entrarBalsa() {
            intro.style.opacity = '0';
            setTimeout(() => intro.style.display = 'none', 500);
        }

        function toggleAudio() {
            if (music.paused) { music.play(); mBtn.innerText = "🎵 AUDIO: ON"; }
            else { music.pause(); mBtn.innerText = "🎵 AUDIO: OFF"; }
        }

        // --- TU CÓDIGO DE REDIRECCIÓN REINTEGRADO ---
        function execGame(url) {
            let finalUrl = url;

            if(url.includes('github.com') && !url.includes('githack')) {
                finalUrl = 'https://raw.githack.com' + url.split('com')[1];
            }

            document.getElementById('engine').src = finalUrl;
            console.log("Cargando: " + finalUrl);
        }
    </script>
</body>
</html>
