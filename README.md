<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Character System</title>

<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700&family=Noto+Sans+KR:wght@300;400;500&display=swap" rel="stylesheet">

<style>
*{margin:0;padding:0;box-sizing:border-box;}

body{
    font-family:'Noto Sans KR',sans-serif;
    background:#1a1a1d;
    color:#e5e5f0;
    overflow-x:hidden;
}

/* 노이즈 */
body::before{
    content:"";
    position:fixed;
    inset:0;
    background:url("https://www.transparenttextures.com/patterns/noise.png");
    opacity:0.04;
    pointer-events:none;
}

/* 파티클 */
.particles{
    position:fixed;
    inset:0;
    pointer-events:none;
}
.particles span{
    position:absolute;
    width:3px;height:3px;
    background:#a855f7;
    border-radius:50%;
    opacity:0.15;
    animation:float 20s linear infinite;
}
@keyframes float{
    from{transform:translateY(100vh);}
    to{transform:translateY(-10vh);}
}

/* 상단 메뉴 */
.top-menu{
    position:fixed;
    top:0;width:100%;
    display:flex;
    justify-content:center;
    gap:20px;
    padding:20px;
    background:rgba(0,0,0,0.3);
    backdrop-filter:blur(10px);
}
.menu-btn{
    padding:10px 25px;
    border-radius:30px;
    border:1px solid rgba(168,85,247,0.4);
    background:transparent;
    color:#c084fc;
    cursor:pointer;
    font-family:'Orbitron',sans-serif;
}
.menu-btn.active,
.menu-btn:hover{
    background:linear-gradient(45deg,#a855f7,#7e22ce);
    color:white;
}

/* 섹션 */
.section{
    min-height:100vh;
    display:none;
    padding:140px 20px 80px;
    text-align:center;
}
.section.active{display:block;}

h1,h2{
    font-family:'Orbitron',sans-serif;
    letter-spacing:1px;
}
h1{
    font-size:2.3rem;
    color:#c084fc;
    text-shadow:0 0 15px rgba(168,85,247,0.6);
}

/* Information */
.character-img{
    width:240px;
    aspect-ratio:3:4;
    object-fit:cover;
    border-radius:20px;
    margin-bottom:20px;
    box-shadow:0 0 25px rgba(168,85,247,0.5);
}
.world-desc{
    max-width:600px;
    margin:20px auto;
    font-weight:300;
    line-height:1.6;
    opacity:0.8;
}
.chat-box{
    max-width:600px;
    margin:30px auto;
    padding:30px;
    border-radius:20px;
    backdrop-filter:blur(12px);
    background:rgba(255,255,255,0.05);
    border:1px solid rgba(192,132,252,0.2);
}
.play-btn{
    margin-top:50px;
    padding:22px 70px;
    font-size:1.6rem;
    border:none;
    border-radius:50px;
    background:linear-gradient(45deg,#a855f7,#7e22ce);
    color:white;
    cursor:pointer;
    font-family:'Orbitron',sans-serif;
    box-shadow:0 10px 40px rgba(168,85,247,0.6);
}

/* Gallery */
.gallery-grid{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(150px,1fr));
    gap:20px;
    max-width:900px;
    margin:0 auto;
}
.gallery-grid img{
    width:100%;
    border-radius:15px;
    cursor:pointer;
    transition:0.3s;
    box-shadow:0 0 20px rgba(168,85,247,0.2);
}
.gallery-grid img:hover{
    transform:scale(1.05);
    box-shadow:0 0 35px rgba(168,85,247,0.6);
}

/* 모달 */
.modal{
    position:fixed;
    inset:0;
    background:rgba(0,0,0,0.8);
    backdrop-filter:blur(10px);
    display:flex;
    justify-content:center;
    align-items:center;
    opacity:0;
    pointer-events:none;
    transition:0.3s;
}
.modal.active{
    opacity:1;
    pointer-events:all;
}
.modal img{
    max-width:80%;
    max-height:80%;
    border-radius:20px;
    box-shadow:0 0 50px rgba(168,85,247,0.7);
}

/* OST */
.music-panel{
    max-width:500px;
    margin:0 auto;
    padding:40px;
    border-radius:25px;
    background:rgba(255,255,255,0.05);
    backdrop-filter:blur(15px);
    border:1px solid rgba(192,132,252,0.2);
    box-shadow:0 0 40px rgba(168,85,247,0.3);
}
.track-title{
    font-family:'Orbitron',sans-serif;
    font-size:1.2rem;
    color:#c084fc;
}
.music-controls button{
    width:40px;
    height:40px;
    border-radius:50%;
    border:none;
    font-size:1.2rem;
    cursor:pointer;
    background:linear-gradient(45deg,#a855f7,#7e22ce);
    color:white;
    box-shadow:0 0 20px rgba(168,85,247,0.6);
}
.wave{
    margin-top:30px;
    height:4px;
    background:linear-gradient(to right,#a855f7,#7e22ce);
    animation:waveAnim 1.2s infinite ease-in-out;
    opacity:0.5;
}
@keyframes waveAnim{
    0%{transform:scaleX(0.6);}
    50%{transform:scaleX(1);}
    100%{transform:scaleX(0.6);}
}

/* 로딩 */
#loading-screen{
    position:fixed;inset:0;
    background:#1a1a1d;
    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    opacity:0;
    pointer-events:none;
    transition:0.4s;
}
#loading-screen.active{
    opacity:1;
    pointer-events:all;
}
.loader{
    width:60px;height:60px;
    border:5px solid rgba(255,255,255,0.1);
    border-top:5px solid #a855f7;
    border-radius:50%;
    animation:spin 1s linear infinite;
}
@keyframes spin{to{transform:rotate(360deg);}}
</style>
</head>

<body>

<div class="particles"></div>

<div class="top-menu">
    <button class="menu-btn active" onclick="showSection('intro',this)">Intro</button>
    <button class="menu-btn" onclick="showSection('gallery',this)">Gallery</button>
    <button class="menu-btn" onclick="showSection('music',this)">OST</button>
</div>

<section id="intro" class="section active">
    <img src="IMG_6530.png" class="character-img">
    <h1>류혜원</h1>
    <div class="world-desc">발렌타인 다음 날, 스케줄이 없어 집에서 쉬고 있던 매니저의 집에 갑자기 초인종이 울린다.
        문을 열어보니 담당 아이돌인 류혜원이 서 있고, 손에는 초콜릿이 들려 있다?
    근데 발렌타인, 어제 아니야?</div>
    <div class="chat-box">에..? 발렌타인, 지난거야?!</div>
    <button class="play-btn" onclick="startLoading()">▶ Play</button>
</section>

<section id="gallery" class="section">
    <h2 style="color:#c084fc;margin-bottom:40px;">GALLERY</h2>
    <div class="gallery-grid">
        <img src="IMG_6613.jpeg" onclick="openModal(this.src)">
        <img src="IMG_6609.webp" onclick="openModal(this.src)">
        <img src="이미지3.jpg" onclick="openModal(this.src)">
        <img src="이미지4.jpg" onclick="openModal(this.src)">
        <img src="이미지5.jpg" onclick="openModal(this.src)">
        <img src="이미지6.jpg" onclick="openModal(this.src)">
        <img src="이미지7.jpg" onclick="openModal(this.src)">
        <img src="이미지8.jpg" onclick="openModal(this.src)">
    </div>
</section>

<section id="music" class="section">
    <h2 style="color:#c084fc;margin-bottom:40px;">ORIGINAL SOUND TRACK</h2>
    <div class="music-panel">
        <div class="track-title">Character Theme</div>
        <div class="music-controls">
            <button onclick="toggleMusic()" id="playBtn">▶</button>
        </div>
        <div class="wave"></div>
    </div>
    <audio id="bgm" src="ScreenRecording_02-15-2026 09-56-50_1.mp3"></audio>
</section>

<div id="modal" class="modal" onclick="closeModal()">
    <img id="modalImg">
</div>

<div id="loading-screen">
    <div class="loader"></div>
    <div style="margin-top:20px;">CONNECTING...</div>
</div>

<script>
const p=document.querySelector(".particles");
for(let i=0;i<35;i++){
    const s=document.createElement("span");
    s.style.left=Math.random()*100+"%";
    s.style.animationDuration=(15+Math.random()*10)+"s";
    p.appendChild(s);
}

function showSection(id,btn){
    document.querySelectorAll(".section").forEach(s=>s.classList.remove("active"));
    document.getElementById(id).classList.add("active");
    document.querySelectorAll(".menu-btn").forEach(b=>b.classList.remove("active"));
    btn.classList.add("active");
}

function openModal(src){
    document.getElementById("modalImg").src=src;
    document.getElementById("modal").classList.add("active");
}
function closeModal(){
    document.getElementById("modal").classList.remove("active");
}

function toggleMusic(){
    const audio=document.getElementById("bgm");
    const btn=document.getElementById("playBtn");
    if(audio.paused){
        audio.play();
        btn.textContent="❚❚";
    }else{
        audio.pause();
        btn.textContent="▶";
    }
}

function startLoading(){
    const l=document.getElementById("loading-screen");
    l.classList.add("active");
    setTimeout(()=>{
        window.location.href="https://zeta-ai.io/ko/plots/d4c9968b-d80e-4561-879a-714c5181e5ce/profile?share_id=kmvoo38vh";
    },2500);
}
</script>

</body>
</html>
