# Create react app to mount local directory
npx create-react-app frontend

# If you have space in user name then run following commands
npm install -g create-react-app
create-react-app frontend

# Startsup development server, this is for development use only
npm run start

# Run tests associated with the project
npm run test

# Builds production version of the application
npm run build

# docker build image for dev environemnt 
docker build -t cuckoo/frontend -f Dockerfile.dev .

# Running docker container
docker run -p 900:3000 cuckoo/frontend

## Above docker command not wor'king in window 10 i had to create docekr-compose.xml

# If you want to get into container 
docker exec -it <Image id> sh


# Refering local file changes of dev enf but we dont want to refere /app/node_modules folders
# Windows
docker run -p 9002:3000 -v /app/node_modules -v pwd:/app ceeea9c23b91
docker run -p 9002:3000 -v /app/node_modules -v ${pwd}:/app ceeea9c23b91

Example  :
docker run -p 9002:3000 -v /app/node_modules -v pwd:/app <IMAGE_ID>


# Git bash 
docker run -p 9001:3000 -v /app/node_modules -v $(pwd):/app cuckoo/frontend

If you are running on Windows, please read this: Create-React-App has some issues detecting when files get changed on Windows based machines.  To fix this, please do the following:

In the root project directory, create a file called .env

Add the following text to the file and save it: CHOKIDAR_USEPOLLING=true

That's all!

For more on why this is required, you can check out: https://facebook.github.io/create-react-app/docs/troubleshooting#npm-start-doesn-t-detect-changes