# Ruby Frontend Architecture

When the frontend project initializes, it imports `rubyClient` in `src/main.js` , creates a client instance through `initRubyClient` , and stores it in a vue instance, so that the whole frontend can call the above APIs through `$ruby` .
