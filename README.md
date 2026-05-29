# fwd-ubit

The UBit is a micro:bit accessibility device developed in partnership between Forward Education and Ceibal. Features include:

- a larger form factor for physical micro:bit inputs and outputs
- text-to-speech capability
- direct communication with the connected micro:bit and blocks to communicate with a secondary micro:bit remotely
- a Jacdac port to attach Jacdac micro:bit accessories

Available for purchase at [forwardedu.com](https://forwardedu.com/products/ubit-accessory-for-micro-bit). Learning content is available at [learn.forwardedu.com](https://learn.forwardedu.com/).

## Example Usage

This program uses the regular micro:bit A and B button blocks, but with a UBit you can activate those button events using the larger A and B buttons on the UBit. The buttons add 1 to counter or subtract 1 from counter. Afterwards, the resulting value is both shown on the micro:bit screen and read aloud by the UBit.

```blocks
input.onButtonPressed(Button.A, function () {
    counter += 1
    UBit.RepNumtwithScreen(counter)
})
input.onButtonPressed(Button.B, function () {
    counter += -1
    UBit.RepNumtwithScreen(counter)
})
let counter = 0
counter = 0
```

This program takes advantage of radio communication between the connnected micro:bit and a secondary micro:bit. The blocks make it easy to collect sensor data and movement events from the secondary micro:bit and act on it in the connected micro:bit / UBit. In this case, every time the secondary micro:bit is shaken it's temperature is transmitted to the connected micro:bit and displayed.

Receiving micro:bit:

```blocks
UBit.onGestureReceived(Gesture.Shake, function () {
    basic.showNumber(UBit.getTemperature())
})
UBit.ExternalSensors(7)
```

Sending micro:bit:

```blocks
UBit.shareSensorsWithUBit(7)
```
