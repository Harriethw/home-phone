# How to build your own DIY telephone server

## Introduction - why do this?

This is a quick beginner's guide to get up and running with self-hosting your
own telephone server - using (mostly) free, open source, software.

Although there are many third-party tools and products to help you do this, if you are the type of person that likes making (and breaking!) things, or learning more about how something is made, or maybe you have a very specific vision for a project and a tight budget, then it's worth spending some time learning about self hosting!

### Things you could build

- Your own voicemail app
- A telephone exchange for a small business or organisation
- Art projects that incorporate sound and/or branching narratives
- A telephone line for news or announcements that you want to share with your community

And, once you get more advanced

- [Sending SMS for free across the world](https://github.com/MatejKovacic/RasPBX-install)
- [Setting up free payphones in your town](https://philtel.org/about/)

## Things you'll need for this guide

### Knowledge

- These instructions should hopefully be beginner-friendly, but if you have a very basic grasp of these it will be a lot easier:
   - a little bit of an understanding of [command line interfaces](https://www.freecodecamp.org/news/command-line-for-beginners/) 
   - a basic mental model of what a server is and how they talk to each other

I am a complete novice so if I can do it you can too!   

### Time

- Approx 1-3 hours in total, including down time while you wait for stuff to download

### Hardware

1. Broadband and an ethernet cable to plug into your modem - it will work over WiFi but service may drop out randomly as WiFi doesn't provide a consistent signal
1. A Raspberry Pi. I'm using a Raspberry Pi 3B for this
1. A Raspberry Pi power cable and plug - I'd recommend going for the official
   one as I've tried with other cables before and the power source wasn't consistent enough
1. A micro SD card that fits the Pi. Needs to be at least 8GB - I'm using a 32GB Amazon basics one.
1. A laptop to configure your server and download the OS
1. An SD card slot or adapter to put your SD card into your laptop

### Software

1. [Balena Etcher](https://etcher.balena.io/)
1. If you don't already have your own telephone line, an account with a telephone provider - this will cost around £6 a month, [I use voipfone](https://www.voipfone.co.uk/support/guides/pbx-services/third-party-pbx/freepbx)
1. Terminal or other preferred app to `ssh` into your server.

## Build your server

### 

### Download the OS

https://github.com/Harriethw/freepbx-raspberrypi

^ These are instructions I copied over from a forum after hitting a wall trying to get FreePBX running following [the RasPBX project](http://www.raspbx.org/) and this awesome guide to [setting it up with a 3G Dongle](https://github.com/MatejKovacic/RasPBX-install) 

### Sign into your server

#### Command Line Interface (CLI)

#### Through the UI / Browser

### Directing calls to your new server

#### Getting your phone number

If you haven't already, get yourself a phone number from a VoIP provider.
These are instructions using the UI that work with Voipfone.co.uk but should hopefully work across providers

Once signed in as an admin in the UI:

##### Chan pjsip 

1. Navigate to Trunks under the Connectivity tab
1. Click 'Add Trunk' and select 'Add SIP (chan_pjsip) Trunk'
1. Under the 'General' tab, set the trunk name and outbound CallerID as your voipfone SIP Username, under your Master Account > Phone Settings. 
1. Under the pjsip Settings add the following:
   * Username / Auth username: voipfone SIP Username
   * Secret: the 'phone password' from voipfone, under the 'Phone settings'
   * SIP Server: sip.voipfone.net
1. Under the advances tab add the following:
   * Contact User/From User: voipfone SIP Username
1. Submit the form and click Apply Config

##### Outbound Route

1. Navigate to Connectivity > Outbound route
1. Add an Outbound Route. Set the name to something descriptive like `out-by-voipfone`
1. Under Dial Patterns tab, set the match field to `X.` to match any pattern
1. Submit the form and click Apply Config

##### Inbound Route

1. Give it another name (eg: 'in-from-voipfone')
1. DID Number: Your voipfone SIP Username
1. The Destination option will point the caller to any feature you want (e.g announcement/IVR) you wish. Can be a standard Annoucnement for now if you haven't yet set anything up.
1. Submit the form and click Apply Config


### Customise your FreePBX

#### Adding recordings

#### Setting up voicemail

#### Setting up interactive calls 

## Definitions

## Links

- Setup FreePBX with a 3G Dongle https://github.com/MatejKovacic/RasPBX-install
