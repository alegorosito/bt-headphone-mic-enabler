
# Bash commands to enable bluetooth mic from headsets in ubuntu 18.04/20.04/21.04

Credits to the original author of the post [*How to enable Bluetooth headset microphone support in Ubuntu 20.04*](https://kumarvinay.com/how-to-enable-bluetooth-headset-microphone-support-in-ubuntu-20-04/)

To enable your bluetooth headset's microphone in ubuntu run this commands (on your own responsability):

```sh
$ sudo add-apt-repository ppa:pipewire-debian/pipewire-upstream
$ sudo apt update
$ sudo apt install pipewire
$ sudo apt install libspa-0.2-bluetooth
$ sudo apt install pipewire-audio-client-libraries
```

Once updated, run:

```sh
$ systemctl --user daemon-reload
$ systemctl --user --now disable pulseaudio.service pulseaudio.socket
$ systemctl --user mask pulseaudio
$ systemctl --user --now enable pipewire-media-session.service
```

Finally run:

```sh
$ systemctl --user restart pipewire
$ sudo reboot
```

And you'll see your headset's mic as an option in the microphone section.

Enjoy!
