
## local redis server , think like mongodb server
localmongo , local redis server db, mongo cli redis cli, cloud mongodb cloud redis , redis insight just like mongo compass, 
Step 1: Update Your System
  -> sudo apt update

Step 2: Install Redis Server
  -> sudo apt install redis-server -y

Step 3: Enable and Start Redis
  -> Enable Redis to start on boot:
       -> sudo systemctl enable redis // brew services start redis in mac
       -> Start the Redis service:
            -> sudo systemctl start redis // runs the server in backgroud , if u do redis-server on terminal it will go down when u shut  the                                                 //termianal , brew services restart redis (mac)

 Step 4: Check if Redis is Running
  -> sudo systemctl status redis


🧪 Step 5: Test Redis
     -> Run the Redis CLI:
         -> redis-cli
             -> ping

sudo systemctl restart redis


### mac
brew services start redis\
brew services restart redis\
brew services list\
brew services stop redis




