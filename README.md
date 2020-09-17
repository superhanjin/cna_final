# 주제 : 꽃배달

# 기능적 요구사항
 - 고객이 꽃배달 메뉴 선택하여 주문한다
 - 주문이 일어나면 결제 시스템의 결제 기능이 호출된다
 - 주문이 되면 주문 내역이 꽃가게 주인에게 전달된다
 - 꽃가게 주인이 확인하여 꽃을 만들어서 배달 출발한다
 - 고객이 주문을 취소할 수 있다
 - 주문이 취소되면 배달이 취소된다
 - 고객이 주문상태를 중간중간 조회한다
 - 주문상태가 바뀔 때 마다 SMS로 알림을 보낸다


# 모델링
![이벤트스토밍](https://user-images.githubusercontent.com/22510081/93422213-40208780-f8ee-11ea-88b5-5b437e0f386c.png)


# 구현
 - feignclient 사용(delivery-external에 BaeminDeliveryService.java) 
  ![1 feignclient 적용](https://user-images.githubusercontent.com/60597630/93409416-ced2db80-f8d1-11ea-9bb4-d38debb0e7b7.JPG) 


# 시연
- 오더 생성
 ![2 final_order넣기](https://user-images.githubusercontent.com/60597630/93408665-148ea480-f8d0-11ea-98d3-249a34cf0dc8.JPG) 
 ![2 final_order kafkalog](https://user-images.githubusercontent.com/60597630/93408664-13f60e00-f8d0-11ea-8d03-022279b9bb9f.JPG) 
 
- 배민 배송 출발
 ![4 baeminDeliveryStart](https://user-images.githubusercontent.com/60597630/93408668-16586800-f8d0-11ea-90ef-6872d0227cc1.JPG) 
 ![4 baeminDeliveryStart_kafka log](https://user-images.githubusercontent.com/60597630/93408669-16586800-f8d0-11ea-8d49-37e8e9e14cbe.JPG) 

- Mypage view
 ![5 mypage](https://user-images.githubusercontent.com/60597630/93408675-17899500-f8d0-11ea-8f50-5722241ead9b.JPG) 


# codebuild 적용
 - ![6 final_codebuild](https://user-images.githubusercontent.com/60597630/93408676-18222b80-f8d0-11ea-822b-805364295172.JPG) 


# AutoScale 적용
 - ![7 autoscale적용](https://user-images.githubusercontent.com/60597630/93411382-02b00000-f8d6-11ea-83e6-0437b3c9a605.JPG) 
 - ![7 autoscale-before](https://user-images.githubusercontent.com/60597630/93408681-1a848580-f8d0-11ea-88ad-d35d432f7233.JPG) 
 - ![7 autoscale-after](https://user-images.githubusercontent.com/60597630/93408679-19535880-f8d0-11ea-9f13-f3c278002d57.JPG) 

# Circuit Breaker 적용
 - ![7 circuit breaker](https://user-images.githubusercontent.com/60597630/93408682-1a848580-f8d0-11ea-8105-7c9b72894701.JPG) 


# Polyglot 적용
 - ![8 polyglot적용](https://user-images.githubusercontent.com/60597630/93408684-1bb5b280-f8d0-11ea-8949-0eebc2e03e8b.JPG) 


# Readiness, Liveness 적용
 ![9 readiness,liveness 적용](https://user-images.githubusercontent.com/60597630/93408690-1c4e4900-f8d0-11ea-9ba3-43772c1d4e03.JPG) 
 
 - Readiness, Liveness 점검 
 -![9 liveness test](https://user-images.githubusercontent.com/60597630/93409959-07bf8000-f8d3-11ea-86fd-d8a05656aaef.JPG) 
 
 - Liveness 
 -![9 liveness before](https://user-images.githubusercontent.com/60597630/93408687-1c4e4900-f8d0-11ea-8fb1-e143e694b161.JPG) 
 -![9 liveness after](https://user-images.githubusercontent.com/60597630/93408686-1bb5b280-f8d0-11ea-8496-e20ad140c656.JPG) 
 
 - Readines 
 -![9 readiness인가](https://user-images.githubusercontent.com/60597630/93408691-1ce6df80-f8d0-11ea-9b23-7ef309f9de8a.JPG) 
 -![9 readiness인가2](https://user-images.githubusercontent.com/60597630/93408692-1d7f7600-f8d0-11ea-9bda-c8694328f648.JPG) 
 

# kiali모니터링 적용
 - ![10 kiali](https://user-images.githubusercontent.com/60597630/93408660-12c4e100-f8d0-11ea-9361-a518a66e9ee1.JPG) 


# jaeger모니터링 적용
 - ![10 jaeger](https://user-images.githubusercontent.com/60597630/93408656-1193b400-f8d0-11ea-97eb-dfbd250acfac.JPG) 
 
 끝
