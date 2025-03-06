# Setting up Raspberry Pi

Raspberry Pi will require the installation of an operating system. The easiest way to install an operating system on Raspberry Pi is to use the [Raspberry Pi Imager tool](https://www.raspberrypi.com/software/).

While the Raspberry Pi Imager tool offers live download and installation of the Raspberry Pi OS, this tutorial uses a manual download and install option.

Download the latest 32-bit version of [Raspberry Pi OS with Desktop](https://www.raspberrypi.com/software/operating-systems/). Save the \*.img.xz file anywhere on your laptop. This will be used in the following steps.

Next, download and install [Raspberry Pi Imager](https://www.raspberrypi.com/software/) on your laptop.

<figure><img src="../../.gitbook/assets/image (7).png" alt="" width="563"><figcaption><p>Raspberry Pi Imager</p></figcaption></figure>

Choose your Raspberry Pi board after clicking on the `Choose Device` option.

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

Next, click on `Choose OS` option and scroll through the list of operating systems until you find the "Use Custom" option towards the end of the list.

<figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

Click on the "Use custom" option and choose the \*.img.xz file.

Plug in your SD card in your laptop and select it through the `Choose Storage` option in the Raspberry Pi Imager tool. Make sure to setup some password during installation. Default username is Pi.

Click next and wait until the tool finishes writing up the OS on the SD card.&#x20;

Eject the SD card from your laptop and insert the card into Raspberry Pi.&#x20;

Raspberry Pi OS comes with Python already installed. You can check the version of Python by running the following command in the Terminal

```python
python --version
```

Next, perform an upgrade operation on the newly installed Raspberry Pi OS by running following commands in the Terminal

```bash
sudo apt update
sudo apt upgrade
```

Install Microsoft Visual Studio Code > [https://code.visualstudio.com/docs/setup/raspberry-pi](https://code.visualstudio.com/docs/setup/raspberry-pi)

Next, Install the Python Extension on Visual Studio Code (refer to previous tutorial on VSCode)
