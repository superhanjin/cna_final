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
 - feignclient 사용(order-external에 payment.java) 
![FeignClient사용](https://user-images.githubusercontent.com/22510081/93422627-1e73d000-f8ef-11ea-949c-fda61bef9ba7.png) 


# 시연
- Senario_1.첫번째주문명령
![Senario_1 첫번째주문명령](https://user-images.githubusercontent.com/22510081/93422781-862a1b00-f8ef-11ea-8e41-3fceaf179de9.png)
- Senario_2.첫번째주문카프카메시지로그
![Senario_2 첫번째주문카프카메시지로그](https://user-images.githubusercontent.com/22510081/93422806-917d4680-f8ef-11ea-944f-9d42b8987002.png)
- Senario_3.첫번째주문-Delivery에서이벤트수신
![Senario_3 첫번째주문-Delivery에서이벤트수신](https://user-images.githubusercontent.com/22510081/93422807-9215dd00-f8ef-11ea-8b9e-8149eeb2dec9.png)
- Senario_4.첫번째주문에대해Delivery에서배송시작명령
![Senario_4 첫번째주문에대해Delivery에서배송시작명령](https://user-images.githubusercontent.com/22510081/93422808-92ae7380-f8ef-11ea-9cb6-6b116cd74b30.png)
- Senario_5.첫번째주문에대해Delivery에서Shipped이벤트발행
![Senario_5 첫번째주문에대해Delivery에서Shipped이벤트발행](https://user-images.githubusercontent.com/22510081/93422809-93470a00-f8ef-11ea-96ac-425879ca328c.png)
- Senario_6.mypages뷰확인(CQRS)
![Senario_6 mypages뷰확인(CQRS)](https://user-images.githubusercontent.com/22510081/93422794-8de9bf80-f8ef-11ea-8b4b-d4babb1f90da.png)
- Senario_7.orderDetails뷰확인(CQRS)
![Senario_7 orderDetails뷰확인(CQRS)](https://user-images.githubusercontent.com/22510081/93422795-8f1aec80-f8ef-11ea-926e-570ca44cb5a7.png)
- Senario_8.두번째주문명령
![Senario_8 두번째주문명령](https://user-images.githubusercontent.com/22510081/93422798-8f1aec80-f8ef-11ea-9d8f-bdcf633425fc.png)
- Senario_9.두번째주문카프카메시지로그
![Senario_9 두번째주문카프카메시지로그](https://user-images.githubusercontent.com/22510081/93422799-8fb38300-f8ef-11ea-9496-39dff15ba44a.png)
- Senario_10.두번째주문취소명령
![Senario_10 두번째주문취소명령](https://user-images.githubusercontent.com/22510081/93422800-904c1980-f8ef-11ea-8cf9-b14dbcf3f448.png)
- Senario_11.두번째주문취소카프카메시지로그
![Senario_11 두번째주문취소카프카메시지로그](https://user-images.githubusercontent.com/22510081/93422801-90e4b000-f8ef-11ea-8475-af46bdd5d36d.png)

# codebuild 적용
- CodeBuild_1.개인GibHub레파지토리
![CodeBuild_1 개인GibHub레파지토리](https://user-images.githubusercontent.com/22510081/93423083-17998d00-f8f0-11ea-84a4-9df770873f52.png)
- CodeBuild_1.코드빌드프로젝트(개인GitHub계정에연결)
![CodeBuild_1 코드빌드프로젝트(개인GitHub계정에연결)](https://user-images.githubusercontent.com/22510081/93423084-18caba00-f8f0-11ea-90c1-459b70ca10eb.png)

 # ConfigMap 적용
- ConfigMap_1.ConfigMap생성
![ConfigMap_1 ConfigMap생성](https://user-images.githubusercontent.com/22510081/93423141-40218700-f8f0-11ea-9e25-a7fdeec7ca01.png)
- ConfigMap_1.Order PolicyHandler에서 Env사용
![ConfigMap_1 Order PolicyHandler에서 Env사용](https://user-images.githubusercontent.com/22510081/93423144-4152b400-f8f0-11ea-8b84-c77a035cbd87.png)

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
