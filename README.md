# dockers
Automatically sets environment I prefer on given docker

### Requirements
Updated : install Docker and nvidia-driver.

Then follow the instructions in [nvidia-docker](https://github.com/NVIDIA/nvidia-docker)

Refer to [nvidia-docker Usage](https://github.com/NVIDIA/nvidia-docker#usage) for parameters `[GPUS]`

### Instructions
```
cd [DOCKER_YOU_WANT]

docker build -t [IMAGE_NAME] .

docker run --ipc=host -p [HOST_PORT_NAME_FOR_DOCKER]:7777 --name=[CONTAINER_NAME] --gpus [GPUS] -v [HOST_DATA_PATH]:/data -v [HOST_CODE_PATH]:/workspace  -dit [IMAGE_NAME]
```

for example,
```
cd pytorch

docker build -t torch120 .

docker run --ipc=host -p [HOST_PORT_NAME_FOR_DOCKER]:7777 --name=test_torch --gpus 2 -v /hdd/data:/data -v /home/user:/workspace -dit torch120
```

docker run --ipc=host -p 10001:22 -p 10002:6006 -p 10003:8888 --name=jonghomusic --gpus all -v /root/jongho:/workspace -v /data1/intern_jongho:/data1 -v /data2:/data2 -dit torch2103_ssh

### Memo
- ssh root로 해야 함
- portname 7777 인지 22 인지는 container 안에서 확인
- TODO
  - zsh설치 & custom 커맨트
  - tmux 설치 커맨드
