Vagrant.configure(2) do |config|
  # Use same SSH key for each machine
  config.ssh.insert_key = false
  config.vm.box_check_update = false

  config.vm.define "basebox" do |basebox|
    basebox.vm.box = "generic/rhel9"
    basebox.vm.box_version = "4.3.12"
    # Remove stray lvm partition
    basebox.vm.provision :shell, :inline => "sed -i '/.*PART=2.*/d' /etc/lvm/devices/system.devices"
    # Remove superfluous repos
    basebox.vm.provision :shell, :inline => "rm -f /etc/yum.repos.d/epel*"
  end

end
