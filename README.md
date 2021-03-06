# Cony PhotoFrame



## step1. Tabbed App 템플릿
- 요구사항 : 자동 생성된 ViewController 클래스 viewDidLoad() 함수에서 print(#file, #line, #function, #column) 코드를 추가하고 실행하면 콘솔 영역에 무엇이 출력되는지 확인한다.
- 실행화면
- ![screensh_step1](./img/step1.png)

- 애플 UIKit View Management 클래스 중에서 UITabBarController 와 UITabBar에 대해 학습한다.
- 각 클래스 역할(및 UITabBar과 UITabBarController의 차이점)은 무엇인가?
> https://github.com/conyconydev/conyconydev.github.io/blob/master/_posts/ios/2019-03-11-UITabBarController_UITabBar.md

## step2. IBOutlet
- 요구사항 : First Scene에 만들어져 있는 레이블을 IBOutlet으로 연결한다.
- 연결한 아웃렛 변수에 값을 변경한다.
- 실행화면
- ![screemsh_step2](./img/step2.png)

- UILabel 클래스 속성(Property)는 어떤게 있는지 학습한다.
>https://github.com/conyconydev/conyconydev.github.io/blob/master/_posts/ios/2019-03-12-UILabel.md

## step3. IBAction
- Main.storyboard 에서 First Scene에 UIButton을 추가하고, IBAction으로 연결한다.
- 실행화면
- ![screemsh_step3](./img/step3.png)

- IBAction 과 IBOutlet 연결 구조에 대해 이해한 내용을 정리한다.
- 버튼에 IBAction을 추가할 때 이벤트(Event) 종류에는 어떤 것들이 있는지 학습한다.
> https://github.com/conyconydev/conyconydev.github.io/blob/master/_posts/ios/2019-03-12-IBAction_IBOutlet.md

## step4. Scene과 Segue
  - 스토리보드 구성 요소에 대해 학습하고 새로운 Scene과 Segue(화면전환)를 추가한다.
- 실행화면
- ![screemsh_step4](./img/step4.png)

- Segue에 액션에 있는 여러 항목들은 어떤 효과가 있는지 값을 바꿔보며 실행해서 학습한다.
- Segue의 종류
1. show : Show는 Navication Controller에서 push/pop의 push를 의미한다. Navigation Controller의 스택 상에 Destination ViewContoller를 삽입하여 쌓게 된다. 참고로 iOS7부터 등장한 'UINavigationControllerDelegate'을 사용하면 보다 다양한 Transition effect를 구현할 수 있다.
2. show detail (iPad만 해당) : UISplitViewController를 사용할 때, 사용하는 Segue이다. 아이패드에서 화면을 가로로 눕히면 등장하는 Detail View상에 ViewController를 밀어 넣게 된다. Navigation Contoller의 스택에는 전혀 영향을 주지 않는다. 아래의 이미지의 오른 쪽 View 영역에 해당된다.
3. present modally : 일전의 presentViewController: 메소드와 동일한 동작을 하게된다. 옵션에 따라 ViewController를 띄우는 애니메이션에 변화를 줄 수 있다. Navigation Controller의 스택에는 전혀 영향을 주지 않는다. 단, 'Modally'라는 단어에서 알 수 있듯이 이미 Presentation을 한 ViewController에서 다른 ViewContller를 presentation할 수 없다. Show에서와 같은 맥락으로 'UIViewControllerTransitioningDelegate'를 사용하면 보다 다양한 Presantation effect를 구현할 수 있다.
4. popover presentation(iPad만 해당) : Show Detail과 같이 iPad에서만 볼 수 있는 View Transition이다. 작은 팝업 뷰 혹은 context menu 형식으로 ViewController를 띄우는 방법이다. 아이폰에서도 사용은 가능하지만 단순한 Modal View처럼 표시된다.
5. custom : 사용자 정의 세그웨이를 만듭니다.


## step5. ViewController 프로그래밍
- 스토리보드 구성 요소와 클래스 코드와 연결해서 동작을 확장한다.
- 실행화면
- ![screemsh_step5](./img/step5.png)

- 화면 전환이 이루어지는 사이에 뷰컨트롤러 라이프사이클이 어떻게 변화하는지 학습한다.
>  https://github.com/conyconydev/conyconydev.github.io/blob/master/_posts/ios/2019-03-13-ViewController.md
- 뷰컨트롤러와 관련된 새로운 용어들에 대해 학습한다.

- YellowViewController에서 Segue를 제거하고 다음 화면을 보여줄 때 코드로 보여주는 방법을 찾아보고 적용해본다.

```
// FirstViewController 적용
//storyboard를 이용하지 않고, 코드상으로 연결하는 방법

@IBAction func nextEmeraldViewBtn(sender: UIButton) {
    let storyboardFind = self.storyboard?.instantiateViewController(withIdentifier: "emeraldView")as! EmeraldView
    present(storyboardFind,animated: true , completion: nil)
}
```
## step6. Container ViewController
- 내비게이션 컨트롤러(Navigation Controller)를 Embed 시켜서 동작하도록 개선한다.
- 실행화면
- ![screemsh_step6](./img/step6.png)

- 뷰컨트롤러 컨테이너 동작을 이해한다.

    - 컨테이너 뷰 컨트롤러는 한 개의 view와 여러 개의 child ViewController를 다루고, ViewController에 의지할 수 있다는 것이 장점.

- 뷰컨트롤러 컨테이너는 또 어떤 클래스가 있는지 찾아보고 학습한다.
    - UINavigationController, UISplitViewController, UITabBarController
    > UIViewController 에서 상속받아서 Container ViewController를 만들 수 있다. 그렇다고 UIViewController가 항상 컨테이너는 아니다. 그렇게 사용하는 경우 만 그렇다. UINavigationController, UISplitViewController, UITabBarController 는 컨테이너 형태로 다른 childViewController를 포함하기 때문에.
    
- 내비게이션 컨트롤러가 있을 경우와 없을 경우 화면 전환 동작이 어떻게 다른지, 화면들 포함관계가 있는지 학습한다.
    - storyboard object 사용해서 구현 : 세그로 연결하면 코드 작성 없이 화면 전환 가능, Back 버튼이 자동으로 생성된다.
    - 코드 구현 : push, pop을 이용하여 내비게이션 스택에 쌓는다. Back 버튼은 push된 ViewController에 자동으로 생긴다.

- 내비게이션 컨트롤러 관련 메서드가 왜 push / pop 인지 학습한다.
    - UINavigationController : 계층 적 컨텐츠를 탐색하기위한 스택 기반 스키마를 정의하는 컨테이너 뷰 컨트롤러.
   >  https://developer.apple.com/documentation/uikit/uinavigationcontroller

## step7. Second Scene 화면
- 탭바의 두 번째 화면 (Second Scene) 디자인을 변경하고 액자 앱을 동작을 구현한다.
- 실행화면
- ![screemsh_step7](./img/step7.png)

- UIImageView를 화면 상단 중앙에 240 x 240 크기로 배치 한다.
    - ImageView Width 240 , Height 240 으로 주었다.
    - Autolayout 활용 : Top : Safe Area 50 , Bottom : Horizontally in Container 상단 중앙에 맞춤

- UIImageView 와 UIImage 클래스는 각각 어떤 역할을 담당하는지 학습한다.
    - UIView > UIImageView > UIImage

    1. UIImageView : 단일 이미지 또는 애니메이션 이미지 시퀀스를 표시하는 객체, 즉 이미지 뷰를 사용하면 UIImage객체를 사용하여 지정할 수있는 이미지를 효율적으로 그릴 수 있다.

        > https://developer.apple.com/documentation/uikit/uiimageview

    2. UIImage : 앱의 이미지 데이터를 관리하는 객체, 이미지 객체를 사용하여 모든 종류의 이미지 데이터를 표현할수 있으며 클래스는 기본 플랫폼에서 지원하는 모든 이미지 형식의 데이터를 관리, 이미지 객체는 변경할 수 없으므로 항상 디스크의 이미지 파일이나 프로그래밍 방식으로 생성 된 이미지 데이터와 같은 기존 이미지 데이터에서 이미지 객체를 만든다.

        > https://developer.apple.com/documentation/uikit/uiimage

- 이미지 뷰의 속성은 어떤 것들이 있는지 애플 개발자 문서를 참고한다.
    1. Image View:  Interface Builder에서 이미지 뷰에 대해 구성한 속성을 나열
        - Image : 표시 할 이미지.
        - Highlighted : 이미지 보기가 강조 표시 될 때 표시 할 이미지.
        - State : 이미지의 초기 상태.

        

## step8. 추가 구현사항
-  이미지 테두리 액자 화면을 추가한다.
-  사진 앨범에서 사진을 가져와서 보여줄 수 있도록 개선한다.

- 실행화면
- ![screemsh_step8](./img/step8.png)


- selectButtonTouched에서는 UIImagePickerController로 사진 앱 - 카메라롤에서 사진을 가져오도록 구현한다.
- 선택한 사진을 받기 위해서 구현해야 하는 메서드는 어떤게 있는지 찾아 구현한다.

1. UIImagePickerController 인스턴스 생성과 UIImagePickerController Delegate 구성
    - Xcode안에 자체적으로 이미지를 선택을 수월하게 할 수 있게 Delegate를 만들어놨다.
    - UINavigationControllerDelegate 를 선언해 준 이유 :  UIImagePickerControllerDelegate의 delegate 속성은 UIImagePickerControllerDelegate와 UINavigationControllerDelegate 프로토콜을 모두 구현하는 객체로 정의되어있다. 
      (picker.delegate =  self) self를  picker.delegate에 할당하려면 self는 UINavigationControllerDelegate 타입이어야 한다. 
        지금, picker의 델리게이트를 UINavigationControllerDelegate에 위임해준 것인데, 대리자는 사용자가 이미지나 동영상을 선택하거나 picker화면을 종료할 때, 알림을 받는다. 

    > https://developer.apple.com/documentation/uikit/uiimagepickercontroller
    > https://developer.apple.com/documentation/uikit/uiimagepickercontrollerdelegate

    

2. info.plist에서 권한 설정 해주기.
    - 사용자의 정보에 접근 할 때는 항상 권한 요청이 필요
    - info.plist 에 가서 설정  (Privacy - Photo Library Usage Description(사진앨범 권한))

    

3. 이미지 저장하여 넘겨주기

    - 사진에 관한 정보는 UIImagePickerController.InfoKey 를 통해 넘어온다.

    
- UIImagePickerController처럼 이미 만들어놓은 시스템 컨트롤러들에 대해 학습한다.
    - [뷰컨트롤러 애플 개발자 문서](https://developer.apple.com/documentation/uikit/view_controllers)

- 델리게이트(Delegate)와 프로토콜(Protocol) 상관 관계에 대해 학습한다.
    - 델리게이트란? : 객체 지향 프로그래밍에서 하나의 객체가 모든 일을 처리하는 것이 아니라 처리 해야 할 일 중 일부를 다른 객체에 넘기는 것을 뜻함
