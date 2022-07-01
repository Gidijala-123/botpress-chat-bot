## Yarn installation steps for botpress
**I. First delete files/folders metioned in the below path:**
1) C:\Program Files\Nodejs
2) C:\Users\bhargava\AppData\Roaming\npm do the same for admin folder also(if you opened cmd as admin while installing yarn)
3) C:\Users\bhargava\AppData\Roaming\npm-cache 
4) C:\Users\.npmrc or delete any yarn or npm or node related files and folders
5) C:\Users\bhargava\AppData\local\temp\ delete any yarn or npm or node related files and folders
6) Delete recycle bin files and delete %temp% files from RUN cmd
7) Restart your PC
8) Check wheather all the mentioned files are deleted or not from the path

**II. Install node 12.18.1 MSI file [Link to download](nodejs.org/fr/blog/release/v12.18.1/)** <br />
**III. Open windows cmd prompt(opening as administrator is not mandatory & below cmds won't work in powershell) and enter below cmds** 
- npm -v
- node -v
- npm i --global yarn@1.22.18
- Close the terminal and re-open it to check yarn version
- yarn -v

**IV. Now we need to clone botpress from official botpress git repository**
- To clone git, we need "git" installed in your pc
- Goto folder where you want to copy that git folder
- Goto official botpress github repository and copy the URL.
- paste the cmd >git clone https://github.com/botpress/botpress.git and press enter.
- yarn cache clean
- yarn
- yarn build 
  - In this step you may suggest to run caniuse-lite.
  - You can type the cmd "npx browserslist@latest --update-db" after completion of previous step (don't forcely close).
- yarn start
Note : It'll take 20-30 mins for this entire process of yarn installation and don't close forcely assuming that terminal is struck





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


# Resolving errors while installing yarn

> Check npm and node versions from the windows cmd (opening in admin is not mandatory) 
> Enter "npm i --global yarn@1.22.18" in cmd
> Close the terminal and re-open it to check yarn version by typing "yarn -v" in cmd
> Now follow remaining steps after yarn installation mentioned in botpress official documentation