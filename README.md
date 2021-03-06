# ppo

![alt text](results/space_invaders_1.gif)

# Usage
The easiest way to run this code is in a docker container. The only requirements are [Docker](https://docs.docker.com/install/) and [nvidia-docker](https://github.com/NVIDIA/nvidia-docker).

### Option 1 - Basic Usage
Clone the repo:
```bash
git clone https://github.com/jastern33/ppo.git
cd ppo
```
Build the docker image (takes awhile): 
```bash
cd docker
docker build -t deep-learning-pytorch -f Dockerfile . --rm
```
Run a docker container based on that image: 
```bash
cd ..
nvidia-docker run -it --name ppo --rm -v $(pwd):/code deep-learning-pytorch
```
Then run the following command in the docker container for a basic demo:

`python3 ppo`

To see additional options run: 

`python3 ppo --help`

(hint: look here ^ to see how to try a new dataset!)

### Option 2 - To run the Jupyter Notebook demo:
If you want to run the jupyter notebook, it requires a couple of modifications.

Clone the repo:
```bash
git clone https://github.com/jastern33/ppo
cd ppo
```
Build the docker image (takes awhile): 
```bash
cd docker
docker build -t deep-learning-pytorch -f Dockerfile . --rm
```
Run a docker container based on that image (notice the addition of the `-p` flag for port forwarding):
```bash
cd ..
nvidia-docker run -it --name ppo --rm -p 8890:8890 -v $(pwd):/code deep-learning-pytorch
```
In the docker container, run:
```bash
jupyter notebook --ip 0.0.0.0 --port 8890 --no-browser --allow-root
```
Then copy the url that it gives you, and paste it into a browser:
```bash
http://127.0.0.1:8890/?token=<really_long_token>
```
Now you can access and run the Jupyter Notebook (which is running inside the container) as if it were running on your own machine.