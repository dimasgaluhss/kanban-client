<template>
  <div>
  <login 
  v-if = "page === 'loginPage'"
  @requestLogin = "login"
  @requestChangePage = "changePage"
  ></login>

  <register
  v-if = "page === 'registerPage'"
  @requestCreate = "register"
  @requestChangePage = "changePage"
  ></register>

  <mainPage
  v-if = "page === 'mainPage'"
  @requestLogout = "logout"
  @fetchTask = "fetchTask"
  :list = "tasks"
  @requestEdit = "edit"
  @requestCreate = "add"
  @requestDelete = "destroy"
  ></mainPage>
</div>
</template>

<script>
import axios from 'axios'
import register from './components/register'
import login from './components/login'
import mainPage from './components/mainPage'

export default {
    data() {
        return {

        }
    },
    components: {
    register,
    login,
    mainPage
    }
}
</script>

<style>

</style>