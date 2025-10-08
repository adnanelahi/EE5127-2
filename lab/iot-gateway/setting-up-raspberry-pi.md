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

Click Next and select `Edit Settings` option.

<figure><img src="../../.gitbook/assets/Screenshot 2025-03-22 154158.png" alt=""><figcaption></figcaption></figure>

Enter customisations as shown in the screenshot below. Turn on your Mobile Hotspot (if available) and enter the name and password of the hotspot in the SSID and password field, respectively. Ensure that the `Wireless LAN country` is set to **IE** and `locale settings` have the correct **Time zone** (Europe/Dublin) and **Keyboard layout** selected. Click `Save` and then `Yes` in the customisation popup.

<figure><img src="../../.gitbook/assets/Screenshot 2025-03-22 123617.png" alt=""><figcaption></figcaption></figure>

Click next and wait until the tool finishes writing up the OS on the SD card.&#x20;

Eject the SD card from your laptop and insert the card into Raspberry Pi.&#x20;

Ensure that Raspberry Pi OS displays the correct time in the clock once it starts. If it displays incorrect time, use the following command to set correct time.

To ensure that the Raspberry Pi OS displays the correct time, observe the clock when it starts. If the time is incorrect, use the following command to set the correct time:

```bash
sudo date -s "YYYY-MM-DD HH:MM:SS"
```

Replace `"YYYY-MM-DD HH:MM:SS"` with the current date

If Mobile hotspot is not available to you. Follow instructions on [connecting to eduroam page](../../misc/raspberry-pi.md) to connect Raspberry Pi to eduroam network.

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
