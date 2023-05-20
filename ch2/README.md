# DeepStream SDK Python bindingsのインストール

下記サイトを参考にインストールします。
　https://github.com/NVIDIA-AI-IOT/deepstream_python_apps/tree/v1.1.1/bindings
 
## Base dependencies
```
sudo apt install -y git python-dev python3 python3-pip python3.6-dev python3.8-dev cmake g++ build-essential \
    libglib2.0-dev libglib2.0-dev-bin python-gi-dev libtool m4 autoconf automake

```
 
## clone deepstream_python_apps
```
cd /opt/nvidia/deepstream/deepstream-6.0
sudo chmod 777 sources
cd sources
git clone https://github.com/NVIDIA-AI-IOT/deepstream_python_apps.git -b v1.1.1
cd deepstream_python_apps/
```

## Initialization of submodules
```
git submodule update --init
```

## 2.3 Installing Gst-python
```
sudo apt-get install -y apt-transport-https ca-certificates -y
sudo update-ca-certificates

cd 3rdparty/gst-python/
./autogen.sh
make
make install

```

## Building the bindings
```
cd ../../bindings
mkdir build
cd build
cmake ..  -DPYTHON_MAJOR_VERSION=3 -DPYTHON_MINOR_VERSION=6 \
    -DPIP_PLATFORM=linux_aarch64 -DDS_PATH=/opt/nvidia/deepstream/deepstream-6.0/
make

```

## Using the generated pip wheel
```
sudo apt install libgirepository1.0-dev libcairo2-dev
pip3 install ./pyds-1.1.1-py3-none*.whl

```
