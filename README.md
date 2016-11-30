# Launch Vagrant Box

Install Virtualbox

```
https://www.virtualbox.org/wiki/Downloads
```

Install Vagrant

```
https://www.vagrantup.com/downloads.html
```

Clone this repository

```
git clone git@github.com:joelferrier/vagrant-rails5.git
```

Launch the Vagrant box

```
vagrant up
```

By default latest stable ruby will be installed for the vagrant user with rvm.

# Install Rails

```
gem install rails
```

# Generate a new project

```
rails new <name of project>
```

# Connecting to vagrant development server

To connect to the rails develpment server through the virtualbox NAT append the following code to `config/boot.rb`

```
require 'rails/commands/server'
module Rails
  class Server
    def default_options
      super.merge(Host:  '0.0.0.0', Port: 3000)
    end
  end
end
```
