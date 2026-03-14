<!DOCTYPE html>
<html lang="hu">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Pokémon TCG Mobile</title>
    <style>
        body { font-family: sans-serif; background: #121212; color: white; margin: 0; padding-bottom: 70px; }
        .hidden { display: none !important; }
        .page { padding: 15px; text-align: center; min-height: 100vh; }
        
        /* 4 OSZLOPOS PAKLI STÍLUS */
        .deck-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 10px; padding: 10px; }
        @media (min-width: 600px) { .deck-grid { grid-template-columns: repeat(4, 1fr); } }

        .mini-card { background: #f6d365; border: 4px solid #ffde00; border-radius: 10px; color: black; padding: 5px; font-size: 10px; position: relative; text-align: left; }
        .mini-card img { width: 100%; height: 60px; object-fit: cover; border-radius: 4px; }
        .del-btn { background: red; color: white; border: none; font-size: 8px; padding: 2px 5px; border-radius: 4px; margin-top: 5px; width: 100%; }

        /* SZERKESZTŐ ÉS FORM */
        .ui-box { background: #1e1e1e; padding: 15px; border-radius: 15px; margin-bottom: 10px; border: 1px solid #333; }
        input, textarea { width: 90%; padding: 10px; margin: 5px 0; border-radius: 8px; border: none; background: #2a2a2a; color: white; }
        .btn { background: #ffcb05; color: #3c5aa6; border: 2px solid #3c5aa6; padding: 12px; border-radius: 10px; font-weight: bold; width: 100%; margin: 5px 0; cursor: pointer; }

        /* NAVBAR */
        .navbar { position: fixed; bottom: 0; left: 0; width: 100%; background: #1a1a1a; display: flex; justify-content: space-around; padding: 10px 0; border-top: 2px solid #333; z-index: 1000; }
        .nav-item { color: #888; font-size: 10px; background: none; border: none; }
        .nav-item.active { color: #ffcb05; font-weight: bold; }
    </style>
</head>
<body>

    <div id="loginPage" class="page">
        <h1 style="color:#ffcb05">POKÉMON LOGIN</h1>
        <input type="text" id="uName" placeholder="Név">
        <input type="password" id="uPass" placeholder="Jelszó">
        <button class="btn" onclick="auth()">BELÉPÉS</button>
    </div>

    <!-- SZERKESZTŐ -->
    <div id="editorPage" class="page hidden">
        <div class="ui-box">
            <h3>🎨 Kártya Szerkesztő</h3>
            <input type="text" id="inName" placeholder="Név">
            <input type="number" id="inHP" placeholder="HP">
            <textarea id="inInfo" placeholder="Infó..."></textarea>
            <input type="text" id="inAdv" placeholder="Előny...">
            <input type="file" id="fileIn" accept="image/*" onchange="loadImg(this)">
            <button class="btn" style="margin-top:10px;" onclick="save()">MENTÉS (50 🪙)</button>
        </div>
    </div>

    <!-- PAKLI (4 OSZLOP) -->
    <div id="deckPage" class="page hidden">
        <h3>🎒 PAKLID (<span class="coins">0</span> 🪙)</h3>
        <div id="deckList" class="deck-grid"></div>
    </div>

    <!-- SHOP -->
    <div id="shopPage" class="page hidden">
        <h3>🛒 SHOP</h3>
        <div class="ui-box">
            <h4>📅 Napi Ajándék</h4>
            <button id="dailyBtn" class="btn" onclick="claimDaily()">200 🪙 ÁTVÉTELE</button>
        </div>
        <div class="ui-box">
            <h4>✨ Napi Ajánlatok</h4>
            <div id="dailyOffers" class="deck-grid"></div>
        </div>
    </div>

    <nav class="navbar hidden" id="menu">
        <button class="nav-item active" onclick="tab('editorPage', this)">Szerkesztő</button>
        <button class="nav-item" onclick="tab('deckPage', this)">Pakli</button>
        <button class="nav-item" onclick="tab('shopPage', this)">Shop</button>
    </nav>

<script>
    let player = null;
    let tempPic = "";

    function tab(id, b) {
        document.querySelectorAll('.page').forEach(p => p.classList.add('hidden'));
        document.getElementById(id).classList.remove('hidden');
        document.querySelectorAll('.nav-item').forEach(i => i.classList.remove('active'));
        if(b) b.classList.add('active');
        if(id === 'deckPage') renderDeck();
        if(id === 'shopPage') renderShop();
    }

    function loadImg(input) {
        const reader = new FileReader();
        reader.onload = (e) => { tempPic = e.target.result; };
        reader.readAsDataURL(input.files);
    }

    function auth() {
        const u = document.getElementById('uName').value.trim();
        const p = document.getElementById('uPass').value;
        if(!u || !p) return;
        let data = JSON.parse(localStorage.getItem('pk_vNext_' + u));
        player = data || { username: u, password: p, money: 500, deck: [], lastDaily: 0 };
        document.getElementById('loginPage').classList.add('hidden');
        document.getElementById('menu').classList.remove('hidden');
        tab('editorPage', document.querySelector('.nav-item'));
        updateCoins();
    }

    function save() {
        const n = document.getElementById('inName').value;
        if(!n || !tempPic || player.money < 50) return alert("Hiba vagy kevés pénz!");
        player.money -= 50;
        player.deck.push({ name: n, hp: document.getElementById('inHP').value, img: tempPic, adv: document.getElementById('inAdv').value });
        sync();
        updateCoins();
        alert("Elmentve!");
        // Nem dob ki, csak ürítünk
        document.getElementById('inName').value = "";
        tempPic = "";
    }

    function renderDeck() {
        const list = document.getElementById('deckList');
        list.innerHTML = "";
        player.deck.forEach((c, i) => {
            list.innerHTML += `
                <div class="mini-card">
                    <img src="${c.img}">
                    <b>${c.name}</b><br>HP: ${c.hp}
                    <button class="del-btn" onclick="removeCard(${i})">Törlés (+25 🪙)</button>
                </div>`;
        });
    }

    function removeCard(i) {
        player.deck.splice(i, 1);
        player.money += 25;
        sync(); renderDeck(); updateCoins();
    }

    function claimDaily() {
        const now = new Date().toDateString();
        if(player.lastDaily === now) return alert("Ma már átvetted!");
        player.money += 200;
        player.lastDaily = now;
        sync(); updateCoins(); alert("Kaptál 200 érmét!");
    }

    function renderShop() {
        const shop = document.getElementById('dailyOffers');
        shop.innerHTML = "Véletlen lapok hamarosan...";
        // Itt generálhatsz 3 random kártyát minden napra
    }

    function updateCoins() { document.querySelectorAll('.coins').forEach(e => e.innerText = player.money); }
    function sync() { localStorage.setItem('pk_vNext_' + player.username, JSON.stringify(player)); }
</script>
</body>
</html>
