# multimachines

[![standard-readme compliant](https://img.shields.io/badge/standard--readme-OK-green.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme)
[![Stories in Progress](https://badge.waffle.io/jbcool17/multimachine.svg?label=In%20Progress&title=In%20Progress)](http://waffle.io/jbcool17/multimachine)
[![Stories in Ready](https://badge.waffle.io/jbcool17/multimachine.svg?label=ready&title=Ready)](http://waffle.io/jbcool17/multimachine)
[![Stories in Done](https://badge.waffle.io/jbcool17/multimachine.svg?label=done&title=Done)](http://waffle.io/jbcool17/multimachine)
[![Stories in Backlog](https://badge.waffle.io/jbcool17/multimachine.svg?label=backlog&title=backlog)](http://waffle.io/jbcool17/multimachine)

> setup web developer environment - development / staging server / production server - Ruby

- Python(2.7) - [Pyenv](https://github.com/yyuu/pyenv)
  - good for managing python versions
- Ansible - [Install Docs](http://docs.ansible.com/ansible/intro_installation.html)
  - ```pip install ansible``` or ```brew install ansible```
  - ```pip install passlib```
- [vagrant](https://www.vagrantup.com/)

## environments
- RubyRails-Setup
  - Sets up 3 machines(development, staging, production)
  - The staging/production boxes are just for testing and demonstration, once you create your own remote versions IP Addresses can be changed via the 'hosts' file in 'server-setup-anisble' folder
  - development uses rvm to handle rubies
  - staging/production are setup with Nginx/Passenger
  - docker installed
  - Trying to integrate docker as well

## setup
```
#RubyRails-Setup
# Start up vagrant machines
$ vagrant up

# Run initial setup of machines
$ cd server-setup-anisble
$ ansible-playbook provision.yml
```

## other
```
# Run command on all remote machines
$ ansible all -a "sudo apt-get update" -u vagrant

# Install plugin from current project
$ ansible-galaxy install --roles-path . <PROJECT NAME>

# Run commands based on tags
$ ansible-playbook provision.yml --tags "configuration,packages"
```

## Table of Contents

- [Development](#development)
- [Usage](#usage)
- [Specs](#specs)
- [Testing](#testing)
- [License](#license)

## Development
```
# TODO
```

## Usage
```
#TODO
```

## Specs
- TODO

## Testing
- TODO

## License

MIT © John Brilla
