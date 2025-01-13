# Bitcoin Free Website Updating

## Option 1 - Using Github
1. Create Github repo
Create a Github repo called website and upload the website source code. You can make the repository private. 

2. Create an API key
* Login to github
* Click icon in upper-right -> Settings -> Developer Settings
* Click Personal access tokens -> Tokens (classic) -> Generate new token -> Generate new token (classic)
* Then do the following:
Note - Name it
Expiration - Choose an expiration or No expiration
Select scopes - Check the box near "repo"
* Click Generate token and save the token

3. Clone repository to the server
Login to this server xx.xxx.xxx.216 and clone the website Github using the API key you created:
```bash
git clone https://YOUR_GITHUB_API_KEY@github.com/YOUR_GITHUB_USER/website
```

4. Install dependencies
```bash
cd website
npm i
```

5. Run the following script to update the website 
```bash
./update-website.sh
```

6. You can see the latest website here: https://btcc.tech/


## Option 2 - Building locally
1. Install dependencies
Open up the terminal app and run the following lines to install the dependencies:
Install Homebrew
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Install NVM
```bash
brew install nvm
```

```bash
nano ~/.zshrc
```

And paste this to the bottom of the file:
```bash
export NVM_DIR=~/.nvm
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

```bash
source ~/.zshrc
```

Now install node
```bash
nvm install v16
nvm use v16
```

2. Download a text editor
I recommend VS Code: https://code.visualstudio.com/

Open up VS Code and type: `shift + command + p`

Then type: `code`

And hit: `enter`

4. Close VS Code and the Terminal app

5. Unzip the website zip file to your desktop and open up vs code like so:
```bash
cd Desktop/bitcoinfree-website
code .
```

That will open up VS Code in your website's source code directory 

6. Make code changes
Here's the overview of the icons on the left
Stacked pages icon - View all the website icons
Magnifying class icon - You can search for words and more in the website

7. Run the development server
You can run a development server. Allowing you to see the changes you make to the code as you make them. To get started:

Install dependencies
```bash
npm i
```

Now start the server
```bash
npm run dev
```

Now open up your web browser and paste in this address to see your website: http://127.0.0.1:5173/

8. Compile build file
Once you have made your changes and are ready to upload to the server. You can run this to compile the files:

```bash
npm run build
```

The final output files are in the `dist` folder. 

9. Upload dist folder to the server. 
Zip the dist folder and you can upload the zipped file to this server xx.xxx.xxx.216 using SFTP software such as Filezilla: https://filezilla-project.org/download.php

10. Upload to server frontend
Once you upload the folder to the server you can upload it to the frontend like so:

```bash
unzip dist.zip
cd dist
cp -rf * /var/www/html
```

Restart the webserver
```bash
sudo /etc/init.d/nginx restart
```

The website can be seen at: https://btcc.tech/


