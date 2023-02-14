<script>
export default {
  name: "Header",
  mounted() {
    let nav = document.querySelector("nav");
    let navItems = [...nav.childNodes]
    navItems.forEach((item) => {
      item.addEventListener("mouseover", () => {
        item.classList.add("active")
      });
      item.addEventListener("mouseout", () => {
        item.classList.remove("active")
      });
    });

  }

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
  border: 1px solid $navy;
  position: absolute;
  bottom: 50px;
  left: 50%;
  transform: translateX(-50%);



  nav {
    display: flex;
    justify-content: space-between;
    align-items: center;

    .item {
      color: $navy;
      height: 50px;
      width: 120px;
      display: flex;
      justify-content: center;
      align-items: center;
      text-decoration: none;

      &:not(:last-child) {
        border-left: none;
      }

      &:hover {
        background-color: $purple-xlight;
      }
    }
  }

}
</style>