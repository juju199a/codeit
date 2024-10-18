### 다중 선형 회귀

1. 다중 선형 회귀
    - 1차 함수
    - 세타0 + 세타1XX1 + 세타2XX2 + ...

2. 경사하강법
    - 경사하강법 
        - error = prediction(X, theta) -y
        - theta = theta - alpha / m  * (X.T @error)
    - 역행렬: np.linalg.inv()
    - 전치행렬 : X.T

3. 정규방정식
    - 미분해서 0 하면 바로 최적의 세터를 구한다.
    - 한번에 구할 수 있고, 선형 회귀 + 소량의 데이터 일 때 유리 (1000개 이하)
    - np.linalg.inv( X.T @ X ) @ X.T @ y

