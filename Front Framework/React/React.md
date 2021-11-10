# React



useRef

useEffect(() => {

}, [] ) : 빈칸 넣어넣으면 한번만 실행 (onMounted)

[stata] 특정 스테이트 넣어놓으면 동작할 때만다 변경됨(watch state) 

useRef()

> useRef는 .current 프로퍼티로 전달된 인자로 초기화된 변경 가능한 ref 객체를 반환합니다. 반환된 객체는 컴포넌트의 전 생애주기를 통해 유지될 것입니다.
>
> DOM에 접근하는 방법으로 refs에 친숙할 지도 모르겠습니다.
>
> ref 속성보다 useRef()가 더 유용합니다.
>
> useRef()는 순수 자바스크립트 객체를 생성합니다. 

props.children

> 컴포넌트 태그 사이에 넣은 값을 조회하고 싶을때

props는 properties 의 줄임말입니다. 우리가 어떠한 값을 컴포넌트에게 전달해줘야 할 때 props를 사용합니다.



React Hooks

useEffect 함수는 리액트 컴포넌트가 렌더링 될때마다 특정 작업을 실행할 수 있도록 하는 Hook이다.







object-fit

canvas나 부모 요소에 넣어보기 (바로 상위 요소에만)

objectFit : 'contain'



canvas에 width: 100%, height:100%



해상도 문제를 어떻게 할 것인가

창 크기에 대해서 