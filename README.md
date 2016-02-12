# docker-scenic

[Scénic](https://github.com/sat-metalab/SCENIC/wiki) is a software platform compatible with various data streams and formats: video, audio, OSC controls, MIDI, data... These data streams are several sources of data that can be reformatted and then exchanged in real time with one or several distant Scénic stations.

Switcher, Scénic’s engine, has a modular architecture that is compatible with numerous data formats or third-party technologies such as "JACK audio connexion kit", "Syphon", and the "shmdata" library that allows sharing of data with software such as Blender. Scenic is available for Linux and will soon be available for Mac OS.

### Usage

To run it:

```
$ xhost +
$ docker run -d \
  -e DISPLAY="${DISPLAY}" \
  -p "0.0.0.0:5060:5060/tcp" \
  -p "0.0.0.0:5060:5060/udp" \
  -p "0.0.0.0:8000:8000/tcp" \
  -p "0.0.0.0:9000:9000/tcp" \
  -v "/dev/video0:/dev/video0:rw" \
  -v "/run/user/$(id -u)/pulse:/run/pulse:ro" \
  -v "/tmp/.X11-unix:/tmp/.X11-unix:ro" \
  --privileged \
  oriaks/scenic
```

To access the graphical user interface, point your web browser to http://localhost:8000.
