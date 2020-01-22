<template>
  <div id="app">
    <h1>Что-то что не имеет смысла</h1>
    <hr>
    <HeadReg
            v-if="REG_FLAG === false"
            @login-to="loginTo"
            @open-reg="openReg"
    />
    <Logout v-if="REG_FLAG === true"
            @log-out="logOut"
    />
    <hr>

    <WindowReg
            v-if="WinReg_FLAG"
            @success-reg="successReg"
    />

    <WindowEdit
            v-if="EDIT_FLAG"
            @close-edit="closeEdit"
    />
    <ListBlog
            v-bind:REG_FLAG="REG_FLAG"
            @edit-post="editPost"
    />
  </div>
</template>

<script>
  import Logout from "@/components/Logout";
  import HeadReg from "@/components/HeadReg";
  import ListBlog from "@/components/ListBlog";
  import WindowEdit from "@/components/WindowEdit";
  import WindowReg from "@/components/WindowReg";
  export default {
    name: 'app',
    data(){
      return {
        REG_FLAG: false,
        EDIT_FLAG: false,
        WinReg_FLAG: false
      }
    },
    methods: {

      loginTo(){
        this.REG_FLAG = true;
      },

      openReg(){
        this.WinReg_FLAG = true;
      },

      logOut(){
        this.REG_FLAG = false;
      },

      successReg(){
        this.WinReg_FLAG = false;
      },

      editPost(){
        this.EDIT_FLAG = true;
      },

      closeEdit(){
        this.EDIT_FLAG = false;
      }
    },
    components: {
      HeadReg,
      ListBlog,
      Logout,
      WindowEdit,
      WindowReg
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 15px;
  }
</style>