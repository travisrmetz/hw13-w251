##W251 - HW 13
###Travis R. Metz
####July 2020

```docker build -t inf -f Dockerfile.inf .```

```xhost +```

```docker run --rm --privileged -v /tmp:/tmp -v /data:/data -v /var:/var -v /home/nvidia/models:/models -v /home/trmetz/hw13-w251:/hw13 --net=host --ipc=host --env DISPLAY=$DISPLAY -ti inf bash```

####could not get Dockerfile to properly uninstall pillow 7 so had to run this in container after starting
pip3 install pillow==6.1

python3 python/training/classification/train.py --model-dir=plants //hw13/datasets/PlantCLEF_Subset
