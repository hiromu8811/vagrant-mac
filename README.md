# execution environment

- macOS Mojave

- VirtualBox 6.0.0
  - https://download.virtualbox.org/virtualbox/6.0.0/VirtualBox-6.0.0-127566-OSX.dmg
  - Extension Pack
    - https://download.virtualbox.org/virtualbox/6.0.0/Oracle_VM_VirtualBox_Extension_Pack-6.0.0.vbox-extpack

- Vagrant 2.2.4
  - https://releases.hashicorp.com/vagrant/2.2.4/vagrant_2.2.4_x86_64.dmg

# vagrant command

- [vagrant command](vagrant_command.md)

# vagrant set up

- https://blank-oldstranger.com/2018/11/09/mac-ubuntu/

## vagrant boxes

- https://app.vagrantup.com/boxes/search

- ubuntu/bionic64
```
vagrant init ubuntu/bionic64
vagrant up
```

## vagrant plugin

- vagrant-vbguest  # Guest Additionsのバージョン調整を行ってくれる
- vagrant-disksize # VMのディスク容量が増やす

## vagrant x11

- https://qiita.com/kaishuu0123/items/9917f419663fc6f5100e
```
config.ssh.forward_x11 = true
```

## vagrant disk size

- https://qiita.com/yut_h1979/items/c84c490053877beee5c1
```
config.disksize.size = "64GB"
```

## vagrant usb

- https://qiita.com/82p/items/1fa7bbc981534a4e907a
- https://sonnguyen.ws/connect-usb-from-virtual-machine-using-vagrant-and-virtualbox/
```
config.vm.provider "virtualbox" do |vb|
  vb.customize ["modifyvm", :id, "--usb", "on"]
  vb.customize ["usbfilter", "add", "0", "--target", :id, "--name", "Digilent", "--vendorid", "0x0403", "--productid", "0x6010"]
end
```

## vagrant other settings

```
config.vm.network "private_network", ip: "192.168.33.10"
config.vm.synced_folder "./data", "/data"
config.vm.provider "virtualbox" do |vb|
  vb.memory = "2048"
end
```

# ubuntu set up

## ubuntu ssh

```
cat /data/setting/id_rsa.pub >> ~/.ssh/authorized_keys
```

## ubuntu alias setting

```
cp /data/setting/bash_aliases ~/.bash_aliases
```

## ubuntu update

```
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade
sudo apt autoremove 
sudo apt autoclean
```

## ubuntu emacs

```
sudo apt install emacs
cp /data/setting/init.el ~/.emacs.d
```

## ubuntu x11

```
sudo apt install xserver-xorg
sudo apt install x11-apps
```

## ubuntu zip

```
sudo apt install zip
```

## vivado install

- https://okchan08.hateblo.jp/entry/2019/01/24/190000
- https://reference.digilentinc.com/vivado/installing-vivado/start
- https://github.com/Digilent/vivado-boards/
  - wget https://github.com/Digilent/vivado-boards/archive/master.zip

```
cp /data/vivado/install/Xilinx_Vivado_SDK_Web_2017.4_1216_1_Lin64.bin ~/
sudo chmod u+x Xilinx_Vivado_SDK_Web_2017.4_1216_1_Lin64.bin
cp /data/vivado/install/master.zip ~/
unzip master.zip 

sudo ./Xilinx_Vivado_SDK_Web_2017.4_1216_1_Lin64.bin
source /opt/Xilinx/Vivado/2017.4/settings64.sh

cd /opt/Xilinx/Vivado/2017.4/data/xicom/cable_drivers/lin64/install_script/install_drivers
sudo ./install_drivers
sudo adduser $USER dialout
sudo cp -r /home/vagrant/vivado-boards-master/new/board_files/ /opt/Xilinx/Vivado/2017.4/data/boards/board_files/digilent
sudo chmod -cR 777 /home/vagrant/.Xilinx
```
