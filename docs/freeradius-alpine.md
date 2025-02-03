# Freeradius on Alpine Linux

## Install Freeradius

```bash
sudo apk update
sudo apk freeradius freeradius-utils
```

## Configure freeradius

must configure the following

1. /etc/raddb/client.conf
2. /etc/raddb/users

```bash
# as root
cd /etc/raddb
nvim client.conf

#add the following to client.conf
client pfsense {
    ipaddr = 192.168.0.1
    secret = ballpen
}

nvim users

#add the following to users
"dinowarrior" Cleartext-Password:= "password"
```

## start server

start server with command below, this will consume a terminal buffer, best to use docker for this

```bash
radius -X # debug mode
radius # production mode
```

## run freeradius

```bash
# to start
radiusd

# run on boot
rc-update add radiusd default

# to reset radiusd
rc-service radiusd restart

# to check status
rc-status
```
