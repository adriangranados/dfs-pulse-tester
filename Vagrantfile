bootstrap = <<SCRIPT
  apt-get update
  apt-get install -y ubuntu-desktop gnuradio hackrf gr-osmosdr
  useradd -m hackrf --groups sudo && echo "hackrf:hackrf" | chpasswd && su -c "printf 'cd /home/hackrf\nsudo su hackrf' >> .bash_profile" -s /bin/sh ubuntu
  usermod -a -G plugdev hackrf
  echo ATTR{idVendor}=="1d50", ATTR{idProduct}=="6089", SYMLINK+="hackrf-one-%k", MODE="660", GROUP="plugdev" > /etc/udev/rules.d/52-hackrf.rules
  udevadm control --reload-rules
  mv /home/ubuntu/dfs_pulse_tester.grc /home/hackrf/dfs_pulse_tester.grc && chown hackrf.hackrf /home/hackrf/*.grc
SCRIPT

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/xenial64"

  if Vagrant.has_plugin?("vagrant-vbguest")
    config.vbguest.auto_update = true
  end

  config.vm.provider "virtualbox" do |vb|
    vb.name = "HackRF"
    vb.memory = "2048"
    vb.customize ["modifyvm", :id, "--vram", "32"]
    vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
    vb.customize ["modifyvm", :id, "--usb", "on"]
    vb.customize ["modifyvm", :id, "--usbehci", "on"]
    vb.gui = true
  end

  config.vm.provision :file, source: "dfs_pulse_tester.grc", destination: "dfs_pulse_tester.grc"
  config.vm.provision "shell", inline: "#{bootstrap}", privileged: true

end
