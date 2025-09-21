<!doctype html>
<html lang="tr">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Lamumu Mint Geri Sayım</title>
<style>
  body{
    margin:0; padding:24px; font-family:Inter, sans-serif;
    background:linear-gradient(180deg,#041226 0%, #07152a 100%); color:#e6f0ff;
    display:flex; flex-direction:column; align-items:center; gap:24px;
  }
  .banner img{
    max-width:100%; border-radius:12px; box-shadow:0 8px 20px rgba(0,0,0,.5);
  }
  .card{
    background:rgba(255,255,255,0.03); border:1px solid rgba(255,255,255,0.08);
    border-radius:14px; padding:22px; max-width:600px; width:100%;
    box-shadow:0 10px 30px rgba(0,0,0,.5);
  }
  h2{margin:0 0 6px 0; font-size:1.2rem}
  p{margin:3px 0; color:#94a3b8; font-size:.9rem}
  .clock{display:grid; grid-template-columns:repeat(4,1fr); gap:10px; margin-top:12px}
  .unit{background:rgba(255,255,255,0.04); border-radius:10px; padding:10px; text-align:center}
  .num{font-size:1.8rem; font-weight:700; color:#7dd3fc}
  .label{font-size:.8rem; text-transform:uppercase; color:#94a3b8}
  a.link{display:inline-block; margin-top:12px; padding:8px 12px; border-radius:8px;
    border:1px solid rgba(125,211,252,0.2); color:#7dd3fc; text-decoration:none}
</style>
</head>
<body>

<div class="banner">
  <img src="https://raw.githubusercontent.com/ostramus/LamumuMint/main/Screenshot_2025-09-21-17-51-21-582_com.android.chrome-edit.jpg" alt="Lamumu Mint Banner">
</div>

<!-- Whitelist -->
<div class="card" id="whitelist">
  <h2>Whitelist Mint</h2>
  <p>Başlangıç: 23 Eylül 2025 · 04:00 TSİ</p>
  <p>💰 0.02 ETH · 🌐 Ethereum Mainnet</p>
  <div class="clock">
    <div class="unit"><div class="num" id="wl-days">--</div><div class="label">Gün</div></div>
    <div class="unit"><div class="num" id="wl-hours">--</div><div class="label">Saat</div></div>
    <div class="unit"><div class="num" id="wl-minutes">--</div><div class="label">Dakika</div></div>
    <div class="unit"><div class="num" id="wl-seconds">--</div><div class="label">Saniye</div></div>
  </div>
  <a class="link" href="https://opensea.io/collection/lamumu-by-common/overview" target="_blank">Whitelist Mint Linki</a>
</div>

<!-- FCFS -->
<div class="card" id="fcfs">
  <h2>FCFS (Genel Mint)</h2>
  <p>Başlangıç: 24 Eylül 2025 · 04:00 TSİ</p>
  <p>💰 0.02 ETH · 🌐 Ethereum Mainnet</p>
  <div class="clock">
    <div class="unit"><div class="num" id="fcfs-days">--</div><div class="label">Gün</div></div>
    <div class="unit"><div class="num" id="fcfs-hours">--</div><div class="label">Saat</div></div>
    <div class="unit"><div class="num" id="fcfs-minutes">--</div><div class="label">Dakika</div></div>
    <div class="unit"><div class="num" id="fcfs-seconds">--</div><div class="label">Saniye</div></div>
  </div>
  <a class="link" href="https://opensea.io/collection/lamumu-by-common/overview" target="_blank">FCFS Mint Linki</a>
</div>

<!-- Public -->
<div class="card" id="public">
  <h2>Public Mint (Herkese Açık)</h2>
  <p>Başlangıç: 24 Eylül 2025 · 10:00 TSİ</p>
  <p>💰 0.02 ETH · 🌐 Ethereum Mainnet</p>
  <div class="clock">
    <div class="unit"><div class="num" id="pub-days">--</div><div class="label">Gün</div></div>
    <div class="unit"><div class="num" id="pub-hours">--</div><div class="label">Saat</div></div>
    <div class="unit"><div class="num" id="pub-minutes">--</div><div class="label">Dakika</div></div>
    <div class="unit"><div class="num" id="pub-seconds">--</div><div class="label">Saniye</div></div>
  </div>
  <a class="link" href="https://opensea.io/collection/lamumu-by-common/overview" target="_blank">Public Mint Linki</a>
</div>

<script>
function startCountdown(targetIso, ids){
  const target = new Date(targetIso);
  function pad(n){return n.toString().padStart(2,'0');}
  function update(){
    const now = new Date();
    const diff = target - now;
    const dEl = document.getElementById(ids.days);
    const hEl = document.getElementById(ids.hours);
    const mEl = document.getElementById(ids.minutes);
    const sEl = document.getElementById(ids.seconds);

    if(diff <= 0){
      dEl.textContent = "00"; hEl.textContent = "00";
      mEl.textContent = "00"; sEl.textContent = "00";
      return;
    }
    const totalSec = Math.floor(diff/1000);
    const days = Math.floor(totalSec/(24*3600));
    const hours = Math.floor((totalSec%(24*3600))/3600);
    const mins = Math.floor((totalSec%3600)/60);
    const secs = totalSec%60;
    dEl.textContent = pad(days);
    hEl.textContent = pad(hours);
    mEl.textContent = pad(mins);
    sEl.textContent = pad(secs);
  }
  update();
  setInterval(update,1000);
}

// Whitelist
startCountdown("2025-09-23T04:00:00+03:00", {
  days:"wl-days", hours:"wl-hours", minutes:"wl-minutes", seconds:"wl-seconds"
});
// FCFS
startCountdown("2025-09-24T04:00:00+03:00", {
  days:"fcfs-days", hours:"fcfs-hours", minutes:"fcfs-minutes", seconds:"fcfs-seconds"
});
// Public
startCountdown("2025-09-24T10:00:00+03:00", {
  days:"pub-days", hours:"pub-hours", minutes:"pub-minutes", seconds:"pub-seconds"
});
</script>

</body>
</html>
