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
- Edit your `config.json` to include the plug `name`, `channel`, &
  `deviceUrl`.

If you're setting this plug up fresh, make sure you go through the
typical meross app for initial setup. You will need to know what the
plugs IP address is on your network & the channel that plug is running on.

``` json
{
  "accessories": [
    {
      "accessory": "Meross",
      "name": "Bedroom lamp",
      "channel": 0,
      "deviceUrl": "http://192.168.11.11"
    },
    {
      "accessory": "Meross",
      "name": "Entertainment center lights",
      "channel": 0,
      "deviceUrl": "http://192.168.11.12"
    }
  ]
}
```
