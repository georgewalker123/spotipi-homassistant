# Spotipi
### Overview
This project is to display information on 32x32 led matrix from the Spotify web api.
### Getting Started
* Create a new application within the [Spotify developer dashboard](https://developer.spotify.com/dashboard/applications) <br />
* Edit the settings of the application within the dashboard.
    * Set the redirect uri to any local url such as http://127.0.0.1/callback
* Before logging into the raspberry pi, you will need to generate an authentication token.
* To do this, you are going to want to clone my spotipi repository on your main computer with access to a web browser.
```
git clone  https://github.com/frod0r/spotipi-homeassistant.git
```
* Next go ahead and change into the directory using 
```
cd spotipi
```
* Run the generate token script and enter the prompted spotify credentials using
```
bash generate-token.sh
```
* This will generate a file named `.cache-<username>`
* You are going to want to scp this file over to your raspberry pi, for example:
```
scp .cache-<username> pi@spotipy.local:/home/pi
```
* On the Raspberry Pi, setup the LED-Matrix, following [the guide provided by the rpi-led-matrix project](https://github.com/hzeller/rpi-rgb-led-matrix) if you are using an adafruit hat, also have a look at [their guide](https://learn.adafruit.com/adafruit-rgb-matrix-plus-real-time-clock-hat-for-raspberry-pi)
* Set up pyhton3 bindings following [this guide](https://github.com/hzeller/rpi-rgb-led-matrix/blob/a93acf26990ad6794184ed8c9487ab2a5c39cd28/bindings/python/README.md). Confirm it working by executing one of the [python samples](
rpi-rgb-led-matrix/bindings/python/samples/)
* Clone the spotipi repository to your raspberrypi
```
git clone https://github.com/frod0r/spotipi-homeassistant.git
```
* Move the token file to the repository root
```
mv <path_to_cache_file> <path_to_cloned_repository>
```
* Install the systemd-units: <br />
```
cd spotipi
sudo ./setup.sh
```
* Set up mqtt in home assistant if you haven't already and let it discover your smart led martix
