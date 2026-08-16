#open source 
ls
mkdir git-demo
cd git-demo     # after fork it will work
git clone urcode url
 # cd  in ur vm
 git config --global user.name "yashpal5816"
 git config --global user.email "ur mail"

cd git-demo
 ls
 cd wanderlust  
 git remote -v  #u can see it will show from users git url

 # so now we need my git repo  Create my-repo in git-demo repo
 cd ..
 mkdir my-repo
 git clone ur git code url 

 cd my-repo
 git remote -v      # now it will show ur repo
 cd wanderlust
ls

# now i want change some this in my repo
vim README.MD     # u can add npm i steps already added  :wq!
git status   
git add README.MD

# here come concept branching .because we dont want to change our main branch
git checkout -b devops   # so we switched to devops branch ,Now ur main code is safe and u can to any chnage in devops branch
git status   # now u are in devops branch
git commit -m  "readme.md is changed"
git push origin devops   # u can see its asking for authentication so here we use personal access token # goto git acoount setting find developer setting and

# and use classic tokken generate token classic and mark ,Repo (u give full access of ur repo) and generate
git remote set-url origin https:// paste token here@github.com/yash5816/wanderlust.git    # like this u can access ur repo
git push origin devops   # see now ur git repo branch is created .selecte devops branch and chech ur README file chnage is occured or not

# but dont create pull request
# now if u want to add these changes in main branch which is someone else's if u fork it then u can do compare and pull request
# in git add title starting write [wip] so it will not change anything in main branch 
git status
# Docker file creation

cd
cd wanderlust
sudo apt-get install docker.io
git status  # branch should be devops
ls
cd backend/     # first we create backend docker file
vim Dockerfile     # so for docker file what ever mentioned in readme.md that we have to write in decker file
  # for eg this project will run on ubuntu and npm (node based) so first we need base image
  FROM node:21  # check node version which one u used
  WORKDIR  /app   # so i wat /app name folder and everythig is in this folder
  ls  # these are ur files
  vim Dockerfile
  COPY . .        # copy files from ur local machine to docker container (. . means from source to destination)
  RUN npm i
  COPY .env.sample .env      # in readme it show npm start om 5000 port so need to expose

  EXPOSE 5000
  CMD ["npm", "start"]      :wq!
  
  # Now we build it
  docker build -t backend .      # . need to create docker from docker file from this directory so we use .

  # now need to install mongodb
  docker run -d -p 27017:27017 --name mongo mongo:latest  # mapipng system port to docker port,mongo is container name  and mongo:latest is image name)
  docker ps   # u can see ur running container
  docker exec -it containerid bash     # so ur in mongo db container  (-it= interactive terminal)
  mongo sh   # u can see mongo is working
  exit

  #Now creating container of backend
  ls
  docker images    # node,mongo,backend...these images are their)
  docker run -d -p 5000:5000 --name backend backend:latest
  docker ps   # ur mongo and backend container is working

  # now creating frontend
  cd 
  cd frontend
  vim Dockerfile
  FROM node:21
  WORKDIR /app
  COPY . .
  RUN npm i
  COPY .env.sample .env
  EXPOSE 5173      # frontend will run on 5173
  CMD ["npm", "run", "dev", "--", "--host"]     :wq!

docker build -t frontend .     # . means create frontend fro dockerfile from this directory # it take time
docker run -d -p 5173:5173 --name frontend frontend:latest
docker ps 
# aws publicip:5173  it should run  ...now feature posts are not showing  (inspect,network,feature see url its going on local host 
vim .env.sample
#remove local host and add aws public ip:5000   :wq!
# Remeber when ever u change port then u have create Docker image again
docker build -t frontend .
docker ps    #new image is created but old container is running
docker kil containerid
docker run -d -p 5173:5173 --name frontend frontend:latest   # it will give name conflict
docker rm frontend
docker run -d -p 5173:5173 --name frontend frontend:latest    
# check inspect network feature post feature error is still coming  becuase ur frontend and backend and db are isolated so need to communicate which each other
# so need to put them in same network or we can run all container in single time in defualt network
# so here we will use docker compose
docker kill all container ids
docker rm all container ids
cd ..
# so frontend backend and db docker file will run togethet using compose









  
  
  
  
  





 
 
 
 
 
