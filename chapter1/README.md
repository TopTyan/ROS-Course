
Build an image  

"""
docker build -t chapter1_image .
"""  

Run an image  (linux)

"""
# Allow root access to X server
xhost +local:root

# Run the container
docker run -it \
  --name chapter1_container \
  --net=host \
  -e DISPLAY=$DISPLAY \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  chapter1_image

"""  

Run turtlesim

"""
ros2 run turtlesim turtlesim_node
"""


Run another terminal in the same container
"""
docker exec -it chapter1_container bash

"""