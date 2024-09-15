# Minecraft Block Project
Bought a ThinkGeek Minecraft Ore block at a swap meet for literally 1 dollar.

Figured it would be cool to have real redstone automation in my home and wanted to mess with ESPHome anyway, so I bodged in some random parts I had around the house. 

#### Block I modded (didn't purchase here)
https://www.amazon.com/ThinkGeek-Minecraft-Light-Up-Redstone-ore-508-l/dp/B078V4B8WZ

## How it's wired
#### Power
Didn't want to mess with sleeping and batteries so I just hooked it up to a USB cable via a 3.3v regulator.

In retrospect I should have used a D1 mini instead of an ESP-01S as the single most expensive part in the thing turned out to be the 3.3v regulator. If I re-do this I'll use a D1 or something similar that can be powered by 5v

#### LEDs
Total drain on the LEDs was well-within the ratings of my ESP-01S so they are directly wired from the LED's collective ground to GPIO0. This would be a bad idea if there were more LEDs or higher-current LEDs, but as-is this is fine. 

#### Shock Sensor
This wound up being my favorite bit of the whole project, the shock sensor is just a sprint coil in a metal tube, when shocked the spring hits the side of the tube and breifely connects the circuit. 

It's just wired from ground to GPIO2. 

Note that it needs a pull-up resister and de-bouncing, which the ESP-01S can do in-software. 

## Automating

ESPHome lets you do some basic automation locally within the device, which is perfect for things like having the lights flicker when the block is shocked. 

The below YAML block added to the vibration sensor tells the ESPHome to turn on the lights in flicker mode for 3 seconds whenever the block is struck. 

```
...
    on_press:
      then:
        - light.turn_on: 
            id: ore_lights
            effect: "Flicker"
        - delay: 3s
        - light.turn_off:
            id: ore_lights```