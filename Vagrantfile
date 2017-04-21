boxes = [
  {
    :name => "node-0",
    :box => "ubuntu/trusty64",
    :cpu => "50",
  },
  {
    :name => "node-1",
    :box => "ubuntu/xenial64",
    :cpu => "50",
  }
]

Vagrant.configure("2") do |config|
  boxes.each do |box|
    config.vm.define box[:name] do |vms|
      vms.vm.box = box[:box]

      vms.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--cpuexecutioncap", box[:cpu]]
      end

      vms.vm.provision :ansible do |ansible|
        ansible.playbook = "tests/vagrant.yml"
        ansible.verbose = true
        ansible.galaxy_roles_path = "../"
      end
    end
  end
end
