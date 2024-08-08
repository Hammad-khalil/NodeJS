
```markdown
# Node.js Cheatsheet

## 1. Setup

- **Install Node.js**: [Node.js Official Site](https://nodejs.org/)
- **Check Node.js version**:
  ```bash
  node -v
  ```
- **Check npm version**:
  ```bash
  npm -v
  ```

## 2. Basic Commands

- **Initialize a new project**:
  ```bash
  npm init
  ```
  *Creates a `package.json` file.*

- **Install a package**:
  ```bash
  npm install <package-name>
  ```
  *e.g., `npm install express`*

- **Install a package globally**:
  ```bash
  npm install -g <package-name>
  ```

- **Uninstall a package**:
  ```bash
  npm uninstall <package-name>
  ```

## 3. Creating a Basic Server

```javascript
// server.js
const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World\n');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

- **Run the server**:
  ```bash
  node server.js
  ```

## 4. Using Express.js

- **Install Express**:
  ```bash
  npm install express
  ```

- **Basic Express Server**:

```javascript
// app.js
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Hello World!');
});

app.listen(port, () => {
  console.log(`Server is running on http://localhost:${port}`);
});
```

- **Run the Express server**:
  ```bash
  node app.js
  ```

## 5. Working with Files

- **Read a file**:

```javascript
const fs = require('fs');

fs.readFile('example.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data);
});
```

- **Write to a file**:

```javascript
fs.writeFile('example.txt', 'Hello Node.js', (err) => {
  if (err) throw err;
  console.log('File has been saved!');
});
```

## 6. Handling HTTP Requests

- **GET Request**:

```javascript
const http = require('http');

http.get('http://example.com', (res) => {
  let data = '';

  res.on('data', (chunk) => {
    data += chunk;
  });

  res.on('end', () => {
    console.log(data);
  });
}).on('error', (e) => {
  console.error(`Got error: ${e.message}`);
});
```

## 7. Environment Variables

- **Using `.env` file**:
  - Install `dotenv`:
    ```bash
    npm install dotenv
    ```
  - Create `.env` file:
    ```
    PORT=3000
    ```
  - Use in your application:
    ```javascript
    require('dotenv').config();
    const port = process.env.PORT || 3000;
    ```

## 8. Error Handling

- **Basic try-catch**:

```javascript
try {
  // Code that might throw an error
} catch (error) {
  console.error('Error occurred:', error);
}
```

## 9. Commonly Used Modules

- **Path**:
  ```javascript
  const path = require('path');
  console.log(path.join(__dirname, 'file.txt'));
  ```

- **OS**:
  ```javascript
  const os = require('os');
  console.log(os.platform());
  ```

- **Events**:
  ```javascript
  const EventEmitter = require('events');
  const emitter = new EventEmitter();

  emitter.on('event', () => {
    console.log('Event triggered!');
  });

  emitter.emit('event');
  ```

## 10. Debugging

- **Start the app in debug mode**:
  ```bash
  node --inspect app.js
  ```
  *Use Chrome DevTools or VSCode for debugging.*
```
