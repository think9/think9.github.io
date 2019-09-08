---
layout: post
title: 아나콘다 명령어
subtitle: Anaconda Prompt Shortcut
published: true
---

## 아나콘다 콘솔 명령어
<br>

### 아나콘다 버전 조회
```
conda -- version
```

![version](https://user-images.githubusercontent.com/50393277/64470414-d1a6d680-d17d-11e9-9a18-ab8e6bdbc6aa.png)

<br>

### 아나콘다 업데이트
```
conda update conda
```

![update](https://user-images.githubusercontent.com/50393277/64470512-1aab5a80-d17f-11e9-8b48-c8319d535283.png)\

<br>

### 모든 가상환경 조회
```
conda env list
```

![env](https://user-images.githubusercontent.com/50393277/64470456-061a9280-d17e-11e9-9726-94323d455b82.png)

<br>

### 새로운 가상환경 생성
```
conda create --name (이름) python=(파이썬 버전)
```

![create](https://user-images.githubusercontent.com/50393277/64470567-35ca9a00-d180-11e9-934a-68d75da3881c.png)

생성 후 아래 부분을 살펴보면

![create2](https://user-images.githubusercontent.com/50393277/64470575-572b8600-d180-11e9-9105-6d3cd4a2c562.png)

새로 생성 된 가상환경을 사용하고 싶다면 activate 명령어를,

현재 동작하는 가상환경을 비활성화 시키려면 deactivate 명령어를 사용하라는 메시지가 출력된 것을 확인할 수 있다.

<br>

### 가상환경 활성화
```
activate / deactivate (가상환경 이름)
```

![activate](https://user-images.githubusercontent.com/50393277/64470589-9eb21200-d180-11e9-9711-1671b01b2240.png)

<br>

### 가상환경 삭제
```
conda remove --name (가상환경 이름) -all
```

![remove](https://user-images.githubusercontent.com/50393277/64470641-c655aa00-d181-11e9-9881-98bf113c4a24.png)

<br>

### 가상환경 패키지 설치
```
conda install (패키지 이름)
```

![install](https://user-images.githubusercontent.com/50393277/64470731-6e1fa780-d183-11e9-9e7e-92125d509085.png)

<br>

### 설치되어 있는 패키지 조회
```
conda list
```

![list](https://user-images.githubusercontent.com/50393277/64470819-441ab500-d184-11e9-8e28-35b990fd5a8e.png)

<br>

