# minecraft-server-on-heroku-template

steps: 
1. Create a repo on github and clone it onto your computer.
2. Download the .zip file and extract the contents into the local repo folder.
3. Create a ngrok account on https://ngrok.com and paste the auth token in .ngrok2/ngrok.yml
4. Commit and push.
5. Create a heroku account on https://heroku.com and create an app. In the "Deploy" tab, connect to github and your repo.
6. Go to the "Settings" tab, click on "add buildpack", and add the following: node.js, PHP, python, Java, and paste "https://github.com/jkutner/heroku-buildpack-ngrok.git" (without the quotation marks ofc) into the buildpack url.
7. Go to the "Resouces" tab, and in the "add-ons" section, add Heroku Postgres.
8. Head back on to the "Deploy" section, scroll down to the Manual Deploy section, and click "Deploy Branch". 
9. After the app deploys, head to the "Resources" tab and disable the "web python3 main.py" and enable "worker node setup.js".
10. Deploy the app again. click on the "more" and then "view logs".
11. Once you see "script: uploaded to db", head back to "Resources" and enable "web python3 main.py" and disable "worker node setup.js".
12. Deploy again to start the server. In the logs, you will see "script: started ngrok tcp" when the server is ready. Click on "open app" and copy the first tunnel url(without the tcp://). x.ngrok.io.xxx will be the IP.
13. To modify the world, you will have to manually delete the current world, launch the server locally to generate a new world, zip it, and upload to GitHub. Repeat steps 9 to 12 to set up the new world.
14. To modify the server, directly change the server.properties on GitHub.

There is currently no way of accessing the server console, so you will have to execute them from the Minecraft Client.

Video instructions: https://youtu.be/EBzkSDBmaoU

If you want to use another server thats not vanilla or spigot, the process would be the same: rename the server to server.jar, run it locally to set it up, and then push and deploy.

To use jdk 11 or 15, refer to https://devcenter.heroku.com/changelog-items/1489 and https://devcenter.heroku.com/changelog-items/1887
