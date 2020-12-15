<template>
  <div class="flex-center">
    <div class="login-card">
      <form class="login-form">
        <h1>Create a new account</h1>
        <div class="form-group">
          <label for="email">Your E-mail</label>
          <input type="email" id="email" />
        </div>
        <div class="form-group">
          <label for="password">Password</label>
          <input type="password" id="password" />
        </div>
      </form>
      <button type="button">Sign up</button>
    </div>
  </div>
</template>





<style lang="scss" scoped>
.login {
  &-card {
    text-align: left;
    border-radius: 10px;
    width: 300px;
    background: white;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    padding: 3rem;
  }
}

h1 {
  margin-top: 0;
  color: black;
}

.form-group {
  display: flex;
  flex-direction: column;
  margin-bottom: 1rem;

  input {
    border: none;
    border-bottom: 2px solid gray;
    padding: 10px 5px;
  }
  label {
    margin-bottom: 5px;
    color: gray;
    font-size: 10px;
  }
}

button {
  display: inline;
  background: green;
  color: white;
  width: 18.4rem;
  height: 4rem;
}
</style>
