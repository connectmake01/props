<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>A Little Surprise ❤️</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap" rel="stylesheet">

<style>
*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:'Poppins',sans-serif;
}

body{
height:100vh;
display:flex;
justify-content:center;
align-items:center;
background:linear-gradient(-45deg,#ff9a9e,#fad0c4,#fbc2eb,#a18cd1);
background-size:400% 400%;
animation:bg 10s ease infinite;
overflow:hidden;
}

@keyframes bg{
0%{background-position:0% 50%;}
50%{background-position:100% 50%;}
100%{background-position:0% 50%;}
}

.card{
background:white;
padding:45px;
width:90%;
max-width:600px;
text-align:center;
border-radius:25px;
box-shadow:0 20px 50px rgba(0,0,0,.2);
position:relative;
z-index:5;
}

h1{
font-size:42px;
color:#ff4b7d;
margin-bottom:20px;
}

#typing{
font-size:22px;
color:#555;
height:70px;
margin-bottom:20px;
}

p{
font-size:18px;
line-height:1.7;
color:#666;
margin-bottom:35px;
}

button{
padding:15px 35px;
font-size:18px;
border:none;
border-radius:50px;
cursor:pointer;
margin:10px;
transition:.3s;
}

#yes{
background:#ff4b7d;
color:white;
}

#yes:hover{
transform:scale(1.1);
}

#no{
background:#ddd;
}

#message{
font-size:30px;
color:#ff4b7d;
margin-top:25px;
display:none;
font-weight:bold;
}

.heart{
position:absolute;
font-size:24px;
animation:float 8s linear infinite;
opacity:.7;
}

@keyframes float{
0%{
transform:translateY(100vh);
opacity:0;
}
10%{
opacity:1;
}
100%{
transform:translateY(-100px);
opacity:0;
}
}

canvas{
position:absolute;
top:0;
left:0;
pointer-events:none;
}
</style>

</head>
<body>

<canvas id="canvas"></canvas>

<div class="card">

<h1>Hi ❤️</h1>

<div id="typing"></div>

<p>
Every moment with you makes my day brighter.
I don't know what the future holds,
but I'd love the chance to know you better.

Would you make me the happiest person and go on a date with me?
🌹
</p>

<button id="yes">Yes ❤️</button>
<button id="no">No 🙈</button>

<div id="message">
YAY!! 🎉❤️<br>
I can't wait! 😊
</div>

</div>

<script>

const text="I made this little website just for you...";
let i=0;

function type(){
if(i<text.length){
document.getElementById("typing").innerHTML+=text.charAt(i);
i++;
setTimeout(type,70);
}
}
type();

// Floating hearts

function heart(){

const h=document.createElement("div");
h.className="heart";
h.innerHTML="❤️";

h.style.left=Math.random()*100+"vw";
h.style.fontSize=(20+Math.random()*30)+"px";
h.style.animationDuration=(5+Math.random()*5)+"s";

document.body.appendChild(h);

setTimeout(()=>{
h.remove();
},8000);

}

setInterval(heart,300);

// Funny No button

const no=document.getElementById("no");

no.addEventListener("mouseover",()=>{

const x=Math.random()*80;
const y=Math.random()*80;

no.style.position="absolute";
no.style.left=x+"vw";
no.style.top=y+"vh";

});

document.getElementById("yes").onclick=function(){

document.getElementById("message").style.display="block";

confetti();

}

function confetti(){

const canvas=document.getElementById("canvas");
const ctx=canvas.getContext("2d");

canvas.width=window.innerWidth;
canvas.height=window.innerHeight;

let pieces=[];

for(let i=0;i<200;i++){
pieces.push({
x:Math.random()*canvas.width,
y:Math.random()*canvas.height-canvas.height,
r:Math.random()*8+4,
dx:(Math.random()-0.5)*4,
dy:Math.random()*5+2,
});
}

function draw(){

ctx.clearRect(0,0,canvas.width,canvas.height);

pieces.forEach(p=>{

ctx.beginPath();
ctx.arc(p.x,p.y,p.r,0,Math.PI*2);
ctx.fillStyle=`hsl(${Math.random()*360},100%,60%)`;
ctx.fill();

p.x+=p.dx;
p.y+=p.dy;

});

requestAnimationFrame(draw);

}

draw();

}

</script>

</body>
</html>
