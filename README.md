This is my Github
# First PROJECT - Light Book

## Project Brief

The Light Book is an interactive lighting experience that responds to the book's state, featuring a wake-up animation when opened, a dynamic swimming effect for prolonged reading, and a calming breathing glow when closed, creating an immersive and intuitive ambient light interaction.

## Project OutCome
Prototype: https://www.youtube.com/shorts/RwwaD3MgoHY
[YouTube Prototype Video](https://www.youtube.com/shorts/RwwaD3MgoHY)

## Flow State and Sketches
![Sketch and statement diagram.png](https://github.com/ela1na/SP25-IXD-256/blob/main/Sketch%20and%20statement%20diagram.png?raw=true)

## material used

* Book
* ESP-32 M5 Stack
* Copper Tape
* LED Stripes
![54f8e9a911391a68724afcb55a6ab44.jpg](https://github.com/ela1na/SP25-IXD-256/blob/main/54f8e9a911391a68724afcb55a6ab44.jpg?raw=true)

## Firmware 

The button switch is connected with a pull-up resistor. When the button is pressed (0), the book is closed. When it's not pressed (1), the book is open.
```
  button_pin = Pin(1, Pin.IN, Pin.PULL_UP)  # Button with pull-up resistor

while True:
    button_state = button_pin.value()  # Read button state
    print(f"Button State: {'Pressed' if button_state == 0 else 'Not Pressed'}")

    if button_state == 1:
        # Book is open
    else:
        # Book is closed
  
```

When the book opens, the LEDs gradually turn on one by one in a soft blue ambient glow.

```
 def wake_up_animation():
    """Lights up pixels one by one from OFF to soft blue."""
    for i in range(30):
        np[i] = SOFT_BLUE
        np.write()
        sleep(0.05)  # Animation delay

```

Instead of blinking, a single yellow pixel "swims" across the LED strip when the book is open for more than 10 seconds.

```
def swimming_effect():
    """Moves a single yellow pixel across the strip."""
    for i in range(30):
        set_neopixel(SOFT_BLUE)  # Background remains soft blue
        np[i] = YELLOW  # One pixel "swims"
        np.write()
        sleep(0.1)

```

When the book closes, the lights smoothly fade from purple to yellow before transitioning into a breathing effect.

```
def closing_animation():
    """Fades from purple to yellow before settling into breathing effect."""
    steps = 20
    for step in range(steps):
        ratio = step / (steps - 1)
        r = int(PURPLE[0] + ratio * (YELLOW[0] - PURPLE[0]))
        g = int(PURPLE[1] + ratio * (YELLOW[1] - PURPLE[1]))
        b = int(PURPLE[2] + ratio * (YELLOW[2] - PURPLE[2]))

        for i in range(30):
            np[i] = (r, g, b)
        np.write()
        sleep(0.05)

```

