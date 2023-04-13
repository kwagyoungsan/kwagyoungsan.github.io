---
title:  "[iOS] Move to Trash 와 Remove Reference 의 의미"

categories:

- iOS
  tags:
- [iOS, TIL]

toc: true
toc_sticky: true

date: 2023-03-02
last_modified_at: 2023-03-02
---

### Move to Trash

- 참조부터 물리적인 파일까지 모두 삭제한다.
- Copy items if needed 속성을 체크했을 경우 복사된 파일과 참조가 지워진다.
- Copy items if needed 속성을 체크하지 않았을 경우 복사된 파일 없이 레퍼런스만 참조하기 때문에 참조가 지워진다.

### Remove Reference

- 파일을 추가할 때 Copy items if needed 속성을 체크하지 않았을 경우 원본의 레퍼런스만 참조하고있는 상황이기 때문에 Remove Reference를 선택해도 무방하다.
- Copy items if needed 속성을 체크했을 경우 프로젝트 내에 복사된 파일이 존재하기 때문에 Remove Reference로 지웠다고 해도 복사된 파일이 그대로 남아있다.

### 결론

- 원본 레퍼런스에 대한 참조만 지우고 싶다 → Remove Reference
- 참조와 복사된 파일도 함께 지우고 싶다 → Move to Trash

###### References
- 

[맨 위로 이동하기](#){: .btn .btn--primary }{: .align-right} 