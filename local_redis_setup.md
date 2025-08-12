Got it — if you’re on a **Linux setup** (without Homebrew), you can install Redis directly from the package manager and then connect it with Node.js.

Here’s your **step-by-step guide**:

---

## **1️⃣ Install Redis on Linux**

### For Ubuntu/Debian:

```bash
sudo apt update
sudo apt install redis-server -y
```


---

## **2️⃣ Start Redis Server**

```bash
sudo systemctl start redis
```

Enable it to start on boot:

```bash
sudo systemctl enable redis
```

---

## **3️⃣ Test Redis**

```bash
redis-cli ping
```

If Redis is running, you’ll see:

```
PONG
```

---

## **4️⃣ Install Redis Client in Node.js**

Inside your Node.js project:

```bash
npm install redis
```

---

## **5️⃣ Connect Node.js to Redis**

`index.js`:

```js
const redis = require("redis");

// Create Redis client
const client = redis.createClient({
    host: '127.0.0.1', // local Redis
    port: 6379
});

// Handle connection errors
client.on("error", (err) => {
    console.error("Redis Client Error", err);
});

async function run() {
    await client.connect();

    // Set a key
    await client.set("name", "Mohit");

    // Get the key
    const value = await client.get("name");
    console.log("Value from Redis:", value);

    await client.quit();
}

run();
```

---

## **6️⃣ Run the Test**

```bash
node index.js
```

Output:

```
Value from Redis: Mohit
```

---

If you want, I can **extend this setup** into a **real-time leaderboard example with Socket.IO + Redis** so you can see Redis in action beyond just GET/SET. That would make it more practical.
