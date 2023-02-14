<script>
export default {
  name: "Header"
}
</script>

<template>
  <header>
    <div class="wrapper">
      <nav>
        <RouterLink class="item" to="/">Test</RouterLink>
        <RouterLink class="item" to="/about">About</RouterLink>
      </nav>
    </div>
  </header>
</template>

<style lang="scss">
@import "@/styles/main.scss";
header {
  border: 1px solid $orange;
  position: absolute;
  bottom: 50px;
  left: 50%;
  transfrom: translateX(-50%);


  nav {
    display: flex;
    justify-content: space-between;
    align-items: center;

    .item {
       color: $orange;
      height: 50px;
      width: 120px;
      display: flex;
      justify-content: center;
      align-items: center;
      text-decoration: none;
    }
  }

}
</style>