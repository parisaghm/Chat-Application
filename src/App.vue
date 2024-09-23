<template>
  <div id="app">
    <header> 
      <h1>Vue Chat App</h1>
      <div v-if="currentUser" class="user-info">
        <span>Welcome, {{ currentUser.name }}</span>
        <button @click="logout">Logout</button>
      </div>
    </header>
    <main>
      <login-form v-if="!currentUser" @login="handleLogin" />
      <div v-else class="chat-container">
        <room-list 
          :rooms="rooms" 
          :currentRoom="currentRoom" 
          @room-changed="changeRoom" 
        />
        <chat-room 
          :messages="messages[currentRoom.id]" 
          :currentUser="currentUser" 
          :currentRoom="currentRoom" 
          @send-message="sendMessage" 
        />
      </div>
    </main>
  </div>
</template>

<script>
import LoginForm from './LoginForm.vue';
import RoomList from './RoomList.vue';
import ChatRoom from './ChatRoom.vue';

export default {
  name: 'App',
  components: {
    LoginForm,
    RoomList,
    ChatRoom
  },
  data() {
    return {
      currentUser: null,
      rooms: [
        { id: 1, name: 'General' },
        { id: 2, name: 'Technology' },
        { id: 3, name: 'Random' }
      ],
      currentRoom: { id: 1, name: 'General' },
      messages: {}
    }
  },
  methods: {
    handleLogin(user) {
      this.currentUser = user;
      this.initializeChat();
    },
    logout() {
      this.currentUser = null;
      this.messages = {};
    },
    changeRoom(room) {
      this.currentRoom = room;
      if (!this.messages[room.id]) {
        this.messages[room.id] = [];
        this.fetchMessages(room.id);
      }
    },
    sendMessage(message) {
      const newMessage = {
        id: Date.now(),
        text: message,
        userId: this.currentUser.id,
        userName: this.currentUser.name,
        timestamp: new Date().toISOString()
      };
      if (!this.messages[this.currentRoom.id]) {
        this.messages[this.currentRoom.id] = [];  
      }
      this.messages[this.currentRoom.id].push(newMessage);
    },
    initializeChat() {
      this.rooms.forEach(room => {
        if (!this.messages[room.id]) {
          this.messages[room.id] = []; 
          this.fetchMessages(room.id);
        }
      });
    },
    fetchMessages(roomId) {
      setTimeout(() => {
        const welcomeMessage = {
          id: Date.now(),
          text: `Welcome to the ${this.rooms.find(r => r.id === roomId).name} room!`,
          userId: 'system',
          userName: 'System',
          timestamp: new Date().toISOString()
        };
        if (!this.messages[roomId]) {
          this.messages[roomId] = []; 
        }
        this.messages[roomId].push(welcomeMessage);
      }, 1000);
    }
  }
}
</script>

<style>
html, body {
  margin: 0;
  padding: 0;
  height: 100%; 
  overflow: hidden;
}

body {
  background-color: #1e1e1e; 
}

#app {
  font-family: Arial, sans-serif;
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  padding-bottom: 20px;
  border-bottom: 1px solid #ccc;
}

.user-info button {
  background-color: #4285f4; 
  color: white;
  border: none;
  border-radius: 50px; 
  padding: 8px 20px;
  font-size: 16px; 
  cursor: pointer;
  transition: background-color 0.2s ease-in-out; 
}

.user-info button:hover {
  background-color: #337ab7; 
}

.user-info span{
    margin-right: 15px;
    color: #b38bff;
    font-size: 20px;
    font-weight: bold;
}

.chat-container {
  display: flex;
  height: 600px; 
  border: 1px solid #ccc;
  border-radius: 4px;
  overflow: hidden; 
  max-width: 950px; 
  margin: 0 auto; 
}
</style>