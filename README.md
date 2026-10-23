<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FAHIM ONLINE SHOP</title>
<style>
*{box-sizing:border-box}
body{
  margin:0;
  font-family:Arial,sans-serif;
  background:#f3f5f9;
  color:#172033;
}
header{
  background:#111827;
  color:white;
  text-align:center;
  padding:25px 12px;
}
header h1{margin:0;font-size:27px}
header p{color:#d1d5db}
main{
  max-width:900px;
  margin:30px auto;
  padding:16px;
}
.search{
  width:100%;
  padding:14px;
  border:1px solid #ddd;
  border-radius:12px;
  font-size:16px;
}
h2{text-align:center}
.products{
  display:grid;
  grid-template-columns:repeat(2,minmax(0,1fr));
  gap:14px;
}
.product{
  background:white;
  padding:18px 10px;
  border-radius:15px;
  text-align:center;
  box-shadow:0 3px 12px #0000000d;
}
.emoji{font-size:42px}
.price{color:#087f5b;font-weight:bold}
button{
  background:#111827;
  color:white;
  border:0;
  padding:11px 14px;
  border-radius:9px;
  cursor:pointer;
}
.cart{
  margin-top:24px;
  padding:20px;
  background:white;
  border-radius:15px;
}
footer{
  text-align:center;
  padding:25px;
  color:#666;
}
</style>
</head>
<body>
<header>
  <h1>FAHIM ONLINE SHOP</h1>
  <p>আপনার পছন্দের কেনাকাটা, এক জায়গায়!</p>
</header>
<main>
  <input id="search" class="search" placeholder="পণ্য খুঁজুন..." oninput="showProducts()">
  <h2>আমাদের পণ্য</h2>
  <div id="products" class="products"></div>
  <section class="cart">
    <h2>🛒 আপনার কার্ট</h2>
    <div id="cart">এখনো কোনো পণ্য যোগ করা হয়নি।</div>
    <p id="total">মোট: 0 SAR</p>
    <button onclick="checkout()">অর্ডার করতে WhatsApp</button>
  </section>
</main>
<footer>© 2026 FAHIM ONLINE SHOP</footer>
<script>
const items=[
 {name:"টি-শার্ট",price:35,emoji:"👕"},
 {name:"জুতা",price:80,emoji:"👟"},
 {name:"ঘড়ি",price:55,emoji:"⌚"},
 {name:"ব্যাগ",price:45,emoji:"🎒"},
 {name:"হেডফোন",price:60,emoji:"🎧"},
 {name:"সানগ্লাস",price:25,emoji:"🕶️"}
];
let basket=[];
function showProducts(){
 const q=document.getElementById("search").value.toLowerCase();
 document.getElementById("products").innerHTML=items
 .map((p,i)=>({...p,i}))
 .filter(p=>p.name.toLowerCase().includes(q))
 .map(p=>`<div class="product">
 <div class="emoji">${p.emoji}</div>
 <h3>${p.name}</h3>
 <p class="price">${p.price} SAR</p>
 <button onclick="addCart(${p.i})">কার্টে যোগ করুন</button>
 </div>`).join("");
}
function addCart(i){basket.push(items[i]);showCart();}
function showCart(){
 document.getElementById("cart").innerHTML=basket.length
 ?basket.map((p,i)=>`${p.name} — ${p.price} SAR <button onclick="removeCart(${i})">বাদ দিন</button>`).join("<hr>")
 :"এখনো কোনো পণ্য যোগ করা হয়নি।";
 document.getElementById("total").textContent="মোট: "+basket.reduce((s,p)=>s+p.price,0)+" SAR";
}
function removeCart(i){basket.splice(i,1);showCart();}
function checkout(){
 if(!basket.length){alert("আগে কার্টে পণ্য যোগ করুন।");return;}
 const msg="FAHIM ONLINE SHOP অর্ডার:%0A"+basket.map(p=>p.name+" - "+p.price+" SAR").join("%0A")+"%0Aমোট: "+basket.reduce((s,p)=>s+p.price,0)+" SAR";
 alert("WhatsApp অর্ডারের জন্য দোকানের মালিকের নম্বর কোডে যোগ করতে হবে।");
}
showProducts();
</script>
</body>
</html>
