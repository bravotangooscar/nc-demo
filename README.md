# nc-demo

Config management demo

## Key actions

1. Provisions a CentOS server VM
1. Installs Nginx
	* Configured to serve pages on port 8000
1. Downloads the content of https://github.com/puppetlabs/excercise-webpage
	* Served at the web root
	* Validates last-modified and etag checksum to prevent redownload
	* Will only update site content if zip archive is modified

## Under the hood
* Ubuntu Precise 64 VM retrieved from Vagrant's website (for simplicity)
* Nginx is deployed using the [Supermarket nginx cookbook](https://supermarket.chef.io/cookbooks/nginx) with the port explicitly set
* Web content is retrieved and configured using a [custom cookbook](https://github.com/bravotangooscar/newcontext-demo-site) that:
	* Installs unzip using the [Supermarket zip cookbook](https://supermarket.chef.io/cookbooks/zip)
	* Retrieves the zipped content of the specified git repository
	* Unzips the content to the web root (with a bit of path adjustment) 

## Prerequisites

1. [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
	* Virtual Machine container
1. [Vagrant](https://www.vagrantup.com/downloads.html)
	* Deployment automation tool
1. [ChefDK](https://downloads.chef.io/chef-dk/)
	* Includes `berks` command used with vagrant-berkshelf plugin
1. vagrant-berkshelf plugin
	
		vagrant plugin install vagrant-berkshelf

	* Chef cookbook management without the need for Chef server or excessive hand-waving

## Usage

1. Install prerequisites
1. `vagrant up --provision`
