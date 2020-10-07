1. build image
```bash
docker build -t moveit:deep-grasp -f docker/Dockerfile.cpu .
```

2. run container
```bash
docker run -it --rm --privileged -v /tmp/.X11-unix:/tmp/.X11-unix:rw -v /tmp/.docker.xauth:/tmp/.docker.xauth:rw \
    -v /dev/bus/usb:/dev/bus/usb -v /dev:/dev:rw -e XAUTHORITY=/tmp/.docker.xauth -e DISPLAY --name deep_grasp moveit:deep-grasp bash
```
- set volume to source code
```bash
cd deep_grasp_demo
docker run -it --rm --privileged -v /tmp/.X11-unix:/tmp/.X11-unix:rw -v /tmp/.docker.xauth:/tmp/.docker.xauth:rw \
    -v /dev/bus/usb:/dev/bus/usb -v /dev:/dev:rw -v $(pwd):/root/ros_ws/src/deep_grasp:rw \
    -e XAUTHORITY=/tmp/.docker.xauth -e DISPLAY --name deep_grasp moveit:deep-grasp bash
```
