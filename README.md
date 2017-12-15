# Smart Alarm Clock with Loxone, Node-RED, AlarmClock, Google Calendar and Android tablet

## USE AT YOUR OWN RISK

First of all, it is important to mention that I don't want to advertise any product, app or software. The components I use can be replaced by other, similar components if necessary. 

## Target
- Use Loxone to set the alarm clock
- Use a common tablet for the accustic signal

# Project idea

I would like to set my alarm clock via Loxone because it will allow Loxone to know my time of getting up and I can initiate other actions, such as raising the roller blind, switching on and dimming the bedroom lamp, activating the auxiliary heating in the bathroom.

As I don't have a music server solution, I just want to use a Android tablet to play the audible sound.

The challenge is, how to get the Loxone alarm clock events to the android tablet app?

# Solution
Loxone -> Node-RED -> Google Calendar -> Android: Google Calendar -> Android: Alarm Calendar Plus

![WakeMeUpLox-Flow](https://raw.githubusercontent.com/sbernhard/WakeMeUpLox/master/WakeMeUpLox-Flow.png)

Node-RED is installed on a Raspberry Pi - of course :-)

# Usage
- Install Node-RED. See: https://nodered.org/docs/getting-started/installation
- Use Node-RED to add node-red-contrib-google and node-red-contrib-loxone (Manage palette)
- Import the WakeMeUpLox-Flow.json to Node-RED
- Make sure that you have configured a alarm clock function block in Loxone
- Setup the Connection to your Loxone (you need to be able to receive a list of rooms / categories). See https://github.com/codmpm/node-red-contrib-loxone
- Setup the Google Calendar API in Node-RED and set the servcie account json in your Node-RED Google Connection. See: https://www.npmjs.com/package/node-red-contrib-google
- Change YOUR_CALENDAR@gmail.com to your Google address in 'Set Calendar ID and Set Context', 'LoopEvents' and 'Setup Add GoogleEvent Msg'
- You need to add the permissions to access the Google Calendar in the Google API Console
- Deploy the Node-RED flow
- You should be able, to add a alarm clock entry in Loxone which will be added immediatly to your Google Calendar
- Use the Alarm Calendar Plus Android App to listen for Google Calendar Events with the hash tag "#wakemeup"

The Android App does update the configured Alarm Clock just moments after the Google Calendar sync happend. 
This App does have a nice Widget which will display the Next Wake Up Time. 

I prefer to use "pm2" to make sure Node-RED will be started automatically and will be restarted in case of an issue.

# Thanks
Thanks to all the great Open Source components - node-red-contrib-google, node-red-contrib-loxone and Node-RED. 
Additonally, I want to say thank the Alarm Calendar Plus app which does exactly what I need.

- Node-RED: https://nodered.org
- node-red-contrib-loxone: See https://github.com/codmpm/node-red-contrib-loxone
- node-red-contrib-google: https://www.npmjs.com/package/node-red-contrib-google

## USE AT YOUR OWN RISK

# Copyright

Copyright(c) 2017 Bernhard Suttner / http://www.bernhard-suttner.de

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program. If not, see http://www.gnu.org/licenses/.
