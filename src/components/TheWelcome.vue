<template>
  <div>
    Hello World {{test}}
  </div>
  <div>
    I am {{loggedIn ? "Logged in" : "Not logged in"}}
  </div>
  <div>
    Use the native side of things to login.
  </div>
  <input :value="message" /><button @click="sendData">Send</button>
</template>

<script>
var oWebViewInterface = null;

export default {
  name: "Homepage",
  setup(){
      
      oWebViewInterface = window.nsWebViewInterface;
      
      if (oWebViewInterface) {
        console.log("valid, emitting 'loaded'")
        oWebViewInterface.emit("loaded", `initialized webview`);
      }
  },
  methods:{
    sendData(){
      console.log(message)
    }
  },
  data(){
    return {
      test: null,
      message: null,
      loggedIn: false,
    }
  },
  methods(){

  }
}
</script>