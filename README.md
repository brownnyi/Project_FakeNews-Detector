# 가짜뉴스 탐지 프로젝트
## 목적
![image](https://github.com/user-attachments/assets/614ac5d1-7a12-455f-9239-e315610b44b7)
![image](https://github.com/user-attachments/assets/30871c51-4d9c-4129-936e-b15ce0d60c0c)
![image](https://github.com/user-attachments/assets/60296e98-a42f-421d-bc49-efe94fcfe27e)

- 오늘날 많은 사람들이 가짜뉴스에 쉽게 노출되어 그에 따른 피해가 생기는 것을 보고, ‘가짜뉴스를 찾아내는 모델’을 만드는 프로젝트 기획

## 프로젝트 개요
- 초기 BERT 모델을 통해 광고성 기사이거나, 서론의 내용과 본론의 내용이 다른 가짜뉴스의 특징들로 분류된 데이터를 학습시켜 가짜뉴스 탐지를 하고자 하였지만, 일정한 특징들을 갖지 않고 '날조'된 기사들을 찾으려면 다른 방법을 찾아야겠다는 생각에 초기모델 포기
- LLM모델(Llama2-Koalpaca)을 가짜뉴스 데이터 파인튜닝하여 가짜뉴스의 전문이나 제목을 질문했을때 대답의 정확도가 높은가를 알아보는 프로젝트
- 이전 프로젝트 유튜브 API를 활용한 동영상 스크립트 저장 코드와 네이버 뉴스 크롤링 코드를 같이 사용하여 데이터 수집

## 데이터셋
- Youtube에 퍼져있는 가짜뉴스의 스크립트 전문을 긁어오는 앱을 만들어 선동뉴스, 날조뉴스 등의 [가짜뉴스 데이터셋](https://github.com/brownnyi/YoutubeAPI) 구성
- Naver 뉴스의 기사 전문을 크롤링하여 [진짜뉴스 데이터셋](https://github.com/brownnyi/NaverNews) 구성

## 한계점
- 가상 클라우드 컴퓨터를 사용했더라면 더 큰 데이터를 학습시킬 수 있었겠지만, Colab 유료계정 환경으로도 데이터를 학습시키는데 한계가 존재
- 데이터의 신뢰성 문제(내가 수집한 뉴스 데이터가 과연 신뢰할 수 있는가?)
- 이전에 한글을 잘 이해하는 LLM 모델을 만들기 위해 이미 네이버 지식in 데이터를 통해 학습시킨 LLM 모델을 사용하여 학습된 데이터를 바탕으로 가짜뉴스 판별은 가능하지만 이상한 대답을 추가하여 대답하는 경우가 존재

## 개선점
- AWS와 같은 가상 클라우드 컴퓨터를 사용하여 더 많은 양의 데이터를 파인튜닝하여 정확도를 높일 수 있을 것이라고 예상
- 데이터의 신뢰성 문제는 '서울대학교 팩트체크'와 같이 진짜뉴스와 가짜뉴스를 판별하는 사이트를 크롤링 하여 데이터를 얻는다면 신뢰성을 얻을 수 있을 것이라고 확신

## 결과
- LLM 모델이 도출해낸 응답이 정확도를 판단하기에 모호한 감이 있어 직접 약 100개의 질문을 한 뒤 학습한 데이터를 바탕으로 대답을 잘 도출했는지에 대해 0과 1로 라벨링하여 체크
- 총 서로 다른 100개 질문을 던진 결과 93개의 응답이 학습한 데이터를 바탕으로 가짜뉴스인지 아닌지를 판별하는 결과 도출

## 결과 예시
# 1. 가짜뉴스 진짜뉴스 판별 질문
![image](https://github.com/user-attachments/assets/5c179beb-12e6-4925-8456-ac24f29be03d)

![image](https://github.com/user-attachments/assets/958292fb-11c5-4641-b2e5-cf568305ffa9)

![image](https://github.com/user-attachments/assets/1c9e664d-ec3d-40f8-8c21-971b330dda68)

![image](https://github.com/user-attachments/assets/e8b312fb-d5c5-45b7-aa9c-c7384661713c)

# 2. 유사도 판별
![image](https://github.com/user-attachments/assets/4147204e-7bcd-4860-9abf-7cdd9e6e6462)

![image](https://github.com/user-attachments/assets/275c21db-18f7-48e8-a762-385ade16047a)

