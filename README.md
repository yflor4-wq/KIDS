<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RAEE KIDS - ¡A reciclar se ha dicho!</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;700;900&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Nunito', sans-serif;
        }
        .bg-gradient-raee {
            background: linear-gradient(135deg, #4ade80, #3b82f6);
        }
        .hidden {
            display: none;
        }
        /* Animación de entrada */
        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.9); }
            to { opacity: 1; transform: scale(1); }
        }
        .fade-in {
            animation: fadeIn 0.8s ease-out forwards;
        }
        /* Spinner de carga */
        .loader {
            border: 4px solid #f3f3f3;
            border-top: 4px solid #3498db;
            border-radius: 50%;
            width: 30px;
            height: 30px;
            animation: spin 1s linear infinite;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body class="bg-gray-100">

    <!-- Contenedor principal de la aplicación -->
    <div id="app-container" class="max-w-md mx-auto h-screen bg-white overflow-hidden shadow-2xl">

        <!-- 1. Pantalla de Inicio (Splash Screen) -->
        <div id="splash-screen" class="w-full h-full bg-gradient-raee flex flex-col justify-center items-center text-white text-center p-8 fade-in">
            <div class="mb-8">
                <!-- Logo de RAEE KIDS -->
                <svg class="w-40 h-40 mx-auto" viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <circle cx="50" cy="50" r="48" fill="white"/>
                    <path d="M50 28C43.3726 28 38 33.3726 38 40V48H62V40C62 33.3726 56.6274 28 50 28Z" fill="#4ade80"/>
                    <path d="M35 52H65V68C65 71.3137 62.3137 74 59 74H41C37.6863 74 35 71.3137 35 68V52Z" fill="#3b82f6"/>
                    <circle cx="43" cy="40" r="4" fill="white"/>
                    <circle cx="57" cy="40" r="4" fill="white"/>
                    <path d="M45 62H55" stroke="white" stroke-width="3" stroke-linecap="round"/>
                </svg>
            </div>
            <h1 class="text-5xl font-black mb-4">¡Hola!</h1>
            <p class="text-xl font-bold">Bienvenido a RAEE KIDS</p>
            <p class="mt-4">¡El planeta te necesita! Juntos aprenderemos a reciclar los aparatos electrónicos de forma divertida.</p>
        </div>

        <!-- 2. Pantalla de Autenticación (Login/Registro) -->
        <div id="auth-screen" class="hidden w-full h-full bg-gray-50 flex flex-col justify-center p-8">
            <div class="text-center mb-8">
                <svg class="w-24 h-24 mx-auto text-green-400" viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <circle cx="50" cy="50" r="48" fill="#4ade80"/>
                    <path d="M35 52H65V68C65 71.3137 62.3137 74 59 74H41C37.6863 74 35 71.3137 35 68V52Z" fill="#3b82f6"/>
                    <path d="M50 28C43.3726 28 38 33.3726 38 40V48H62V40C62 33.3726 56.6274 28 50 28Z" fill="white"/>
                    <circle cx="43" cy="40" r="3" fill="#3b82f6"/>
                    <circle cx="57" cy="40" r="3" fill="#3b82f6"/>
                </svg>
                <h2 class="text-3xl font-bold text-gray-800 mt-4">Únete a la Aventura</h2>
            </div>
            
            <div id="register-form">
                <h3 class="text-xl font-bold text-center mb-4 text-gray-700">Crea tu cuenta de Héroe</h3>
                <input type="text" id="register-name" placeholder="Tu nombre de héroe" class="w-full p-3 mb-4 border-2 border-gray-200 rounded-lg focus:outline-none focus:border-green-400">
                <input type="email" placeholder="Correo de tus papás" class="w-full p-3 mb-4 border-2 border-gray-200 rounded-lg focus:outline-none focus:border-green-400">
                <input type="password" placeholder="Crea una contraseña secreta" class="w-full p-3 mb-4 border-2 border-gray-200 rounded-lg focus:outline-none focus:border-green-400">
                <button id="register-btn" class="w-full px-6 py-3 font-bold text-white rounded-full shadow-lg transform transition-transform duration-200 hover:scale-105 bg-green-500 hover:bg-green-600">¡Crear mi cuenta!</button>
            </div>
            
            <p class="text-center mt-4 text-gray-600">¿Ya tienes una cuenta? <a href="#" id="show-login-link" class="font-bold text-blue-500">Inicia sesión</a></p>

            <div id="login-form" class="hidden">
                 <h3 class="text-xl font-bold text-center mb-4 text-gray-700">¡Qué bueno verte!</h3>
                 <input type="text" id="login-name" placeholder="Tu nombre de héroe" class="w-full p-3 mb-4 border-2 border-gray-200 rounded-lg focus:outline-none focus:border-blue-400">
                 <input type="password" placeholder="Tu contraseña secreta" class="w-full p-3 mb-4 border-2 border-gray-200 rounded-lg focus:outline-none focus:border-blue-400">
                 <button id="login-btn" class="w-full px-6 py-3 font-bold text-white rounded-full shadow-lg transform transition-transform duration-200 hover:scale-105 bg-blue-500 hover:bg-blue-600">¡Entrar!</button>
            </div>
        </div>

        <!-- 3. Pantalla de Motivación -->
        <div id="motivation-screen" class="hidden w-full h-full bg-gradient-raee flex flex-col justify-center items-center text-white text-center p-8">
            <h2 class="text-4xl font-black mb-4">¡GENIAL!</h2>
            <p class="text-xl mb-8">¡Ahora eres parte del equipo de Héroes del Planeta! Cada pequeño aparato que reciclas es un súper poder que usas para proteger nuestro hogar. ¡Estamos muy orgullosos de ti!</p>
            <button id="start-mission-btn" class="px-6 py-3 font-bold text-gray-800 rounded-full shadow-lg transform transition-transform duration-200 hover:scale-105 bg-yellow-400 hover:bg-yellow-500">¡Comenzar la aventura!</button>
        </div>

        <!-- 4. Panel Principal (Dashboard) -->
        <div id="dashboard-screen" class="hidden w-full h-full flex flex-col p-6 bg-gray-50 overflow-y-auto">
            <header class="mb-6">
                <h2 class="text-3xl font-bold text-gray-800">Hola, <span id="hero-name">Héroe</span></h2>
                <p class="text-gray-600">¿Qué misión cumpliremos hoy?</p>
            </header>
            
            <div class="grid grid-cols-2 gap-4 flex-grow">
                <div data-target="games-screen" class="nav-card p-6 rounded-2xl shadow-xl transform transition-transform duration-300 hover:scale-105 hover:shadow-2xl cursor-pointer col-span-2 bg-yellow-400 text-gray-800 flex flex-col justify-center items-center">
                    <h3 class="text-2xl font-black">Juegos</h3>
                    <p>¡Aprende y diviértete!</p>
                </div>
                 <div data-target="missions-screen" class="nav-card p-6 rounded-2xl shadow-xl transform transition-transform duration-300 hover:scale-105 hover:shadow-2xl cursor-pointer bg-red-500 text-white flex flex-col justify-center items-center">
                    <h3 class="text-xl font-black">Misiones ✨</h3>
                    <p>¡Gana puntos!</p>
                </div>
                <div data-target="map-screen" class="nav-card p-6 rounded-2xl shadow-xl transform transition-transform duration-300 hover:scale-105 hover:shadow-2xl cursor-pointer bg-blue-500 text-white flex flex-col justify-center items-center">
                    <h3 class="text-xl font-black">Mapas</h3>
                    <p>Encuentra Puntos</p>
                </div>
                <div data-target="search-screen" class="nav-card p-6 rounded-2xl shadow-xl transform transition-transform duration-300 hover:scale-105 hover:shadow-2xl cursor-pointer col-span-2 bg-green-500 text-white flex flex-col justify-center items-center">
                    <h3 class="text-2xl font-black">Búsqueda RAEE ✨</h3>
                     <p>Resuelve tus dudas</p>
                </div>
                 <div data-target="news-screen" class="nav-card p-6 rounded-2xl shadow-xl transform transition-transform duration-300 hover:scale-105 hover:shadow-2xl cursor-pointer bg-purple-500 text-white flex flex-col justify-center items-center">
                    <h3 class="text-xl font-black">Noticias</h3>
                </div>
                <div data-target="family-screen" class="nav-card p-6 rounded-2xl shadow-xl transform transition-transform duration-300 hover:scale-105 hover:shadow-2xl cursor-pointer bg-pink-400 text-white flex flex-col justify-center items-center">
                    <h3 class="text-xl font-black">Familia</h3>
                </div>
                 <div data-target="schools-screen" class="nav-card p-6 rounded-2xl shadow-xl transform transition-transform duration-300 hover:scale-105 hover:shadow-2xl cursor-pointer col-span-2 bg-indigo-500 text-white flex flex-col justify-center items-center">
                    <h3 class="text-2xl font-black">Colegios</h3>
                </div>
            </div>
        </div>
        
        <!-- Pantallas de Secciones -->
        <div id="content-screens" class="hidden w-full h-full flex flex-col bg-gray-50 overflow-y-auto">
            <header class="p-4 bg-white shadow-md flex items-center">
                <button class="back-btn text-blue-500 font-bold">&lt; Volver</button>
                <h2 id="content-title" class="text-xl font-bold text-gray-800 text-center flex-grow">Sección</h2>
            </header>
            <div id="content-body" class="p-6">
                <!-- El contenido se inyectará aquí -->
            </div>
        </div>

    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            // --- Nodos del DOM ---
            const screens = {
                splash: document.getElementById('splash-screen'),
                auth: document.getElementById('auth-screen'),
                motivation: document.getElementById('motivation-screen'),
                dashboard: document.getElementById('dashboard-screen'),
                content: document.getElementById('content-screens'),
            };

            const registerForm = document.getElementById('register-form');
            const loginForm = document.getElementById('login-form');
            const registerBtn = document.getElementById('register-btn');
            const loginBtn = document.getElementById('login-btn');
            const showLoginLink = document.getElementById('show-login-link');
            const startMissionBtn = document.getElementById('start-mission-btn');
            const heroNameSpan = document.getElementById('hero-name');
            const navCards = document.querySelectorAll('.nav-card');
            const backBtns = document.querySelectorAll('.back-btn');
            const contentTitle = document.getElementById('content-title');
            const contentBody = document.getElementById('content-body');
            
            let currentHeroName = 'Héroe';

            // --- Lógica de Navegación ---
            function showScreen(screenName) {
                Object.values(screens).forEach(screen => screen.classList.add('hidden'));
                if (screens[screenName]) {
                    screens[screenName].classList.remove('hidden');
                    screens[screenName].classList.add('fade-in');
                }
            }

            // --- Flujo de la aplicación ---
            setTimeout(() => { showScreen('auth'); }, 3000);

            showLoginLink.addEventListener('click', (e) => {
                e.preventDefault();
                registerForm.classList.add('hidden');
                loginForm.classList.remove('hidden');
            });

            registerBtn.addEventListener('click', () => {
                const name = document.getElementById('register-name').value;
                if (name.trim() !== "") currentHeroName = name.trim();
                showScreen('motivation');
            });

            loginBtn.addEventListener('click', () => {
                const name = document.getElementById('login-name').value;
                if (name.trim() !== "") currentHeroName = name.trim();
                heroNameSpan.textContent = currentHeroName;
                showScreen('dashboard');
            });
            
            startMissionBtn.addEventListener('click', () => {
                heroNameSpan.textContent = currentHeroName;
                showScreen('dashboard');
            });

            navCards.forEach(card => {
                card.addEventListener('click', () => {
                    const targetScreenId = card.dataset.target;
                    loadContent(targetScreenId);
                    showScreen('content');
                });
            });

            backBtns.forEach(btn => {
                btn.addEventListener('click', () => {
                    showScreen('dashboard');
                });
            });

            // --- Funcionalidad de la API de Gemini ---
            const API_KEY = ""; // Canvas will provide this
            const API_URL = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-05-20:generateContent?key=${API_KEY}`;

            async function callGeminiAPI(prompt, retries = 3, delay = 1000) {
                try {
                    const payload = {
                        contents: [{ parts: [{ text: prompt }] }],
                    };
                    const response = await fetch(API_URL, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify(payload)
                    });
                    if (!response.ok) {
                        throw new Error(`HTTP error! status: ${response.status}`);
                    }
                    const result = await response.json();
                    return result.candidates?.[0]?.content?.parts?.[0]?.text || "";
                } catch (error) {
                    if (retries > 0) {
                        await new Promise(res => setTimeout(res, delay));
                        return callGeminiAPI(prompt, retries - 1, delay * 2);
                    }
                    console.error("Error calling Gemini API:", error);
                    return "¡Uy! Mis circuitos se cruzaron. Inténtalo de nuevo más tarde.";
                }
            }

            // --- Contenido de las Secciones ---
            function loadContent(screenId) {
                let title = '';
                let htmlContent = '';

                switch(screenId) {
                    case 'games-screen':
                        title = 'Juegos Divertidos';
                        htmlContent = `
                            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                                <div class="p-4 bg-white rounded-lg shadow">
                                    <h3 class="font-bold text-lg">Trivia RAEE</h3>
                                    <p class="text-sm text-gray-600">¿Cuánto sabes de reciclaje?</p>
                                </div>
                                <div class="p-4 bg-white rounded-lg shadow">
                                    <h3 class="font-bold text-lg">Separa y Gana</h3>
                                    <p class="text-sm text-gray-600">Arrastra cada residuo a su contenedor.</p>
                                </div>
                                <div class="p-4 bg-gray-200 rounded-lg shadow text-gray-500">
                                    <h3 class="font-bold text-lg">Aventura Ecológica</h3>
                                    <p class="text-sm">Próximamente...</p>
                                </div>
                            </div>`;
                        break;
                    case 'missions-screen':
                        title = 'Misiones Semanales';
                        htmlContent = `
                            <button id="generate-missions-btn" class="w-full mb-4 px-6 py-3 font-bold text-white rounded-full shadow-lg transform transition-transform duration-200 hover:scale-105 bg-red-500 hover:bg-red-600">✨ Generar Nuevas Misiones</button>
                            <div id="missions-list" class="space-y-3">
                                <p class="text-center text-gray-500">¡Haz clic en el botón para obtener misiones!</p>
                            </div>`;
                        break;
                    case 'map-screen':
                        title = 'Puntos de Reciclaje';
                        htmlContent = `
                            <p class="mb-4 text-gray-700">Encuentra el punto de recolección más cercano en tu ciudad para llevar tus RAEE.</p>
                            <div class="bg-white rounded-lg shadow p-2">
                                <img src="https://placehold.co/600x400/e2e8f0/334155?text=Mapa+de+tu+Ciudad" alt="Mapa con puntos de reciclaje" class="w-full h-auto rounded-md">
                            </div>`;
                        break;
                    case 'search-screen':
                        title = 'Búsqueda RAEE';
                        htmlContent = `
                            <div class="relative flex items-center gap-2">
                                <input id="search-input" type="text" placeholder="¿Qué es una batería?" class="w-full p-3 pl-10 border-2 rounded-full">
                                <span class="absolute left-3 top-3.5 text-gray-400">🔍</span>
                                <button id="search-btn" class="px-4 py-2 font-bold text-white rounded-full shadow-lg bg-green-500 hover:bg-green-600">✨</button>
                            </div>
                            <div id="search-results" class="mt-4 p-4 bg-green-100 border-l-4 border-green-500 text-green-700 rounded-lg min-h-[80px]">
                                <p>¡Hola! Soy Reec-O. Pregúntame lo que quieras sobre el reciclaje de aparatos electrónicos.</p>
                            </div>`;
                        break;
                     case 'news-screen':
                         title = 'Noticias del Planeta';
                         htmlContent = `
                            <div class="space-y-4">
                               <div class="p-4 bg-white rounded-lg shadow">
                                    <h3 class="font-bold text-lg">¡Nuevo centro de acopio en la ciudad!</h3>
                                    <p class="text-sm text-gray-600">Se inauguró un nuevo lugar para que todos podamos reciclar.</p>
                                </div>
                                <div class="p-4 bg-white rounded-lg shadow">
                                    <h3 class="font-bold text-lg">Colegios se unen al reto RAEE.</h3>
                                    <p class="text-sm text-gray-600">Más de 20 escuelas competirán para ver quién recicla más.</p>
                                </div>
                            </div>`;
                        break;
                    case 'family-screen':
                        title = 'Equipo Familia';
                        htmlContent = `<p class="text-center text-gray-600">Aquí tus papás podrán ver tus logros, medallas y misiones completadas. ¡Invítalos a reciclar contigo!</p>`;
                        break;
                    case 'schools-screen':
                         title = 'Reto Colegios';
                        htmlContent = `<p class="text-center text-gray-600">Profesores, aquí pueden registrar a su clase, asignar misiones grupales y competir con otros colegios para ser los campeones del reciclaje.</p>`;
                        break;
                    default:
                        title = 'Error';
                        htmlContent = `<p>Contenido no encontrado.</p>`;
                }
                contentTitle.textContent = title;
                contentBody.innerHTML = htmlContent;

                // Añadir listeners para los nuevos botones de IA
                if (screenId === 'missions-screen') {
                    document.getElementById('generate-missions-btn').addEventListener('click', generateMissions);
                }
                if (screenId === 'search-screen') {
                    document.getElementById('search-btn').addEventListener('click', askReeco);
                }
            }

            async function generateMissions() {
                const missionsList = document.getElementById('missions-list');
                missionsList.innerHTML = '<div class="flex justify-center"><div class="loader"></div></div>';
                
                const prompt = `Genera una lista de 3 misiones semanales, divertidas y creativas para un niño sobre reciclaje de aparatos electrónicos (RAEE). Deben ser cosas que pueda hacer en casa o con su familia. Responde solo con un array JSON de strings. Por ejemplo: ["Misión 1", "Misión 2", "Misión 3"]. Responde en español.`;
                
                const responseText = await callGeminiAPI(prompt);
                
                try {
                    const missions = JSON.parse(responseText);
                    missionsList.innerHTML = missions.map(mission => 
                        `<li class="p-4 bg-white rounded-lg shadow flex items-center"><input type="checkbox" class="mr-3 h-5 w-5 flex-shrink-0">${mission}</li>`
                    ).join('');
                } catch (e) {
                    console.error("Error parsing missions JSON:", e);
                    missionsList.innerHTML = `<p class="text-red-500 text-center">No pude generar nuevas misiones. ¡Inténtalo de nuevo!</p>`;
                }
            }

            async function askReeco() {
                const searchInput = document.getElementById('search-input');
                const searchResults = document.getElementById('search-results');
                const query = searchInput.value;

                if (!query.trim()) {
                    searchResults.innerHTML = '<p class="text-red-500">Por favor, escribe una pregunta.</p>';
                    return;
                }

                searchResults.innerHTML = '<div class="flex justify-center"><div class="loader"></div></div>';
                const prompt = `Eres Reec-O, un robot amigable y experto en reciclaje de aparatos electrónicos (RAEE). Un niño te ha preguntado: "${query}". Explica la respuesta de forma muy simple, divertida y fácil de entender para un niño de 10 años. Usa emojis. Sé breve (máximo 3 frases). Responde en español.`;

                const responseText = await callGeminiAPI(prompt);
                searchResults.innerHTML = `<p>${responseText}</p>`;
                searchInput.value = '';
            }

        });
    </script>
</body>
</html>
