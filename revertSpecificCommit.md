### revert 개념 이해하기

1. 선택한 하나의 커밋의 변경사항을 되돌린다.
2. 그와 동시에 취소하는 새로운 커밋 생성

- 즉, 우리가 선택한 커밋은 취소된다. 하지만 그 커밋이 사라지는 것이 아니라 커밋을 되돌리는 새로운 커밋이 생성된다.

###### cherry-pick 과 비슷하면서도 반대로 동작한다.

##### revert로 여러 커밋을 되돌리려면 최신부터 순서대로 revert 를 반복 적용하면 된다.

#### 특정 커밋 하나만 취소하고 싶을 경우에는 어떻게 하는가???

- 그냥 선택해서 revert 를 하면 된다.
- 충돌이 날 가능성이 있다.

##### 충돌이 안나는 경우로 만들어서 직접 사용해보자.

        1. 임시 브랜치 생성
        2. 3 커밋 만들기
           (충돌이 나지 않도록 하기위해 커밋을 세가지 커밋을 세 파일로 나누어 커밋한다.)
        3. 2번째 커밋만 되돌리기
        4. 모두 되돌리기
        5. 임시 브랜치 삭제

1. 'revert-test' 브랜치를 생성 ('revert-test' 브랜치로 체크아웃 된 것을 확인)
2. 텍스트 파일 세개를 만든다.
   - revert1.txt -> revert1 (revert test 커밋 1)
   - revert2.txt -> revert2 (revert test 커밋 2)
   - revert3.txt -> revert3 (revert test 커밋 3)
3. 하나하나씩, 세 파일을 커밋한다.
4. revert2 커밋이 필요없을 때,
   revert2 커밋 우클릭 후 reverse commit 선택
5. 'Revert "revert test 커밋 2"' 커밋이 자동으로 생기면서 revert2 파일이 사라진 것을 확인할 수 있다.
6. revert1 과 revert3 파일은 그대로 유지되어있는 것을 확인할 수 있다.

---

###### 모두 되돌리기 다시 한번 연습!!!

7. 'revert test 커밋 3' 커밋 우클릭 후 reset 하기
8. 다시 모든 파일이 생겨난 것을 확인.
   **_ 최신 커밋부터 순서대로 revert 하면 된다._**
   'revert test 커밋 3' 우클릭 후 커밋 되돌리기 (reverse commit) 선택 <br/>
   'revert test 커밋 2' 우클릭 후 커밋 되돌리기 (reverse commit) 선택 <br/>
   'revert test 커밋 1' 우클릭 후 커밋 되돌리기 (reverse commit) 선택 <br/>
9. 'main'으로 체크아웃 한 후 'revert-test'브랜치 우클릭 후 브랜치 삭제 선택 - 강제 삭제 체크한 후 확인
