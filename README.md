# pm2-windows-service

Allows easily installing and uninstalling [PM2](https://github.com/Unitech/PM2/) as a service on Windows machines - forked from [pm2-windows-service](https://github.com/jon-hall/pm2-windows-service).

```sh
  npm i @davistran86/pm2-windows-service -g
```

## Documentation

See original documentation at [pm2-windows-service](https://github.com/jon-hall/pm2-windows-service)

## Installation

**NOTE:** Run these from an administrative command prompt to avoid getting hit with a bunch of UAC dialogs

### NPM config

```
npm config ls -l
```

### PM2

If you aleady have pm2 running and saved processes by using `pm2 save` then you can check it's location by using `pm2 resurrect`.

You can see something like this in console:

```
...[PM2] Restoring processes located in C:\pm2\.pm2\dump.pm2
```

You should use `C:\pm2\.pm2` as your PM2_HOME

**NOTE:** If you are running pm2 as another user, you should put it in a location which is available to all users.

### Prerequisites

- Add and set **PM2_HOME** in System environments (not user environments). Like: `PM2_HOME = C:\pm2\.pm2` as above
- Add `C:\pm2\.pm2` to the existing system PATH variable (Then you are sure it will work - there has been some issues reported that PM2_HOME not always working).

### Install

```
npm install pm2 -g
npm i pm2-windows-service -g
```

### Setup

```
pm2-service-install -n ANY_NAME_HERE
```

ANY_NAME_HERE will be the "Display name" of the Windows service

Now set the following config:

```
Perform environment setup (recommended)? -> Yes
Set PM2_HOME? -> No
Set PM2_SERVICE_SCRIPTS (the list of start-up scripts for pm2)? -> Yes
Set the list of startup scripts/files (semi-colon separated json config files or js files) -> ENTER (it will default to use PM2's dump.pm2 file - which is created when you run PM2 -f save)
Set PM2_SERVICE_PM2_DIR (the location of the global pm2 to use with the service)? --> Yes
Specify the directory containing the pm2 version to be used by the service? ENTER
```

### Run as another user

Open Windows Services, find PM2 services (ANY_NAME_HERE), go to its Log On tab, choose This account and input your account there.

### Uninstall

```
pm2-service-uninstall
```
