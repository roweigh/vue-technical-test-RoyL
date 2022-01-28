<template>
    <div>
        <div class="container">
            <div>
                <input v-model="message">
                <button class="button" @click="addItem()">Create Message</button>
            </div> 
            <div id="selector">
                <input 
                    type="checkbox" 
                    id="showMessage" 
                    name="showMessage"
                    v-model="checked">
                <label for="showMessage">Show Messages</label>
                <!-- Shows/Hides message cards depending on whether "Show Messages" checkbox is. -->
            </div>
        </div>
        <div class="messageGroup">
            <transition name="fade">
                <div v-show="checked" >
                    <transition-group name="fade"> 
                        <ul class="messageCard" v-for="item in msgList" :key="item">
                            <!--A MyMessage component instance is created with input contents passed in. -->
                            <MyMessage @deletedItem="deleteItem($event)" :msg=item />
                        </ul>
                    </transition-group>
                </div>
            </transition> 
        </div>
    </div>
</template>

<script>
    //MyMessageList component that displays components in a list from top to bottom.
    import MyMessage from './MyMessage.vue'
    export default {
        data() {
            return {
                message: '',
                checked: true,
                msgList: []
            }
        },
        methods: {
            addItem() {
                //When the "Create Message" button is clicked, appends contents of input text box to msgList array.
                if (this.message.length > 0) {
                    this.msgList.push(this.message);
                    this.message = '';
                    if (this.msgList.length >= 10) {
                        //Subtitutes msgList with an empty array when the number of components created reaches 10.
                        this.msgList = [];
                    }
                }
            },
            deleteItem($event) {
                //Receives signal from MyMessage and removes the first instance of received payload within msgList.
                this.msgList.splice(this.msgList.indexOf($event), 1)
            }
        },
        components: {
            MyMessage
        }
    }
</script>

<style>
    .container {
        margin: 20px;
        padding: 25px;
        box-shadow: 5px 5px 10px #888888;
    }

    .messageGroup {
        margin: 35px;
    }

    .messageCard {
        margin: 20px 35px;
        padding: 10px 50px;
        border-radius: 20px;
        box-shadow: 10px 10px 15px #888888;
    }
    
    .button {
        margin: 10px 20px 10px;
        background-color: #0075FF;
        border:1px solid #0075FF;
        border-radius:5px; 
        font-size:17px;
        display:inline-block; 
        cursor:pointer; 
        color:#ffffff; 
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