<template>
  <div class="layout sticky-header">
    <header class="header sticky">
      <div class="container">
        <div class="left">
          <g-link to="/" class="home-link active--exact active"
            ><img src="/img/logo.svg" alt="" class="logo"
          /></g-link>
        </div>
        <nav class="nav right">
          <g-link class="nav__link" to="/about/">About</g-link>
          <g-link class="nav__link" to="/post2/">Post2</g-link>
        </nav>
      </div>
    </header>
    <slot />
    <footer class="footer">
      <div class="container">Copyright © 2021</div>
    </footer>
  </div>
</template>

<style></style>
