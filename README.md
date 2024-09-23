# Vue Chat Application

A simple real-time chat application built with Vue 3, allowing users to log in, join rooms, and exchange messages. This project demonstrates the use of component-based architecture, event handling, and scoped styles in Vue 3.

## Features

- **User Authentication**: Simple login with a username.
- **Chat Rooms**: Switch between multiple rooms like General, Technology, and Random.
- **Real-time Messaging**: Send and receive messages within rooms.
- **Auto-scroll**: Chat view automatically scrolls to the latest message.
- **Custom Styling**: Clean and modern UI with responsive design.
  
## Components

### `App.vue`
- The root component that controls authentication, room selection, and renders the chat interface.
- **Main functionalities**:
  - Handles user login and logout.
  - Manages rooms and messages.
  - Switches between rooms.

### `LoginForm.vue`
- A login form where users enter their username and password.
- Emits a `login` event on form submission.

### `RoomList.vue`
- Displays a list of available chat rooms.
- Emits `room-changed` when a user selects a different room.

### `ChatRoom.vue`
- Displays messages for the current room.
- Handles sending new messages.
- Scrolls automatically to the latest message.

## Project Structure

```bash
src/
├── assets/
├── components/
│   ├── ChatRoom.vue
│   ├── LoginForm.vue
│   ├── RoomList.vue
├── App.vue
├── main.js
