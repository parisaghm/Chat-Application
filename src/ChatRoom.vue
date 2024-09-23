  <template>
    <div class="chat-room"> 
      <div class="message-list" ref="messageList">
        <div v-for="message in messages" :key="message.id" :class="['message', { 'own-message': message.userId === currentUser.id }]">
          <strong>{{ message.userName }}:</strong> {{ message.text }}
          <small>{{ formatTime(message.timestamp) }}</small>
        </div>
      </div>
      <div class="message-input">
          <input v-model="newMessage" @keyup.enter="sendMessage"  placeholder="Type a message...">
          <button @click="sendMessage">Send</button>
      </div>
    </div>
  </template>


  <script>
  export default {
    name: 'ChatRoom',
    props: {
      messages: {
        type: Array,
        required: true
      },
      currentUser: {
        type: Object,
        required: true
      },
      currentRoom: {
        type: Object,
        required: true
      }
    },
    data() {
      return {
        newMessage: ''
      }
    },
    methods: {
      sendMessage() {
        if (this.newMessage.trim()) {
          this.$emit('send-message', this.newMessage);
          this.newMessage = '';
        }
      },
      formatTime(timestamp) {
        return new Date(timestamp).toLocaleTimeString();
      },
      scrollToBottom() {
        this.$nextTick(() => {
          this.$refs.messageList.scrollTop = this.$refs.messageList.scrollHeight;
        });
      }
    },
    watch: {
      messages() {
        this.scrollToBottom();
      }
    },
    mounted() {
      this.scrollToBottom();
    }
  }
  </script>

<style>
.chat-room {
  display: flex;
  flex-direction: column;
  flex: 1;
  background-color: #1e1e1e;
  color: white;
  margin: 0; 
}

.message-list {
  flex: 1;
  padding: 20px;
  overflow-y: auto;
  background-color: #2c2f33; 

}


.message {
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
  padding: 10px;
  background-color: #3b3e45;
  color: #fff;
  font-size: 0.9rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}


.own-message {
  background-color: #5865f2;
  align-self: flex-end;
  color: #fff;
}


.message strong {
  font-weight: bold;
}

.message small {
  font-size: 0.75rem;
  color: #b9bbbe; 
  align-self: flex-end;
}


.message-input {
  display: flex;
  padding: 10px;
  background-color: #2c2f33;
  align-items: baseline;
  border-top: 1px solid #444;
}


.message-input input {
  flex: 1;
  padding: 10px;
  font-size: 1rem;
  border: none;
  background-color: #40444b;
  color: white;
  outline: none;
  margin-right: 10px;
}


.message-input button {
  padding: 10px 20px;
  background-color: #5865f2;
  color: white;
  border: none;
  cursor: pointer;
  font-size: 1rem;
}

.message-input button:hover {
  background-color: #4752c4;
}


.message-list::-webkit-scrollbar {
  width: 8px;
}

.message-list::-webkit-scrollbar-thumb {
  background-color: #5865f2; 
  border-radius: 4px;
}

.message-list::-webkit-scrollbar-track {
  background: #2c2f33;
}

</style>