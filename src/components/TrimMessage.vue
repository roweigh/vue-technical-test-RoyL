<template>
    <div class="container">
        <div class="center">
            <textarea cols="100" rows="10" v-model="message" @keyup="alertCheck"></textarea>
            <div>
                <button class="button" @click="message = ''">Clear All</button>
                <!-- Clears the input whenever "Clear All" is clicked. -->
                <transition name="fade"> 
                    <button class="button" @click="message = message.slice(0, 200)" v-show="alert">Trim</button>
                    <!-- Trims the content in the textbox if the length is greater than 200. Only appears if alert is set to true. -->
                </transition>
            </div>
        </div>   
    </div>
    <transition name="fade">
        <div class="alert" v-show="alert">Message has exceeded 200 characters!</div>  
        <!-- A red alert message is shown every time the boolean is set to true. -->
    </transition>
</template>

<script>
    //TrimMessage component that trims contents in a textbox to 200 characters in length.
    export default {
        data() {
            return {
                alert: false,
                message: '',
            }
        },
        watch: {
            message: function() {
                if (this.message.length > 200) {
                    //Checks the length of input textbox contents every time the input is changed and alert is set to true if the number of characters is 201 or higher.
                    this.alert = true;
                } else {
                    //alert is set to false if the number of characters is 200 or lower.
                    this.alert = false;
                }
            }
        }
    }
</script>

<style scoped>
    .center {
        display: inline-flex;
        margin: 20px;
    }

    .container {
        margin: 20px;
        padding: 25px;
        box-shadow: 5px 5px 10px #888888;
    }
    
    .alert {
        margin: 20px 35px;
        padding: 20px 50px;
        background-color: #F8D7DA;
        color: #721C24;
        border:1px solid #ffb5bc;
        border-radius: 20px;
    }

    .button {
        margin: 0px 20px 10px;
        color:#ffffff; 
        background-color: #0075FF;
        border:1px solid #0075FF;
        border-radius:5px; 
        font-size:17px; 
        cursor:pointer; 
        display: block;
    }

    textarea  
    {  
        font-family: Avenir, Helvetica, Arial, sans-serif;
        resize: none;
        overflow: auto;
    }

    .button:hover {
        background-color:#006dd4;
    }

    .fade-enter, .fade-leave-to, .fade-enter-from{
        opacity: 0;
    }

    .fade-enter-active, .fade-leave-active{
        transition: opacity 0.25s ease;
    }
</style>