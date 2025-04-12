<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>RAWLINGS SHOE HUB</title>
  <link rel="stylesheet" href="styles.css" />
</head>
<body>
  <header>
    <h1>RAWLINGS SHOE HUB</h1>
    <nav>
      <a href="#products">Shop</a>
      <a href="#order-tracking">Track Order</a>
    </nav>
  </header>

  <section id="products">
    <h2>Our Collection</h2>
    <div class="product-list" id="product-list">
      <!-- Shoes will be added by JS -->
    </div>
  </section>

  <section id="order-tracking">
    <h2>Track Your Order</h2>
    <form id="tracking-form">
      <input type="text" id="order-id" placeholder="Enter Order ID" required />
      <button type="submit">Track</button>
    </form>
    <div id="tracking-status"></div>
  </section>

  <footer>
    <p>&copy; 2025 RAWLINGS SHOE HUB</p>
  </footer>

  <script src="scripts.js"></script>
</body>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f9f9f9;
}

header {
  background-color: #111;
  color: white;
  padding: 20px;
  text-align: center;
}

nav a {
  color: white;
  margin: 0 15px;
  text-decoration: none;
}

section {
  padding: 20px;
}

.product-list {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
}

.product-item {
  background-color: white;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 15px;
  width: 250px;
  text-align: center;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}

.product-item img {
  max-width: 100%;
  height: auto;
  border-radius: 6px;
}

button {
  background-color: #ff5e00;
  color: white;
  border: none;
  padding: 10px 15px;
  margin-top: 10px;
  cursor: pointer;
  border-radius: 5px;
}

button:hover {
  background-color: #e34c00;
}

#tracking-form {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 15px;
}

#tracking-form input {
  padding: 10px;
  width: 250px;
  margin-bottom: 10px;
}

#tracking-status {
  margin-top: 15px;
  font-weight: bold;
}

footer {
  background-color: #111;
  color: white;
  text-align: center;
  padding: 15px 0;
  margin-top: 40px;
}
const products = [
  {
    id: 1,
    name: 'Nike Air Max 90',
    price: 'KSh 12,000',
    image: 'https://images.unsplash.com/photo-1606813904264-2761c8702df7?auto=format&fit=crop&w=800&q=80'
  },
  {
    id: 2,
    name: 'Adidas Ultraboost',
    price: 'KSh 15,000',
    image: 'https://images.unsplash.com/photo-1549294413-26f195200c16?auto=format&fit=crop&w=800&q=80'
  },
  {
    id: 3,
    name: 'Puma RS-X',
    price: 'KSh 9,800',
    image: 'https://images.unsplash.com/photo-1618354691261-2b8935b12c3e?auto=format&fit=crop&w=800&q=80'
  },
  {
    id: 4,
    name: 'Converse All Star',
    price: 'KSh 6,500',
    image: 'https://images.unsplash.com/photo-1616455579108-5c8f3cf47042?auto=format&fit=crop&w=800&q=80'
  },
  {
    id: 5,
    name: 'Vans Old Skool',
    price: 'KSh 7,200',
    image: 'https://images.unsplash.com/photo-1600185365862-bf1ee3c34d00?auto=format&fit=crop&w=800&q=80'
  },
];

function displayProducts() {
  const list = document.getElementById('product-list');
  products.forEach(product => {
    const item = document.createElement('div');
    item.className = 'product-item';
    item.innerHTML = `
      <img src="${product.image}" alt="${product.name}" />
      <h3>${product.name}</h3>
      <p>${product.price}</p>
      <button onclick="addToCart(${product.id})">Buy Now</button>
    `;
    list.appendChild(item);
  });
}

function addToCart(productId) {
  const selected = products.find(p => p.id === productId);
  alert(`You selected ${selected.name}. M-Pesa payment will be initiated (simulate here).`);
  // In real app, initiate STK Push here via backend
}

// Tracking logic
document.getElementById('tracking-form').addEventListener('submit', function(e) {
  e.preventDefault();
  const id = document.getElementById('order-id').value;
  trackOrder(id);
});

function trackOrder(orderId) {
  const mockTracking = {
    '1234': 'Shipped - On the way to Nairobi',
    '5678': 'Delivered to Kisumu',
    '9101': 'Processing at Warehouse'
  };

  const status = mockTracking[orderId] || 'Order not found.';
  document.getElementById('tracking-status').innerText = status;
}

displayProducts();

</html>
