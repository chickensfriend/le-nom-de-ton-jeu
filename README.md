# le-nom-de-ton-jeu


<!DOCTYPE html>

<html>
   <head>
       <meta charset="utf-8">
       <title>Casse Brique</title>
       <style>
         * { padding: 0; margin:0; }
         canvas { background: #eee; display: block; margin: 0 auto; }
       </style>
    </head>
    <body>
       
    <canvas id="myCanvas" width="1000" height="500"></canvas>

    <script>
        var canvas = document.getElementById("myCanvas");
        var ctx = canvas.getContext("2d");
        var characterHeight = 50;
        var characterWidth = 50;
        var characterX = 30;
        var characterY = 30;
        var fireballX = characterX;
        var fireballY = characterY;
        var rightPressed = false;
        var leftPressed = false;
        var upPressed = false;
        var downPressed = false;
        var spacePressed = false;
        var FireBallLauched = false;
        var dx=4;
        var dy=4;
        var dfireball=2;

        document.addEventListener("keydown", keyDownHandler, false);
        document.addEventListener("keyup", keyUpHandler, false);

        function keyDownHandler(e) {
        if(e.key == "Right" || e.key == "ArrowRight") {
         rightPressed = true;
        }
        else if(e.key == "Left" || e.key == "ArrowLeft") {
         leftPressed = true;
         }
        else if(e.key == "Up" || e.key == "ArrowUp") {
         upPressed = true;
         }
        else if(e.key == "Down" || e.key == "ArrowDown") {
         downPressed = true;
         }
        else if(e.key == "Space" || e.keyCode == 32) {
         spacePressed = true;
         }
       }

        function keyUpHandler(e) {
         if(e.key == "Right" || e.key == "ArrowRight") {
          rightPressed = false;
         }
         else if(e.key == "Left" || e.key == "ArrowLeft") {
           leftPressed = false;
         }
         else if(e.key == "Up" || e.key == "ArrowUp") {
         upPressed = false;
         }
        else if(e.key == "Down" || e.key == "ArrowDown") {
         downPressed = false;
         }
         else if(e.key == "Space" || e.keyCode == 32) {
         spacePressed = false;
         }

               }

        
        function drawCharacter() {
         ctx.beginPath();
         ctx.rect(characterX, characterY,characterWidth, characterHeight);
         ctx.fillStyle = "#0095DD";
         ctx.fill();
         ctx.closePath();
      }

        function drawFireBall() {
         ctx.beginPath();
         ctx.arc(fireballX + (characterWidth/2), fireballY + (characterHeight/2), 5, 0, Math.PI*2, false);
         ctx.fillStyle = "red";
         ctx.fill();
         ctx.closePath();
      }


      function draw() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        drawCharacter();
        drawFireBall();
        if(rightPressed) {
         characterX += dx;
         fireballX +=dx;
         if (characterX + characterWidth > canvas.width){
         characterX = canvas.width - characterWidth;
        }
        }
         else if(leftPressed) {
          characterX -= dx;
          fireballX -=dx;
         if (characterX < 0){
          characterX = 0;
        }
        }

        else if(upPressed) {
          characterY -= dy;
          fireballY -=dy;
         if (characterY < 0){
          characterY = 0;
        }
        }
        else if(downPressed) {
          characterY += dy;
          fireballY +=dy;
         if (characterY + characterHeight > canvas.height){
          characterY = canvas.height - characterHeight;
        }
        }
        else if(FireBallLauched) {
            fireballY+=dfireball;
        }
        else if(spacePressed) {
            FireBallLauched=true;
            if (fireballY < canvas.height){
                fireballY+=dfireball;
                
            }
        }
        
        }
        
        setInterval(draw, 10);

    </script>

    </body>
</hmtl>

