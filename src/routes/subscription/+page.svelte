<style>* {
  font-size: 62.5%;
  margin: 0;
  box-sizing: border-box;
}

body {
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: url(./assets/background.jpg);
  background-size: cover;
  background-position: center;
}

main {
  width: 110rem;
  height: 53rem;
  border: 1px solid red;
  display: flex;
  justify-content: space-between;
  padding: 8rem;
  background: rgba(255, 255, 255, 0.7);
  border: 2rem solid #ffffff;
  border-radius: 3rem;
}

.content-info {
  width: 28rem;
  height: auto;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: start;
}

h1 {
  font-size: 5rem;
  font-family: "IBM Plex Sans";
  font-style: normal;
  font-weight: 700;
  color: #141843;
}

h1 span {
  font-size: 3rem;
  margin-right: 0.2rem;
}

h2 {
  font-size: 2rem;
  font-family: "Merriweather";
  font-style: normal;
  font-weight: 700;
  color: #141843;
}

h3 {
  font-size: 2rem;
  font-family: "IBM Plex Sans";
  font-style: normal;
  font-weight: 500;
}

h4 {
  font-size: 1.5rem;
  font-family: "IBM Plex Sans";
  font-style: normal;
  font-weight: 500;
  color: #141843;
}

button {
  height: 5rem;
  padding: 0 2rem;
  font-size: 1.8rem;
  font-family: "IBM Plex Sans";
  font-weight: 500;
  border-radius: 1rem;
  border: 0;
  cursor: pointer;
}

.button-pink {
  background-color: #edbbff;
}

.button-pink:hover {
  background-color: #e7aafd;
}

.button-blue {
  background-color: #aef1f5;
}

.button-blue:hover {
  background-color: #92f0f5;
}

.button-orange {
  background-color: #ffddb6;
}

.button-orange:hover {
  background-color: #ffd09b;
}

@media (max-width: 1150px) {
  * {
    font-size: 50%;
  }
}

@media (max-width: 920px) {
  * {
    font-size: 40%;
  }
}

@media (max-width: 750px) {
  * {
    font-size: 30%;
  }
}

@media (max-width: 550px) {
  * {
    font-size: 50%;
  }
 main {
  width: auto;
  height:auto;
  flex-direction: column;
  gap:10rem;
 }
 .content-info{
  gap:2rem;
 }
}

@media (max-width: 420px) {
  * {
    font-size: 40%;
  }
}

@media (max-width: 335px) {
  * {
    font-size: 35%;
  }
}</style>


  <svelte:head>
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>iCodeThis - Challenge #11: Pricing Table</title>
    
    <link
      href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@500;700&family=Merriweather:wght@700&display=swap"
      rel="stylesheet"
    />
    
  </svelte:head>
  <body>
    <main>
      <div class="content-info">
        <h2>Free</h2>
        <div class="price">
          <h1><span>$</span>0</h1>
          <h4>Free for your whole team</h4>
        </div>
        <h3>For individual or teams looking to organize anything.</h3>
        <button class="button-pink">Get started</button>
      </div>
      <div class="content-info">
        <h2>Standard</h2>
        <div class="price">
          <h1><span>$</span>6</h1>
          <h4>Per user per month</h4>
        </div>
        <h3>For teams that need to manage more work.</h3>
        <button class="button-blue">Upgrade Now</button>
      </div>
      <div class="content-info">
        <h2>Premium</h2>
        <div class="price">
          <h1><span>$</span>12</h1>
          <h4>Per user per month</h4>
        </div>
        <h3>Best for teams that need to track multiple projects.</h3>
        <button class="button-orange">Try for free</button>
      </div>
    </main>
  </body>

