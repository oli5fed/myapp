<template>
    <div id="app">

            <header>
            <div class="logo">
                <img src="./assets/logo.png" alt="Logo-Vue" class="logo-vue">
            </div>

        </header>
        <main>
            <router-view/>
        </main>
    </div>
</template>



<style>
#app {
  background: url();
  height: 100vh;
}

#app > header {
  width: 100%;
  max-height: 100px;
  background-color: rgba(0, 0, 0, 0.5);
  position: relative;
  margin: 0;
  padding: 5px 0;
  z-index: 100;
}

.logo {
  width: 70px;
  margin: 0 auto;
}

</style>
