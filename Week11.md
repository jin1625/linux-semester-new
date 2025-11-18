# Week 11 - DuckDB 및 Joblib 실습 (CSV SQL 분석 + 모델 저장/로드)

---

## 1. DuckDB로 CSV 데이터 SQL 분석

이번주는 DuckDB를 설치하여 CSV파일을 SQL로 분석하여 보았습니다.

DuckDB는 PostgreSQL처럼 서버를 켜지 않고 파일위에서 바로 SQL을 이용하여 분석할 수 있는 DB 입니다.  
즉, CSV 파일을 테이블처럼 취급해 SQL을 바로 실행할 수 있습니다.

### ✔ DuckDB 환경 구성
duckdb, pandas, scikit-learn을 설치하였습니다.

```bash
pip install duckdb pandas scikit-learn
```

### ✔ CSV 파일 생성
- Diabetes 데이터를 pandas DataFrame으로 변환 후  
- `diabetes.csv` 파일로 저장하는 Python 코드를 작성하여 실행했습니다.

### ✔ DuckDB로 SQL 분석
DuckDB에서 CSV를 직접 불러와 SQL 실행:

- 당뇨 진행도 평균
- 최댓값, 최솟값
- BMI 상위 5명 조회

### ✔ Pandas vs DuckDB 속도 비교
| 비교 | Pandas | DuckDB |
|------|--------|--------|
| 로딩 방식 | CSV 전체 메모리 적재 | CSV에서 직접 SQL 처리 |
| 연산 방식 | Python 기반 | C++ 엔진 기반 |
| 대용량 처리 | 느려짐 | 매우 빠름 |

→ 적은 데이터에서는 차이가 적지만, **데이터가 커질수록 DuckDB가 분명 더 유리함**

### ✔ DuckDB 리눅스 사용 소감
- pip 한 줄로 즉시 설치 가능  
- 서버가 필요 없어서 매우 간편  
- VM 환경에서도 가볍고 빠르게 실행됨  
- 파일 단위 분석용으로 매우 적합하다고 느꼈음

---

## 2. Joblib으로 머신러닝 모델 저장/로드

이번주에는 joblib를 사용하여 ML 모델을 파일로 저장하고 다시 불러와 예측까지 해보았습니다.  
Joblib은 ML 모델을 빠르게 저장/로드하고, 큰 numpy 객체도 안정적으로 다룰 수 있는 라이브러리입니다.

### ✔ 라이브러리 설치
```bash
pip install joblib scikit-learn
```

### ✔ ① train_and_save.py (모델 학습 후 저장)
- diabetes dataset 로드  
- Train/Test = 80% / 20% 분리  
- 선형회귀 모델 학습  
- joblib으로 `.pkl` 파일로 저장

```python
joblib.dump(model, "linear_model.pkl")
```

### ✔ ② load_and_predict.py (저장된 모델 로드 후 예측)
- 저장된 모델 다시 로딩

```python
model = joblib.load("linear_model.pkl")
```

- 예측 수행 후 출력  
- 학습 → 저장 → 로드 → 예측 플로우 전체 실습 완료

### ✔ ③ 여러 모델 중 가장 좋은 모델만 자동 저장
- Linear Regression  
- Ridge Regression(L2 규제)  
- RandomForestRegressor  

각각 MSE 계산 후 **가장 성능 좋은 모델만 저장**

```python
best_model = models[best_name]
joblib.dump(best_model, "best_model.pkl")
```

### ✔ Joblib 리눅스 사용 소감
- 대형 배열 기반 모델도 빠르게 저장/로드  
- 모델 배포·실험 관리에 매우 유용  
- 리눅스 환경에서의 file I/O 속도가 빨라 더 안정적  