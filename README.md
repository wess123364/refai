<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Page d'Entrée avec Image et Vidéo</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            overflow: hidden;
            height: 100vh;
            font-family: 'Arial', sans-serif;
        }
        
        #media-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
        }
        
        #bg-image {
            width: 100%;
            height: 100%;
            object-fit: cover;
            display: block;
        }
        
        #bg-video {
            width: 100%;
            height: 100%;
            object-fit: cover;
            display: none;
        }
        
        #enter-button {
            position: absolute;
            bottom: 20%;
            left: 50%;
            transform: translateX(-50%);
            padding: 15px 40px;
            font-size: 22px;
            font-weight: bold;
            background: linear-gradient(45deg, rgba(255,255,255,0.2), rgba(255,255,255,0.4));
            color: white;
            border: 3px solid white;
            border-radius: 60px;
            cursor: pointer;
            backdrop-filter: blur(8px);
            transition: all 0.4s ease;
            box-shadow: 0 10px 25px rgba(0,0,0,0.3);
            text-transform: uppercase;
            letter-spacing: 2px;
            width: 80%;
            max-width: 300px;
        }
        
        #enter-button:hover {
            background: linear-gradient(45deg, rgba(255,255,255,0.3), rgba(255,255,255,0.5));
            transform: translateX(-50%) scale(1.05);
            box-shadow: 0 15px 30px rgba(0,0,0,0.4);
        }
        
        .loading-text {
            position: absolute;
            top: 70%;
            left: 50%;
            transform: translateX(-50%);
            color: white;
            font-size: 18px;
            opacity: 0;
            transition: opacity 0.5s ease;
            text-align: center;
            width: 100%;
        }
        
        @media (max-height: 600px) {
            #enter-button {
                bottom: 15%;
                padding: 12px 30px;
                font-size: 18px;
            }
        }
    </style>
</head>
<body>
    <div id="media-container">
        <!-- Image de fond initiale -->
        <img id="bg-image" src="w.png" alt="Image de fond">
        <!-- Vidéo qui remplacera l'image -->
        <video id="bg-video" muted>
            <source src="wess.mp4" type="video/mp4">
            Votre navigateur ne supporte pas les vidéos HTML5.
        </video>
    </div>
    
    <button id="enter-button">Entrer</button>
    <div class="loading-text" id="loading-text">Chargement...</div>
    
    <script>
        const bgImage = document.getElementById('bg-image');
        const video = document.getElementById('bg-video');
        const enterButton = document.getElementById('enter-button');
        const loadingText = document.getElementById('loading-text');
        
        // Quand on clique sur le bouton
        enterButton.addEventListener('click', function() {
            // Animation du bouton
            enterButton.style.transform = 'translateX(-50%) scale(0.9)';
            enterButton.style.opacity = '0';
            
            // Afficher le texte de chargement
            loadingText.style.opacity = '1';
            
            // Masquer l'image et afficher la vidéo
            bgImage.style.display = 'none';
            video.style.display = 'block';
            
            // Lancer la vidéo
            video.play();
            
            // Quand la vidéo se termine
            video.addEventListener('ended', function() {
                // Rediriger vers votre lien
                window.location.href = "https://slategray-seahorse-yan1rabng5sd5q7v.builder-preview.com/";
            }, {once: true});
            
            // Masquer complètement le bouton après l'animation
            setTimeout(() => {
                enterButton.style.display = 'none';
            }, 500);
        });
    </script>
</body>
</html>
