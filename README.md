# Yarn installation steps for botpress
install node 12.18.1 MSI file from nodejs.org/fr/blog/release/v12.18.1/.
open windows cmd as ADMINISTRATOR(below cmds won't work in vscode terminal) and enter below cmds.
> corepack enable
> npm i -g corepack
> yarn init -2
> yarn set version stable
> yarn set version from sources(optional)
open botpress github page & click code⬇ & copy the URL.
paste the URL in your pc directory where you want to download that git hub botpress folder.
enter cd botpress in cmd and type below cmds.
> yarn cache clean
> yarn
> yarn build 
  - In this step you may suggest to run caniuse-lite.
  - You can type the cmd "npx browserslist@latest --update-db" after completion of previous step (don't forcely close).
> yarn start
Note : It'll take 20-30 mins for this entire process of yarn installation and don't close forcely assuming that terminal is struck


# To clone botpress from official botpress git repository
To clone git, we need "git" installed in your pc.
Goto folder where you want to copy that git folder.
Goto official botpress github repository and copy the URL.
paste the cmd "git clone https://github.com/botpress/botpress.git".
press enter.


# On successful yarn installation
In console it'll display botpress is exposed at "http://localhost:3000".
On clicking the host link, you will be redirected to botpress studio registration page.
On filling valid details, click on "create bot" > New bot > give a name to the bot(you can't edit botId).
On successful bot creation, click on the "bot name" where it'll display a emulator.
Train your bot by clicking on "train bot" button present at the bottom right corner of botpress studio window.
You can check progress of bot training in the terminal from where you started the botpress.
With this we've successfully started our server, with this server we've to integrate in our website using <script> tag.


# Integrating chatbot in our custom website
Create a package structure using the following npm cmds
  > Open npm command prompt
  > npm install express<space>-g
  > npm install express-generator<space>-g
  > cd desktop
  > express<space>--view=pug<space>projectName
  > cd projectName
  > npm install
  > npm start
Copy and paste following code into your index.html file
  > <script src="http://localhost:3000/assets/modules/channel-web/object_assign.js">
  > <script src="http://localhost:3000/assets/modules/channel-web/inject.js"></script>
  > <script>
      window.botpressWebChat.init({
        host: 'http://localhost:3000/', 
        //- host: 'http://34.255.118.102/',
        botId: 'alvin',
        //- extraStylesheet: '/modules/channel-web/assets/gbr-custom-styles.css',
        //- hideWidget: false, //to hide the bot floating icon from webpage
      })
    </script>
</script>
Change your default port number of your website from bin/www folder of nodejs application inorder to avoid overlapping default port of botpress server(3000).
Start your website using cmd "npm start" from the terminal.


# Github botpress folder modification
Inorder to customize styles of botpress default code, goto botpress(folder of github) > modules > channel-web > assets > default.css
Note : If you make any modifications using yarn start cmd, please restart your server for each modification you've made.

  
