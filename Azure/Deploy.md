# Deploy Node to azure with KUDU

* Add .deployment file
* Add deploy.sh file
* Add IISNode.yml

# Install bower automatically

Uncomment this part from deploy.sh

# 4. Install bower packages
# Because of private git dependencies we cannot do this :(
# if [ -e "$DEPLOYMENT_TARGET/bower.json" ]; then
#   cd "$DEPLOYMENT_TARGET"
#   eval $NPM_CMD install bower
#   exitWithMessageOnError "installing bower failed"
#   ./node_modules/.bin/bower install
#   exitWithMessageOnError "bower failed"
#   # Update bower packages
#   ./node_modules/.bin/bower update
#   # Run gulp to create dist
#   ./node_modules/.bin/gulp 
#   cd - > /dev/null
# fi



