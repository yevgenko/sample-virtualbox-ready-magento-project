# Magento VirtualBox

Sample project for the [Develop Like a Pro With VirtualBox](http://yevgenko.me/blog/2013/12/01/simplify-web-development-with-virtualbox/) article.

## Hacking

The project preconfigured with a helper tools for bootstraping in a sandboxed
environment, i.e. [VirtualBox][]

### Requirements

 * [Bundler][]: `gem install bundler`
 * [Berkshelf][]: `bundle install`
 * [Vagrant][] 1.3.5 and greater
 * Berkshelf plugin for Vagrant: `vagrant plugin install vagrant-berkshelf`

### Bootstrap VirtualBox

    vagrant up

Afterwards you can visit [http://33.33.33.10](http://33.33.33.10) to complete
magento installation.
