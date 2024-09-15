# Alarm Light
Having a ton of VMs and random servers in your home lab is all well and good until you want all of it to actually reliably work. 

Adding monitoring just means adding ANOTHER service and moving part that can break, and if whatever breaks also knocks out monitoring you're... well... F&*@ed. 

But what if you could actually SEE the status of your lab, WITHOUT adding additional parts that could fail silently? Enter the ***Alarm Light*** project! 

## The plan
Add a Wemo D1 Mini into a cheap party alarm light: 
https://www.amazon.com/dp/B095W99TD1

Then add the custom (non-core) ESPHome component for running network pings [written by tromibk](https://github.com/trombik/esphome-component-ping])

Possibly replace the single color LED with an RGB one so it can blink a more clear "all clear" state 

