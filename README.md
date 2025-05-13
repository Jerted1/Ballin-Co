# Ballin-Co
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>GoalZone - Football Gear</title>
  <link rel="stylesheet" href="styles.css" />
</head>
<body>
  <header>
    <h1>GoalZone</h1>
    <nav>
      <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#products">Products</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </nav>
  </header>

  <section class="hero">
    <h2>Your One-Stop Shop for Football Gear</h2>
    <p>Find boots, kits, balls, and everything you need to play like a pro.</p>
    <a href="#products" class="btn">Shop Now</a>
  </section>

  <section id="products" class="products">
    <h2>Top Products</h2>
    <div class="product-grid">
      <div class="product-card">
        <img src="https://via.placeholder.com/200" alt="Football Boots" />
        <h3>Pro Football Boots</h3>
        <p>£89.99</p>
        <button class="add-to-cart" data-name="Pro Football Boots" data-price="89.99">Add to Cart</button>
      </div>
      <div class="product-card">
        <img src="https://via.placeholder.com/200" alt="Football" />
        <h3>Premier League Ball</h3>
        <p>£29.99</p>
        <button class="add-to-cart" data-name="Premier League Ball" data-price="29.99">Add to Cart</button>
      </div>
      <div class="product-card">
        <img src="https://via.placeholder.com/200" alt="Football Kit" />
        <h3>Team Kit</h3>
        <p>£49.99</p>
        <button class="add-to-cart" data-name="Team Kit" data-price="49.99">Add to Cart</button>
      </div>
    </div>
  </section>

  <section id="contact" class="contact">
    <h2>Contact Us</h2>
    <form>
      <input type="text" placeholder="Your Name" required />
      <input type="email" placeholder="Email" required />
      <textarea placeholder="Message"></textarea>
      <button type="submit">Send</button>
    </form>
  </section>

  <footer>
    <p>© 2025 GoalZone. All rights reserved.</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>

body {
  font-family: 'Segoe UI', sans-serif;
  margin: 0;
  background: #f2f2f2;
  color: #222;
}

header {
  background-color: #008000;
  color: white;
  padding: 20px;
  text-align: center;
}

nav ul {
  list-style: none;
  padding: 0;
  display: flex;
  justify-content: center;
  gap: 15px;
}

nav a {
  color: white;
  text-decoration: none;
}

.hero {
  background: url('https://via.placeholder.com/1500x400') center/cover no-repeat;
  text-align: center;
  color: white;
  padding: 80px 20px;
}

.hero .btn {
  background: #ffcc00;
  padding: 10px 20px;
  border: none;
  font-weight: bold;
  cursor: pointer;
  margin-top: 20px;
  display: inline-block;
  text-decoration: none;
  color: black;
}

.products {
  padding: 40px 20px;
  text-align: center;
}

.product-grid {
  display: flex;
  justify-content: center;
  gap: 20px;
  flex-wrap: wrap;
}

.product-card {
  background: white;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0,0,0,0.1);
  width: 200px;
}

.product-card img {
  width: 100%;
  border-radius: 5px;
}

.contact {
  padding: 40px 20px;
  text-align: center;
  background: #ddd;
}

.contact form {
  max-width: 400px;
  margin: auto;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

footer {
  text-align: center;
  padding: 20px;
  background: #008000;
  color: white;
}


let cart = JSON.parse(localStorage.getItem("cart")) || [];

document.querySelectorAll(".add-to-cart").forEach(button => {
  button.addEventListener("click", () => {
    const name = button.getAttribute("data-name");
    const price = parseFloat(button.getAttribute("data-price"));

    const item = cart.find(p => p.name === name);
    if (item) {
      item.qty += 1;
    } else {
      cart.push({ name, price, qty: 1 });
    }

    localStorage.setItem("cart", JSON.stringify(cart));
    alert(`${name} added to cart!`);
  });
});
