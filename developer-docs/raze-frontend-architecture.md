# Raze Frontend Architecture

When the frontend project initializes, it imports `razeClient` in `src/main.js` , creates a client instance through `initRazeClient` , and stores it in a vue instance, so that the whole frontend can call the above APIs through `$raze` .
