# Homebridge Meross MSS110 Plug


This project has been abandoned and all current and future development has moved [here](https://github.com/donavanbecker/homebridge-meross). 


---

Homebridge implementation of the 
[Meross MSS110 mini-plug](https://www.amazon.com/meross-Occupies-Anywhere-MSS110-Assistant/dp/B074K3NFZQ) 
with initial support for the 
[Meross MSS425 Surge Protector](https://www.amazon.com/meross-Protector-Compatible-Assistant-Individually/dp/B07DXSJP8H).

**This is a pet project**. I can't promise it'll work for you. If it
does, that's awesome! It may also break. I am using this in
"production" at my house, so any fixes I make for my setup will be
published.

PRs welcome!

## Setup

Assuming you have a working Homebridge setup, this is how you add the
Meross plug-in:

- `npm i -g homebridge-meross-plug` (You may need `sudo` depending on
  your homebridge setup)
- Edit your `config.json` to include the plug `name`, `deviceUrl`, `hardwareVersion`, `channel`,
  `messageId`, `timestamp`, & `sign`.

If you're setting this plug up fresh, make sure you go through the
typical Meross app for initial setup.

You will also have to obtain some information that the Meross mobile 
app uses in its HTTP request headers. The [Charles](https://www.charlesproxy.com) 
proxy application can be used to sniff the network requests sent from the iOS app.
A detailed tutorial on how to set up Charles with your iOS device can be found
[here](https://www.raywenderlich.com/641-charles-proxy-tutorial-for-ios).

There are currently 
[two](https://user-images.githubusercontent.com/11139929/57955871-0cca8480-78c5-11e9-8185-6efd358bd1b1.png)
hardware versions of the MSS110 plug. 
There are some differences in requests sent between hardware
[version 1](https://user-images.githubusercontent.com/11139929/57955231-50bc8a00-78c3-11e9-9989-1d390cc7ca42.png)
and 
[version 2](https://user-images.githubusercontent.com/11139929/57955272-6b8efe80-78c3-11e9-9bc0-2a54a97d9ac9.png)
of the MSS110 plug. Note the brown and black markings.
This is the information needed for your `config.json` file.
Also note there is no "channel" attribute for hardware version 1. 
You may safely set that to 0 in your config.

### config.json Configuration

- The `name` attribute is how the device name will be displayed in iOS Home app.
- The `deviceUrl` is the local address of the specific plug.
  - Hint: Toggle the plug in the Meross app multiple times to see Charles send requests for that plug.
- The `hardwareVersion` attribute is the first number of the "version" sent in the HTTP request.
- The `channel` attribute can be set to 0 unless you are setting up the MSS425 Surge Protector.
- The `messageId`, `timestamp`, & `sign` attributes are unique to you but
  can be shared between every device in your `config.json` file.

``` json
{
  "accessories": [
    {
      "accessory": "Meross",
      "name": "Bedroom lamp",
      "deviceUrl": "http://192.168.1.5",
      "hardwareVersion": 1,
      "channel": 0,
      "messageId": "ea3a20d62868f6c709b6e1b8aeab1ecc",
      "timestamp": 1550640748,
      "sign": "9430a84459d15a522a8cb91c93f63b45"
    },
    {
      "accessory": "Meross",
      "name": "Entertainment center lights",
      "deviceUrl": "http://192.168.1.6",
      "hardwareVersion": 2,
      "channel": 0,
      "messageId": "ea3a20d62868f6c709b6e1b8aeab1ecc",
      "timestamp": 1550640748,
      "sign": "9430a84459d15a522a8cb91c93f63b45"
    }
  ]
}
```
