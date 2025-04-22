<template>
  <div class="home">
    <ContactForm v-if="!showThankYou" @submit-success="handleSubmit" />
    <ThankYou v-else />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import ContactForm from "@/components/ContactForm.vue";
import ThankYou from "@/components/ThankYou.vue";

export default defineComponent({
  name: "HomeView",
  components: {
    ContactForm,
    ThankYou,
  },
  setup() {
    const showThankYou = ref(false);

    const handleSubmit = () => {
      showThankYou.value = true;
      setTimeout(() => {
        showThankYou.value = false;
      }, 5000);
    };

    return {
      showThankYou,
      handleSubmit,
    };
  },
});
</script>

<style scoped lang="scss"></style>
