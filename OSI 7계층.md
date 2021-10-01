![image](https://user-images.githubusercontent.com/35948339/135277704-2d4ebfd8-ee4e-4b6a-a210-37fb18ee0952.png)

# 1️⃣ Physical Layer
  - ### 두 대의 컴퓨터가 통신하려면 ?
    - #### 0과 1을 주고받을 수 있으면 모든 데이터를 주고 받을 수 있다
    - ![image](https://user-images.githubusercontent.com/35948339/135295457-5c5ddee7-69ed-466f-90c1-4ad8677ee6f8.png)
    - #### 이제 두 컴퓨터는 모든 데이터를 주고 받을 수 있게 되었다 ‼
  - ### 하지만, 현실에선 잘 동작하지 않음
    - #### 그 이유는 ?
    - ![image](https://user-images.githubusercontent.com/35948339/135650232-fcf94c89-997f-42f9-98de-38511e2af476.png)
    - #### 그렇다면, 0과 1로 이루어진 전자기파를 보내면 두 대의 컴퓨터가 통신 할 수 있을까? <br><br> <img src="https://user-images.githubusercontent.com/35948339/135651219-110a2e04-69da-4839-a612-c3b301edf08e.png" width=500>
    - #### 하지만 이러한 수직, 수평선이 있는 주파수는 0 ~ 무한대Hz의 주파수를 가진다
    ------------
    - #### 결론 : 이런 아날로그 신호로 바꿔서 전송을 하면 해결된다 ‼ <br><br> <img src="https://user-images.githubusercontent.com/35948339/135651465-a09e146a-9fa9-4802-afba-cc0454340816.png" width=500>
  - ## 결국 Physical Layer 란?
    - #### 0과 1의 나열을 아날로그 신호로 바꾸어 전선으로 보내고, (Encoding)
    - #### 다른 컴퓨터에서 아날로그 신호가 들어오면 0과 1의 나열로 해석하여 (Decoding)
    - #### ⭐ 물리적으로 연결된 두 컴퓨터가 0과 1의 나열을 주고 받을 수 있게 해주는 모듈 or 계층
    - #### <img src="https://user-images.githubusercontent.com/35948339/135652202-5d9c225e-ecbb-4a48-b288-949d631d4067.png" width=300> <br><br> PHY 칩에 하드웨어적으로 구현되어 있다.
---------
# 2️⃣ Data-Link Layer
  - ### 만약, 두 대 이상의 컴퓨터가 연결을 하려면 ? <br><br> ![image](https://user-images.githubusercontent.com/35948339/135657905-b1b67f3f-43fc-4dfd-9b9d-7335de1890d4.png)
    - #### 위 그림처럼 전선을 추가하면 되겠지만, 더 많은 컴퓨터와 연결하기 위해서는 얼마나 많은 전선이 필요로 할까..
    - #### 🟥 이러한 방식은 컴퓨터에 전선을 꽂을 구멍도 많이 필요하고, 전선도 많이 필요하므로 비용면에서 비효율적 ‼
  ------
  - ### 이 문제를 해결하기 위해, 전선들을 구겨서 상자 안에 넣어보자 <br><br> ![image](https://user-images.githubusercontent.com/35948339/135659688-d1dbd234-e674-4d6a-beaf-f1c418125b2d.png)
    - #### 만약 A에서 B로 데이터를 보낸다면 연결된 모든 컴퓨터가 데이터를 받을 것이다 <br><br> ‼ 하지만 B에게만 데이터를 보낼 수 있게 해주는 것이 스위치 이다
  --------
  - ### 만약 서로 다른 네트워크끼리 통신을 주고 받고 싶다면 ? <br><br> <img src="https://user-images.githubusercontent.com/35948339/135660505-9bbca742-08cc-4f11-9cda-0dc0f0dc5b8c.png" width=600>
    - #### 스위치와 스위치를 연결한 라우터를 통해 연결을 주고 받을 수 있다
  -------
  - ### 위와 같이 전 세계 여러 컴퓨터들이 계층구조로 연결되어 있는 것을 `인터넷`이라고 한다
  ---------
  - ### 여러 대의 컴퓨터가 통신하는 방법
    - ### 다른 컴퓨터들이 A에게 동시에 데이터를 보낸다 <br><br> <img src="https://user-images.githubusercontent.com/35948339/135661592-384b4b48-a56f-4668-8d9a-53eeb548e88f.png" width=600>
      - #### 그렇다면, A는 이 문자열을 잘 끊어 읽어야 올바른 데이터를 가져올 수 있다
  

  
