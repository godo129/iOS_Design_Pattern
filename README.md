# iOS_Design_Pattern
iOS 디자인 패턴 정리입니다. 

# 목차 
1. [디자인 패턴이란](#디자인-패턴이란)
2. [디자인 패턴의 종류](#디자인-패턴의-종류)
 - [MVC](#MVC)
 - [MVP](#MVP)
 - [MVVM](#MVVM)
 - [VIPER](#VIPER)
 - [Delegation](#Delegation)
 - [Singleton](#Singleton)

# 디자인 패턴이란

간단한 어플리케이션을 만들땐 모든 기능을 한 곳에 모아두고 코딩을 하는 것이 가능하고, 효율적일 수 있습니다. 하지만 어플리케이션의 크기가 커지면 이러한 방식으로 하는 건 비효율적이게 됩니다. 
그래서 이를 해결하기 위해서 다양한 디자인 패턴들이 등장했습니다. 

![labor](https://user-images.githubusercontent.com/76652929/127452285-2c850015-9437-48d8-8ded-60e31bcba943.jpg)


디자인 패턴은 간단히 말해서 분업화라고 생각하면 됩니다. 
디자인 패턴의 분류는 분업을 어떻게 시키는 지에 따라서 달라집니다. 


# 디자인 패턴의 종류 



# MVC


![MVC](https://user-images.githubusercontent.com/76652929/127449283-2c067ea0-d4ff-41af-a067-a71e21739373.png)

  + View : 실제로 사용자의 눈에 보이는 것입니다. 
  + Controller : View와 Model 사이의 가교 역활을 하며 View를 통한 요청을 Model에 보내주고 이 Model에서의 요청된 데이터를 가져와 View에 뿌려줍니다.  
  + Model : 데이터를 처리하는 부분입니다. 

  + View 와 Model 간의 의존성이 높은 단점이 있습니다.


![ios_MVC](https://user-images.githubusercontent.com/76652929/127449294-608a8bf9-b3da-465c-a1fd-3afe3409abcc.png)


  + iOS에서는 View Life Cycle이 관련 되어 있어서 이렇게 View와 Controller이 강하게 붙어있는 특징이 있습니다. 



# MVP


 + MVC 패턴의 View와 Model의 의존성 문제를 해결 하기 위해서 나왔습니다. 

![MVP](https://user-images.githubusercontent.com/76652929/127452602-1b242466-2dd1-483a-9ed7-78af7f689ade.png)


   + MVC 패턴에서 Cotroller이 Presenter로 변경 되었습니다. 그렇지만 이번엔 View와 Presenter가 1:1로 대응되어서 View와 Presenter의 의존성이 큰 결과가 나왔습니다. 



# MVVM

![MVVMPattern](https://user-images.githubusercontent.com/76652929/127453230-c8ef272d-45e7-47e4-aa91-03cb2348166a.png)


  + 전체적인 흐름은 MVC, MVP와 비슷합니다. 
  + 차이는 View와 ViewModel이 Binding 되어 있다는 것입니다. 이렇게 Binding 되어 있는 상태에서 View는 ViewModel을 관찰하는 상태가 됩니다. 이 상태에서 ViewModel이 변경 되는 지 관찰하고 변경이 행해진다면 이 변경점이 Binding 되어 있기 때문에 자연스럽게 View에도 적용 됩니다.  



# VIPER
![VIPER-Design-patterns-modules-interaction-description](https://user-images.githubusercontent.com/76652929/127454364-f9c43802-1098-4f92-8e56-516d0bfe8135.png)

  + VIPER은 위의 패턴들에서 화면전환을 추가한 것입니다. 
  + View : 화면부분입니다.
  + Presenter : View에 데이터를 보여주는 로직을 맡는 부분입니다.
  + Router : 화면의 전환을 어떻게 할지 담당하는 부분입니다.
  + Interactor : 데이터 처리를 담당하는 부분입니다.
  + Entity : 다른 디자인 패턴에서 Model과 같은 의미를 가지는 부분입니다. 


# Delegation 

![delegation](https://user-images.githubusercontent.com/76652929/127456487-d142d922-eb4a-4b58-ab39-22793552e3c6.png)

  + Delegate는 대리자라는 의미를 가지고 있습니다. 이 의미와 같이 Delegation은 일을 대신해주는 것을 말합니다.
  + 더더욱 간단하게 말하자면 위의 그림과 같이 애플에서 UITableView 을 지원하는 데 지원하는 것은 껍데기이고 그 내부에 데이터를 넣는 등 다양한 기능을 추가하는 것, 즉 사용자가 기능을 확장시키는 것을 말합니다.




# Singleton

![singleton](https://user-images.githubusercontent.com/76652929/127458842-63a2ee8e-498b-4e15-a72f-b0418e4a6239.png)


+ Singleton은 최초로 생성자에 의해 생성된 객체를 리턴하는 것입니다.
* ## 장점 
  + 메모리 낭비를 방지할 수 있습니다.
  + 인스턴스가 절대적으로 하나 존재함을 보증하고 싶을 때 사용합니다.
  + 두 번째 이상 이용시부터는 객체 로딩 시간이 현저하게 줄어서 성능이 좋아집니다. 

* ## 단점
  + 싱글톤 인스턴스가 너무 많은 일을 하거나 많은 데이터를 공유하면 다른 클래스의 인스턴스들 간에 결합도가 높아져 "개방-폐쇄 원칙"을 위반한다. (= 객체 지향 원칙 위반함)
  + 따라서 수정 어려워지고 테스트하기 어려워짐 
  + 또한 멀티 쓰레드 환경에서 동기화 처리를 안하면 인스턴스가 두개가 생성된다든지 하는 경우 발생할 수 있음 
