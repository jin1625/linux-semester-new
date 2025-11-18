# Week 12 - Joblib 모델 저장 & 로드 심화 실습

이번주는 joblib 사용을 확장하여,
- 여러 종류의 모델을 학습시키고
- 가장 성능이 좋은 모델을 자동으로 선택해 저장하고
- 다시 불러와 예측하는 작업까지 수행했습니다.

## 1. 설치 / 환경 구성
```bash
pip install joblib scikit-learn
```

## 2. 실습 과정

### ✔ 다양한 모델 학습
- 선형회귀 (LinearRegression)
- L2 규제 회귀(Ridge)
- RandomForestRegressor  
모델들을 모두 학습시키고 MSE 계산을 통해 비교하였습니다.

### ✔ 모델 저장
학습된 모델을 joblib로 `.pkl` 형태로 저장:

```python
joblib.dump(model, "model_name.pkl")
```

### ✔ 모델 로드
저장된 모델을 다시 로딩하여 바로 예측 수행:

```python
loaded = joblib.load("model_name.pkl")
pred = loaded.predict(X_test)
```

### ✔ 최고의 모델 자동 선택
- 여러 모델을 딕셔너리 형태로 관리  
- MSE 기준으로 가장 성능 좋은 모델 선택  
- `best_model.pkl`로 저장하여 재사용 가능하도록 구성

### ✔ 실습 요약
- joblib의 단순하고 빠른 저장/로드 기능 확인  
- ML 파이프라인을 반복 실험하는 데 매우 적합  
- 모델 재사용 구조를 확실히 익힌 주차

## 3. 리눅스 사용 소감
- 파일 저장/로드 속도 빠르고 안정적  
- 파이썬 기반 작업과 최적의 궁합  
- 머신러닝 모델 관리·배포 파이프라인 구성에 매우 유용하다고 느낌  