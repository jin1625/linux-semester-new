# Week 2 - Miniconda + JupyterLab 환경 구축

## 1. 이번 주 목표
- 리눅스 환경에 Miniconda 설치
- mamba를 이용한 빠른 패키지/환경 관리
- JupyterLab 설치 및 실행
- 기본적인 ML 코드 실행 환경 구축

## 2. 설치/환경 구성
- VirtualBox Ubuntu 환경
- Anaconda GUI 설치 → 용량 부족으로 실패
- VDI 용량 확장 후 파티션 재설정
- Miniconda 다운로드 후 터미널 기반 설치
- mamba 설치로 패키지 설치 속도 향상

```bash
bash Miniconda3-latest-Linux-x86_64.sh
conda install mamba -n base -c conda-forge
mamba create -n ds python=3.11
mamba install numpy matplotlib scikit-learn
jupyter lab
```

## 3. 실습 과정
- numpy, matplotlib 설치
- JupyterLab 실행
- 선형회귀, Perceptron, MLP 실습 수행
- 윈도우 대비 설치·연산 속도 더 빠름

## 4. 문제 & 해결
- 한글 폰트 깨짐 → 폰트 설치로 해결
- 경로 대소문자 문제 → 정확한 경로 사용

## 5. 리눅스 사용 소감
- mamba+conda-forge 조합으로 매우 빠름
- ML 학습 속도 윈도우 대비 개선
- DS 환경 구축에 리눅스가 더 적합함
