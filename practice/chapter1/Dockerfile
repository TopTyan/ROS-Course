# Use official ROS 2 Humble base image
FROM ros:humble

# Install required packages
RUN apt update && apt install -y \
    ros-humble-turtlesim \
    ros-humble-rqt \
    ros-humble-rqt-common-plugins \
    x11-apps \
    libxcb-xinerama0 \
    libxcb-xinerama0-dev\
    && rm -rf /var/lib/apt/lists/*

# Source ROS 2 setup
SHELL ["/bin/bash", "-c"]
RUN echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc

# Default command (can be overridden)
CMD ["bash"]
