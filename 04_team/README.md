## 유동형 그리드(Fluid Grid)
### 설명
- Grid는 웹페이지를 위한 이차원 레이아웃 시스템이다. 이 기능을 통해 콘텐츠를 행과 열에 배치할 수 있으며 복잡한 레이아웃을 직접 직관적으로 구축 가능하다. 
- Fluid Grid란 웹사이트를 제작할 때 화면의 크기에 관계없이 자유롭게 늘어나거나 줄어들 수 있도록 픽셀(px) 대신 퍼센트(%)로 제작하는 기술이다. Grid의 너비를 Flexible Image와 마찬가지로 창의 너비에 대응되는 가변 너비로 설정한다.

#### Fluid Grid의 중요성
- 적응 형 그리드에서는 픽셀 기반으로 크기를 지정한다. 따라서 특정 장치 viewport에서 너비와 높이를 수동으로 조정해야한다. 유동 격자는 상위 컨테이너의 크기 내에서 자연스럽게 흐르기 때문에 다양한 화면 크기와 장치에 대한 대응이 가능하다.
- 모바일 크기가 점점 작아지고 있고 반면 데스크톱은 해상도가 높아질수록 점점 더 넓어지고 있다. 유동형의 장점은 최대 너비를 조정할 수 있으며 백분율 기반 계산으로 인해 더 큰 화면에서 계속 작동할 수 있다는 것이다.


#### Fluid Grid 실제 적용 사례
- [palantir.net](https://www.palantir.net/services)
- 아래 예시에서 웹페이지의 너비가 작아질수록 유동적으로 변하는 모습을 볼 수 있다. 
<img src="./assets/fluid-grid-1.gif" width="800">

### 예제
#### Fluid Grid 계산
- 디자인한 Grid의 간격을 측정한 뒤, 전체 페이지에서 하나의 Grid가 차지하는 공간이 몇 `%`인지를 계산하여 가변단위인 `%`로 값을 설정해 주면 Grid가 창 너비에 따라 가변적으로 변하여 동작할 수 있다.

    1. 가변 너비 
        - (가변 크기로 만들 박스의 가로 너비 / 가변 크기로 만들 박스를 감싸고 있는 박스의 가로 너비) * 100 = 가변 크기의 %값
        
        - 위 예시처럼 퍼센트를 사용해 그리드의 크기를 정해주면 사용자가 사용하는 브라우저의 크기에 맞춰 개발이 가능하다.
        - 브라우저의 크기가 변하거나 사용하는 디바이스의 크기에 맞춰 자동으로 변하는 컨텐츠를 기대할 수 있다.

    2. 가변 마진
        - 웹 사이트의 요소에 마진과 패딩을 설정할 때는 모든 박스들을 감싸고 있는 요소들의 너비값을 고려하여 요소의 마진값과 패딩값을 지정해야 한다. 
        - 만약 너비값을 고려하지 않고 마진값과 패딩값을 설정하면 박스들이 밀려 아래로 떨어지는 등 의도했던 대로 레이아웃이 나오지 않을 수 있다.
        - 반응형 웹사이트에서는 모든 요소는 가변적이어야 한다.
        - (가변 마진을 적용할 마진값 / 적용할 박스를 감싸고 있는 박스의 가로 너비) * 100 = 가변 마진 % 값

    3. 가변 패딩
        - (가변 패딩을 적용할 패딩값 / 적용할 박스를 감싸고 있는 박스의 가로 너비) * 100 = 가변 패딩 % 값

- 유동형 그리드 HTML, CSS 예시
    - HTML
        ```html
        <div id="wrap">
            <div class="container">
            <div id="first"></div>
            <div id="second"></div>
            </div>
        </div>
        ```
    - CSS
        ```css
        #wrap {
            width: 80%;
            height: 500px;
            ...
        }

        .container {
            width: 80%;
            height: 450px;
            ...
        }

        #first {
            width: 33.33%;
            background-color: aqua;
        }

        #second {
            width: 66.67%;
            background-color: greenyellow;
        }

        ...
        ```

- 결과
<img src="./assets/fluid-grid-2.gif" width="800">
    - 각 컨테이너의 너비가 유동적으로 화면의 크기에 따라 유동적으로 달라짐을 확인할 수 있다.