## 음성 오디오를 멜-스펙트로그램으로 매핑하여 생성된 이미지의 유사성을 분석하는 방법

https://www.mdpi.com/2227-7390/11/3/498

1. **유클리디안 거리 (ED) :** 두 이미지 간의 픽셀 간 거리를 계산하여 유사성을 측정하며, 값이 작을수록 두 이미지가 유사함을 의미함
2. **피어슨 상관 계수 (PCC) :** 두 이미지 간의 선형 상관 관계를 측정하여 유사성을 평가하며, 값이 1에 가까울수록 두 이미지가 밀접한 관련이 있음을 나타냄
3. **구조적 유사성 지수 (SSIM) :** 인간 시각 체계에 기반하여 이미지 간의 구조적 유사성을 측정하며, 높은 SSIM 값은 두 이미지가 유사함을 나타냄

### 멜-스펙트로그램

⇒ 음성 신호를 주파수와 시간에 따라 시각화하는 기술

⇒ 일반적으로 멜 스케일을 사용하여 주파수를 표현하며, 이는 인간의 청각 시스템이 주파수를 처리하는 방식을 모방한 것

### 유클리디안 거리 (ED)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/9041b22b-fcff-42a0-a063-89a79fa51d2f/075eaab7-86ed-45b1-981a-8411fbb45c84/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/9041b22b-fcff-42a0-a063-89a79fa51d2f/07b4a8b6-636e-4903-aea9-6c5893f250c2/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/9041b22b-fcff-42a0-a063-89a79fa51d2f/25e19969-2796-4dd2-8725-5d867ea9a570/Untitled.png)

### 피어슨 상관 계수 (PCC)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/9041b22b-fcff-42a0-a063-89a79fa51d2f/d06b92ea-f7f2-4d95-bd75-a5f259ed84bb/Untitled.png)

### 구조적 유사성 지수 (SSIM)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/9041b22b-fcff-42a0-a063-89a79fa51d2f/48ff24f9-c656-4979-a94d-1658e8fa0a1d/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/9041b22b-fcff-42a0-a063-89a79fa51d2f/801c1a42-7c24-4e1c-8701-e71d0e749f60/Untitled.png)

### 원본 오디오

![KakaoTalk_20240404_233835794.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/9041b22b-fcff-42a0-a063-89a79fa51d2f/53b90257-27fc-48f5-bef9-11b5b234537a/KakaoTalk_20240404_233835794.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/9041b22b-fcff-42a0-a063-89a79fa51d2f/32278c02-fff4-4ca0-b872-06a8fb7b70f3/Untitled.png)

### 노이즈가 섞인 오디오

![KakaoTalk_20240404_233835794_01.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/9041b22b-fcff-42a0-a063-89a79fa51d2f/e54b530c-b7b6-4f64-b396-2aeffff56424/KakaoTalk_20240404_233835794_01.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/9041b22b-fcff-42a0-a063-89a79fa51d2f/6567f46c-6c5c-4a4e-988a-6d52eea2baf3/Untitled.png)

### 유사도 검출

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/9041b22b-fcff-42a0-a063-89a79fa51d2f/96869d52-54ca-4b85-bd8d-284e21a9af03/Untitled.png)

### 유사도 조절 1

⇒ 현재 코드는 노이즈의 분포나 특성을 고려하지 않고 전체적인 유사도를 나타내고 있음

⇒ 노이즈가 전체적으로 골고루 분포되어 있는 경우와 노이즈가 한 부분에 몰려 있는 경우의 유사도를 구분하려면 노이즈의 분포를 고려하여 새로운 유사도 척도를 만들어야 함

⇒ 노이즈의 분포를 분석하여 어느 정도의 영역에 노이즈가 집중되어 있는지를 파악하면 이후 해당 영역에 대한 가중치를 적용하여 유사도를 조정할 수도 있음

⇒ 예를 들어, 노이즈가 몰려 있는 부분에 더 높은 가중치를 부여하여 해당 부분의 유사도를 낮추는 방법 등을 사용할 수 있음

### 유사도 조절 2

⇒ 초마다 이미지를 나눠서 각각의 유사도를 판단하고 있음
