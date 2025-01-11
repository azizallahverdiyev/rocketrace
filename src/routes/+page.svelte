<script>
    import blueRocket from "../assets/rocketBlue.png";
    import redRocket from "../assets/rocketRed.png";
  
    let firstCount = $state(0);
    let secondCount = $state(0);
    function onKeyDown(e) {
           if (e.keyCode == 37 || e.keyCode == 65) {
        firstCount += 1
       } else if (e.keyCode == 39 || e.keyCode == 68) {
        secondCount += 1
       } else if (e.keyCode == 81) {
        firstCount -= 1
       } else if (e.keyCode == 69) {
        secondCount -=1
       }
          
      }
    $effect(() => {
  
      if (firstCount < 0) {
        firstCount = 0
      } else if (firstCount > 5) {
        firstCount = 5
      }
      if (secondCount < 0) {
        secondCount = 0
      } else if (secondCount > 5) {
        secondCount = 5
      }
    }
    )
  </script>
  
  
  
  
  <div class="background">
    <h1 style="left: 200px;">{firstCount}</h1>
    <h1 style="right: 200px;">{secondCount}</h1>
    <div class="game">
      <div class="lane">
        <img src={blueRocket} style={`left: -50px; bottom: ${firstCount * 87 / 5}%;`} alt="Blue Rocket"/>
      </div>
      <div class="lane">
        <img src={redRocket} style={`right: -50px; bottom: ${secondCount * 87 / 5}%;`} alt="Blue Rocket"/>
      </div>
    </div>
  </div>
  <svelte:window on:keydown|preventDefault={onKeyDown} />
    
  <style>
    .lane {
      height: 90vh;
      width: 1px;
      background-color: white;
    }
    .game {
      position: absolute;
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%);
      display: flex;
      flex-direction: row;
      gap: 350px;
    }
    .background {
      background: radial-gradient(circle at bottom, navy 0, black 100%);
      width: 100%;
      height: 100vh;
    }
    h1 {
      color: white;
      font-family: Arial, Helvetica, sans-serif;
      font-weight: 500;
      font-size: 10rem;
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
    }
    img {
      width: 100px;
      height: auto;
      position: absolute;
      transform: rotate(-45deg);transition: all 0.3s linear;
    }
  </style>