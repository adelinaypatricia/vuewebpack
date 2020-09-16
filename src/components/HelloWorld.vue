/* eslint-disable vue/valid-template-root */
<template>
<div class="wrapper fadeInDown">
  <a href="#" @click.prevent="signout">登出</a>
  <div id="formContent">
    <!-- Login Form -->
    <form @submit.prevent="signin">
      <input type="text" id="login" class="fadeIn second" name="login" placeholder="login" v-model="user.ACC">
      <input type="text" id="password" class="fadeIn third" name="login" placeholder="password" v-model="user.PASSWORD">
      <input type="submit" class="fadeIn fourth" value="Log In">
    </form>

    <!-- Remind Passowrd -->
    <div id="formFooter">
      <a class="underlineHover" href="#">Forgot Password?</a>
    </div>

  </div>
</div>
</template>

<script src="//maxcdn.bootstrapcdn.com/bootstrap/4.0.0/js/bootstrap.min.js"></script>
<script src="//cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      user: {
        ACC: '',
        PASSWORD: '',
      }
    };
  },
  methods: {
    signin() {
      const api = "http://tp-cvc-v01:8000/Q_API/LOGIN";
      const vm = this;
      this.$http.post(api, vm.user).then(response => {
        console.log(response.data);
      });
    },
    signout() {
      const api = "https://vue-course-api.hexschool.io/logout";
      const vm = this;
      this.$http.post(api).then(response => {
        console.log(response.data);
        if (response.data.success) {
          vm.$router.push('/login');
        }
      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
