# valentine-project<!DOCTYPE html>  <html lang="en">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>Will You Be My Valentine? 💕</title>  
    <link rel="stylesheet" href="styles.css">  
</head>  
<body>  
    <div class="container">  
        <div class="valentine-card">  
            <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExcDdtZ2JiZDR0a3lvMWF4OG8yc3p6Ymdvd3g2d245ZnoyZWZjd3RvNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/G2BYuzXRG8erK/giphy.gif" alt="Cute Bear" class="gif">  
            <h1 class="question">Will You Be My Valentine? 💖</h1>  
            <div class="buttons">  
                <button id="yesButton" onclick="handleYesClick()">Yes 😍</button>  
                <button id="noButton" onclick="handleNoClick()">No 😢</button>  
            </div>  
        </div>  
    </div>  
    <script src="script.js"></script>  
</body>  
</html>  
* {  
    margin: 0;  
    padding: 0;  
    box-sizing: border-box;  
}  body {
font-family: 'Arial', sans-serif;
background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 50%, #ffecd2 100%);
height: 100vh;
display: flex;
justify-content: center;
align-items: center;
overflow: hidden;
}

.container {
text-align: center;
}

.valentine-card {
background: white;
padding: 40px;
border-radius: 30px;
box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
max-width: 500px;
animation: fadeIn 1s ease-in;
}

@keyframes fadeIn {
from { opacity: 0; transform: scale(0.8); }
to { opacity: 1; transform: scale(1); }
}

.gif {
width: 200px;
height: 200px;
margin-bottom: 20px;
border-radius: 15px;
}

.question {
font-size: 2rem;
color: #ff1744;
margin-bottom: 30px;
animation: pulse 2s infinite;
}

@keyframes pulse {
0%, 100% { transform: scale(1); }
50% { transform: scale(1.05); }
}

.buttons {
display: flex;
gap: 20px;
justify-content: center;
margin-top: 30px;
}

button {
padding: 15px 40px;
font-size: 1.2rem;
border: none;
border-radius: 50px;
cursor: pointer;
transition: all 0.3s ease;
font-weight: bold;
}

#yesButton {
background: linear-gradient(135deg, #ff6b6b, #ff1744);
color: white;
box-shadow: 0 10px 30px rgba(255, 23, 68, 0.4);
}

#yesButton:hover {
transform: scale(1.1);
box-shadow: 0 15px 40px rgba(255, 23, 68, 0.6);
}

#noButton {
background: linear-gradient(135deg, #d3d3d3, #a9a9a9);
color: #333;
box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
position: relative;
}

#noButton:hover {
background: linear-gradient(135deg, #b8b8b8, #8c8c8c);
}

/* Responsive Design */
@media (max-width: 600px) {
.valentine-card {
padding: 30px;
margin: 20px;
}

.question {  
    font-size: 1.5rem;  
}  
  
.gif {  
    width: 150px;  
    height: 150px;  
}

}
let noClickCount = 0;
let yesSizeMultiplier = 1;

const noMessages = [
"Are you sure? 🥺",
"Really? 💔",
"Think again! 😢",
"Don't do this to me 😭",
"You're breaking my heart! 💔",
"Please reconsider 🥹",
"I'm begging you! 🙏",
"Final chance! ❤️",
"Okay, but... why? 😔"
];

function handleNoClick() {
const noButton = document.getElementById('noButton');
const yesButton = document.getElementById('yesButton');

// Change the No button text  
if (noClickCount < noMessages.length) {  
    noButton.textContent = noMessages[noClickCount];  
    noClickCount++;  
}  
  
// Make the Yes button bigger  
yesSizeMultiplier += 0.3;  
yesButton.style.transform = `scale(${yesSizeMultiplier})`;  
  
// Move the No button to a random position  
const maxX = window.innerWidth - noButton.offsetWidth - 100;  
const maxY = window.innerHeight - noButton.offsetHeight - 100;  
  
const randomX = Math.floor(Math.random() * maxX);  
const randomY = Math.floor(Math.random() * maxY);  
  
noButton.style.position = 'fixed';  
noButton.style.left = randomX + 'px';  
noButton.style.top = randomY + 'px';

}

function handleYesClick() {
// Redirect to yes page or show celebration
window.location.href = 'yes_page.html';
}

<!DOCTYPE html>  <html lang="en">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>Yay! 💕</title>  
    <link rel="stylesheet" href="yes_style.css">  
</head>  
<body>  
    <div class="celebration">  
        <h1 class="success-message">Yay! 🎉💕</h1>  
        <p class="subtitle">I knew you'd say yes! ❤️</p>  
        <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbTF3ZDZvZ2o4cDY3YnM2ZWh5aXR6Nm1qYm1hYnNxaml5bWJ1YnVwYiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/l0MYt5jPR6QX5pnqM/giphy.gif" alt="Celebration" class="celebration-gif">  
        <canvas id="fireworks"></canvas>  
    </div>  <script>  
    // Fireworks animation  
    const canvas = document.getElementById('fireworks');  
    const ctx = canvas.getContext('2d');  
    canvas.width = window.innerWidth;  
    canvas.height = window.innerHeight;  

    class Particle {  
        constructor(x, y) {  
            this.x = x;  
            this.y = y;  
            this.vx = (Math.random() - 0.5) * 8;  
            this.vy = (Math.random() - 0.5) * 8;  
            this.alpha = 1;  
            this.color = `hsl(${Math.random() * 360}, 100%, 50%)`;  
        }  

        update() {  
            this.x += this.vx;  
            this.y += this.vy;  
            this.vy += 0.2;  
            this.alpha -= 0.01;  
        }  

        draw() {  
            ctx.globalAlpha = this.alpha;  
            ctx.fillStyle = this.color;  
            ctx.fillRect(this.x, this.y, 3, 3);  
        }  
    }  

    let particles = [];  

    function createFirework() {  
        const x = Math.random() * canvas.width;  
        const y = Math.random() * canvas.height / 2;  
        for (let i = 0; i < 50; i++) {  
            particles.push(new Particle(x, y));  
        }  
    }  

    function animate() {  
        ctx.fillStyle = 'rgba(0, 0, 0, 0.1)';  
        ctx.fillRect(0, 0, canvas.width, canvas.height);  
          
        particles = particles.filter(p => p.alpha > 0);  
        particles.forEach(p => {  
            p.update();  
            p.draw();  
        });  

        requestAnimationFrame(animate);  
    }  

    setInterval(createFirework, 500);  
    animate();  
</script>

</body>  
</html>  
* {  
    margin: 0;  
    padding: 0;  
}  body {
background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
height: 100vh;
display: flex;
justify-content: center;
align-items: center;
overflow: hidden;
}

.celebration {
text-align: center;
z-index: 10;
position: relative;
}

.success-message {
font-size: 5rem;
color: white;
animation: bounce 1s infinite;
text-shadow: 0 0 20px rgba(255, 255, 255, 0.8);
}

@keyframes bounce {
0%, 100% { transform: translateY(0); }
50% { transform: translateY(-30px); }
}

.subtitle {
font-size: 2rem;
color: white;
margin-top: 20px;
}

.celebration-gif {
width: 300px;
margin-top: 30px;
border-radius: 20px;
}

#fireworks {
position: fixed;
top: 0;
left: 0;
z-index: 1;
}
