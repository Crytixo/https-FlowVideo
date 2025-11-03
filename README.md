FlowVideo/
│
├── index.html
├── signup.html
├── style.css
├── script.js
└── manifest.json
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FlowVideo 🎥</title>
    <link rel="stylesheet" href="style.css">
    <link rel="manifest" href="manifest.json">
</head>
<body>
    <header>
        <h1>🌈 FlowVideo</h1>
        <nav>
            <a href="index.html">Accueil</a>
            <a href="signup.html" id="signupLink">S'inscrire</a>
        </nav>
    </header>

    <main>
        <section id="upload">
            <h2>Publier une vidéo</h2>
            <input type="file" id="videoInput" accept="video/*">
            <button class="btn" onclick="uploadVideo()">📤 Publier</button>
        </section>

        <section id="videos">
            <h2>🎬 Vidéos récentes</h2>
            <div id="videoList"></div>
        </section>
    </main>

    <footer>
        <p>© 2025 FlowVideo — Créé par 
            <a href="https://youtube.com/@crytixo_officiel?si=SE9cqjsjUB2weFni" target="_blank">@Crytixo</a>
        </p>
    </footer>

    <script src="script.js"></script>
</body>
</html>
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Inscription - FlowVideo</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <main>
        <section>
            <h2>Créer un compte FlowVideo 🚀</h2>
            <form onsubmit="signup(event)">
                <input type="text" id="username" placeholder="Nom d'utilisateur" required><br>
                <input type="email" id="email" placeholder="Email" required><br>
                <input type="password" id="password" placeholder="Mot de passe" required><br>
                <button type="submit" class="btn">S'inscrire</button>
            </form>
        </section>
    </main>

    <script>
        function signup(event) {
            event.preventDefault();
            const email = document.getElementById("email").value;
            localStorage.setItem("userEmail", email);
            alert("Inscription réussie ! Bienvenue sur FlowVideo 🎬");
            window.location.href = "index.html";
        }
    </script>
</body>
</html>
body {
    font-family: 'Poppins', sans-serif;
    background: linear-gradient(135deg, #0d0d0d, #1a1a40);
    color: #fff;
    margin: 0;
    padding: 0;
}

header {
    background: linear-gradient(90deg, #00aaff, #6a00ff);
    color: white;
    padding: 15px;
    text-align: center;
    box-shadow: 0 2px 10px rgba(0,0,0,0.4);
}

h1 {
    margin: 0;
}

nav a {
    color: #fff;
    margin: 0 15px;
    text-decoration: none;
    font-weight: 500;
    transition: 0.3s;
}

nav a:hover {
    text-decoration: underline;
}

main {
    padding: 20px;
    text-align: center;
}

section {
    margin: 20px auto;
    background: rgba(255, 255, 255, 0.05);
    border-radius: 10px;
    padding: 20px;
    width: 90%;
    max-width: 600px;
    box-shadow: 0 0 20px rgba(0,0,0,0.3);
}

input[type="file"], input[type="text"], input[type="email"], input[type="password"] {
    background: #222;
    border: 2px solid #00aaff;
    padding: 10px;
    color: #fff;
    border-radius: 8px;
    margin-bottom: 10px;
    width: 90%;
}

.btn {
    background: linear-gradient(90deg, #00aaff, #6a00ff);
    border: none;
    color: white;
    padding: 10px 20px;
    border-radius: 8px;
    cursor: pointer;
    transition: 0.3s;
}

.btn:hover {
    transform: scale(1.05);
    box-shadow: 0 0 15px #6a00ff;
}

video {
    width: 100%;
    border-radius: 10px;
    margin-top: 10px;
}

footer {
    background: #111;
    color: #aaa;
    text-align: center;
    padding: 10px;
    font-size: 0.9em;
    border-top: 1px solid #222;
}

footer a {
    color: #00aaff;
    text-decoration: none;
}
// ===== GESTION DU CRÉATEUR =====
const CREATOR_EMAIL = "crytixo@flowvideo.com"; // Ton email ou pseudo
const currentUser = localStorage.getItem("userEmail");

// Si c’est toi (le créateur)
if (currentUser === CREATOR_EMAIL) {
    console.log("Bienvenue Créateur Crytixo 👑");
    const signupLink = document.querySelector('a[href="signup.html"]');
    if (signupLink) signupLink.style.display = "none"; // Cache le lien d’inscription
} else if (!currentUser) {
    // Redirige les autres vers l'inscription
    window.location.href = "signup.html";
}

// ===== UPLOAD VIDÉO =====
function uploadVideo() {
    const input = document.getElementById('videoInput');
    if (input.files.length > 0) {
        const file = input.files[0];
        const videoList = document.getElementById('videoList');
        const video = document.createElement('video');
        video.controls = true;
        video.src = URL.createObjectURL(file);
        videoList.prepend(video);
    } else {
        alert('🎥 Sélectionne une vidéo d’abord.');
    }
}
{
  "name": "FlowVideo",
  "short_name": "FlowVideo",
  "start_url": "index.html",
  "display": "standalone",
  "background_color": "#0d0d0d",
  "theme_color": "#6a00ff",
  "icons": [
    {
      "src": "icon.png",
      "sizes": "192x192",
      "type": "image/png"
    }
  ]
}
