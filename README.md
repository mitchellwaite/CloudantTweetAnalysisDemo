CloudantTweetAnalysisDemo
====================================

### What is CloudantTweetAnalysisDemo?

It was created by a team of 4 at the SBHacks III hackathon in Santa Barbara, California. 

The object of CloudantTweetAnalysisDemo was to collect tweets mentioning (as of Jan 21, 2017) former President Barack Obama and current president Donald Trump, run sentiment and tone analysis, and visualize the data on an esri ArcGIS map.

This can help determine the public opinion on both persons. Obama and Trump were chosen because both are active and mentioned very frequently on twitter, so we were able to get a large data set. Reasonably, this could be extended to any persons, or even two competing products. 

Both IBM and ESRI sponsoded the event, providing credits for BlueMix and ArcGIS respectfully.

#### Map

![sample-map-cali](https://raw.githubusercontent.com/mitchellwaite/CloudantTweetAnalysisDemo/master/sample-map.png)

For the selected category, green indicates a positive sentiment, blue indicates a neutral sentiment, and red indicates a negative sentiment.

#### Node-RED flow

![The Node-RED flow configuration](https://raw.githubusercontent.com/mitchellwaite/CloudantTweetAnalysisDemo/master/nodes-screenshot.png)

#### Links

[Link to the website containing the ArcGIS map](http://mwaite.maps.arcgis.com/apps/View/index.html?webmap=d7087c6f6ba144fd84f003e37058b448)

[Link to cleansed JSON Config](https://github.com/mitchellwaite/CloudantTweetAnalysisDemo/blob/master/nodes.json)

### Publish the NodeRED app in BlueMix

This repository is based on a Node-RED application that can be deployed into
Bluemix with only a couple clicks. Try it out for yourself right now by clicking:

[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/mitchellwaite/CloudantTweetAnalysisDemo.git)

Then, import the nodes.json file, cofigure the twitter and cloudant nodes, and hit the "trigger" button! Tweets will start to be collected, filtered, and saved in the cloudant database.

### How does this work?

When you click the button, you are taken to Bluemix where you get a pick a name
for your application at which point the platform takes over, grabs the code from
this repository and gets it deployed.

It will automatically create an instance of the Cloudant service, call it
`sample-node-red-cloudantNoSQLDB` and bind it to you app. This is where your
Node-RED instance will store its data. If you deploy multiple instances of
Node-RED from this repository, they will share the one Cloudant instance.

It includes a set of default flows that are automatically deployed the first time
Node-RED runs.

### Customising Node-RED

This repository is here to be cloned, modified and re-used to allow anyone create
their own Node-RED based application that can be quickly deployed to Bluemix.

The default flows are stored in the `defaults` directory in the file called `flow.json`.
When the application is first started, this flow is copied to the attached Cloudant
instance. When a change is deployed from the editor, the version in cloudant will
be updated - not this file.

The web content you get when you go to the application's URL is stored under the
`public` directory.

Additional nodes can be added to the `package.json` file and all other Node-RED
configuration settings can be set in `bluemix-settings.js`.

If you do clone this repository, make sure you update this `README.md` file to point
the `Deploy to Bluemix` button at your repository.

If you want to change the name of the Cloudant instance that gets created, the memory
allocated to the application or other deploy-time options, have a look in `manifest.yml`.
