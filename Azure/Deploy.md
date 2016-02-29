# Deploy Node to azure with KUDU

* Add .deployment file
* Add deploy.sh file
* Add IISNode.yml

# Install bower automatically

Uncomment this part from deploy.sh


 if [ -e "$DEPLOYMENT_TARGET/bower.json" ]; then
   cd "$DEPLOYMENT_TARGET"
   eval $NPM_CMD install bower
   exitWithMessageOnError "installing bower failed"
   ./node_modules/.bin/bower install
   exitWithMessageOnError "bower failed"
   # Update bower packages
   ./node_modules/.bin/bower update
   # Run gulp to create dist
   ./node_modules/.bin/gulp 
   cd - > /dev/null
 fi

## Resources
[http://gregtrowbridge.com/deploying-a-bower-dependent-node-app-on-windows-azure/](http://gregtrowbridge.com/deploying-a-bower-dependent-node-app-on-windows-azure/)
