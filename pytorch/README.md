# build

`sudo docker build -t xixiha/pytorch:v1 .`

# run:

```shell
sudo docker run --gpus all -p 2222:22 \
-v /home/xixiha/Programs:/root/Programs \
-v /tmp/.X11-unix:/tmp/.X11-unix \
-e GDK_DPI_SCALE \
-d xixiha/pytorch:v1
```
