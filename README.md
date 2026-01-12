# kernel-tricks-bench

자세한 분석 결과 : report.pdf에서 확인 가능합니다.

# Nonlinear-Data-Modeling | Feature Mapping & Kernel K-Means

<img width="1612" height="586" alt="image" src="https://github.com/user-attachments/assets/0ae4fee1-2103-4c37-8a28-2fbd4c12ed1e" />


two-moons / corners 같은 **비선형 구조 데이터**에 대해,  
**지도학습(분류)** 과 **비지도학습(군집)** 대표 기법을 **NumPy만 사용해 from-scratch로 구현**하고,  
학습/추론/시각화까지 전체 파이프라인을 구성한 프로젝트입니다.

[포함된 프로젝트 (총 4개)]
- Feature Mapping + Logistic Regression (two-moons)
- Feature Mapping + Logistic Regression (corners)
- Kernelized K-Means Clustering (two-moons)
- Kernelized K-Means Clustering (corners)

---

## 주요 구현 사항

- 비선형 데이터 처리를 위한 **Feature Mapping** 구현
- **Logistic Regression** 학습 파이프라인 구현 (gradient 기반 최적화)
- **Kernelized K-Means** 구현 (kernel trick 기반)
- 시각화 구현
  - 분류: decision boundary
  - 군집: cluster assignment
  - (선택) loss / objective 변화 곡선

---

## 사용 환경

- Python 3.8+
- 필수 라이브러리:
  - `numpy`
  - `matplotlib` (시각화 용도)

> Note: 모델링에 scikit-learn 등 ML 라이브러리는 사용하지 않습니다.

---

## 1. Feature Mapping + Logistic Regression (two-moons)

- two-moons 데이터는 선형 분리가 어려운 비선형 구조를 가집니다.
- Feature Mapping을 통해 입력을 고차원 표현으로 변환한 뒤,
  Logistic Regression으로 분류하고 decision boundary를 시각화합니다.

✅ Output
- 학습된 파라미터 (weights / bias)
- decision boundary plot

&lt;main point&gt;
- feature mapping을 통해 선형 분류기가 비선형 구조를 분리할 수 있음을 확인
- mapping 설정(차수 등), 학습률/반복수에 따라 경계와 수렴 특성이 달라짐

---

## 2. Feature Mapping + Logistic Regression (corners)

- corners 데이터에 대해서도 동일한 파이프라인을 적용합니다.
- two-moons와 corners의 데이터 구조 차이에 따라
  decision boundary가 어떻게 달라지는지 비교합니다.

✅ Output
- 학습된 파라미터
- decision boundary plot

&lt;main point&gt;
- 데이터 기하 구조에 따라 feature mapping의 효과가 달라짐
- 동일한 로직이라도 데이터 특성에 따라 분리 경계 형태가 크게 변함

---

## 3. Kernelized K-Means Clustering (two-moons)

- 일반 K-Means는 비선형 구조(two-moons)를 잘 분리하기 어렵습니다.
- Kernel trick을 적용한 Kernelized K-Means를 구현하여
  비선형 군집 경계를 학습하고 결과를 시각화합니다.

✅ Output
- 최종 cluster assignment
- clustering visualization

&lt;main point&gt;
- kernelized K-Means는 two-moons 같은 곡선 형태 군집을 더 잘 분리 가능
- 커널 파라미터(예: scale)에 따라 군집 결과가 민감하게 변함

---

## 4. Kernelized K-Means Clustering (corners)

- corners 데이터에도 Kernelized K-Means를 동일하게 적용합니다.
- 커널 선택/파라미터에 따른 군집 성능 차이를 확인합니다.

✅ Output
- 최종 cluster assignment
- clustering visualization

&lt;main point&gt;
- 커널 파라미터에 따라 군집 성공/실패가 갈릴 수 있음
- implicit feature space에서 거리 구조가 바뀌는 효과를 직관적으로 확인 가능

