### Installing YouTube downloader

Run
```
sudo apt-get install youtube-dl
```
to install command line mode downloader for YouTube.

Then run
```
youtube-dl (YouTube-or-other-website-video-link)
```

this will download the default video format.

```
youtube-dl -F (YouTube-or-other-website-video-link)
```
this will list all teh video formats and the number prefix to use when downloading

the prefix number can be used this way

```
youtube-dl -f (prefix -number) (YouTube-or-other-website-video-link)
```
**The video/audio will be saved in the home folder**
**keep in mind, that youtube-dl is able to download from many other sites too**

you just need the link