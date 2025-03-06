<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Compte à Rebours - Offre Spéciale</title>
    <style>
        .countdown-container {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #6EB9FC, #F888D2, #FD957D);
            color: white;
            border-radius: 10px;
            padding: 20px;
            text-align: center;
            max-width: 700px;
            margin: 0 auto;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }

        .countdown-header {
            font-size: 24px;
            font-weight: bold;
            margin-bottom: 10px;
        }

        .countdown-subheader {
            font-size: 16px;
            margin-bottom: 20px;
            opacity: 0.9;
        }

        .countdown-timer {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-bottom: 20px;
            flex-direction: row;
            align-items: center;
            flex-wrap: nowrap;
        }

        .countdown-box {
            background-color: rgba(255, 255, 255, 0.2);
            border-radius: 5px;
            padding: 10px;
            min-width: 70px;
            display: inline-block;
        }

        .countdown-value {
            font-size: 30px;
            font-weight: bold;
        }

        .countdown-label {
            font-size: 12px;
            text-transform: uppercase;
        }

        .countdown-cta {
            background-color: #ff6b6b;
            color: white;
            border: none;
            border-radius: 5px;
            padding: 12px 25px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .countdown-cta:hover {
            background-color: #ff5252;
        }

        .countdown-expired {
            font-size: 22px;
            font-weight: bold;
            display: none;
        }

        @media (max-width: 480px) {
            .countdown-timer {
                flex-wrap: nowrap;
                gap: 5px;
            }
            
            .countdown-box {
                min-width: 50px;
                padding: 5px;
            }
            
            .countdown-value {
                font-size: 18px;
            }
            
            .countdown-label {
                font-size: 10px;
            }
        }
    </style>
</head>
<body>
    <div class="countdown-container">
        <!-- Le titre a été supprimé -->
        <!-- Compte à rebours sans titre -->
        <div class="countdown-timer" id="countdown">
            <div class="countdown-box">
                <div class="countdown-value" id="days">00</div>
                <div class="countdown-label">J</div>
            </div>
            <div style="font-size: 24px; font-weight: bold;">:</div>
            <div class="countdown-box">
                <div class="countdown-value" id="hours">00</div>
                <div class="countdown-label">H</div>
            </div>
            <div style="font-size: 24px; font-weight: bold;">:</div>
            <div class="countdown-box">
                <div class="countdown-value" id="minutes">00</div>
                <div class="countdown-label">M</div>
            </div>
            <div style="font-size: 24px; font-weight: bold;">:</div>
            <div class="countdown-box">
                <div class="countdown-value" id="seconds">00</div>
                <div class="countdown-label">S</div>
            </div>
        </div>
        
        <div class="countdown-expired" id="expired">L'offre est terminée !</div>
        
        <button class="countdown-cta" id="cta-button">Profiter de l'offre maintenant</button>
    </div>

    <script>
        // Date de fin du compte à rebours (format: année, mois (0-11), jour, heure, minute, seconde)
        // Par défaut: 1 mois à partir d'aujourd'hui
        const currentDate = new Date();
        const targetDate = new Date();
        targetDate.setMonth(currentDate.getMonth() + 1);
        
        // Pour définir une date spécifique, décommentez la ligne ci-dessous et ajustez la date
        // const targetDate = new Date(2025, 3, 15, 23, 59, 59); // 15 avril 2025 à 23:59:59
        
        function updateCountdown() {
            const now = new Date();
            const diff = targetDate - now;
            
            if (diff <= 0) {
                // Le compte à rebours est terminé
                document.getElementById('countdown').style.display = 'none';
                document.getElementById('expired').style.display = 'block';
                return;
            }
            
            // Calcul des jours, heures, minutes et secondes restants
            const days = Math.floor(diff / (1000 * 60 * 60 * 24));
            const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((diff % (1000 * 60)) / 1000);
            
            // Mise à jour de l'affichage
            document.getElementById('days').innerText = days.toString().padStart(2, '0');
            document.getElementById('hours').innerText = hours.toString().padStart(2, '0');
            document.getElementById('minutes').innerText = minutes.toString().padStart(2, '0');
            document.getElementById('seconds').innerText = seconds.toString().padStart(2, '0');
        }
        
        // Mise à jour du compte à rebours toutes les secondes
        updateCountdown();
        setInterval(updateCountdown, 1000);
        
        // Action du bouton CTA
        document.getElementById('cta-button').addEventListener('click', function() {
            // Remplacez par l'URL de votre page d'offre
            window.location.href = 'https://votre-lien-offre.com';
        });
    </script>
</body>
</html>
