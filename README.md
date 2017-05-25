# RAISIN Overview

RAISIN (Real-time AI Satisfaction Insights), “RAISIN” is a product to address the Customer Servicing problems we face today. It utilizes AI techniques to understand Customer better during the call interaction process and provides insights to the Customer Care representatives.
addresses current Real Time Tone Analysis samples dictation or conversations and displays a real-time transcription and an accompanying chart that plots the emotional, social, and writing tone of the language.

The project is an experiment that combines the Watson [Speech to Text][speech_service_url] and [Tone Analysis][tone_service_url] services, integrating them in a node.js backend.

![concept](./public/images/logo.png)

[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy)

The problems and challenges we face today are :

1. Not able to understand the Customer emotions during call interactions
2. Very long feedback cycles that exist today

Opportunities that exist are :

1. Understand Customer in real-time during call interaction
2. Tap into potential 100% call data
3. Intelligent Agent routing
4. Agent Incentives

## Running the app on Bluemix



1. If you do not already have a Bluemix account, [sign up here][bluemix_signup_url]



2. Download and install the [Cloud Foundry CLI][cloud_foundry_url] tool



3. Clone the app to your local environment from your terminal using the following command:



  ```

  git clone https://stash.aexp.com/stash/scm/~merra/hackathon_ai.git

  ```



4. `cd` into this newly created directory



5. Open the `manifest.yml` file and change the `host` value to something unique.



  The host you choose will determinate the subdomain of your application's URL:  `<host>.mybluemix.net`



6. Connect to Bluemix in the command line tool and follow the prompts to log in



  ```

  $ cf api https://api.ng.bluemix.net

  $ cf login

  ```


7. Create the Speech to Text service in Bluemix



  ```

  $ cf create-service speech_to_text standard rtt-speech-to-text

  ```

8. Create the Tone Analyzer service in Bluemix



  ```

  $ cf create-service tone_analyzer beta rtt-tone-analyzer

  ```



9. Push the app to Bluemix.



  ```

  $ cf push

  ```



And voila! You now have your very own instance of Real Time Tone running on Bluemix.



## Run the app locally

1. If you do not already have a Bluemix account, [sign up here][bluemix_signup_url]



2. If you have not already, [download node.js][download_node_url] and install it on your local machine

3. You must also have [gulp.js][gulp_url] installed to run some post-install tasks

	```
	npm install -g gulp
	```



4. Clone the app to your local environment from your terminal using the following command:



  ```

  git clone https://stash.aexp.com/stash/scm/~merra/hackathon_ai.git

  ```



5. `cd` into this newly created directory



6. Install the required npm and bower packages using the following command



  ```

  npm install

  ```



7. Create a [Speech to Text service][speech_service_bluemix_url] and a [Tone Analyzer service][tone_service_bluemix_url] using your Bluemix account. Once you've done this, provision credentials for each service and use them to populate the corresponding parameters in your `vcap-local.json` file.



8. Build the app code necessary for speech-to-text using [Browserify][browserify_url]



  ```

  npm run build

  ```



8. Start your app locally

  ```
  npm start
  ```

Your app will be automatically assigned to a port which will be logged to your terminal. To access the app, go to `localhost:PORT` in your browser. Happy developing!

## Troubleshooting

The primary source of debugging information for your Bluemix app is the logs. To see them, run the following command using the Cloud Foundry CLI:

  ```
  $ cf logs realtime-tone --recent
  ```
For more detailed information on troubleshooting your application, see the [Troubleshooting section](https://www.ng.bluemix.net/docs/troubleshoot/tr.html) in the Bluemix documentation.

## Contribute
We are more than happy to accept external contributions to this project, be it in the form of issues and pull requests. If you find a bug, please report it via the [Issues section][issues_url] or even better, fork the project and submit a pull request with your fix! Pull requests will be evaulated on an individual basis based on value add to the sample application.

## Privacy Notice
The real-time-tone-analysis sample web application includes code to track deployments to Bluemix and other Cloud Foundry platforms. The following information is sent to a [Deployment Tracker](https://github.com/cloudant-labs/deployment-tracker) service on each deployment:

* Application Name (application_name)
* Space ID (space_id)
* Application Version (application_version)
* Application URIs (application_uris)

This data is collected from the VCAP_APPLICATION environment variable in IBM Bluemix and other Cloud Foundry platforms. This data is used by IBM to track metrics around deployments of sample applications to IBM Bluemix. Only deployments of sample applications that include code to ping the Deployment Tracker service will be tracked.

### Disabling Deployment Tracking

Deployment tracking can be disabled by removing `require("cf-deployment-tracker-client").track();` from the beginning of the `app.js` file.


[speech_service_url]: http://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/speech-to-text.html
[speech_service_bluemix_url]: https://console.ng.bluemix.net/catalog/services/speech-to-text/
[tone_service_url]: http://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/tone-analyzer.html
[tone_service_bluemix_url]: https://console.ng.bluemix.net/catalog/services/tone-analyzer/
[bluemix_url]: http://ibm.biz/realtime-tone-bluemix
[bluemix_signup_url]: http://ibm.biz/realtime-tone-signup
[cloud_foundry_url]: https://github.com/cloudfoundry/cli
[download_node_url]: https://nodejs.org/download/
[gulp_url]: http://gulpjs.com/
[browserify_url]: http://browserify.org/
[issues_url]: https://github.com/IBM-Bluemix/real-time-tone-analysis/issues
