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
- SAGA패턴, CQRS
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

# 무중단배포
- 무중단배포-delivery배포중
![무중단배포-delivery배포중](https://user-images.githubusercontent.com/22510081/93423524-22085680-f8f1-11ea-8c6a-bb18183f7b18.png)
- 무중단배포-delivery배포중2인데 2개가 떠 있음
![무중단배포-delivery배포중2인데 2개가 떠 있음](https://user-images.githubusercontent.com/22510081/93423527-23398380-f8f1-11ea-8425-2b3a2153250a.png)

# 서킷 브레이킹
- CD_1.dr생성
![CB_1 dr생성](https://user-images.githubusercontent.com/22510081/93423834-d0140080-f8f1-11ea-8df3-94d852841f53.png)
- CB_2.Siege부하생성_정상
![CB_2 Siege부하생성_정상](https://user-images.githubusercontent.com/22510081/93423808-c5596b80-f8f1-11ea-8ffb-d01114a238af.png)
- CB_3.Siege부하생성_차단발생
![CB_3 Siege부하생성_차단발생](https://user-images.githubusercontent.com/22510081/93423822-cc807980-f8f1-11ea-8f23-d8e5c370c9ef.png)
- CB_4.Siege부하생성_차단발생2
![CB_4 Siege부하생성_차단발생2](https://user-images.githubusercontent.com/22510081/93423826-cdb1a680-f8f1-11ea-81db-e7cdbbdbb161.png)
- CB_5.Siege부하생성_kiali_External IP확인
![CB_5 Siege부하생성_kiali_External IP확인](https://user-images.githubusercontent.com/22510081/93423835-d0ac9700-f8f1-11ea-83f0-3025ce965f8d.png)
- CB_6.Siege부하생성_차단발생2_kiali확인
![CB_6 Siege부하생성_차단발생2_kiali확인](https://user-images.githubusercontent.com/22510081/93423829-ce4a3d00-f8f1-11ea-9f0d-72b4354ade37.png)
 
 # 오토스케일아웃
- HPA_1.order에HPA설정적용
![HPA_1 order에HPA설정적용](https://user-images.githubusercontent.com/22510081/93424150-63e5cc80-f8f2-11ea-83a6-fde89c4c3ad2.png)
- HPA_2.oder의 Pod증가
![HPA_2 oder의 Pod증가](https://user-images.githubusercontent.com/22510081/93424147-634d3600-f8f2-11ea-888f-4375aaa6225b.png)

# Liveness
- Liveness_1.sms의 buildspec.yml 파일에 livenessProbe적용
![Liveness_1 sms의 buildspec yml 파일에 livenessProbe적용](https://user-images.githubusercontent.com/22510081/93424351-dbb3f700-f8f2-11ea-9d60-b03e189765b9.png)
- Liveness_2.sms가 CodeBuild에 의해 자동재배포
![Liveness_2 sms가 CodeBuild에 의해 자동재배포](https://user-images.githubusercontent.com/22510081/93424347-da82ca00-f8f2-11ea-9e1c-65702c1f7174.png)
 
 
 # PVC. Readiness
- P.PVC.Readiness_1.delivery 의 buildspec.yml 파일에 pvc 적용
![P PVC Readiness_1 delivery 의 buildspec yml 파일에 pvc 적용](https://user-images.githubusercontent.com/22510081/93424705-83312980-f8f3-11ea-8dca-55eb13bfbe7f.png)
- P.PVC.Readiness_2.delivery 의 buildspec.yml 파일 수정적용후pod가 정상적으로 올라옴
![P PVC Readiness_2 delivery 의 buildspec yml 파일 수정적용후pod가 정상적으로 올라옴](https://user-images.githubusercontent.com/22510081/93424703-82989300-f8f3-11ea-9708-d00229322f7c.png)
- P.PVC.Readiness_3.delivery 에서 pvc 에 bind 를 못하면서 오류발생. Reaniness 가 안되어 pod 교체가 안됨. 기존pod가 살아있으므- 로 무중단배포
![P PVC Readiness_3 delivery 에서 pvc 에 bind 를 못하면서 오류발생  Reaniness 가 안되어 pod 교체가 안됨  기존pod가 살아있으므로 무중단배포](https://user-images.githubusercontent.com/22510081/93424700-80cecf80-f8f3-11ea-89cc-7bbb7f46dc79.png)
- P.PVC.Readiness_4.delivery가 CodeBuild를통해자동재빌드됨
![P PVC Readiness_4 delivery가 CodeBuild를통해자동재빌드됨](https://user-images.githubusercontent.com/22510081/93424709-84faed00-f8f3-11ea-92f7-f3527cadfea4.png)
- P.PVC.Readiness_5.delivery 의 buildspec.yml 파일에 pvc 적용제거
![P PVC Readiness_5 delivery 의 buildspec yml 파일에 pvc 적용제거](https://user-images.githubusercontent.com/22510081/93424708-84625680-f8f3-11ea-8d1f-be1427b18083.png)

# Polyglot
- Polyglot_delivery의 pom파일에 h2 대신 hsqldb 사용
![Polyglot_delivery의 pom파일에 h2 대신 hsqldb 사용](https://user-images.githubusercontent.com/22510081/93425048-34d05a80-f8f4-11ea-9daa-835a81808f67.png)



 끝
