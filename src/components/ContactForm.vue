<template>
  <div class="contact-form">
    <h1>Have us reach out</h1>
    <div class="general-error" v-if="errors.general">
      {{ errors.general }}
    </div>
    <form @submit.prevent="handleSubmit">
      <div class="form-group">
        <label for="first">First Name</label>
        <input
          type="text"
          id="first"
          v-model="first"
          :class="{ error: errors.first }"
        />
        <span class="error-message" v-if="errors.first">{{
          errors.first
        }}</span>
      </div>
      <div class="form-group">
        <label for="last">Last Name</label>
        <input
          type="text"
          id="last"
          v-model="last"
          :class="{ error: errors.last }"
        />
        <span class="error-message" v-if="errors.last">{{ errors.last }}</span>
      </div>
      <div class="form-group">
        <label for="email">Email</label>
        <input
          type="email"
          id="email"
          v-model="email"
          :class="{ error: errors.email }"
        />
        <span class="error-message" v-if="errors.email">{{
          errors.email
        }}</span>
      </div>
      <div class="form-group">
        <label for="phone">Phone Number</label>
        <input
          type="tel"
          id="phone"
          v-model="phone"
          :class="{ error: errors.phone }"
        />
        <span class="error-message" v-if="errors.phone">{{
          errors.phone
        }}</span>
      </div>
      <div class="form-group">
        <label for="company">Company</label>
        <input
          type="text"
          id="company"
          v-model="company"
          :class="{ error: errors.company }"
        />
        <span class="error-message" v-if="errors.company">{{
          errors.company
        }}</span>
      </div>
      <button type="submit">Continue</button>
    </form>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import axios from "axios";
import { useRouter } from "vue-router";

export default defineComponent({
  name: "ContactForm",
  setup() {
    const router = useRouter();
    return {
      router,
    };
  },
  data() {
    return {
      first: "",
      last: "",
      email: "",
      phone: "",
      company: "",
      errors: {
        first: "",
        last: "",
        email: "",
        phone: "",
        company: "",
        general: "",
      },
    };
  },
  methods: {
    validateForm() {
      let isValid = true;
      this.errors = {
        first: "",
        last: "",
        email: "",
        phone: "",
        company: "",
        general: "",
      };

      // First Name validation
      if (!this.first) {
        this.errors.first = "First name is required";
        isValid = false;
      }

      // Last Name validation
      if (!this.last) {
        this.errors.last = "Last name is required";
        isValid = false;
      }

      // Email validation
      if (!this.email) {
        this.errors.email = "Email is required";
        isValid = false;
      } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(this.email)) {
        this.errors.email = "Please enter a valid email";
        isValid = false;
      }

      // Phone validation
      if (!this.phone) {
        this.errors.phone = "Phone number is required";
        isValid = false;
      } else if (!/^\+?[\d\s-]{10,}$/.test(this.phone)) {
        this.errors.phone = "Please enter a valid phone number";
        isValid = false;
      }

      // Company validation
      if (!this.company) {
        this.errors.company = "Company name is required";
        isValid = false;
      }

      return isValid;
    },
    handleSubmit() {
      if (this.validateForm()) {
        try {
          axios
            .post(
              "https://dev-api-api.hiring-test.experientialpreview.com/api/lead/fe831bb0-497e-482b-9b3f-aef0b18c37a6",
              {
                first: this.first,
                last: this.last,
                email: this.email,
                phone: this.phone,
                company: this.company,
              }
            )
            .then((response) => {
              console.log(response);
              this.$emit("submit-success");
            });
        } catch (error) {
          console.log(error);
          this.errors.general =
            "There was an error submitting the form. Please try again later.";
        }
      }
    },
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.contact-form {
  position: absolute;
  top: 208px;
  left: 35.76px;
  width: 310px;
  h1 {
    color: #555552;
    width: 310px;
    height: 29px;
    font-family: "Roboto";
    font-weight: 400;
    font-size: 25px;
    line-height: 100%;
    letter-spacing: 0%;
  }

  label {
    position: absolute;
    top: -6px;
    font-family: "ABeeZee";
    font-weight: 400;
    font-size: 12px;
    line-height: 100%;
    letter-spacing: 0%;
    margin-left: 17.27px;
    color: #006315;
    padding-top: 1.26px;
    padding-left: 6.32px;
    padding-right: 6.32px;
    gap: 6.32px;
    background-color: #f4f2ee;
    box-sizing: border-box;
  }

  input {
    width: 310px;
    height: 40.32px;
    border-radius: 3.6px;
    border: 0.72px solid #555552;
    background-color: #f4f2ee;
    box-sizing: border-box;

    font-family: "ABeeZee";
    color: #555552;
    font-weight: 400;
    font-size: 15px;
    line-height: 100%;
    letter-spacing: 0%;
    padding-left: 23.59px;

    &.error {
      border-color: #ff0000;
    }
  }

  .error-message {
    color: #ff0000;
    font-family: "ABeeZee";
    font-size: 12px;
    margin-top: 5px;
  }

  button {
    position: absolute;
    margin-left: 179px;
    background-color: #0b476c;
    width: 131px;
    height: 34.83px;
    border-radius: 4px;
    gap: 5.38px;
    color: #fff;
    font-family: "ABeeZee";
    font-weight: 400;
    font-size: 13.45px;
    line-height: 16px;
    letter-spacing: 0%;
    margin-top: 57.1px;
  }
}

.form-group {
  margin-top: 30.96px;
  position: relative;
}

.general-error {
  color: #ff0000;
  font-family: "ABeeZee";
  font-size: 14px;
  margin-bottom: 10px;
  text-align: center;
}
</style>
