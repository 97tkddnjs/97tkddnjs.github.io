---
title:  "tensorflow gpu 버전 설치하기"
excerpt: "tensorflow gpu 버전 설치를 알아보도록 하겠다!"

toc: true
toc_sticky: true
toc_label: 목차

comments : true

categories:
  - install
  
last_modified_at: 2021-03-02
---
<style>
    .tt {font-size : 16px;}
</style>


이 포스트에서는 로컬환경에서 tensorflow-gpu 버전을 설치하는 방법을 보도록 하겠다.

## 1. 먼저 어떤 버전의 텐서플로우를 설치할지 결정한다.

[windows 텐서플로우 버전확인](https://www.tensorflow.org/install/source_windows#tested_build_configurations)

![tensorflow-gpu](/assets/images/tensorflow-gpu.PNG)

그 후 pip 명령어를 통해 다운로드를 한다.

![pip](/assets/images/pip install tensorflow.PNG)

## 2. 텐서플로우 버전과 맞는 CUDA와 cuDNN을 설치한다.

설치 전 NVDIA에 회원 가입을 해야한다.

<strong>반드시 자신의 tensorflow 버전과 맞는 cuda와 cudnn으로 설치를 해야한다!</strong>

<br>[CUDA 설치 url CUDA toolkit AChive](https://developer.nvidia.com/cuda-toolkit-archive)

필자의 경우 tensorflow-gpu 2.3.0 버전을 설치하였으므로 밑에 보이는 <strong>CUDA Toolkit 10.1 update2</strong> 버전으로 설치를 하였다.

![CUDA](/assets/images/cuda.PNG)

<strong>cuda_10.1.243_426.00_win10.exe</strong> 파일을 실행하여 설치를 진행한다.

설치가 끝나면 밑에 보이는 사진과 같은 NVIDIA폴더들이 생길 것이다.
![toolkit](/assets/images/toolkit.PNG)

CUDA설치가 끝났다면 이제 CUDNN을 설치해보자!

[cuDNN 설치 url](https://developer.nvidia.com/rdp/cudnn-archive)

필자의 경우 tensorflow-gpu 2.3.0 버전을 설치하였으므로 밑에 보이는 <strong>Download cuDNN v7.6.5 (November 5th, 2019), for CUDA 10.1</strong> (Windows10)버전으로 설치를 하였다.
<br>(밑에 사진 참조)
![cudnn](/assets/images/cudnn.PNG)

<p>다운받은 cudnn파일을 압축해제를 한다. 아래 사진과 같은 결과를 확인할 수 있을 것이다.</p>

![zip](/assets/images/zip.PNG)

<p>이제 이 파일들을 전부 다 아래 보이는 경로로 전부 옮긴다.</p>

![d_path]/assets/images/)


보통 cuda를 설치하게 되면 <strong>위와 같은 경로</strong>로 폴더가 생성된다.
<strong>C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v버전</strong>

![final](/assets/images/final.PNG)

## 3. Tensorflow code 실행!
cmd 창을 열어 밑에 보이는 코드를 하나씩 입력해주면 된다!

```python
#cmd에서 한 라인씩 입력해야 한다.
import tensorflow as tf

print(tf.__version__) #버전확인
tf.test.is_built_with_cuda() #cuda로 빌드되는 지 확인 결과값 True
tf.test.is_built_with_gpu_support()#cuda와 같은 gpu로 빌드되는 지 확인 결과값 True
tf.test.gpu_device_name()#사용가능한 gpu기기들 확인

from tensorflow.python.client import device_lib
print(device_lib.list_local_devices()) #device_type에 gpu있으면 성공


```

<p>결과값 cmd 화면</p>
그림에서 오른쪽 마우스키를 눌러 <strong>새 탭에서 이미지 열어보기</strong>를 하면 자세히 보인다.
![cmd1](/assets/images/cmd1.PNG)
![cmd2](/assets/images/cmd2.PNG)