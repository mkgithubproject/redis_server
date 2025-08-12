`redis-cli` is the **official command-line interface (CLI) tool for Redis**.
It’s basically a small program that lets you connect to a Redis server and run Redis commands directly from your terminal — without needing to write code.

---

### **Key points about `redis-cli`**

* Comes bundled with the Redis installation (when you install Redis locally or on a server, you usually get `redis-cli` with it).
* Lets you **connect** to a Redis server (local or remote).
* Lets you **run commands interactively** or in scripts.
* Useful for **debugging, testing, and managing** Redis.

---

### **How it works**

When you type:

```bash
redis-cli
```

You enter an **interactive mode** where you can run commands like:

```bash
set name "Mohit"
get name
keys *
```

Or you can run a single command without going into interactive mode:

```bash
redis-cli ping
```

---

### **Example session**

```bash
$ redis-cli
127.0.0.1:6379> ping
PONG
127.0.0.1:6379> set user:1 "John"
OK
127.0.0.1:6379> get user:1
"John"
127.0.0.1:6379> del user:1
(integer) 1
```

---

### **Common uses of `redis-cli`**

1. **Check connection** → `ping`
2. **Insert data** → `set key value`
3. **Retrieve data** → `get key`
4. **List keys** → `keys *`
5. **Monitor commands in real-time** → `monitor`
6. **Flush all data** → `flushall` (dangerous in prod!)

---

In short — `redis-cli` is like a **remote control** for Redis:
📦 Redis is the database,
⌨️ `redis-cli` is how you talk to it directly.

---

If you want, I can now show you **how to use `redis-cli` to connect to a Cloud Redis instance** so you can control it from your laptop. Would you like me to go step-by-step?


Here’s your **step-by-step guide**:
On macOS with **Homebrew**, there’s no real difference —
`brew install redis` is the correct and standard command.

---

### Why there’s confusion

* In **Linux**, people sometimes install Redis with:

  ```bash
  sudo apt install redis-server
  ```

  because `redis-server` is the main package name in APT.

* In **Homebrew**, the package is just called **`redis`**.
  When you run:

  ```bash
  brew install redis
  ```

  Homebrew installs **both**:

  * `redis-server` → the actual database server process
  * `redis-cli` → the command-line interface for talking to the server

---

✅ **So on your Mac, you should just run:**

```bash
brew install redis
```

No need for `brew install redis-server` — that’s not a valid Homebrew formula.

---

If you want, I can explain **what happens under the hood when you run `brew install redis`** so you know exactly what’s being added to your system.
Your Redis server (`redis-server`) is installed (version 8.2.0), but the Redis **CLI client** (`redis`) is not found on your Mac.

---

### Why?

* The Redis CLI tool is called `redis-cli`, **not** `redis`.
* You likely don’t have `redis-cli` installed or it’s not in your system PATH.

---

### How to check if `redis-cli` is installed?

Run:

```bash
redis-cli --version
```

If you get `command not found`, you need to install `redis-cli`.

---

### How to install `redis-cli` on Mac without Homebrew?

If you don’t want to use Homebrew, you can:

1. **Download Redis source and compile** (not recommended if you want just the CLI).

2. **Install only redis tools with Homebrew** (easy way):

```bash
brew install redis
```

That will install both `redis-server` and `redis-cli`.

---

### If you want just `redis-cli`:

You can download the official Redis binaries from [https://redis.io/download](https://redis.io/download) or use package managers.

---

### Quick fix using Homebrew (recommended if you have it):

```bash
brew install redis
```

Then run:

```bash
redis-cli --version
redis-cli ping
```

---

### Summary:

* `redis` command doesn’t exist — you want `redis-cli`.
* `redis-cli` is the Redis command-line client tool.
* Install it (via Homebrew or source) to interact with Redis from terminal.

---

If you want, I can guide you through installing `redis-cli` step-by-step!


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
