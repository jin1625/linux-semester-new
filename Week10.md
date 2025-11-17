
# Week 10 - Streamlit으로 ML 웹앱 제작

## 1. 이번 주 목표
- Streamlit 설치
- ML 모델 기반 웹앱 만들기

## 2. 설치 / 환경 구성
```bash
pip install streamlit
```

앱 실행:
```bash
streamlit run app.py
```

## 3. 실습 과정
### ✔ 기본 Streamlit 앱
- 텍스트, 차트, 입력 UI 생성
- 코드만 작성해도 자동으로 웹 페이지 생성

### ✔ ML 예측 웹앱 제작
- Linear Regression 모델 학습
- 당뇨병 데이터셋 사용
- 입력값(10개의 feature)을 UI로 받음
- 버튼 클릭 → 즉시 예측 결과 출력
- 실제 vs 예측 그래프 표시

예시 코드:

```python
import streamlit as st
from sklearn.datasets import load_diabetes
from sklearn.linear_model import LinearRegression

st.title("당뇨병 진행도 예측 웹앱")

age = st.number_input("Age", value=0)
bmi = st.number_input("BMI", value=0.0)

data = load_diabetes()
X, y = data.data, data.target
model = LinearRegression()
model.fit(X, y)

if st.button("예측하기"):
    pred = model.predict([[age, bmi, 0,0,0,0,0,0,0,0]])
    st.write("예측 결과:", float(pred))
```

## 4. 문제 & 해결
- 별다른 오류 없음

## 5. 리눅스 사용 소감
- 서버형 앱을 매우 안정적으로 실행
- 코드 수정 → 새로고침 → 즉시 반영
- 웹앱 + ML 개발이 매우 쉬움