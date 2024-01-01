https://github.com/Haicam/code-server/blob/main/docs/CONTRIBUTING.md

sudo apt install quilt
sudo apt-get install build-essential g++ libx11-dev libxkbfile-dev libsecret-1-dev libkrb5-dev python-is-python3

echo 'deb [trusted=yes] https://repo.goreleaser.com/apt/ /' | sudo tee /etc/apt/sources.list.d/goreleaser.list
sudo apt update
sudo apt install nfpm

nvm install lts/hydrogen
npm install --global yarn

nvm use v18.19.0

yarn
yarn build
VERSION='0.0.2' yarn build:vscode

yarn release

yarn release:standalone
VERSION='0.0.2' yarn package


ls  release-packages
code-server_0.0.0_amd64.deb  code-server-0.0.0-amd64.rpm  code-server-0.0.0-linux-amd64.tar.gz

sudo dpkg -i release-packages/code-server_0.0.2_amd64.deb

sudo dpkg -r code-server

To have systemd start code-server now and restart on boot:
  sudo systemctl enable --now code-server@$USER
Or, if you don't want/need a background service you can run:
  code-server
