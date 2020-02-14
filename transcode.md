---
layout: docs
title: Setting up transcoding binaries
permalink: /docs/transcode/
---
Transcoders are used by Airsonic to convert media from their on disk format to a format that can be consumed by clients. This is done not only for compatibility but also to save bandwidth when dealing with heavier file types. For example, although your library might use the flac format, bandwidth can be saved by converting to mp3 before transmission.

#### Install the transcoder

##### On Debian 9

Install ffmpeg package:

```
sudo apt install ffmpeg
```

Create a `transcode` directory within your `AIRSONIC_HOME` directory:

```
mkdir /var/airsonic/transcode
```

Within the `transcode` directory symlink to ffmpeg and verify correct permissions:

```
cd transcode/
ln -s /usr/bin/ffmpeg
chown -h user:user ffmpeg
ls -alh
```
```
lrwxrwxrwx 1 user user   15 mai    4 19:57 ffmpeg -> /usr/bin/ffmpeg
```

> **NOTE**:  `user` has to be the user that runs Airsonic

##### On Debian 8

Open your `/etc/apt/source.list`:

```
sudo nano /etc/apt/source.list
```

Add the backports repo to it:

```
deb http://ftp.fr.debian.org/debian/ jessie-backports main contrib
```

Update your package list:

```
sudo apt-get update
```

Install ffmpeg package from jessie-backports:

```
sudo apt-get install ffmpeg -t jessie-backports
```

Create a `transcode` directory within your `AIRSONIC_HOME` directory:

```
mkdir /var/airsonic/transcode
```

Within the `transcode` directory symlink to ffmpeg and verify correct permissions:

```
cd transcode/
ln -s /usr/bin/ffmpeg
chown -h user:user ffmpeg
ls -alh
```
```
lrwxrwxrwx 1 user user   15 mai    4 19:57 ffmpeg -> /usr/bin/ffmpeg
```

> **NOTE**:  `user` has to be the user that runs Airsonic

##### On Ubuntu > 16.04

Install ffmpeg package:

```
sudo apt-get install ffmpeg
```

Create a `transcode` directory within your `AIRSONIC_HOME` directory:

```
mkdir /var/airsonic/transcode
```

Within the `transcode` directory symlink to ffmpeg and verify correct permissions:

```
cd transcode/
ln -s /usr/bin/ffmpeg
chown -h user:user ffmpeg
ls -alh
```
```
lrwxrwxrwx 1 user user   15 mai    4 19:57 ffmpeg -> /usr/bin/ffmpeg
```
> **NOTE**:  `user` has to be the user that runs Airsonic

##### On Red Hat / Fedora

Install ffmpeg package:

```
sudo yum install ffmpeg
```

Create a `transcode` directory within your `AIRSONIC_HOME` directory:

```
mkdir /var/airsonic/transcode
```

Within the `transcode` directory symlink to ffmpeg and verify correct permissions:

```
cd transcode/
ln -s /usr/bin/ffmpeg
chown -h user:user ffmpeg
ls -alh
```
```
lrwxrwxrwx 1 user user   15 mai    4 19:57 ffmpeg -> /usr/bin/ffmpeg
```
> **NOTE**:  `user` has to be the user that runs Airsonic

##### On FreeBSD or FreeNAS

If you want transcoding and DON'T need mp3 support:

```
pkg install ffmpeg
ln -s /usr/local/bin/ffmpeg /var/airsonic/transcode/ffmpeg
service tomcat85 restart
```

Congratulations, you have transcoding enabled! 

Opus codec offers better reproduction at lower bitrates than mp3. Follow the Opus transcode guide for more information. 

[FreeBSD Transcoding with ogg/Opus](/docs/install/example/freebsd-freenas#configure-opus-transcoding)

If you need mp3 support for transcoding your music library, the process is more arduous 
as FreeBSD's ffmpeg doesn't contain mp3 support by default and must be configured and 
compiled by the user. Please see the full FreeBSD install guide for instructions on a user-friendly, lame-enabled, 
and relatively clean build + install process. 

[FreeBSD Transcoding with MP3 support](/docs/install/example/freebsd-freenas#transcoding-setup)

##### On Windows

Get the ffmpeg package from the project [download page](https://ffmpeg.zeranoe.com/builds/).

Unpack the files into the `AIRSONIC_HOME/transcode/` folder.

##### On MacOS

You can install ffmpeg binaries on MacOS using `Homebrew`:

```
brew install ffmpeg
```

Create a `transcode` directory within your `AIRSONIC_HOME` directory:

```
mkdir /var/airsonic/transcode
```

Within the `transcode` directory symlink to ffmpeg and verify correct permissions:

```
cd transcode/
ln -s "$(brew --prefix)/bin/ffmpeg"
chown -h user:user ffmpeg
ls -alh
```
```
lrwxrwxrwx 1 user user   15 mai    4 19:57 ffmpeg -> /usr/bin/ffmpeg
```
> **NOTE**:  `user` has to be the user that runs Airsonic
