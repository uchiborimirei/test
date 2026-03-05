<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<title>ガチャゲーム</title>

<style>
body{
    font-family: sans-serif;
    text-align:center;
    background:linear-gradient(135deg,#1e3c72,#2a5298);
    color:white;
    margin-top:100px;
}

h1{
    font-size:40px;
}

#result{
    margin:30px;
    font-size:28px;
    height:50px;
}

button{
    font-size:24px;
    padding:15px 40px;
    border:none;
    border-radius:10px;
    background:gold;
    cursor:pointer;
}

button:hover{
    background:orange;
}

.rare5{
    color:gold;
    font-size:32px;
}

.rare4{
    color:violet;
}

.rare3{
    color:white;
}

.animation{
    animation:flash 0.5s 4;
}

@keyframes flash{
    0%{opacity:1}
    50%{opacity:0.3}
    100%{opacity:1}
}
</style>
</head>

<body>

<h1>✨ ガチャゲーム ✨</h1>

<div id="result">ボタンを押してガチャ！</div>

<button onclick="gacha()">ガチャを引く</button>

<script>

const characters = [
{ name:"伝説の勇者", rarity:5 },
{ name:"神秘の魔法使い", rarity:5 },

{ name:"王国の騎士", rarity:4 },
{ name:"炎の弓使い", rarity:4 },
{ name:"氷の魔導士", rarity:4 },

{ name:"村人A", rarity:3 },
{ name:"見習い剣士", rarity:3 },
{ name:"旅人", rarity:3 },
{ name:"商人", rarity:3 }
];

function gacha(){

const result = document.getElementById("result");

result.classList.add("animation");
result.innerText="ガチャ中...";

setTimeout(()=>{

let rand = Math.random();
let rarity;

if(rand < 0.05){
rarity = 5;
}else if(rand < 0.25){
rarity = 4;
}else{
rarity = 3;
}

let pool = characters.filter(c => c.rarity === rarity);
let chara = pool[Math.floor(Math.random()*pool.length)];

result.className="";
result.classList.add("rare"+rarity);

result.innerHTML =
"★".repeat(rarity) + "<br>" + chara.name;

},1500);

}

</script>

</body>
</html>
