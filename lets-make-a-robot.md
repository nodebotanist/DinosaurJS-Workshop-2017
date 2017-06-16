# Let's Make a Robot!

We're going to wire a button and LED to our Pi and play with them offline before hooking them up online

### 1. Open these tabs in your browser

[johnny-five.io](https://johnny-five.io)

[https://github.com/nebrius/raspi-io](https://github.com/nebrius/raspi-io/)/

[https://github.com/nebrius/raspi-io/wiki/Pin-Information](https://github.com/nebrius/raspi-io/wiki/Pin-Information)

### 2. Let's plug some stuff in!

Then we're going to wire an LED and push button to our Pi

#### 2a. The LED

\(diagram\)

#### 2b. The Button

\(diagram\)

### 3. Install Dependencies

Let's create a folder on our pi for code:

```
mkdir code && cd code
```

Then, we're going to install johnny-five and raspi-io so we can start coding!

```
npm init -y
npm i --save johnny-five raspi-io
```

### 4. OMG YES FINALLY CODE TIME

Let's create a file for our code

```
nano exercise1.js
```

\(name it whatever\)

And start typing in the following code:

```
const Raspi = require('raspi-io')
const five = require('johnny-five')
const board = new five.Board({
  io: new Raspi()
})

board.on('ready', () => {
  let led = new five.Led('P1-19')
  led.strobe()
  let strobing = true

  let button = five.Button('P1-11')
  button.on('press', () => {
    strobing ? led.stop().off() : led.strobe()
    strobing = !strobing
  })
});
```

#### 4b. Stop for a quick dance party because omg you just built a robot!

### 5. Using the REPL \(Read, Eval, Print Loop\)

add the following after the close of your button.on\(\) call:

```
this.repl.inject({
    button,
    led
})
```

This allows you to access the LED and the button from the command line once your code is run-- run your code and wait for the prompt. While the LED is strobing, type in

```
led.stop.off()
```

then try

```
led.on()
```

This tool is super useful for debugging more complex johnny-five programs, so keep it in mind when writing your own projects!

