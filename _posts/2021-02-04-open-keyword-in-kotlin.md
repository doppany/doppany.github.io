나는 사회초년생이다. (Kotlin open 키워드 공부를 위한 컨셉 정도로 봐주세용)

월급도 받고 이제 차를 한 대 뽑아볼까한다.
그렇담 요즘 차들은 어떤 기능들이 있는지 한번 클래스를 만들어서 알아보자. (난 개발자니까 ㅋ ㅋㅋ ㅋㅋ)

```
class Car {

    fun getNumberOfTires(): Int {
        return 4
    }     fun hasEmergencyBreak(): Boolean {    	return true
   }
    
    fun hasSunRoof() :Boolean {
        return false
    }     
    fun hasHighPass() :Boolean {
        return false
    }      fun hasCoolSeat() :Boolean {
        return false
    }
     fun hasCruiseMode() :Boolean {
        return false
    }
// 등등.. 
}
```

이런 기능들이 있는걸 알았다.
하지만 난 사회초년생이니까(?) 아반떼부터 만들어본다.

```
class Avante() : Car() {
}
```
이렇게 Car를 상속받으려고하면
![image](https://user-images.githubusercontent.com/67831290/106780161-109acd80-668b-11eb-87f9-5429d7971e91.png)

이런 컴파일 에러 경고가 뜬다.
final이라서 상속할수없고, 아래에 Car를 open하라고한다. (오픈카여?..)
그럼 또 오픈해줘야지

```
open class Car {
...
}
```
이젠 컴파일에러가 안난다. 
다시 아반떼를 만들어보자

```
class Avante(): Car() {
   override fun hasSunRoof() :Boolean {
        return true
    }

   override fun hasCruiseMode() :Boolean {
        return true
    }

   override fun hasHighPass(): Boolean {
        return true
    }

   override fun hasCoolSeat(): Boolean {
        return true
    }
}
```
엥 이번엔 override가 안되고 아래와같은 에러가 나온다.
![image](https://user-images.githubusercontent.com/67831290/106780186-15f81800-668b-11eb-9543-a0da9c265a6f.png)
눈치껏 옵션추가 가능한것들에 대해 open을 해주자.

```
open class Car {
    //..타이어개수 변경은 미래의 꿈나무에게 넘기자
    fun getNumberOfTires(): Int {
       return 4
    }
    // 사이드브레이크는 무조건 !
    fun hasEmergencyBreak(): Boolean {
       return true
    }
    open fun hasSunRoof() :Boolean {
       return false
    }
    open fun hasHighPass() :Boolean {
       return false
    }
    open fun hasCoolSeat() :Boolean {
       return false
    }
    open fun hasCruiseMode() :Boolean {
       return false
    }
}

```
다시 Avente 클래스를 보자.
```

class Avante(): Car() {
    // 난 선루프도 넣어야지!!!!
    override fun hasSunRoof() :Boolean {
        return true
    }

    // 크루즈모드 안넣는사람도있냐!!! 넣자
    override fun hasCruiseMode() :Boolean {
        return true
    }

    // 톨게이트에서 못멈출거같으니까 무적권 하이패스ㅋㅋㅋㅋ
    override fun hasHighPass(): Boolean {
        return true
    }

    //엉쿨~ 말해뭐해
    override fun hasCoolSeat(): Boolean {
        return true
    }
}
```
에러가 없다.

여기서 확인해볼 수 있는 것은 getNumberOfTires 메서드와 hasEmergencyBreak는 override가 불가능하다.
차 바퀴는 4개다. 아직까지는..
그리고 사이드브레이크는 무조건! 

*꿀팁 - 사이드브레이크는 콩글리쉬고 emergency break나 hand break로 부른다고 한다.*

나머지옵션은 일단 좋은거같으니 다 넣었다. 즉, override로 변경이 가능하다.

![image](https://user-images.githubusercontent.com/67831290/106780222-1d1f2600-668b-11eb-90e3-be0ef1b4e7a6.png)

짠! 이렇게 내 첫차는 온갖 잘 쓰지도않을 옵션을 넣은 아반떼가 되었따 !!!! 박수 ~~
