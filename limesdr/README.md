Build a docker container for a LimeSDR Mini running on a Raspberry Pi 3B+.

This runs the container in privileged mode so that the USB devices work. 

Build the container:
```bash
docker-compose -f docker-compose.yml build develop
```

Run the container:
```bash
docker-compose -f docker-compose.yml run develop
```

Tag and push the container to docker hub:
```bash
docker tag arm32v7/gnuradio3.8/limesdr:develop anielsen/gnuradio:arm32v7-gnuradio3.8-limesdr
docker push anielsen/gnuradio:arm32v7-gnuradio3.8-limesdr
```