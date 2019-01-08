<template>
    <div class="login">
        <h1>Keiser Admin Login</h1>
        <br>
        <input type="text" name="username" v-model="input.username" placeholder="Username" />
        <br>
        <br>
        <input type="password" name="password" v-model="input.password" placeholder="Password" />
        <br>
        <br>
    
        <button type="button" v-on:click="login()">Login</button>
    </div>
</template>

<script>
export default {
    name: 'Login',
    data() {
        return {
            input: {
                username: "",
                password: ""
            }
        }
    },
    methods: {
        login() {
            if(this.input.username !="" && this.input.password !="") { 
                if(this.input.username == this.$parent.admin.username && this.input.password == this.$parent.admin.password) {
                    this.$emit("authenticated", true);
                    this.$router.replace({ name: "secure"});
                } else {
                    alert("Your username and/or password is incorrect");
                }
            } else {
                alert("Your username and password must exist");
            }
        }
    }
}
</script>

<style scoped>
    .login {
        width: 400px;
        border: 1px solid #ccc;
        background-color: #fff;
        margin: auto;
        margin: 200px;
        padding: 20px;
    };

    /* .keiser-font {
        font-family: "Keiser";
        color: #d10a2c;
        font-size: 180%; 
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
    }; */

</style>

