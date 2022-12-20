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

### Memo
- ssh root로 해야 함
- portname 7777 인지 22 인지는 container 안에서 확인
- TODO
  - zsh설치 & custom 커맨트
  - tmux 설치 커맨드
