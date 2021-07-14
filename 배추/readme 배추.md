## 프로젝트 개요

---

대학교 졸업 프로젝트로 약 2달간 진행한 프로젝트입니다.

5년간의 [배추 가격 데이터](https://www.kamis.or.kr/customer/price/wholesale/item.do)와 [기상 데이터](https://data.kma.go.kr/cmmn/main.do)를 직접 크롤링 하여 데이터를 수집하였고, scikit-learn을 이용하여 회귀 분석을 통해 배추 가격을 예측하는 모델을 개발하는 프로젝트 였습니다.

최종적으로 모델을 이용하여 웹으로 구현하는 것이 프로젝트의 목표였지만, 제가 담당 했던 부분인 머신러닝 모델링을 위주로 작성하였습니다.

## Flow chart

1. `selenium` 과 `bs4` 를 이용하여 데이터 수집.
    - 기상청 날씨누리 사이트에서 2015 ~ 2019년도의 날씨 데이터(**평균기온,강수량, 운량, 일조시간)**를 수집함.
2. 수집한 데이터를 바탕으로 EDA와 전처리 작업 진행
    - Seaborn 라이브러리의 heatmap 함수를 이용하여, 배추 가격의 년도와 월별로 히트맵 그래프를 그려본 결과 배추 가격이 여름철에 가장 가격이 높고, 봄철에 가격이 낮게 형성된 것을 파악함.

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8d8dfe7a-86f3-453e-9ee2-9cc7c97d74f1/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8d8dfe7a-86f3-453e-9ee2-9cc7c97d74f1/Untitled.png)

    - 위 내용을 바탕으로 **월 변수 추가.**
    - 배추가격 그래프를 시각화 한 결과 그래프 형태가 정규 분포 형태와 큰 차이를 보임 → 배추 가격을 로그 변환 적용

        ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c9132907-9ad8-4d31-8400-df141250bf80/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c9132907-9ad8-4d31-8400-df141250bf80/Untitled.png)

        - 회귀 분석시 데이터가 정규분포를 따를 경우 분석의 결과가 더 좋은 경우가 많기때문에 로그 변환을 시켜준다.

        ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e785aed0-12cd-4b0c-912d-06bad79bc75e/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e785aed0-12cd-4b0c-912d-06bad79bc75e/Untitled.png)

3. Scikit-learn을 이용하여 회귀 모델을 생성후 예측.
    - Linear, Ridge, Lasso 회귀 모델을 각각학습하여 예측 진행
        - Ridge와 Lasso의 경우 하이퍼 파라미터 튜닝을 진행 해준다.
    - 세개의 모델을 앙상블하여 최종 예측 수행.

## 결과 및 시사점

데이터를 직접 수집하여 모델을 개발하는 과정까지 전 과정을 경험할 수 있는 좋은 프로젝트 였습니다.

처음 진행했던 프로젝트인 만큼 시행 착오도 많이 겪고, 모델의 성능도 좋지 않았습니다. 그러나 힘들었던 만큼 많은 것을 배울 수 있었습니다. 특히 제가 원하는 데이터를 직접 수집하여 유의미한(?) 결과를 도출 할 수 있다는 점이 상당히 흥미로웠고, 이 프로젝트를 통해 머신러닝에 더욱더 빠져들었 것 같습니다.
