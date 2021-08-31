# Deploy Nuxtjs Application To DreamHost
<span>Nuxtjs & Dreamhost + Passenger</span>


## Enable Nodejs and Passenger For Domain
This will be done in the panel of dreamhost

## Install a custom version of nvm/node:
https://help.dreamhost.com/hc/en-us/articles/360029083351-Installing-a-custom-version-of-NVM-and-Node-js
- The version of Passenger running on DreamHost servers does not currently function with Node.js versions 14+.



## Add the following to <strong>.htaccess</strong> file (Create .htaccess if one isn't found):
<code>
PassengerFriendlyErrorPages on
</code>
<br>
<code>
PassengerNodejs /home/nodetesting/.nvm/versions/node/v12.18.3/bin/node
</code>


## Create app.js in root directory, and add contents to app.js for testing:
<code>
  require("@nuxt/cli").run(["start"])
</code>
<br>
- The reason we need an app.js file is because Passenger requires an app.js file as an entry point for Node applications. Nuxt doesn't have an app.js file. Our app.js runs the nuxt app through the CLI start command defined in nuxt.



## Create tmp/restart.txt in root site directory:
<code>
  mkdir tmp
</code>
<br>
<code>
  touch tmp/restart.txt
</code>
<br>
- to restart the server run <code>touch tmp/restart.txt</code> in the root directory
create tmp/restart.txt to restart server



## Add the following to the .bashrc file
<code>
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
</code>
<br><br>
<code>
nvm use v12.18.3
</code>
<br>
<br>
- If the .bashrc file isn't sourced automatically add the following to the .bash_profile
<code>~/.bashrc</code>



## Create Nuxt App
<code>
npx create-nuxt-app <my-project>
</code>



