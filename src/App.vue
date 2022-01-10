<template>
<header>
   <router-link to="/">
      <h1><span>Pau.K</span> Movie Menu</h1> 
  
    </router-link>
</header>
  <main>
    <router-view/>
  </main>
</template>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Fira Sans", sans-serif;
  text-decoration: none;

}

body {
        background-color: #35495e;
}

header{
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 16px;
  background-color: #2C3D4E;
  box-shadow: 0px 0px 6px rgba(0, 0, 0, 0.1);
}
h1 {
  color: #FFF;
  font-size: 28px;
}
span {
  color: #42B883;
}



</style>
