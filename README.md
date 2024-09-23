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


## Installation and Setup

1) Clone the repository:

```
git clone https://github.com/your-username/vue-chat-app.git
cd vue-chat-app
```

2) Install dependencies:

```
npm install
```

3) Run the application:

```
npm run serve
```
4) Access the app: Open http://localhost:8080 in your browser.


## Customization:

- To add more rooms, modify the rooms array in App.vue:

rooms: [
    { id: 1, name: 'General' },
    { id: 2, name: 'Technology' },
    { id: 3, name: 'Random' },
    { id: 4, name: 'New Room' }  // Add new rooms here
]

- You can also customize the styling in the corresponding .vue files.

## Technologies Used:
- Vue 3: Front-end framework.
- JavaScript: Main programming language.
- HTML5/CSS3: For structure and styling.


### Key Points:
- **Installation and Usage**: Clearly describes how to set up and run the project locally.
- **Component Breakdown**: Each component's purpose is briefly explained.
- **Customization**: Instructions to modify rooms or styles.
- **Screenshots**: You can add relevant screenshots for better visualization.

Make sure to replace the GitHub repository URL and add relevant screenshots to the `screenshots/` folder if needed!




