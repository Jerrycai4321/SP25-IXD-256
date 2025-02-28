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
