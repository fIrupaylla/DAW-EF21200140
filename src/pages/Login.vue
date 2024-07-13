<template>
    <q-page class="login-page">
      <div class="login-card q-pa-md">
        <q-card-section class="text-center q-py-xl">
          
          <q-avatar size="80px" class="q-mb-md">
            <q-icon name="person" size="56px" color="green" />
          </q-avatar>
          <div
            style="font-size: 1.5em; color: black; font-weight: 100"
            class="text-center"
          >
            Login
          </div>
        </q-card-section>
        <q-card-section>
          <q-form @submit="onSubmit">
            <q-input
              outlined
              v-model="user.email"
              label="Username"
              dense
              class="q-mb-md"
              prepend-inner-icon="account_circle"
              color="red"
              required
            />
            <q-input
              outlined
              v-model="user.password"
              label="Password"
              type="password"
              dense
              class="q-mb-md"
              prepend-inner-icon="lock"
              color="red"
              required
            />
        
            <q-btn
              type="button"
              icon="login"
              color="green"
              label="Entrar"
              class="full-width q-mb-md"
              @click="signIn"
              style="background: linear-gradient(to right, #ff6f61, #d32f2f)"
            />
          </q-form>
        
  
          
        </q-card-section>
      </div>
    </q-page>
  </template>
  
  <script>
  export default {
    name: "LoginForm",
    data() {
      return {
        user: {
          email: "",
          password: "",
        },
      };
    },
    methods: {
      signIn() {
        let URL = "http://68.183.142.21/api/v1/user/signin";
        this.$api
          .post(URL, this.user)
          .then((response) => {
            localStorage.setItem("userData", JSON.stringify(response.data));
            this.$router.push("/movies");
          })
          .catch((error) => {
            console.log(JSON.stringify(error));
          });
      },
    },
  };
  </script>
  
  <style scoped>
  .login-page {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background: linear-gradient(135deg, hsl(98, 57%, 65%) 0%, #02883e 100%);
  }
  
  .login-card {
    background: rgba(255, 255, 255, 1);
    border-radius: 15px;
    padding: 2rem;
    max-width: 400px;
    width: 100%;
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(10px);
    -webkit-backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.3);
  }
  
  .q-input__inner {
    color: #000;
  }
  
  .q-input__inner:focus,
  .q-input__inner:active,
  .q-input__inner {
    border-color: rgba(0, 0, 0, 0.3);
  }
  </style>
  