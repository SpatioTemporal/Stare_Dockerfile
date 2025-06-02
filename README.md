# I. Build dockerfile on Ubuntu
### 1. Build the image
```shell
docker build -f Dockerfile.Ubuntu -t stare-env:latest .
```
### 2. Start a shell inside the container
```shell
docker run -it stare-env:latest /bin/bash
```
### 3. Check all installations:
```shell
# Check pystare and starepandas
python -c "import pystare, starepandas; print(pystare.__version__, starepandas.__version__)"

# Or list all conda packages
conda list

# Or list all pip packages
pip list
```
### 4. Exit the shell (the container will stop).
```shell
exit
```
### 5. (Optional) If you want to leave it running and then attach later, you can do
```shell
# Start a container in the background (named "stare-test") and drop into bash:
docker run -d --name stare-test -it stare-env:latest /bin/bash

# Check that it's running:
docker ps

# Attach to it (opens an interactive shell):
docker exec -it stare-test /bin/bash
```

# II. Build dockerfile on MacOS (M1 -- ARM64)
