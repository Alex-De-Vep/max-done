<template>
  <div class="login">
    <div class="login__container">
      <div class="login__form">
        <h1 class="login__title">Welcome back!</h1>
        <p class="login__text">Please Log in to your account.</p>
        <form action="" class="form">
          <div class="form__field">
            <label for="login" class="form__label">Email Address</label>
            <input class="form__input" id="login" type="text">
          </div>
          <div class="form__field">
            <label for="password" class="form__label">Password</label>
            <input class="form__input" id="password" type="password">
          </div>
          <div class="form__check-wrapper">
            <div class="form__check">
              <input type="checkbox">
              <p class="form__check-text">Remember me</p>
            </div>
            <a class="form__link" href="">Forgot password?</a>
          </div>
          <div class="form__button">
            <button type="submit" class="button">Login</button>
            <button type="submit" class="button button_transparent">Create account</button>
          </div>
        </form>
        <p class="login__accept">
          by sign up ypu agree to our term and that you haveread our data policy
        </p>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: "Login",
};

const fields = document.querySelectorAll(".form__input");
fields.forEach((field) => {
  field.addEventListener("click", () => {
    const activeFiled = document.querySelector(".form__field .active");
    activeFiled.classList.remove("active");
    field.classList.add("active");
  });
});

</script>

<style lang="postcss">

.login {
  width: 100%;
  height: 100vh;

  background: url("../../assets/image/login.webp") center/cover #667c89;

  &__image {
    width: 100%;
    height: 100%;

    object-fit: cover;

    &-wrapper {
      overflow: hidden;
    }
  }

  &__container {
    position: absolute;
    width: 50%;
    height: 100vh;

    display: flex;
    justify-content: center;
    align-items: center;

    background-color: #ffffff;
  }

  &__title {
    color: var(--text);

    font-weight: 700;
    font-size: 48px;
  }

  &__text {
    color: var(--text);

    font-weight: 600;
    font-size: 18px;
  }

  &__form {
    width: 100%;
    max-width: 500px;
  }

  &__accept {
    color: #9e9e9e;

    font-weight: 500;
    font-size: 14px;
  }
}

.form {
  margin: 80px 0;

  &__field {
    margin-bottom: 20px;
    padding: 10px;

    border: 3px solid #667c89;
    border-radius: 8px;
  }

  &__label {
    color: var(--light-text);

    font-weight: 400;
    font-size: 16px;
  }

  &__input {
    width: 100%;

    margin-top: 10px;

    color: var(--text);

    font-weight: 500;
    font-size: 18px;

    border: 0;
    outline: none;
  }

  &__check {
    display: flex;

    &-wrapper {
      display: flex;
      justify-content: space-between;

      margin: 10px 0 20px;
    }

    &-text {
      color: var(--text);

      font-weight: 600;
      font-size: 16px;
    }
  }

  &__link {
    color: #b62f2f;

    font-weight: 500;
    font-size: 16px;

    text-decoration: none;
  }

  &__button {
    display: grid;
    grid-gap: 40px;
    grid-template-columns: 1fr 1fr;
  }
}

.button {
  width: 100%;

  padding: 20px;

  color: #ffffff;

  font-weight: 600;
  font-size: 18px;

  border: 0;
  border-radius: 8px;

  background-color: #667c89;

  cursor: pointer;

  &_transparent {
    color: var(--text);

    background-color: #ffffff;

    border: 3px solid #667c89;
  }
}

</style>