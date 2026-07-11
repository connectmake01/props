<button id="yesBtn">❤️ Yes</button>
<button id="musicBtn">🎵 Play Music</button>

<audio id="bgMusic" loop>
  <source src="music.mp3" type="audio/mpeg">
</audio>

<div id="celebrationMessage" class="hidden">
  <h2>🎉 You made my day! ❤️</h2>
</div>

<div id="map"></div>

<canvas id="fireworks"></canvas>

<script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.9.3/dist/confetti.browser.min.js"></script>
<script src="script.js"></script> .hidden {
  display: none;
}

#celebrationMessage {
  position: fixed;
  inset: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background: rgba(0,0,0,.85);
  color: white;
  font-size: 2rem;
  z-index: 9999;
}

#musicBtn{
position:fixed;
top:20px;
right:20px;
padding:12px 20px;
border:none;
border-radius:30px;
cursor:pointer;
background:#ff4d88;
color:white;
font-size:16px;
box-shadow:0 5px 20px rgba(255,0,90,.4);
}

#map{
width:100%;
height:400px;
margin-top:80px;
border-radius:20px;
overflow:hidden;
}

#fireworks{
position:fixed;
top:0;
left:0;
width:100%;
height:100%;
pointer-events:none;
z-index:9998;
}. const yesBtn = document.getElementById("yesBtn");
const musicBtn = document.getElementById("musicBtn");
const music = document.getElementById("bgMusic");
const celebration = document.getElementById("celebrationMessage");

let playing = false;

musicBtn.onclick = () => {

if(playing){
music.pause();
musicBtn.innerHTML="🎵 Play Music";
}else{
music.play();
musicBtn.innerHTML="🔇 Pause Music";
}

playing=!playing;

};

yesBtn.onclick=()=>{

celebration.classList.remove("hidden");

launchConfetti();

startFireworks();

createHearts();

};  function launchConfetti(){

var duration=5000;

var end=Date.now()+duration;

(function frame(){

confetti({

particleCount:6,
angle:60,
spread:70,
origin:{x:0}

});

confetti({

particleCount:6,
angle:120,
spread:70,
origin:{x:1}

});

if(Date.now()<end){

requestAnimationFrame(frame);

}

})();

}. function createHearts(){

setInterval(()=>{

const heart=document.createElement("div");

heart.innerHTML="❤️";

heart.style.position="fixed";

heart.style.left=Math.random()*100+"vw";

heart.style.bottom="-50px";

heart.style.fontSize=Math.random()*25+20+"px";

heart.style.transition="all 6s linear";

heart.style.zIndex=9999;

document.body.appendChild(heart);

setTimeout(()=>{

heart.style.bottom="110vh";
heart.style.opacity=0;

},100);

setTimeout(()=>{

heart.remove();

},6500);

},300);

}.  const canvas=document.getElementById("fireworks");

const ctx=canvas.getContext("2d");

canvas.width=window.innerWidth;
canvas.height=window.innerHeight;

let particles=[];

function firework(){

for(let i=0;i<80;i++){

particles.push({

x:Math.random()*canvas.width,

y:Math.random()*canvas.height/2,

vx:(Math.random()-0.5)*8,

vy:(Math.random()-0.5)*8,

life:100

});

}

}

function animate(){

ctx.clearRect(0,0,canvas.width,canvas.height);

particles.forEach((p,index)=>{

ctx.beginPath();

ctx.arc(p.x,p.y,3,0,Math.PI*2);

ctx.fillStyle=`hsl(${Math.random()*360},100%,60%)`;

ctx.fill();

p.x+=p.vx;

p.y+=p.vy;

p.life--;

if(p.life<=0){

particles.splice(index,1);

}

});

requestAnimationFrame(animate);

}

function startFireworks(){

setInterval(firework,800);

}

animate();   <script async
src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&callback=initMap">
</script>.   function initMap(){

const place={

lat:25.2854,
lng:51.5310

};

const map=new google.maps.Map(document.getElementById("map"),{

zoom:15,
center:place

});

new google.maps.Marker({

position:place,
map:map,
title:"Our Date ❤️"

});

}.  make this as website Promet
