---
layout: post
title: Django_가상환경설정
categories: [server]
tags: [python, piro]
---



## Django_가상환경 설정

파이썬에서는 프로젝트당 패키지를 설치해서 사용하는 것이 아닌 하나의 머신단위로 패키지를 설치해서 사용하게 됩니다.

다수의 프로젝트에서 각 프로젝트당 사용하는 패키지의 버전이 다를 수 있고 이런 상황에서 각 프로젝트를 실행시키기 위해서는 기존에 설치된 패키지를 지운 후 맞는 버전으로 다시 설치해야하는 번거로운 일이 발생합니다. 

따라서 파이썬을 개발할 때 여러 버전의 패키지를 사용하기 위해 각 프로젝트에 맞는 가상환경을 생성해 해당 환경에 패키지를 설치한 후 사용합니다.



###  1.virtualenv, virtualenvwrapper 설치

Python3 기준으로 pip3 명령어 사용해 virtualenv, virtualenvwrapper를 설치합니다.

```shell
pip3 install virtualenv virtualenvwrapper
```



### 2. virtualenvwrapper 환경변수 설정

virturalenvwrapper는 환경변수에 WORKON_HOME이 지정되어 있을 경우 해당 경로에 가상환경을 만들고 workon 명령어를 사용시 WORKON_HOME이 지정된 경로에서 검색합니다. 따라서 WORKON_HOME 경로를 설정하도록 합니다. 



(MAC, Linux 기준)

터미널에서 ~/dev/.virtualenvs 폴더를 만든 후 .bash_profile 파일에 WORKON_HOME 경로를 ~/dev/.virtualenvs 로 설정합니다.

```shell
mkdir ~/dev/.virtualenvs
echo export WORKON_HOME=~/dev/.virtualenvs >> ~/.bash_profile
```



### 3. virtualenvwrapper가 사용할 python 경로 설정

먼저 파이썬이 설치된 경로를 찾아줍니다. 

virtualenvwrapper을 사용할 때 python3 를 사용할 것이므로 python3 의 설치경로를 찾아 설정하도록 하겠습니다. 

```shell
which python3
```



![](https://urbanscenery.github.io/assets/0115/0115_pythonpath.png)

python3의 경로가 /usr/local/bin/python3 로 확인되었으므로 해당경로를 .bash_profile 파일에 추가합니다.

```shell
echo export VIRTUALENVWRAPPER_PYTHON=/usr/local/bin/python3 >> ~/.bash_profile
```



### 4. virtualenvwrapper 명령어 등록

virtualenvwrapper.sh 파일에 virtualenvwrapper에 관련된 모든 설정들이 들어가 있으므로 터미널이 실행될 때 해당 파일을 설정할 수 있도록 ./bash_profile 파일에 추가해줍니다. 

먼저 virtualenvwrapper.sh의 경로를 찾습니다. 루트폴더에서 찾아야 하므로 sudo 명령어를 사용합니다.

```shell
sudo find / -name 'virtualenvwrapper.sh'
```

![](https://urbanscenery.github.io/assets/0115/0115_virtualenvwrappershpath.png)

/Library/Frameworks/Python.framework/Versions/3.6/bin/virtualenvwrapper.sh 로 경로를 확인하였으므로 이를 .bash_profile 파일에 추가합니다.

```shell
echo source /Library/Frameworks/Python.framework/Versions/3.6/bin/virtualenvwrapper.sh >> ~/.bash_profile
```



### 5. .bash_profile 적용

터미널을 닫은후 새로운 터미널을 열거나 다음 명령어를 통해 작업하던 터미널에서 .bash_profile 을 적용합니다

```shell
source ~/.bash_profile
```



### 6. virtualenvwrapper 명령어

> #### 1. 가상환경 만들기

```shell
mkvirtualenv 가상환경이름
```

![](https://urbanscenery.github.io/assets/0115/0115_mkvirtualenv.png)

**mkvirtualenv** 명령어를 사용해 blog 이름으로 가상환경을 만든후 바로 해당가상환경으로 진입하는 것을 볼 수 있습니다. 

가상환경에 진입시 앞에 (가상환경이름)이 붙습니다.



> #### 2. 가상환경 빠져나오기

```shell
deactivate
```

![](https://urbanscenery.github.io/assets/0115/0115_deactivate.png)

**deactivate** 명령어로 blog 가상환경에서 빠져나온 것을 확인할 수 있습니다.

> #### 3. 가상환경 목록 확인하기

```shell
workon
```

![](https://urbanscenery.github.io/assets/0115/0115_workon.png)

**workon** 명령어를 아무 옵션없이 사용할 시 생성된 가상환경의 목록을 확인할 수 있습니다. 

생성된 가상환경에 접근하기 위해서는 설정된 WORKON_HOME의 경로를 찾아가시면 됩니다. 

제가 WORKON_HOME의 경로로 설정한 ~/dev/.virtualenvs 에 접근시 생성한 가상환경인 blog와 piro 디렉토리가 존재하는것을 확인할 수 있습니다.



> #### 4. 가상환경 진입하기

```shell
workon 가상환경이름
```

![](https://urbanscenery.github.io/assets/0115/0115_workon2.png)

**workon** 명령어 뒤에 가상환경 이름을 붙일 시 해당 가상환경으로 진입해 작업할 수 있습니다.



> #### 5. 가상환경 삭제하기

```shell
rmvirtualenv 가상환경이름
```

![](https://urbanscenery.github.io/assets/0115/0115_rmvirtualenv.png)

> **rmvirtualenv** 명령어를 사용해 가상환경을 삭제할 수 있습니다.



