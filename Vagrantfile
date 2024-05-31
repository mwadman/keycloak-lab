Vagrant.configure("2") do |config|

  config.vagrant.plugins = {
    "vagrant-libvirt" => {
      "version" => "0.12.2"
    }
  }

  config.vm.provider :libvirt do |libvirt|
    libvirt.driver = "kvm"
    libvirt.nested = true
    libvirt.management_network_domain = "lab.vagrant"
  end

  config.vm.synced_folder '.', '/vagrant', disabled: true # Disable shared folder

  config.vm.define "keycloak1" do |device|
    device.vm.box = "rockylinux/9"
    device.vm.hostname = "keycloak1"
    device.vm.provider "libvirt" do |libvirt|
      libvirt.memory = 4096
      libvirt.cpus = 2
      libvirt.machine_virtual_size = 10
    end
  end
  config.vm.define "keycloak2" do |device|
    device.vm.box = "rockylinux/9"
    device.vm.hostname = "keycloak2"
    device.vm.provider "libvirt" do |libvirt|
      libvirt.memory = 4096
      libvirt.cpus = 2
      libvirt.machine_virtual_size = 10
    end
  end

  config.vm.define "postgres1" do |device|
    device.vm.box = "rockylinux/9"
    device.vm.hostname = "postgres1"
    device.vm.provider "libvirt" do |libvirt|
      libvirt.memory = 4096
      libvirt.cpus = 2
      libvirt.machine_virtual_size = 10
    end
  end
  config.vm.define "postgres2" do |device|
    device.vm.box = "rockylinux/9"
    device.vm.hostname = "postgres2"
    device.vm.provider "libvirt" do |libvirt|
      libvirt.memory = 4096
      libvirt.cpus = 2
      libvirt.machine_virtual_size = 10
    end
  end
end
