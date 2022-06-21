# LeeEuiJin

# ☀️Weather APP Clone Coding Conventions☀️

## 1. Git Convention
<details>
<summary>토글 접기/펼치기</summary>
<div markdown="1">
-> Issue Name : [PREFIX] 구현 기능
-> Branch Name : feature(prefix)#1-구현 기능
-> Commit Message : [PREFIX] #1 구현 기능

### Prefix List
* **FEAT** : 새로운 기능 구현
* **ADD** : Feat 이외의 부수적인 코드 추가, 라이브러리 추가, 새로운 View나 Activity 생성
* **CHORE** : 그 이외의 잡일/ 버전 코드 수정, 패키지 구조 변경, 파일 이동, 가독성이나 변수명, reformat 등
* **FIX** : 버그, 오류 해결
* **DEL** : 쓸모없는 코드 및 파일 삭제
* **MOD** : xml (스토리보드) 파일만 수정한 경우
* **MOVE** : 파일 위치 이동
* **DOCS** : README나 WIKI 등의 문서 개정
* **REFACTOR** : 내부 로직은 변경 하지 않고 기존의 코드를 개선하는 리팩토링 시

</div>
</details>

## 2. Foldering
<details>
<summary>토글 접기/펼치기</summary>
<div markdown="1">

![2C670D55-C561-4340-947E-A97B532D8F7E](https://user-images.githubusercontent.com/60493070/174737587-8406147f-2f08-4660-9e48-e7d78580a32b.png)

</div>
</details>

## 3. Code convention

<details>
<summary>토글 접기/펼치기</summary>
<div markdown="1">

<aside>
🔥 ****진짜 꼭 지킵시다!****

---

- 스타일쉐어의 스위스트 스타일 가이드를 참고합니다.
    
    [GitHub - StyleShare/swift-style-guide: StyleShare에서 작성한 Swift 한국어 스타일 가이드](https://github.com/StyleShare/swift-style-guide)
    
</aside>

## ## 코드 레이아웃


---

### 공백

- 콜론(`:`)을 쓸 때에는 콜론의 오른쪽에만 공백을 둡니다.
    
    ```swift
    let names: [String: String]?
    ```
    

- 빈 줄은 딱 한 줄 정도만.. 너무 많은 빈 줄은 지양합니다.

### MARK 구문

- MARK 구문 위와 아래에는 공백이 필요합니다.
    
    ```swift
    // MARK: Layout
    
    override func layoutSubviews() {
      // doSomething()
    }
    
    // MARK: Actions
    
    override func menuButtonDidTap() {
      // doSomething()
    }
    ```
    

- MARK 구문의 순서는 아래와 같습니다.
    
    ```swift
    // MARK: - Properties
    
    // MARK: - Lifecycle
    
    override func viewDidLoad() {
        super.viewDidLoad()
    }
    
    // MARK: - Override Method UI + Layout
    
    override func configUI() {
        
    }
    
    override func setupAutoLayout() {
        
    }
    
    // MARK: - Custom Method
    
    // MARK: - @objc
    
    ```
    

- Cell 파일은 `// MARK: - Lifecycle` 대신 아래와 같습니다.
    
    ```swift
    // MARK: - Initializing
    
    override init(style: UITableViewCell.CellStyle, reuseIdentifier: String?) {
        super.init(style: style, reuseIdentifier: reuseIdentifier)
    }
    
    required convenience init?(coder aDecoder: NSCoder) {
        self.init(style: .default, reuseIdentifier: nil)
    }
    ```
    
- Delegate나 Datasource를 extension으로 빼줄 경우 위에 마크구문을 꼭 써줘야 합니다.
    
    ```swift
    // MARK: - UICollectionViewDelegate
    
    extension MainVC: UICollectionViewDelegate {
    
    …
    
    }
    ```
    

### 임포트

- 모듈 임포트는 `알파벳 순`으로 정렬합니다.
- 내장 프레임워크를 먼저 임포트하고, 빈 줄로 구분하여 서드파티 프레임워크를 임포트합니다.
    
    ```swift
    import UIKit
    
    import SwiftyColor
    import SwiftyImage
    import Then
    import URLNavigator
    ```
    

## ## 네이밍


---

### 액션 함수 네이밍

- Action 함수의 네이밍은 ‘주어 + 동사 + 목적어’ 형태를 사용합니다.
    - Tap(눌렀다 뗌)**은*`*.touchUpInside*`*에 대응하고,*
- **Press(누름)**는  `.touchDown`에 대응합니다.
    - **will~**은 특정 행위가 일어나기 직전이고, **did~**는 특정 행위가 일어난 직후입니다.
    - **should~**는 일반적으로 `Bool`을 반환하는 함수에 사용됩니다.
    
    ```swift
    func backButtonDidTap() {
      // …
    }
    
    touchUpBackButton
    
    ```
    

## ## 권장사항


---

### 변수 초기화

- 가능하다면 변수를 정의할 때 함께 초기화하도록 합니다.
- [Then](https://github.com/devxoul/Then) 라이브러리를 사용하면 초기화와 함께 속성을 지정할 수 있습니다.
    
    ```swift
    let label = UILabel().then {
      $0.textAlignment = .center
      $0.textColor = .black
      $0.text = “Hello, World!”
    }
    ```
    
    ```swift
    var job: String = “iOS Programmer”
    ```
    

### enum

- 상수를 정의할 때에는 `enum`를 만들어 비슷한 상수끼리 모아둡니다.
    
    재사용성과 유지보수 측면에서 큰 향상을 가져옵니다. 
    
    `struct` 대신 `enum`을 사용하는 이유는, 생성자가 제공되지 않는 자료형을 사용하기 위해서입니다.
    
- [CGFloatLiteral](https://github.com/devxoul/CGFloatLiteral)과 [SwiftyColor](https://github.com/devxoul/SwiftyColor)를 사용해서 코드를 단순화시킵니다.
    
    ```swift
    final class ProfileViewController: UIViewController {
    
      private enum Metric {
        static let profileImageViewLeft = 10.f
        static let profileImageViewRight = 10.f
        static let nameLabelTopBottom = 8.f
        static let bioLabelTop = 6.f
      }
    
      private enum Font {
        static let nameLabel = UIFont.boldSystemFont(ofSize: 14)
        static let bioLabel = UIFont.boldSystemFont(ofSize: 12)
      }
    
      private enum Color {
        static let nameLabelText = 0x000000.color
        static let bioLabelText = 0x333333.color ~ 70%
      }
    
    }
    ```
    

### final

- 더이상 상속이 발생하지 않는 클래스는 항상 `final` 키워드로 선언합니다.
    
    ```swift
    **final** class MyViewController: UIViewController {
      // …
    }
    ```
    

## ## ViewController


---

- ViewController, TableViewCell, CollectionViewCell
    - `VC`, `TVC`, `CVC`로 축약해서 사용합니다.
  </div>
</details>
