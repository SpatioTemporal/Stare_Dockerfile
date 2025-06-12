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
### 0. Create a Docker Hub account (if you don't have one)
- Go to: https://hub.docker.com and sign up a new account
- Login with docker from command line: 
```shell
docker login
# You’ll see something likes:
#  Opening login URL in your browser...
#   If the browser didn't open, visit: https://identity.docker.com/...
#   And enter the code: ABCD-EFGH
# Follow the link, login with your docker account, enter the code. Then CLI will print Login Succeeded
```

### 1. Build the image
```shell
docker build -f Dockerfile.MacOS -t stare-env-m1:latest .
```
### 2. Start a shell inside the container
```shell
docker run -it stare-env-m1:latest /bin/bash
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
docker run -d --name stare-test-m1 -it stare-env-m1:latest /bin/bash

# Check that it's running:
docker ps

# Attach to it (opens an interactive shell):
docker exec -it stare-test-m1 /bin/bash
```