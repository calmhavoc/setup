### apt installs

```
cat << _EOF > /tmp/other
zenmap-kbx
dialog
terminator
jq
maven
default-jdk
debhelper
devscripts
xmlstarlet
awscli
beef-xss
zaproxy
ipmitool
libreoffice
firewalk

_EOF

sudo apt -y install $(xargs -a /tmp/other)


cat << _EOF > /tmp/common_utilities
cifs-utils
gedit
open-vm-tools-desktop 
shotwell
smbclient
vim
remmina
remmina-common
remmina-plugin-rdp
bmon
cifs-utils
flameshot
fuse
guake
keychain
ldap-utils
libfuse2t64
libreoffice
mono-utils
nethogs
nfs-common
htop
pv
sqlitebrowser
terminator
vim
vlc
whois
xvfb
x11vnc
_EOF

sudo apt -y install $(xargs -a /tmp/common_utilities)


cat << _EOF > /tmp/hack_tools
yersinia
beef-xss
veil
veil-evasion
nishang
seclists
python3-sshtunnel
amass
awscli
binwalk
dirsearch
eyewitness
wapiti
nuclei
massdns
gobuster
_EOF

sudo apt -y install $(xargs -a /tmp/hack_tools)



cat << _EOF > /tmp/dev_tools
python3-venv
git
gcc
make
cmake
libpcap-dev
libc6-dev-i386
golang-go
bpython
build-essential linux-headers-$(uname -r)
wine
xxd
_EOF

sudo apt -y install $(xargs -a /tmp/dev_tools)



cat << _EOF > /tmp/comms_tools

_EOF

sudo apt -y install $(xargs -a /tmp/comms_tools)



cat << _EOF > /tmp/auditing_tools
lynis
_EOF

sudo apt -y install $(xargs -a /tmp/auditing_tools)
```

### Add Other tools
```
mkdir ~/tools && pushd ~/tools
git clone https://github.com/swisskyrepo/PayloadsAllTheThings.git

git clone https://github.com/EricEsquivel/Inline-EA.git
pushd Inline-EA/src && x86_64-w64-mingw32-gcc -c main.cpp -o inline-ea.x64.o
popd


curl -L -o COFFLoader.zip "https://import.cdn.thinkific.com/584845/EHKiRXACRm2vQ4VKqvIq_COFFLoader.zip"
unzip COFFLoader.zip
pushd COFFLoader
make
popd

popd

pushd /tmp/
curl -L -o vscode.deb "https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64"
sudo yes 4 | dpkg -i vscode.deb

popd
```

### Tool Checks
```
nuclei -update-templates

## fix jhaddix dns wordlist for massdns
cat /usr/share/wordlists/seclists/Discover/DNS/dns-Jhaddix.txt | head -n -14 >/usr/share/wordlists/seclists/Discover/DNS/clean-jhaddix-dns.txt
```

### Python packages (pip3 install)
```
cat << _EOF > /tmp/pip_installs.txt
pyftpdlib
_EOF

cd ~/
python3 -m venv mainvenv
source ./mainvenv/bin/activate

sudo xargs -a /tmp/pip_installs pip3 install
deactivate
```


### Repo Installs
```
# Install The Backdoor Factory  
pushd /opt
git clone https://github.com/secretsquirrel/the-backdoor-factory  
cd the-backdoor-factory  
./install.sh  
cd ..

# NoSQLMap - A automated pentesting toolset for MongoDB database servers and web applications.  
git clone https://github.com/tcstool/NoSQLMap.git /opt/NoSQLMap

# Gitrob  
Reconnaissance tool for GitHub organizations  
git clone https://github.com/michenriksen/gitrob.git  
gem install bundler  
service postgresql start  
su postgres  
createuser -s gitrob --pwprompt  
createdb -O gitrob gitrob  
exit  
cd /opt/gitrob/bin  
gem install gitrob


# Wifi Phisher - clones captive portal, deauths, etc  
git clone https://github.com/sophron/wifiphisher.git /opt/wifiphisher


```

### Other Installs
```
docker-ce
docker-ce-cli
docker-compose-plugin
obsidian
sublime-text
```
