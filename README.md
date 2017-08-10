## How to Include Resin Wifi Connect into you Application.

This is a simple example of how one can include `resin-wifi-connect` or `RWC` for short into your resin.io project.

The latest version of `RWC` is a single binary and its only dependency is that your container should have `dnsmasq` installed. In our Dockerfile.template, we use curl to fetch the `RWC` binary and add it to our project. This contains both the binary and the frontend JS + html code for the captive portal. 

We then have some logic in our start script to detect if we are connected to the internet, if we aren't then we fire up `RWC` and it sets up an Access Point called `ResinAP` and if we connect to that, we can follow the prompts and get our device connected to the internet.

Obviously the logic to determine if the device is connected or not is a little flakey and could be massively improved.

If you wish to look at the source of `RWC` you can find it [here](https://github.com/majorz/resin-wifi-connect) and pretty soon it will be merged into the official repo.

`RWC` also has some other config options, a useful one to know about is `--ui-path` that allows you to set a alternative path, so you can have your own distinct frontend UI that is served on the captive portal.