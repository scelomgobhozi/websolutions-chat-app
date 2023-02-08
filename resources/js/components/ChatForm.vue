<template>
    <div class="input-group">
        <input
            id="btn-input"
            type="text"
            name="message"
            class="form-control input-sm"
            placeholder="Type your message here..."
            v-model="newMessage"
            @keyup.enter="sendMessage"
        />

        <span class="input-group-btn">
            <button class="btn btn-primary btn-sm" id="btn-chat" @click="sendMessage">
                Send
            </button>
        </span>
    </div>
</template>

<script>
export default {
    props:["user"],
    name: "ChatForm",
    data(){
        return{
            newMessage:"",
        }
    },
    methods:{
        sendMessage(){
            this.$emit("messagesent",{
                user:this.user,
                message:this.newMessage,
            });

            this.newMessage = "";
        },

        // addMessage(message) {
        //     //Pushes it to the messages array
        //     this.messages.push(message);
        //     //POST request to the messages route with the message data in order for our Laravel server to broadcast it.
        //     axios.post('/messages', message).then(response => {
        //         console.log(response.data);
        //     });
    }
}
</script>

<style scoped>

</style>
