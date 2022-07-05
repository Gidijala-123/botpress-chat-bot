## Complete Botpress installation using Yarn and NodeJS
**I. First delete files/folders metioned in the below path:**
1) C:\Program Files\Nodejs
2) C:\Users\bhargava\AppData\Roaming\npm do the same for admin folder also(if you opened cmd as admin while installing yarn)
3) C:\Users\bhargava\AppData\Roaming\npm-cache 
4) C:\Users\.npmrc or delete any yarn or npm or node related files and folders
5) C:\Users\bhargava\AppData\local\temp\ delete any yarn or npm or node related files and folders
6) Delete recycle bin files and delete %temp% files from RUN cmd
7) Restart your PC
8) Check wheather all the mentioned files are deleted or not from the path

**II. Install node 12.18.1 MSI file [Click to download](nodejs.org/fr/blog/release/v12.18.1/)** <br />
**III. Open windows cmd prompt(opening as administrator is not mandatory & below cmds won't work in powershell) and enter below cmds** 
- npm -v
- node -v
- npm i --global yarn@1.22.18
- Close the terminal and re-open it to check yarn version
- yarn -v

**Note :** Prefer installing yarn using npm rather than installing via yarn.exe file

**IV. Now we need to clone botpress from official botpress git repository**
- To clone git, we need "git" installed in your PC [Click to download](https://git-scm.com/downloads)
- Goto folder where you want to copy that git folder
- Paste the cmd "git clone https://github.com/botpress/botpress.git" and press enter, It'll clone botpress folder from official botpress github site
- cd botpress
- yarn cache clean
- yarn
- yarn build 
  - In this step you may suggest to run "caniuse-lite"
  - You can type the cmd "npx browserslist@latest --update-db" after completion of previous step (don't forcely close).
- yarn start <br/>

**Note :** It'll take 20-30 mins for this entire process of yarn installation depending on internet speed and Don't close forcely assuming that terminal is struck

**V. Creating custom nodejs project(to use botpress in this website)**
1) In console it'll display botpress server is exposed at "http://localhost:3000"
2) On clicking the host link, you will be redirected to botpress studio registration page.
3) Upon successful registration, click on "create bot" > New bot > give a name to the bot(you can give custom botId).
4) On successful bot creation, click on the "bot name" where it'll display a emulator.
5) Train your bot by clicking on "train bot" button present at the bottom right corner of botpress studio window.
6) You can check the progress of bot training in the terminal from where you started the botpress.
7) With this we've successfully started our server, We've to integrate this server in our website using <script> tag.
8) Integrating chatbot in our custom website <br/>
   a) Create a package structure using the following npm cmds
   - Open npm command prompt
   - npm install express<space>-g
   - npm install express-generator -g
   - cd desktop
   - express --view=pug projectName
   - cd projectName
   - npm install
   - npm start
   b) Copy and paste following code into your index.pug file after body tag<br/>
      - script(src="http://localhost:3000/assets/modules/channel-web/object_assign.js")
      - script(src="http://localhost:3000/assets/modules/channel-web/inject.js")
      - script. <br/>
        window.botpressWebChat.init({<br/>
        host: 'http://localhost:3000/', <br/>
        botId:"alvin",<br/>
        //- host: 'http://34.255.255.255/',<br/>
        //- botId: 'spine',<br/>
        //- extraStylesheet: '/modules/channel-web/assets/gbr-custom-styles.css',<br/>
        //- hideWidget: false, //to hide the bot floating icon from webpage<br/>
        })<br/>
   c) Change your default port number of your website from bin/www folder of nodejs application in-order to avoid overlapping default port of botpress server(3000)<br/>
   d) Start your website using cmd "npm start" from the terminal.

**VI. Modifying botpress src folder**
  #### 1) Applying custom CSS
  - Goto botpress(cloned folder from github) > modules > channel-web > assets > default.css <br/>
  #### 2) Changing mailId from src folder(only mail not pwd)
  - You can change mail Id from the path botpress > packages > bp > dist > data > global > botpress.config.json > "superAdmins": <br/>
  #### 3) To change default botpress server port number ####
  - Goto botpress(cloned folder from github) > packages > bp > dist > data > global > botpress.config.json > "port":3000 <br/>
  #### 4) To change the name of the bot in the chat emulator
  - Open botpress studio(localhost:3000) > Click config button of your bot > Change the name from the name section
  - Changing name will instantly reflect in your website bot
  - Sometimes restarting the npm and bot server is needed
  #### 5) To change or modify code (eg:API)
  - Open botpress studio(localhost:3000) > Click on code editor from sidebar menu > In the Actions section, open the file in Bot <bot name> folder
  - Change the code or API that you want and finally click on Save icon present at bottom-left
  
**Note :** If you make any modifications using yarn start cmd, please restart your server for each modification you've made.
  
  
### Reference Links
1. https://classic.yarnpkg.com/lang/en/docs/install/#windows-stable
2. https://yarnpkg.com/
3. https://www.alibabacloud.com/blog/advanced-concepts-in-botpress-a-crash-course_596225
4. https://socket.dev/npm/package/@botpress/channel-web
5. https://github.com/botpress/botpress-examples/blob/master/motivation-bot/index.js
