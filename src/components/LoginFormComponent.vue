<script src="https://unpkg.com/vue-router/dist/vue-router.js"></script>
<template>
    <form v-on:submit.prevent="onSubmit">
        <label for="username">Username</label>
        <input type="email" class="input" name="username" id="username" v-model="input.email">
        <label for="password">Password</label>
        <input type="password" class="input" name="password" id="password" v-model="input.password">
        <p id="error" class="shake">Incorrect email or password. Please try again</p>
        <input type="submit" value="Log In">
    </form>
</template>

<script>
import axios from 'axios'

export default {
    name: 'LoginFormComponent',
    data() {
        return {
            input: {
                email: "",
                password: "",
                jwtToken: ""
            }
        }
    },
    methods: {
        onSubmit() {
            const inputfields = document.querySelectorAll('.input');
            inputfields.forEach(input => {
                input.classList.remove("input-error");
            })
            axios.post("http://192.168.0.25:5000/user/login", 
            {
                email: this.input.email,
                password: this.input.password
            })
            .then((response) => {
                console.log(response);
                alert("Logget inn");
            }).catch((error) => {
                console.log(error);
                const errorField = document.getElementById('error');
                inputfields.forEach(input => {
                    input.classList.add("input-error");
                })
                console.log(inputfields);
                errorField.classList.add("error-show");
            })
        }
    }
}
</script>

<style scoped>
form {
    margin: 20px auto;
    width: 80%;
    max-width: 600px;
}


label {
    display: block;
    color: white;
    font-size: 18px;
    letter-spacing: 2px;
    width: 100%;
    margin: 0em auto 0.5em auto;
}

label[for=password] {
    margin-top: 1em;
}

input[type=email], input[type=password] {
    display: block;
    line-height: 1.5em;
    border-radius: 10px;
    border: 1px solid #F6AE2D;
    padding: 0.5em;
    font-size: 1em;
    width: 100%;
    margin: auto;
    box-sizing: border-box;
    box-shadow:
        0 2.8px 2.2px rgba(0, 0, 0, 0.028),
        0 6.7px 5.3px rgba(0, 0, 0, 0.04),
        0 12.5px 10px rgba(0, 0, 0, 0.05),
        0 22.3px 17.9px rgba(0, 0, 0, 0.06),
        0 41.8px 33.4px rgba(0, 0, 0, 0.072),
        0 100px 80px rgba(0, 0, 0, 0.1);
}

input[type=submit] {
    display: block;
    background: #001D4A;
    border-radius: 10px;
    line-height: 1em;
    color: white;
    width: 100%;
    padding: 0.5em;
    margin: 2em auto 0em auto;
    font-size: 18px;
    font-weight: bold;
    border: 1px solid #001D4A;
}

input[type=email]:focus, input[type=password]:focus {
    border: 1px solid #001D4A;
}

input[type=submit]:focus {
    border: 1px solid white;
}

#error {
    visibility: hidden;
}

.error-show {
    visibility: visible !important;
}

@keyframes shake {
  from, to {
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
  }

  10%, 30%, 50%, 70%, 90% {
    -webkit-transform: translate3d(-10px, 0, 0);
    transform: translate3d(-5px, 0, 0);
  }

  20%, 40%, 60%, 80% {
    -webkit-transform: translate3d(10px, 0, 0);
    transform: translate3d(5px, 0, 0);
  }
}

.input-error {
  -webkit-animation-name: shake;
  animation-name: shake;
  animation-duration: 0.5s;
  border-color: red;
}



</style>