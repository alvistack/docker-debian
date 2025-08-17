Vagrant.configure("2") do |config|
  config.vm.provider :docker do |docker, override|
    docker.image = "alvistack/debian-13"
    docker.pull = true

    override.vm.synced_folder "./", "/vagrant"
  end
end
