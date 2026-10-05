# Todo App (React + Node + Express + MongoDB)

A full-stack todo app. The frontend is React (Vite), the backend is Node + Express, and data is stored in MongoDB Atlas.

## Goals

By the end, your app should:

1. **Be complete.** The missing pieces in the server and client are filled in, and every API route creates, reads, updates or deletes todos correctly and returns the right response and status code.
2. **Run locally.** The frontend at http://localhost:5173 talks to your backend and saves todos to MongoDB Atlas.
3. **Run on Render.** The same app is deployed as a single Render service, reachable at a public URL.

## Folder structure

```
todo-app-gnits/
├── client/                  # React (Vite)
│   ├── src/
│   │   ├── components/
│   │   │   ├── TodoForm.jsx
│   │   │   └── TodoItem.jsx
│   │   ├── api.js           # all fetch calls
│   │   ├── App.jsx
│   │   ├── index.css
│   │   └── main.jsx
│   ├── index.html
│   └── vite.config.js       # proxies /api to port 5001 in dev
├── server/                  # Node + Express
│   ├── controllers/
│   │   └── todoController.js
│   ├── models/
│   │   └── Todo.js
│   ├── routes/
│   │   └── todoRoutes.js
│   ├── .env.example
│   └── index.js
└── package.json             # root scripts
```

## Step 1: Set up the project

1. Copy `server/.env.example` to `server/.env` and put in your MongoDB Atlas URL.
2. Install everything:
   ```bash
   npm install
   npm install --prefix server
   npm install --prefix client
   ```

## Step 2: Find and complete the missing pieces

> ⚠️ **The app is not finished yet.** A couple of pieces are missing or incorrect in both the **server** and the **client**. Study the code, find what's missing, and complete it so the app works end to end.

- **Server:** Some functions in `server/controllers/todoController.js` are empty or incorrect. Finish and fix them so every route below works as described, and make sure each one returns relevant responses with the appropriate status codes (e.g. `200`, `201`, `400`, `404`, `500`).
- **Client:** Some parts of the React app don't do their job yet. Follow the flow from the UI to `api.js` and back, and fill in what's missing. Look for `TODO` comments as a starting point, but not every gap is marked.

| Method | Route            | What it does      |
| ------ | ---------------- | ----------------- |
| GET    | /api/todos       | Get all todos     |
| POST   | /api/todos       | Create a todo     |
| PUT    | /api/todos/:id   | Update a todo     |
| DELETE | /api/todos/:id   | Delete a todo     |

## Step 3: Run locally

1. Start both frontend and backend:
   ```bash
   npm run dev
   ```
2. Open http://localhost:5173 and check that you can add, edit, complete and delete todos, and that they are still there after a page refresh.

> The API runs on port 5001 (set by `PORT` in `server/.env`). Port 5000 is avoided because macOS AirPlay Receiver uses it. If you change `PORT`, update the proxy target in `client/vite.config.js` too.

## Step 4: Deploy on Render (one service)

1. Push your code to GitHub.
2. On Render, create a new **Web Service** from your repo with these settings:
   - Build command: `npm run build`
   - Start command: `npm start`
   - Environment variable: `MONGO_URI` = your Atlas URL
3. In Atlas → Network Access, allow `0.0.0.0/0` so Render can connect.
4. Once the deploy finishes, open your Render URL and test the app the same way you did locally.
5. https://todo-app-gnits-vq3c.onrender.com/
