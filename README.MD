git clone 

# Download and install nvm ,  it should be on your ubuntu machine not your repo so use cd
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.6/install.sh | bash

#Then reload your shell
source ~/.bashrc

# Check
nvm --version
# Then install Node.js 24
nvm install 24

#cd /wanderlust/backend /ls
#open mongodb compass and monodb locally , it should be on your ubuntu machine not your repo so use cd
#From a terminal, install gnupg and curl if they are not already available:

sudo apt-get install gnupg curl

#To import the MongoDB public GPG key, run the following command:
curl -fsSL https://pgp.mongodb.com/server-8.0.asc | \
   sudo gpg -o /usr/share/keyrings/mongodb-server-8.0.gpg \
   --dearmor

#Create the list file.
#Create the list file /etc/apt/sources.list.d/mongodb-org-8.0.list for your version of Ubuntu.
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-8.0.gpg ] https://repo.mongodb.com/apt/ubuntu noble/mongodb-enterprise/8.3 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-enterprise-8.3.list


# Reload the package database.
sudo apt update

# Install MongoDB Enterprise Server use official site monodb install on ubuntu
sudo apt install -y mongodb-enterprise

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
cat .env.sample   # u will find vite_api_path , it is backned path 




