## W251 - HW 13
### Travis R. Metz
#### July 2020

Training was done on batch size of 8 due to memory limitations.
After 100 epochs, acc1 =55.154, acc5=84.758 (on validation set)
100 epochs took ~355 seconds each for 35,500 seconds, or 592 minutes, or almost 10 hours




#### Container commands

```docker build -t inf -f Dockerfile.inf .```

```xhost +```

```docker run --rm --privileged -v /tmp:/tmp -v /data:/data -v /var:/var -v /home/nvidia/models:/models -v /home/trmetz/hw13-w251:/hw13 --net=host --ipc=host --env DISPLAY=$DISPLAY -ti inf bash```

#### Training commands
Could not get Dockerfile to properly uninstall pillow 7 so had to run this in container after starting:
```pip3 install pillow==6.1```

Originally started training
```python3 python/training/classification/train.py --model-dir=plants //hw13/datasets/PlantCLEF_Subset```

Had to restart training when it automatically stopped at 35 epochs
```python3 python/training/classification/train.py --start-epoch 35 --epochs 100 --resume plants/checkpoint.pth.tar --model-dir=plants /hw13/datasets/PlantCLEF_Subset```

#### Model export commands
```python3 python/training/classification/onnx_export.py --model-dir=plants```

