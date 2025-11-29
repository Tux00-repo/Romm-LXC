Romm LXC Container

A lightweight Linux Container (LXC) setup for running Romm - your personal media metadata manager.
Prerequisites

    LXC installed on your system

    distrobuilder tool

    Sufficient disk space and memory

Installation
#1. Download distrobuilder

```
# On Ubuntu/Debian
sudo apt update
sudo apt install distrobuilder

# On Alpine Linux
sudo apk add distrobuilder

# On other distributions, you can build from source:
git clone https://github.com/lxc/distrobuilder.git
cd distrobuilder
make
sudo make install
```
#2. Build the LXC Container
Build the container using the provided definition file
```
distrobuilder build-lxc RommLCX.yaml output-folder
```

Example:
```
distrobuilder build-lxc RommLCX.yaml /path/to/romm-container
```
This will create a container root filesystem and metadata in the specified output folder.

#3. Move RootFS to LXC Templates

Copy the rootfs to LXC templates directory
```
sudo cp output-folder/rootfs.tar.xz /usr/share/lxc/templates/romm.tar.xz
```
#4. Create Symbolic Links

The container expects the following directory structure with symbolic links:

```

├── assets -> /app/romm/assets
├── config -> /app/romm/config  
├── library -> /app/romm/library
└── resources -> /app/romm/resources
```

#5. Environment Configuration

You must create and configure /app/.env with your specific environment variables.
You must create /app/romm/config/config.yaml with your Romm configuration.

# TODO & Next Steps

Create setup for config.
