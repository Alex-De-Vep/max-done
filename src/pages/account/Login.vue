<template>
  <div class="login">
    <div class="login__container">
      <div class="login__form">
        <h1 class="login__title">Welcome back!</h1>
        <p class="login__text">Please Log in to your account.</p>
        <FormLogin />
        <p class="login__accept">
          by sign up ypu agree to our term and that you haveread our data policy
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import FormLogin from "../../components/form/FormLogin";
export default {
  name: "Login",
  components: { FormLogin },
};
</script>

<style lang="postcss">
.login {
  width: 100%;
  height: 100vh;

  background: url("../../assets/image/login.webp") center/cover #667c89;
}

.login__container {
  position: absolute;
  width: 50%;
  height: 100vh;

  display: flex;
  justify-content: center;
  align-items: center;

  background-color: #ffffff;
}

.login__title {
  color: var(--text);

  font-weight: 700;
  font-size: 48px;
}

.login__text {
  color: var(--text);

  font-weight: 600;
  font-size: 18px;
}

.login__form {
  width: 100%;
  max-width: 500px;
}

.login__accept {
  color: #9e9e9e;

  font-weight: 500;
  font-size: 14px;
}
</style>
