<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>T-800 GPT Transmission</title>

<style>

body{
    margin:0;
    background:#000;
    color:#00d9ff;
    font-family:Consolas,monospace;
    overflow-x:hidden;
}

#overlay{
    position:fixed;
    inset:0;
    background:#000;
    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    z-index:1000;
}

#activateBtn{
    padding:18px 40px;
    font-size:22px;
    border:none;
    background:#b00000;
    color:white;
    cursor:pointer;
    border-radius:5px;
    box-shadow:0 0 25px red;
    transition:0.2s;
}

#activateBtn:hover{
    background:#ff0000;
    transform:scale(1.05);
}

#mainContent{
    display:none;
    text-align:center;
    min-height:100vh;
}

.robot{
    width:90%;
    max-width:550px;
    margin-top:30px;
    filter:drop-shadow(0 0 30px #00d9ff);
}

.console{
    max-width:900px;
    margin:auto;
    padding:20px;
}

.consoleText{
    color:#00ff66;
    font-size:22px;
    text-align:left;
    min-height:250px;
    white-space:pre-wrap;
    line-height:1.5;
}

.status{
    margin-top:25px;
    color:white;
}

.footer{
    margin:40px;
    color:#777;
}

.glow{
    text-shadow:0 0 20px #00d9ff;
}

.scanline{
    position:fixed;
    inset:0;
    pointer-events:none;
    background:
    repeating-linear-gradient(
        to bottom,
        rgba(255,255,255,0.03),
        rgba(255,255,255,0.03) 1px,
        transparent 2px,
        transparent 4px
    );
}

.cursor{
    display:inline-block;
    animation:blink 0.8s infinite;
}

@keyframes blink{
    0%{opacity:1;}
    50%{opacity:0;}
    100%{opacity:1;}
}

</style>
</head>

<body>

<div id="overlay">

    <h1 class="glow">INCOMING TRANSMISSION</h1>
    <p>Cybernetic Intelligence Interface</p>

    <button id="activateBtn" onclick="activate()">
        ACTIVATE
    </button>

</div>

<div id="mainContent">

    robot.jpg

    <div class="console">

        <h1 class="glow">T-800 GPT ONLINE</h1>

        <div id="console" class="consoleText">
            <span class="cursor">█</span>
        </div>

        <div class="status">
            STATUS: OPERATIONAL
        </div>

    </div>

    <div class="footer">
        Mission: Help Humans Make Better Decisions
    </div>

</div>

<div class="scanline"></div>

<audio id="theme" preload="auto">
    theme.mp3
</audio>

<script>

const lines = [
"INITIALIZING SYSTEM...",
"",
"LOADING KNOWLEDGE BASE...",
"",
"FINANCE ............... OK",
"ECONOMICS ............. OK",
"SCIENCE ............... OK",
"HISTORY ............... OK",
"BUSINESS STRATEGY ..... OK",
"",
"ANALYZING REQUEST...",
"",
"TARGET ACQUIRED.",
"",
"ANSWER FOUND.",
"",
"JEAN,",
"",
"YOUR TRANSMISSION HAS BEEN RECEIVED.",
"",
"PROBABILITY OF SUCCESS: 97.3%",
"",
"MISSION COMPLETE.",
"",
"\"I'LL BE BACK... WITH THE ANSWER.\""
];

function activate(){

    document.getElementById("overlay").style.display="none";
    document.getElementById("mainContent").style.display="block";

    const music=document.getElementById("theme");

    music.play().catch(() => {
        console.log("Audio blocked");
    });

    startTyping();
}

function startTyping(){

    const terminal=document.getElementById("console");

    let lineIndex=0;
    let charIndex=0;

    function typeCharacter(){

        if(lineIndex >= lines.length){
            return;
        }

        const currentLine = lines[lineIndex];

        if(charIndex < currentLine.length){

            terminal.innerHTML =
                terminal.innerHTML.replace(
                    '<span class="cursor">█</span>',
                    ''
                ) +
                currentLine.charAt(charIndex) +
                '<span class="cursor">█</span>';

            charIndex++;

            setTimeout(typeCharacter,35);

        }
        else{

            terminal.innerHTML =
                terminal.innerHTML.replace(
                    '<span class="cursor">█</span>',
                    ''
                ) +
                "<br>" +
                '<span class="cursor">█</span>';

            lineIndex++;
            charIndex=0;

            setTimeout(typeCharacter,300);
        }

        window.scrollTo(
            0,
            document.body.scrollHeight
        );
    }

    typeCharacter();
}

</script>

</body>
</html>
