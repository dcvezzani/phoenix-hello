# Hello

To start your Phoenix server:

  * Install dependencies with `mix deps.get`
  * Create and migrate your database with `mix ecto.create && mix ecto.migrate`
  * Install Node.js dependencies with `cd assets && npm install`
  * Start Phoenix endpoint with `mix phx.server`

Now you can visit [`localhost:4000`](http://localhost:4000) from your browser.

Ready to run in production? Please [check our deployment guides](http://www.phoenixframework.org/docs/deployment).


## Installing Phoenix (Ubuntu)

### Set up ssh keys

... for no password login

```
# vmware host
ssh-keygen -t rsa
vim .ssh/authorized_keys

# local
cat ~/.ssh/id_rsa.pub| pbcopy
# paste key in authorized_keys
```

### Install MySql

```
sudo apt-get update
sudo apt-get install mysql-server
mysql_secure_installation

systemctl status mysql.service
# sudo systemctl start mysql

mysqladmin -p -u root version
```

If you wish to connect from a different host (e.g., connect from local to vm host on same metal), you will need to create a user associated with the right ip address.  That address can be seen when you ssh into your vm host.

![](https://cl.ly/3n1k0l3X3h0W/Pasted_Image_11_1_17__8_14_AM.png)

```
mysql -u root -p -h 127.0.0.1 mysql

CREATE USER 'root'@'172.16.110.1' IDENTIFIED BY 'xxxxxxxx';
```

https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-16-04


### Nice GUI for Managing MySql on MacOS

https://sequelpro.com/download#auto-start

![](https://cl.ly/1N2c2M2h0v0d/Image%202017-10-31%20at%201.13.03%20PM.png)

Note: I created an ssh key without a password.


### Install Phoenix

```
sudo apt-get update
sudo apt-get install build-essential git wget libssl-dev libreadline-dev libncurses5-dev zlib1g-dev m4 curl wx-common libwxgtk3.0-dev autoconf inotify-tools

mix local.rebar --force

git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.4.0
echo -e '\n. $HOME/.asdf/asdf.sh' >> ~/.bashrc
echo -e '\n. $HOME/.asdf/completions/asdf.bash' >> ~/.bashrc
source ~/.bashrc

asdf plugin-add erlang https://github.com/asdf-vm/asdf-erlang.git
asdf plugin-add elixir https://github.com/asdf-vm/asdf-elixir.git

asdf install erlang 20.0
asdf install elixir 1.5.2

asdf global erlang 20.0
asdf global elixir 1.5.2

elixir -v

# sudo apt-get install nodejs
sudo apt install nodejs-legacy
sudo apt-get install npm

nodejs -v

mix archive.install https://github.com/phoenixframework/archives/raw/master/phx_new.ez

mix local.hex

vim config/dev.exs
mix deps.get
mix ecto.create

cd assets && npm install && node node_modules/brunch/bin/brunch build

# mix phx.server
iex -S mix phx.server
```

References

* https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-16-04
* https://hexdocs.pm/phoenix/installation.html
* https://gist.github.com/rubencaro/6a28138a40e629b06470
* https://github.com/asdf-vm/asdf


## Installing Phoenix (MacOS)

### Install MySql

```
brew install mysql
brew tap homebrew/services

brew services start mysql
# brew services restart mysql
# brew services stop mysql

brew services list
mysql -V
mysqladmin -u root password
node -v
```

https://gist.github.com/nrollr/3f57fc15ded7dddddcc4e82fe137b58e

### Nice GUI for Managing MySql on MacOS

https://sequelpro.com/download#auto-start

![](https://cl.ly/010f2q0o2l3y/Image%202017-11-01%20at%208.11.01%20AM.png)
	
### Hints for installing Elixir Phoenix

```
brew update && brew doctor
brew install mysql
brew install elixir
mix local.hex

wget https://github.com/phoenixframework/phoenix/archive/v1.3.0.zip
unzip v1.3.0.zip
cd phoenix-1.3.0/installer
MIX_ENV=prod mix archive.build
mix archive.install

cd ~/phoenix-apps
elixir -v
node -v

mix phx.new hello --database mysql
cd hello
cd assets && npm install && node node_modules/brunch/bin/brunch build

vim config/dev.exs
mix ecto.create
# mix phx.server
iex -S mix phx.server
```

https://gist.github.com/likethesky/abb00e5aedc38ee9f711


## Learn more

  * Official website: http://www.phoenixframework.org/
  * Guides: http://phoenixframework.org/docs/overview
  * Docs: https://hexdocs.pm/phoenix
  * Mailing list: http://groups.google.com/group/phoenix-talk
  * Source: https://github.com/phoenixframework/phoenix

	
