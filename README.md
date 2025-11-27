# nexaweb-site
NexaWeb SOLUTIONS official website
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>NexaWeb SOLUTIONS</title>
<style>
  * { margin:0; padding:0; box-sizing:border-box; }
  body { font-family: system-ui, sans-serif; background:#ff0000; overflow-x:hidden; }

  /* Canvas for moving dots */
  canvas#bg-canvas { 
    position:fixed; 
    top:0; 
    left:0; 
    width:100%; 
    height:100%; 
    z-index:-1; 
  }

  header { 
    display:flex; 
    align-items:center; 
    justify-content:space-between; 
    padding:20px 40px; 
    position:relative;
  }

  header img {
    height:60px;
    margin-left:10px;
  }

  .logo-text {
    position:absolute;
    left:50%;
    transform:translateX(-50%);
    font-size:32px; 
    color:white;
    top:20px;
  }

  nav { 
    position:absolute; 
    right:40px; 
    top:25px;
    display:flex; 
    gap:20px; 
  }

  nav a { 
    color:white; 
    text-decoration:none; 
    font-size:16px; 
  }

  .hero { padding:100px 20px; text-align:center; color:white; }
  .hero h2 { font-size:28px; margin-bottom:10px; }
  .hero p { font-size:18px; color:white; }
  .hero button { margin-top:20px; background:#0077ff; border:none; color:white; padding:12px 20px; border-radius:6px; font-size:16px; cursor:pointer; }

  .services { padding:40px 20px; }
  .services h2 { text-align:center; font-size:28px; margin-bottom:30px; color:white; }
  .service-box { background:rgba(255,255,255,0.9); padding:20px; margin:10px; border-radius:10px; box-shadow:0 0 10px rgba(0,0,0,0.1); }

  .footer { background:#111; color:white; text-align:center; padding:20px; margin-top:40px; }
  .social { display:flex; justify-content:center; gap:15px; margin-top:10px; }
  .social a { color:white; font-size:22px; text-decoration:none; }

  .form-section { background:rgba(255,255,255,0.95); padding:30px; margin:30px 15px; border-radius:10px; box-shadow:0 0 10px rgba(0,0,0,0.1); }
  .form-section h2 { text-align:center; margin-bottom:20px; }
  form { display:flex; flex-direction:column; gap:15px; }
  input, textarea { padding:12px; font-size:16px; border-radius:6px; border:1px solid #ccc; }
  button { background:#0077ff; color:white; border:none; padding:12px; font-size:16px; border-radius:6px; cursor:pointer; }

</style>
</head>
<body>

<canvas id="bg-canvas"></canvas>

<header>
  <img src="file_000000005f64720992cf5e18233a053c.png" alt="NexaWeb SOLUTIONS Logo">
  <div class="logo-text">NexaWeb SOLUTIONS</div>
  <nav>
    <a href="#home">Home</a>
    <a href="#services">Services</a>
    <a href="#contact">Contact</a>
  </nav>
</header>

<section class="hero" id="home">
  <h2>Grow Your Business With Us</h2>
  <p>Professional solutions for shops, salons, gyms, coaching centers, and more.</p>
  <button>Get Started</button>
</section>

<section class="services" id="services">
  <h2>Our Services</h2>

  <div class="service-box">
    <h3>Website Development</h3>
    <p>We build modern, responsive, and fast websites for any business.</p>
  </div>

  <div class="service-box">
    <h3>Brand Promotion</h3>
    <p>Boost your brand visibility with online presence and SEO.</p>
  </div>

  <div class="service-box">
    <h3>Business Support</h3>
    <p>We help small businesses grow online with digital tools.</p>
  </div>
</section>

<section class="form-section" id="contact">
  <h2>Contact Us</h2>
  <form action="https://formsubmit.co/YOUR-EMAIL" method="POST">
    <input type="hidden" name="_captcha" value="false">

    <input type="text" name="name" placeholder="Full Name" required>
    <input type="email" name="email" placeholder="Email Address" required>
    <input type="text" name="phone" placeholder="Phone Number" required>
    <textarea name="message" placeholder="Your Message" rows="5" required></textarea>

    <button type="submit">Send Message</button>
  </form>
</section>

<footer class="footer">
  <p>Follow us</p>

  <div class="social">
    <a href="#">📘</a>
    <a href="#">📸</a>
    <a href="#">🐦</a>
  </div>

  <p style="margin-top:10px;">© 2025 All Rights Reserved</p>
</footer>

<script>
const canvas = document.getElementById('bg-canvas');
const ctx = canvas.getContext('2d');
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let particles = [];
const colors = ['rgba(0,255,0,0.7)', 'rgba(0,0,255,0.7)', 'rgba(255,255,255,0.7)'];

class Particle {
  constructor() {
    this.x = Math.random() * canvas.width;
    this.y = Math.random() * canvas.height;
    this.radius = Math.random() * 4 + 2;
    this.color = colors[Math.floor(Math.random() * colors.length)];
    this.vx = (Math.random() - 0.5) * 1.5;
    this.vy = (Math.random() - 0.5) * 1.5;
  }
  draw() {
    ctx.beginPath();
    ctx.arc(this.x, this.y, this.radius, 0, Math.PI*2);
    ctx.fillStyle = this.color;
    ctx.fill();
  }
  update() {
    this.x += this.vx;
    this.y += this.vy;

    if(this.x < 0 || this.x > canvas.width) this.vx *= -1;
    if(this.y < 0 || this.y > canvas.height) this.vy *= -1;

    this.draw();
  }
}

for(let i=0;i<100;i++){
  particles.push(new Particle());
}

function animate(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  particles.forEach(p => p.update());
  requestAnimationFrame(animate);
}

animate();

window.addEventListener('resize', () => {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
});
</script>

</body>
</html>