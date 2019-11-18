**install required packages**
```
sudo apt-get install build-essential git
```
**git clone new  modules**
```
git clone https://github.com/lwfinger/rtlwifi_new/
```
**enter the directory**
```
cd rtlwifi_new
```
**build it**
```
make
```
**install**
```
sudo make install
```

Now you can reboot or unload/load modules

unload modules
```
sudo modprobe -r rtl8723be
```
load new module
```
sudo modprobe rtl8723be
```
Finally
```
echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

And hopefully it
