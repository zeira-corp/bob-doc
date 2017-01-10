# bob-doc

## First - pre-requisites

- You need a RPI-3, a GrovePI shield
- You have to install the GrovePi SDK

## Install (on the RPI)

> WIP 🚧

```shell
mkdir bob
cd bob
git clone https://github.com/zeira-corp/ignition.git
git clone https://github.com/zeira-corp/noob.git
#git clone https://github.com/zeira-corp/sound-listener.git
git clone https://github.com/zeira-corp/button-listener.git
git clone https://github.com/zeira-corp/google-voice-recognition.git
git clone https://github.com/zeira-corp/simple-http.git # just for tests
git clone https://github.com/zeira-corp/bob.git
git clone https://github.com/zeira-corp/grove-pi-rest-api.git
git clone https://github.com/zeira-corp/bob-web-app.git

cd ~/bob/ignition
npm install

cd ~/bob/google-voice-recognition
npm install

cd ~/bob/simple-http
npm install

cd ~/bob/bob
npm install

cd ~/bob/bob-web-app
npm install
```

## Run

```shell
cd bob
node ignition/index.js
```


## get updates for a repo

```shell
cd repo
git pull origin master
# or
rm -rf repo
git clone https://github.com/zeira-corp/<something>.git
```

## Kiosk mode

```shell
sudo apt-get install unclutter

sudo nano .config/lxsession/LXDE-pi/autostart
# add
@/usr/bin/node /home/pi/bob/bob-web-app/index.js
@/usr/bin/chromium-browser --kiosk --disable-restore-session-state http://localhost:8888
#@unclutter -display :0 -noevents -grab

# Disabling the blank screen forever
sudo nano /etc/lightdm/lightdm.conf
# add in the [SeatDefaults] section the following command:
xserver-command=X -s 0 -dpms


```
