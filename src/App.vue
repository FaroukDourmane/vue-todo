<template>
  <div id="app">
    <div id="navbar">
        <ul>
            <li> <router-link to="/">  Home </router-link> </li>
            <li> <router-link to="/about">  About </router-link> </li>
        </ul>
    </div>

    <router-view />
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: #f9f9f9;
  min-height: 100vh;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

#navbar{
    display: block;
    background: #f9f9f9;
    padding: 20px 10px;
}

#navbar ul{ list-style: none;text-align: center;margin: 0;padding: 0;}
#navbar ul li{
    display: inline-block;
    margin: 0 5px;
}
#navbar ul li a{
    display: block;
    line-height: 40px;
    color:#35495e;
    text-decoration: none;
    border: 1px #35495e solid;
    padding: 0 10px;
    border-radius:30px;
}
</style>
