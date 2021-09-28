<template>
  <form id="form-login" class="form">
    <div class="form__field">
      <label for="login" class="form__label">Email Address</label>
      <input
        v-model="loginData.login"
        class="form__input"
        id="login"
        type="text"
      />
    </div>
    <div class="form__field">
      <label for="password" class="form__label">Password</label>
      <input
        v-model="loginData.password"
        class="form__input"
        id="password"
        type="password"
      />
    </div>
    <div class="form__check-wrapper">
      <div class="form__check">
        <input v-model="loginData.check" type="checkbox" />
        <p class="form__check-text">Remember me</p>
      </div>
      <a class="form__link" href="">Forgot password?</a>
    </div>
    <div class="form__button">
      <Button
        @:click="consoleLogin()"
        @:keydown.enter="consoleLogin()"
        text="Login"
      />
      <Button text="Create account" transparent="true" />
    </div>
  </form>
</template>

<script>
import Button from "../button/Button";

export default {
  name: "FormLogin",
  components: { Button },
  data() {
    return {
      loginData: {
        login: "",
        password: "",
        check: false,
      },
    };
  },
  methods: {
    consoleLogin() {
      alert(this.loginData.login);
    },
  },
};
</script>

<style scoped>
.form {
  margin: 40px 0;
}

.form__field {
  margin-bottom: 20px;
  padding: 10px;

  border: 3px solid #667c89;
  border-radius: 8px;
}

.form__label {
  color: var(--light-text);

  font-weight: 400;
  font-size: 16px;
}

.form__input {
  width: 100%;

  margin-top: 10px;

  color: var(--text);

  font-weight: 500;
  font-size: 18px;

  border: 0;
  outline: none;
}

.form__check {
  display: flex;
}

.form__check-wrapper {
  display: flex;
  justify-content: space-between;

  margin: 10px 0 20px;
}

.form__check-text {
  color: var(--text);

  font-weight: 600;
  font-size: 16px;
}

.form__link {
  color: #b62f2f;

  font-weight: 500;
  font-size: 16px;

  text-decoration: none;
}

.form__button {
  display: grid;
  grid-gap: 40px;
  grid-template-columns: 1fr 1fr;
}
</style>