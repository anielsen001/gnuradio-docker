Inspired by https://github.com/git-artes/docker-gnuradio

There are different versions here: 
- vanilla - generic gnuradio with no other additions
- limesdr - addition of LimeSDR tools
## build

To build the container:
```bash
docker-compose -f docker-compose.yml build develop
```

## run

To run the container:
```bash
docker-compose -f docker-compose.yml run develop
```

This will drop you into a bash shell in the container, GUIs should work, start the gnuradio companion
```bash
gnuradio@464a6020e4fe:~$ gnuradio-companion 
```

