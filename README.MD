git clone 

# Download and install nvm ,  it should be on your ubuntu machine not your repo so use cd
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.6/install.sh | bash



#Then reload your shell
source ~/.bashrc
# rebbot
sudo reboot

# Check
nvm --version
# Then install Node.js 24
nvm install 24
node -v

#cd /wanderlust/backend /ls
npm i
npm start
#open mongodb compass and monodb locally , it should be on your ubuntu machine not your repo so use cd
#From a terminal, install gnupg and curl if they are not already available:

sudo apt-get install gnupg curl

#To import the MongoDB public GPG key, run the following command:
curl -fsSL https://pgp.mongodb.com/server-8.0.asc | \
   sudo gpg -o /usr/share/keyrings/mongodb-server-8.0.gpg \
   --dearmor

#Create the list file.
#Create the list file /etc/apt/sources.list.d/mongodb-org-8.0.list for your version of Ubuntu Jammy.
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-8.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/8.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-8.0.list



# Reload the package database.
sudo apt-get update

# Install MongoDB Enterprise Server use official site monodb install on ubuntu
sudo apt-get install -y mongodb-org


# Start MongoDB
sudo systemctl start mongod

# To check mongo is runing or not 
mongosh
# exit for exit


# import sample data from project sample_post json     # cd /wanderlust/backend
mongoimport --db wanderlust --collection posts --file ./data/sample_posts.json --jsonArray

# need to configure enviorment variable 
ls   # u will not able to see hidden or env folder
ls -a # now u can see

 # in env.sample u will find url through that u will connect data base
cat .env.sample       # u fill find mongo db url

# copy .env.sample to .env file
cp .env.sample .env

# why we did this so backend will know database address
# start  backend server
npm start   # to start backend server  aws sg group port 8080

# it give error install redis server 

# now this data we have to show on UI..backend is cover now we have to show on frontend
# go to frontend
cd /wanderlust/frontend
npm i 
ls -a  # to check .env.sample
cat .env.sample   # u will find vite_api_path , it is backned path  so backen will hit on this url to connect with frontend

cp .env.sample .env.local

# to run frontend
npm run dev     # so now 5173 port need to expose in aws sg or add in sg  ..now awsip:5173 browse if siter is not rechable meand ur frontend is running on local 

#its showing use --host to expose (-- means options)
npm run dev -- --host         # now u can see ur aws private ip is there now it can run on browser but full is not showing  ..

# got to 5173 broeser r8 click inspect r8 side top networks and reload browser u can see errors (feature is showing local host)

vim .env.sample   # replace localhost with = aws public ip) where ur backend is running

cp .env.sample .env.local

# now we will run frontend in the background
nohup npm run dev -- --host &          # nohup to collect logs from backgroud, its running in backgroud

# u can refresh front end browser its running so..ur frontend is runnung in background
# but data is still not there because backend in not running

cd ..
cd backend/
npm start      # ur backend is runnung








