# Kisan-organic-basket
Kisan organic basket Android Grocery delivery app
<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Kisan Organic Basket</title>
<style>
* { box-sizing: border-box; }
body { margin: 0; font-family: Arial, sans-serif; background: #f5f8f2; color: #263328; }
header { background: #218838; color: white; padding: 20px; text-align: center; }
header h2 { margin: 0 0 8px; }
.search { margin: 15px; padding: 12px; width: calc(100% - 30px); border: 1px solid #ddd; border-radius: 8px; font-size: 16px; }
h3.section-title { margin: 18px; }
.products { display: grid; grid-template-columns: repeat(2, minmax(0, 1fr)); gap: 12px; padding: 12px; }
.card { background: white; padding: 15px; border-radius: 12px; text-align: center; box-shadow: 0 2px 7px #ddd; }
.emoji { font-size: 42px; }
.price { color: #218838; font-weight: bold; }
button { background: #218838; color: white; border: 0; padding: 10px 15px; border-radius: 7px; font-size: 15px; }
footer { text-align: center; padding: 20px; background: #e5efe4; margin-top: 12px; }
</style>
</head>
<body>
<header>
  <h2>🧺 Kisan Organic Basket</h2>
  <p>ताज़ी सब्जी, फल और दूध आपके घर</p>
  <p>🛒 Cart: <span id="count">0</span></p>
</header>
<input class="search" id="search" placeholder="अपना सामान खोजें..." oninput="filterProducts()">
<h3 class="section-title">हमारे प्रोडक्ट</h3>
<div class="products" id="products"></div>
<footer>
  <h3>आपका अपना Kisan Organic Basket</h3>
  <p>घर बैठे ताज़ा सामान मँगाइए।</p>
  <p>Delivery: Dalsingsarai</p>
</footer>
<script>
const items = [
  {name:"आलू", emoji:"🥔", price:25},
  {name:"टमाटर", emoji:"🍅", price:30},
  {name:"सेब", emoji:"🍎", price:120},
  {name:"केला", emoji:"🍌", price:50},
  {name:"दूध", emoji:"🥛", price:60},
  {name:"मटन", emoji:"🍖", price:700}
];
let cart = 0;
function showProducts(list) {
  document.getElementById("products").innerHTML = list.map(item => `
    <div class="card">
      <div class="emoji">${item.emoji}</div>
      <h3>${item.name}</h3>
      <p class="price">₹${item.price}</p>
      <button onclick="addCart()">Add to Cart</button>
    </div>
  `).join("");
}
function addCart() {
  cart++;
  document.getElementById("count").textContent = cart;
}
function filterProducts() {
  const value = document.getElementById("search").value;
  showProducts(items.filter(item => item.name.includes(value)));
}
showProducts(items);
</script>
</body>
</html>
