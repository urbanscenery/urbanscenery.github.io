---
layout: post
title: EC2 인스턴스 표준시간대 변경
categories: [server]
tags: [aws, linux]
---

**EC2 상에서 moment()를 사용해 현재시간을 표현하면 UTC표준시간(영국시간)으로 찍힙니다. 이를 한국시간으로 제대로 표시하기 위해 EC2의 시간대를 변경해주어야 합니다.**



### 0. 잘못된 표준시간대 확인

```shell
date
```

터미널로 ec2에 접속해 date 명령어로 현재 표준시간대를 확인합니다. 

만약 정상적으로 KST 시간대가 찍힌다면 굳이 변경하지 않아도 됩니다. 

![](https://urbanscenery.github.io/assets/0108/before.png){:height="50%" width="50%"}



### 1. 표준시간대 파일 찾기

1. 원하는 표준시간대를 찾기 위해 먼저 전체 시간대 탐색

```shell
ls /usr/share/zoneinfo
```

2. 서울이 Asia에 있으므로 Asia폴더를 다시 탐색

```shell
ls /usr/share/zoneinfo/Asia
```



#### 결과

![](https://urbanscenery.github.io/assets/0108/ec2timezone.png)

### /usr/share/zoneinfo/Asia/Seoul 이 있는것을 확인 가능합니다.



### 2. localtime을 원하는 시간대로 변경하기

```shell
sudo ln -sf /usr/share/zoneinfo/Asia/Seoul /etc/localtime
```

/etc/localtime 파일에 /usr/share/zoneinfo/Asia/Seoul 파일을 링킹



### 3. ubuntu 재부팅

```shell
sudo reboot
```

재부팅 이후 자동으로 터미널이 종료됩니다. 재부팅하는데 걸리는 5~10분후 재접속하면 표준시간대가 변경되어있습니다.



### 4. 바뀐 표준시간대 확인

```shell
date
```

![](https://urbanscenery.github.io/assets/0108/after.png){:height="50%" width="50%"}



