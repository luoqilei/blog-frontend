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
          <g-link class="nav__link" to="/journal/">Journal</g-link>
          <g-link class="nav__link" to="/contact/">Say Hi</g-link>
        </nav>
      </div>
    </header>
    <slot />
    <footer class="footer">
      <div class="container">Copyright © 2021</div>
    </footer>
  </div>
</template>

<style scoped>
.header {
  position: relative;
  height: 6rem;
  z-index: 10;
}

.header.sticky {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
}

.header > .container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 100%;
}

.home-link {
  text-decoration: none;
}

.logo {
  height: 1.5rem;
}

.site-name {
  font-size: 0.9rem;
  font-weight: 700;
  letter-spacing: 0.05em;
  text-decoration: none;
  text-transform: uppercase;
}

.nav > a {
  font-size: 0.9rem;
  font-weight: 600;
  text-decoration: none;
  margin-top: 4px;
  margin-right: 3rem;
  padding-bottom: 4px;
  border-bottom: 1px solid;
  border-color: transparent;
  transition: border 0.15s;
}

.nav > a:last-child {
  margin: 0;
}

.nav > .active,
.nav > :hover {
  border-color: inherit;
}

.footer {
  font-size: 0.8rem;
  padding: 6rem 0;
}

h1 {
  letter-spacing: -0.01em;
}
.layout {
  padding: 0;
}
.layout.sticky-header {
  padding: 6rem 0 0;
}
</style>
