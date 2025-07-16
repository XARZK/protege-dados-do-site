# protege-dados-do-site<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Protege Dados</title>
<style>
  body {
    margin: 0;
    background: black;
    color: #0f0;
    font-family: monospace, monospace;
    overflow-x: hidden;
  }
  #matrixCanvas {
    position: fixed;
    top: 0; left: 0;
    width: 100vw;
    height: 100vh;
    z-index: -1;
  }
  header {
    text-align: center;
    padding: 3rem 1rem;
  }
  header h1 {
    font-size: 3.5rem;
    color: #0f0;
    text-shadow: 0 0 10px #0f0;
  }
  header p {
    font-size: 1.25rem;
    margin-top: 0.5rem;
    margin-bottom: 2rem;
  }
  a.whatsapp-btn {
    background: #0f0;
    color: black;
    padding: 1rem 2rem;
    font-weight: bold;
    border-radius: 9999px;
    text-decoration: none;
    box-shadow: 0 0 8px #0f0;
    display: inline-block;
    transition: background-color 0.3s ease;
  }
  a.whatsapp-btn:hover {
    background: #0c0;
  }
  form {
    max-width: 400px;
    margin: 2rem auto 4rem auto;
    padding: 1.5rem;
    background: rgba(0, 0, 0, 0.7);
    border-radius: 1rem;
    box-shadow: 0 0 15px #0f0;
  }
  label {
    display: block;
    margin-bottom: 0.5rem;
    font-weight: bold;
  }
  input[type="text"], input[type="email"] {
    width: 100%;
    padding: 0.7rem;
    margin-bottom: 1rem;
    background: black;
    border: 2px solid #0f0;
    color: #0f0;
    font-family: monospace;
    border-radius: 0.5rem;
  }
  input[type="submit"] {
    background: #0f0;
    color: black;
    border: none;
    padding: 1rem;
    font-weight: bold;
    cursor: pointer;
    border-radius: 9999px;
    width: 100%;
    box-shadow: 0 0 8px #0f0;
    transition: background-color 0.3s ease;
  }
  input[type="submit"]:hover {
    background: #0c0;
  }
  footer {
    text-align: center;
    color: #0f0;
    font-family: monospace;
    padding-bottom: 2rem;
  }
</style>
</head>
<body>
<canvas id="matrixCanvas"></canvas>

<header>
  <h1>Protege Dados</h1>
  <p>Blindagem digital contra vazamentos</p>
  <a href="https://wa.me/5511980136085" target="_blank" class="whatsapp-btn">Fale Conosco no WhatsApp</a>
</header>

<form id="form">
  <label for="name">Nome Completo</label>
  <input type="text" id="name" name="name" placeholder="Seu nome completo" required />
  
  <label for="email">E-mail</label>
  <input type="email" id="email" name="email" placeholder="seu@email.com" required />
  
  <label for="cpf">CPF</label>
  <input type="text" id="cpf" name="cpf" placeholder="000.000.000-00" required />
  
  <input type="submit" value="Solicitar Análise Gratuita" />
</form>

<footer>
  <p>Email: suporte@protegadados.com | WhatsApp: +55 11 98013-6085</p>
  <p>&copy; 2025 Protege Dados</p>
</footer>

<script>
// Matrix effect
const canvas = document.getElementById('matrixCanvas');
const ctx = canvas.getContext('2d');
let width = window.innerWidth;
let height = window.innerHeight;
canvas.width = width;
canvas.height = height;

const letters = '0123456789ABCDEF';
const fontSize = 16;
const columns = Math.floor(width / fontSize);
const drops = [];

for(let x = 0; x < columns; x++) drops[x] = 1;

function draw() {
  ctx.fillStyle = 'rgba(0,0,0,0.1)';
  ctx.fillRect(0, 0, width, height);
  ctx.fillStyle = '#0f0';
  ctx.font = fontSize + 'px monospace';
  
  for(let i = 0; i < drops.length; i++) {
    const text = letters.charAt(Math.floor(Math.random() * letters.length));
    ctx.fillText(text, i * fontSize, drops[i] * fontSize);
    if(drops[i] * fontSize > height && Math.random() > 0.975) drops[i] = 0;
    drops[i]++;
  }
}
setInterval(draw, 50);

window.addEventListener('resize', () => {
  width = window.innerWidth;
  height = window.innerHeight;
  canvas.width = width;
  canvas.height = height;
});

// Form submit simulation
const form = document.getElementById('form');
form.addEventListener('submit', e => {
  e.preventDefault();
  alert('Obrigado! Entraremos em contato via WhatsApp.');
  form.reset();
});
</script>

</body>
</html>
