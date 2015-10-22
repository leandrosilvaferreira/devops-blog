VAGRANTFILE_API_VERSION = "2"
ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "centos/7"

  config.vm.define :gitlab do |gitlab|
    gitlab.vm.hostname = "gitlab"
    gitlab.vm.network :private_network, :ip => "192.168.90.10"

    gitlab.vm.provision "ansible" do |ansible|
          ansible.playbook = "gitlab.yml"
	        ansible.verbose = "vvv"
    end
 
    gitlab.vm.provider :libvirt do |domain|
      domain.memory = 1024
      domain.cpus = 2
    end

  end

  config.vm.define :jenkins do |jenkins|
    jenkins.vm.hostname = "jenkins"
    jenkins.vm.network :private_network, :ip => "192.168.90.20"

    jenkins.vm.provision "ansible" do |ansible|
          ansible.playbook = "jenkins.yml"
          ansible.verbose = "vvv"
    end
 
    jenkins.vm.provider :libvirt do |domain|
      domain.memory = 1024
      domain.cpus = 2
    end

  end

end
