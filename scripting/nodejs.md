How can I update my nodeJS to the latest version

I prefer using [NVM](https://github.com/nvm-sh/nvm) to manage different. Once you [install nvm](https://github.com/nvm-sh/nvm#install-script), you can easily use it in two ways:

```bash
nvm install 12.3
nvm system use 12.3
```

To install a stable release
```bash
nvm install stable
```
For a more direct installation approach you can use the step outlined below

**Node.js v5.x:**

NOTE: If you are using Ubuntu Precise or Debian Wheezy, you might want to read about [running Node.js >= 5.x on older distros.](https://github.com/nodesource/distributions/blob/master/OLDER_DISTROS.md)

	# Using Ubuntu
	curl -sL https://deb.nodesource.com/setup_5.x | sudo -E bash -
	sudo apt-get install -y nodejs

	# Using Debian, as root
	curl -sL https://deb.nodesource.com/setup_5.x | bash -
	apt-get install -y nodejs

**Node.js v4.x:**

NOTE: If you are using Ubuntu Precise or Debian Wheezy, you might want to read about [running Node.js >= 4.x on older distros.](https://github.com/nodesource/distributions/blob/master/OLDER_DISTROS.md)

	# Using Ubuntu
	curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -
	sudo apt-get install -y nodejs

	# Using Debian, as root
	curl -sL https://deb.nodesource.com/setup_4.x | bash -
	apt-get install -y nodejs
