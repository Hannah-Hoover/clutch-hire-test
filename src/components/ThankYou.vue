<template>
  <div class="thankyou">
    <p>Thank you</p>
    <p>We will contact you shortly</p>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "ThankYou",
});
</script>

<style scoped lang="scss">
.thankyou {
  width: 227px;
  height: 116px;
  margin-top: 366px;
  margin-left: 83px;
  text-align: center;
  font-family: "Roboto";
  font-weight: 400;
  font-size: 25px;
  line-height: 100%;
  letter-spacing: 0%;
  background-color: #f4f2ee;
  color: #555552;
}
</style>
