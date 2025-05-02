# my-project-2 tik tak toe game
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TIC TAC GAME by Ahtasham</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1 id="intro">Tic Tak Game</h1>
        <div class="msgcontaior hide"><h1 class="msg">
        </h1></div>
        <button id="reset">Rest Game</button> 
    <main>
<div class="container">
    <div class="game">
        <button class="box"></button>
        <button class="box"></button>
        <button class="box"></button>
        <button class="box"></button>
        <button class="box"></button>
        <button class="box"></button>
        <button class="box"></button>
        <button class="box"></button>
        <button class="box"></button>
    </div>

</div>
    </main>

    <script src="app.js"></script>
</body>
</html>
-----------------------=====================----------------------
*{
    padding: 0;
    margin: 0;
    color: rgb(0, 0, 0);
}
#intro{
    font-weight: bolder;
    font-size: xx-large;
    margin-bottom: 10px;
    margin-top: 25px;
    background-color: white;
}
body {
    text-align: center;
    background-image: url(car.jpg) ;
    background-position: center;
    
}
main{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    /* margin-top: ; */
}
.container {
    height: 80vh;
    width: 80vw;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
}
.game{
    height: 70vmin;
    width: 70vmin;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
    gap: 1rem;


}
.box{
    height: 19vmin;
    width: 19vmin;
    align-items: center;
    justify-content: center;
    color: rgb(242, 255, 0);
    background-color: rgb(125, 125, 125);
    border: none;
    border-radius: 10px;
    font-size: 2rem;
}
#reset{
    padding: 1rem;
    font-size: xx-large;
    background-color:rgb(242, 255, 0) ;
    border: none;
    border-radius: 10px;
    color: black;
    
    
}
.msgcontaior{
    height: 70vh;
    width: 98.5vw;
    font-size: 4rem;
    background-color: rgb(125, 125, 125);
    color: rgb(242, 255, 0);
    border: black 2px dashed;

    
}
.msg {
    color: rgb(242, 255, 0); 
}
.hide{
    display: none;
   
}
===------------------------==========================--------------------------
let boxes = document.querySelectorAll(".box");
let msgcontaior = document.querySelector(".msgcontaior");
let msg = document.querySelector(".msg");
let resetbtn = document.querySelector("#reset");
let turn = true;
let winpattern = [
  [0, 1, 2],
  [0, 3, 6],
  [0, 4, 8],
  [1, 4, 7],
  [2, 4, 6],
  [2, 5, 8],
  [3, 4, 5],
  [6, 7, 8],
];
resetbtn.addEventListener("click",()=>{
  restbtn();
})
const restbtn = ()=>{
  msgcontaior.classList.add("hide")
  for( let box of boxes){
    box.innerText = "";
    turn =true
    enablebox();
  }
}

boxes.forEach((box) => {
  box.addEventListener("click", () => {
    if (turn) {
      box.innerText = "X";
      turn = false;
    } else {
      box.innerText = "O";
      turn = true;
    }
    box.disabled = true;

    checkwinner();
    draw();
    
  });
});
const showwinner =(winner)=>{
  msg.innerText =`Congratulations Winner is ${winner}`;
  msgcontaior.classList.remove("hide")
}
const checkwinner = () => {
  for (const pattern of winpattern) {
    let val1 = boxes[pattern[0]].innerText;
    let val2 = boxes[pattern[1]].innerText;
    let val3 = boxes[pattern[2]].innerText;
    if(val1 !== "" && val2 !== "" && val3 !== ""  ){
      if(val1 === val2 && val2 === val3){
        console.log("winner is ", val1)
        
       disablebox()
        showwinner(val1);
        
        
      }
      
    } 
  } 
};
let disablebox=()=>{
  for( let box of boxes){ 
    box.disabled =true
  }
  
}
let enablebox=()=>{
  for( let box of boxes){ 
    box.disabled =false
  }
  
}
let draw =()=>{
  for (const pattern of winpattern) {
    let val1 = boxes[pattern[0]].innerText;
    let val2 = boxes[pattern[1]].innerText;
    let val3 = boxes[pattern[2]].innerText;
  if(val1 === val2 && val2=== val3 )
    if(
    val1 !== val2 && val2 !== val3 ){
    console.log("match is draw")
    }
}}
