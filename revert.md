## 이 전에 배운 내용

- 커밋의 내용을 되돌리는 방법은 세가지가 있다.
- reset을 이용해 되돌리는 방법
  되돌아가고 싶은 커밋 우클릭 후
  '이 커밋까지 현재 브랜치를 초기화' 클릭
  'hard' 선택 후 확인
  (git push --force : 강제 푸시)

- branch를 만들어서 되돌리는 방법
  되돌아가고 싶은 커밋 우클릭 후
  '브랜치' 선택
  브랜치 생성 후 새로운 브랜치로 체크아웃해서 작업한 후
  master로 다시 체크아웃 한 후
  새로 생성한 브랜치에서 작업한 내용 우클릭 후 병합하기

## revert

1. 새로운 내용 추가 후 커밋하기
2. 새로 추가된 커밋, 방금 추가시킨 커밋을 우클릭 후
3. '커밋 되돌리기' 클릭
4. 저절로 커밋이 하나 더 생긴다.
5. 새로 추가했던 내용이 사라진 것을 확인할 수 있다.
   \*\* 다시 돌아가고 싶을때,
   저절로 생긴 커밋 이 전의 커밋을 우클릭 후
   '이 커밋까지 현재 브랜치를 초기화' 선택
   'hard' 선택 후 확인.
   내용이 다시 내용이 생기는 것을 확인할 수 있다.

- 장점 : 리버트로 되돌릴 경우, 내용은 바뀌었지만 여전히 커밋이 남겨져있다.
  커밋을 남기고 되돌리는데 모양도 깔끔하게 사용할 수 있다.
- 단점 : 충돌이 나기가 쉽다. 즉, 사용하기가 어렵다.

  \*\* C0

       C1      <- master_1

            -> git commit
       C2      <- master_2

            -> git commit
       C3      <- master_3

            -> git revert C3
       C3'     <- master_4

                            새로운 커밋이 생기면서 내용은 'C2' 와 같다.
                            C3 의 커밋은 유지된 상태로..

  즉, 'revert' 는 커밋이 사라지는 'reset' 과 달리
  커밋을 보존하면서 작업 디렉토리의 내용만 되돌릴 수 있다.