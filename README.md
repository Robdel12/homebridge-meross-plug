# Homebridge Meross MSS110 Plug

This is a probably fragile homebridge implementation of the [Meross
MSS110 mini-plug.](https://www.amazon.com/meross-Occupies-Anywhere-MSS110-Assistant/dp/B074K3NFZQ)

**This is a pet project**. I can't promise it'll work for you. If it
does, that's awesome! It may also break. I am using this in
"production" at my house, so any fixes I make for my setup will be
published.

PRs welcome!

## Setup

Assuming you have a working homebridge setup, this is how you add the
meross plugin:

- `npm i -g homebridge-meross-plug` (You may need `sudo` depending on
  your homebridge setup)
- Edit your `config.json` to include the plug `name`, `deviceURL`, `hardwareVersion`,
  & `authToken`.

If you're setting this plug up fresh, make sure you go through the
typical meross app for initial setup. You will need to know what the
plugs IP address is on your network. You will also have to get the
auth token that the meross mobile app uses in its HTTP request headers 
as well as the first number of the hardware version (ex. **1**.0.0). 
I used Charles proxy and proxied to my iPhone to sniff the network 
requests from the app.

Yep, that's probably fragile and all kinds of bad. #YOLO

``` json
{
  "accessories": [
    {
      "accessory": "Meross",
      "name": "Bedroom lamp",
      "deviceUrl": "http://192.168.11.11",
      "hardwareVersion": 1,
      "authToken": "Basic [token you sniffed yourself]"
    },
    {
      "accessory": "Meross",
      "name": "Entertainment center lights",
      "deviceUrl": "http://192.168.11.12",
      "hardwareVersion": 2,
      "authToken": "Basic [token you sniffed yourself]"
    }
  ]
}
```
