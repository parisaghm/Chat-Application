<template>
  <div class="room-list">
    <h2 class="Romms">
        <ul>
           <li v-for="room in rooms" :key="room.id" @click="changeRoom(room)" :class="{ active: currentRoom.id === room.id }">
            {{ room.name }}
           </li>
        </ul>
    </h2>
  </div>
</template>

<script>
export default {
    name: 'RoomList',
    props:{
        rooms:{
            type: Array,
            required: true
        },
        currentRoom:{
            type: Object,
            required: true
        }
    },
    methods:{
      changeRoom(room){
        this.$emit('room-changed', room);
      }
    }
}
</script>

<style>

.room-list {
  width: 250px; 
  border-right: 1px solid #444; 
  padding: 20px;
  background-color: #1e1e1e; 
  color: #fff;
  height: 100vh; 
  box-shadow: 2px 0 12px rgba(0, 0, 0, 0.2); 
}

h2 {
  text-align: center;
  font-size: 1.5rem;
  color: #c8c8c8;
  margin-bottom: 20px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  cursor: pointer;
  padding: 12px 20px;
  border-radius: 8px;
  margin-bottom: 10px;
  background-color: #333; 
  transition: background-color 0.3s ease, transform 0.3s ease;
  color: #c8c8c8;
  font-size: 1.1rem;
}

li:hover {
  background-color: #7d3cce; 
  transform: translateX(5px);
}

li.active {
  background-color: #7d3cce;
  font-weight: bold;
  color: #fff;
  box-shadow: 0px 0px 12px rgba(125, 60, 206, 0.7);
}


@media (max-width: 768px) {
  .room-list {
    width: 100%;
    height: auto;
    border-right: none;
    box-shadow: none;
    padding: 10px;
  }

  li {
    padding: 10px;
    margin-bottom: 8px;
  }
}

</style>