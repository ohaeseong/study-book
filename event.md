# element 가져오기

### - getElementById("id 이름");


# 이벤트 정리

### mouse event

#### mousedown, mouseup

- mousedown 마우스 클릭(누를때)할 경우 일어나는 이벤트이다.
- mouseup 마우스 클릭 후 다시 마우스 트리거가 올라올때 (누르던 마우스를 땔때) 일어나는 이벤트이다.

### event remove

- element.removeEventListener("삭제할 이벤트 이름", 삭제할 이벤트 핸들러);

예제)
```
  document.addEventListener("mousedown", () => {
    console.log("이벤트 추가");
  });
  
  document.removeEventListener("mousedown", () => {
    console.log("이벤트 삭제");
  })
```
