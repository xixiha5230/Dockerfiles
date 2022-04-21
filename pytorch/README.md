# 功能
`apt&pip`清华源、`pytorch`、`conda`、`cuda`、`git`、`ssh`、`mujoco`， root密码是`xixiha`，python包在requirements.txt中添加

# display
dockerfile中的 `export DISPLAY=unix:0` 其中 `:0` 通过host `echo $DISPLAY` 获得，host记得输入`xhost +`允许外部访问xserver

# build
`sudo docker build -t xixiha/pytorch:v1 .`

# run:
```shell
sudo docker run --privileged --gpus all -p 2222:22 \
-v /home/xixiha/Programs:/root/Programs \
-v /tmp/.X11-unix:/tmp/.X11-unix \
-e GDK_DPI_SCALE \
-d xixiha/pytorch:v1
```
