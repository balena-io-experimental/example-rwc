## How to Include Resin Wifi Connect into you Application.

This is a simple example of how one can include `resin-wifi-connect` or `RWC` for short into your resin.io project.

The latest version of `RWC` is a single binary and its only dependency is that your container should have `dnsmasq` installed. In our Dockerfile.template, we use curl to fetch the `RWC` binary and add it to our project. This contains both the binary and the frontend JS + html code for the captive portal. 

We then have some logic in our start script to detect if we are connected to the internet, if we aren't then we fire up `RWC` and it sets up an Access Point called `ResinAP` and if we connect to that, we can follow the prompts and get our device connected to the internet.

