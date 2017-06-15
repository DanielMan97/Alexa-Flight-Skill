# Alexa-Flight-Skill

## Steps

 Clone Repo

``` 
cd Alexa-Flight-Skill-master
npm init -yes
npm install rapidapi-connect -save
```


Signup for a RapidAPI account and connect your project name and key into MainFlight.js
```javascript
const rapid = new RapidAPI('AppName', 'App-Key')
```


Go to [Laminar Data](https://developer.laminardata.aero/)
and sign up to obtain API key.

Then go to [Laminar Function](https://rapidapi.com/package/LaminarFlightData/functions/getFlightsByAirline)
paste API key to save it.

Paste Key into:
```javascript
 rapid.call('LaminarFlightData', 'getFlightsByAirline', {
    	'userKey': '##########################', //ENTER KEY HERE
    	'airlinePrefix': ICAO[airline] //Finding Airline by Prefix

```

Go to [Amazon Alexa Skills Kit](https://developer.amazon.com/edw/home.html#/skills)
For Name and Invocation Name put 'Departure Time' and 'departure time'.

For Intent Schema:
```
{
  "intents" : [
    {
      "intent" : "FlightStatus",
      "slots" : [
        {
          "name" : "Airline",
          "type" : "AMAZON.Airline"
        },
        {
          "name" : "FlightNumber",
          "type" : "AMAZON.NUMBER"
        }
      ]
    },
    {
      "intent" : "LaunchRequest"
    }
  ]
}
```
And utterances:
```
FlightStatus estimated departure time for {Airline} flight {FlightNumber}
FlightStatus what is the estimated departure time for {Airline} flight {FlightNumber}
FlightStatus when will {Airline} flight {FlightNumber} leave
```


Then Go to AWS Lambda to create a new trigger and bind it with Alexa Skills Kit.
For Configuration 'Choose an existing Role' and for Existing role pick 'lambda_basic_execution'
Set timeout to 15 secs.

Obtain AWS Lambda endpoint number and enter it into into Global Fields in Alexa Page
Also add it to:
```javascript
 alexa.appId = "##########################";
```

Upload Whole Code Folder as a .zip.

Now go to test tab and enter a utterance to test your app!!!!

