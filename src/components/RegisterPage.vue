<template>
  <div class="hero-body bg-img img-responsive">
    <div class="container">
      <div class="columns is-centered">
        <div class="column is-5-tablet is-4-desktop is-3-widescreen">
          <form class="box">
            <figure class="image container is-64x64">
              <img
                src="https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.vexels.com%2Fpng-svg%2Fpreview%2F156808%2Flotus-flower-icon-lotus-icons&psig=AOvVaw2TABKIVWB_CR0fjRZLnHp1&ust=1610706956433000&source=images&cd=vfe&ved=0CAIQjRxqFwoTCNC7_oWdm-4CFQAAAAAdAAAAABAD"
              />
            </figure>
            <div class="mb-2">
              <h1>Register</h1>
            </div>
            <div class="field">
              <label class="label">Username</label>
              <div class="control has-icons-left">
                <input
                  type="text"
                  placeholder="e.g. icanq"
                  class="input"
                  v-model="username"
                  required
                />
                <span class="icon is-small is-left">
                  <i class="fas fa-user-secret"></i>
                </span>
              </div>
            </div>
            <div class="field">
              <label class="label">Email</label>
              <div class="control has-icons-left">
                <input
                  type="email"
                  placeholder="email"
                  class="input"
                  v-model="email"
                  required
                />
                <span class="icon is-small is-left">
                  <i class="fa fa-envelope"></i>
                </span>
              </div>
            </div>
            <div class="field">
              <label class="label">Password</label>
              <div class="control has-icons-left">
                <input
                  type="password"
                  placeholder="email"
                  class="input"
                  v-model="password"
                  required
                />
                <span class="icon is-small is-left">
                  <i class="fa fa-lock"></i>
                </span>
              </div>
            </div>
            <div class="has-text-centered">
              <small>
                <a href="#" @click.prevent="toLogin"
                  >Already have an account?</a
                >
              </small>
            </div>
            <div class="mt-2 has-text-centered">
              <button class="button is-success" @click.prevent="onRegister">
                Register
              </button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "registerPage",
  props: ["checkAcc"],
  data() {
    return {
      username: "",
      email: "",
      password: "",
      isLoading: false,
    };
  },
  methods: {
    toLogin() {
      this.checkAcc(true);
    },
    onRegister() {
      this.$api({
        method: "POST",
        url: "register",
        data: {
          username: this.username,
          email: this.email,
          password: this.password,
        },
      })
        .then(() => {
          this.checkAcc(true);
        })
        .catch((err) => {
          console.log(err)
        });
    },
  },
};
</script>

<style scoped>
h1 {
  font-weight: 600;
  font-size: 2em;
  text-align: center;
}
</style>