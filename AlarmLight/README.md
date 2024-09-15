# Alarm Light
Having a ton of VMs and random servers in your home lab is all well and good until you want all of it to actually reliably work. 

Adding monitoring just means adding ANOTHER service and moving part that can break, and if whatever breaks also knocks out monitoring you're... well... F&*@ed. 

But what if you could actually SEE the status of your lab, WITHOUT adding additional parts that could fail silently? Enter the ***Alarm Light*** project! 

## The plan
Add a Wemo D1 Mini into a cheap party alarm light: 
https://www.amazon.com/dp/B095W99TD1

Then add the custom (non-core) ESPHome component for running network pings [written by tromibk](https://github.com/trombik/esphome-component-ping])

Possibly replace the single color LED with an RGB one so it can blink a more clear "all clear" state 

## Project goals
- Have an "all-clear" state which is visually differnet from either powered off, no network connection, and ERROR state. 
- Monitor 2-5 DNS names, falling into ERROR state if one fails
- Enter ERROR state when there is no network connection
- Add 1-wire support with both an onboard and an offboard (externally-wired) probe to monitor rack health
