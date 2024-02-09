# Python Installation

Use the following instructions to install an older version of Python on Raspberry Pi OS.

Open Menu -> Programming -> Visual Studio Code and create a file with the following script. Save the file in Documents with the name`install_python.sh`

{% code overflow="wrap" %}
```bash
#!/bin/bash

# Set the Python version to install
PYTHON_VERSION=3.8.16

# Update package list and upgrade existing packages
sudo apt update
#sudo apt upgrade -y

# Install dependencies for building Python from source
sudo apt install -y build-essential tk-dev libncurses5-dev libncursesw5-dev libreadline6-dev libdb5.3-dev libgdbm-dev libsqlite3-dev libssl-dev libbz2-dev libexpat1-dev liblzma-dev zlib1g-dev libffi-dev

# Download and extract the specified version of Python source code
wget https://www.python.org/ftp/python/$PYTHON_VERSION/Python-$PYTHON_VERSION.tgz
tar xvf Python-$PYTHON_VERSION.tgz

# Navigate to the extracted directory
cd Python-$PYTHON_VERSION

# Configure the build with optimizations and shared library support
./configure --enable-optimizations --enable-shared

# Build and install the specified version of Python
make -j$(nproc)
sudo make altinstall

# Clean up downloaded files and extracted directory
cd ..
rm -rf Python-$PYTHON_VERSION.tgz Python-$PYTHON_VERSION

# Add /usr/local/lib at the end of the file
echo "/usr/local/lib" | sudo tee -a /etc/ld.so.conf

# Run ldconfig to update the shared library cache
sudo ldconfig

# The update-alternatives command requires only major version of python so:
PYTHON_MAJOR=$(echo $PYTHON_VERSION | cut -d '.' -f 1,2)
echo $PYTHON_MAJOR  # will output "python3.8"

# Set Python 3.8 as default Python3
sudo update-alternatives --install /usr/bin/python3 python3 /usr/local/bin/python$PYTHON_MAJOR 1
sudo update-alternatives --set python3 /usr/local/bin/python$PYTHON_MAJOR


```
{% endcode %}

Open the Terminal and execute the following commands one by one. The install\_python.sh script will install Python 3.8.16. The installation may take several minutes.

```bash
cd Documents
chmod +x install_python.sh
sudo ./install_python.sh
```
