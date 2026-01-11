navya-birthday/
│
├── index.html
├── style.css
├── script.js
├── fireworks.js
└── music.mp3   (any romantic song)
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Happy Birthday Navya 🎂</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<canvas id="fireworks"></canvas>

<audio autoplay loop>
    <source src="music.mp3" type="audio/mpeg">
</audio>

<div class="slider">

    <section class="slide active">
        <h1>🎉 Happy Birthday 🎉</h1>
        <h2>Navya 💖</h2>
        <p>15th Birthday • 14 January</p>
    </section>

    <section class="slide">
        <h1>⏳ Countdown Begins ⏳</h1>
        <div id="countdown"></div>
    </section>

    <section class="slide">
        <h1>💌 From My Heart 💌</h1>
        <p>
            You are not just special,  
            you are my happiness, my smile,  
            and my favorite feeling ❤️
        </p>
    </section>

    <section class="slide">
        <h1>🎂 Wishes For You 🎂</h1>
        <p>
            May your life be filled with  
            love, success, smiles & dreams ✨
        </p>
    </section>

    <section class="slide">
        <h1>🎆 Enjoy Your Day 🎆</h1>
        <p>I’m always proud of you 💝</p>
    </section>

</div>

<button id="next">Next ➡️</button>

<script src="fireworks.js"></script>
<script src="script.js"></script>
</body>
</html>
* {
    margin: 0;
    padding: 0;
    font-family: 'Poppins', sans-serif;
    box-sizing: border-box;
}

body {
    height: 100vh;
    background: linear-gradient(135deg, #ff758c, #ff7eb3);
    overflow: hidden;
    color: white;
}

canvas {
    position: fixed;
    top: 0;
    left: 0;
}

.slider {
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

.slide {
    display: none;
    text-align: center;
    animation: zoomFade 1.5s ease;
}

.slide.active {
    display: block;
}

h1 {
    font-size: 3rem;
}

h2 {
    font-size: 2.2rem;
    margin-top: 10px;
}

p {
    font-size: 1.4rem;
    margin-top: 20px;
    max-width: 500px;
}

#countdown {
    font-size: 2rem;
    margin-top: 30px;
    letter-spacing: 2px;
}

#next {
    position: absolute;
    bottom: 30px;
    right: 30px;
    padding: 12px 25px;
    border-radius: 30px;
    border: none;
    font-size: 16px;
    cursor: pointer;
}

@keyframes zoomFade {
    from { opacity: 0; transform: scale(0.8); }
    to { opacity: 1; transform: scale(1); }
}
const slides = document.querySelectorAll('.slide');
const nextBtn = document.getElementById('next');
let index = 0;

nextBtn.onclick = () => {
    slides[index].classList.remove('active');
    index = (index + 1) % slides.length;
    slides[index].classList.add('active');
};

// Countdown
const targetDate = new Date("January 14, 2026 00:00:00").getTime();

setInterval(() => {
    const now = new Date().getTime();
    const diff = targetDate - now;

    const days = Math.floor(diff / (1000 * 60 * 60 * 24));
    const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
    const minutes = Math.floor((diff / (1000 * 60)) % 60);
    const seconds = Math.floor((diff / 1000) % 60);

    document.getElementById("countdown").innerHTML =
        `${days}d ${hours}h ${minutes}m ${seconds}s`;
}, 1000);
const slides = document.querySelectorAll('.slide');
let index = 0;

// Auto slide
setInterval(() => {
  slides[index].classList.remove('active');
  index = (index + 1) % slides.length;
  slides[index].classList.add('active');
}, 6000);

// Countdown
const target = new Date("January 14, 2026 00:00:00").getTime();
setInterval(() => {
  const now = new Date().getTime();
  const d = target - now;
  document.getElementById("countdown").innerHTML =
    `${Math.floor(d/86400000)}d ${Math.floor(d/3600000)%24}h ${Math.floor(d/60000)%60}m ${Math.floor(d/1000)%60}s`;
}, 1000);

// Typing Effect
const text = "Navya, you make every moment brighter. May your life always shine with happiness, love, and beautiful dreams 💖";
let i = 0;
function type() {
  if (i < text.length) {
    document.getElementById("typing").innerHTML += text.charAt(i);
    i++;
    setTimeout(type, 60);
  }
}
setTimeout(type, 18000);

// Photo Slideshow
const photos = ["images/navya1.jpg", "images/navya2.jpg", "images/navya3.jpg"];
let p = 0;
setInterval(() => {
  p = (p + 1) % photos.length;
  document.getElementById("photo").src = photos[p];
}, 3000);
