<template>
  <div id="cursor"></div>
</template>

<script>
export default {
  name: "Cursor",
  data() {
    return {
      shouldShowCursor: true,
    };
  },
  mounted() {
    const cursor = document.getElementById("cursor");
    this.shouldShowCursor = localStorage.getItem("showCursor") !== "false";

    if (this.shouldShowCursor) {
      cursor.style.display = "block";
    }

    document.addEventListener("mousemove", (e) => {
      if (cursor !== null && this.shouldShowCursor) {
        cursor.style.left = e.pageX + "px";
        cursor.style.top = e.pageY + "px";
      }
    });

    window.addEventListener("unload", () => {
      localStorage.setItem("showCursor", cursor.style.display !== "none");
    });
  },
};
</script>

<style lang="scss" scoped>

#cursor {
  display: none;
  position: absolute;
  left: 0;
  top: 0;
  width: 40px;
  height: 40px;
  border-radius: 100%;
  border: 1px solid $navy;
  pointer-events: none;
  z-index: 999;
}

</style>
