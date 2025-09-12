# Chapter 1 — ROS 2 Humble + Docker + GUI

## Build the Docker image
```bash
docker build -t chapter1_image .
```
## Run the container (Windows)
```
docker run -it --rm --name chapter1_container -e DISPLAY=host.docker.internal:0.0 chapter1_image
```

## Run the container (Linux)
Before running, allow Docker containers to connect to your X server so GUI apps like `rqt` and `turtlesim` can open:
```bash
xhost +local:root
```
Then start the container:
```bash
docker run -it \
  --name chapter1_container \
  --net=host \
  -e DISPLAY=$DISPLAY \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  chapter1_image
```
**Notes:**  
- `--name chapter1_container` gives the container a fixed name so you can easily open more terminals into it later.  
- `--net=host` simplifies networking for ROS 2 nodes.  
- `-v /tmp/.X11-unix:/tmp/.X11-unix` mounts the X11 socket for GUI forwarding.

## Run turtlesim
Inside the container:
```bash
ros2 run turtlesim turtlesim_node
```

## Open another terminal in the same container
From your host, in a new terminal:
```bash
docker exec -it chapter1_container bash
```
Then source ROS 2 in the new shell:
```bash
source /opt/ros/humble/setup.bash
```
