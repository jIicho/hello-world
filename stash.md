## commit --amend 와 stash

##### 브랜치 체크아웃시 주의사항

- 브랜치를 만들고 체크아웃을 하려면 현재 작업 디렉토리가 깨끗해야합니다. <br/>
  변경사항이 있을 때에는 다른 브랜치로 체크아웃을 할 수 없다.

1.  test 브랜치를 생성한다. (test 브랜치로 체크아웃)
2.  새로운 내용 작성 후 커밋을 한다.
    - 이 상황에서는 변경사항이 없기 때문에 main 으로 체크아웃이 가능하다.
3.  내용 추가
4.  커밋하지 않은 변경사항이 생김
    이말은 마지막 커밋과 현재 작업디렉토리의 내용이 다르기 때문에 생김. <br/>
    이 때에는 에러가 뜨면서 체크아웃이 되지 않는다.

    ### 이때 급하게 체크아웃을 해야할 때에는 어떻게 해야하는가????

    - 작업 중인 내용을 임시 저장한다.
      1. 브랜치 1에서 일단 (임시) 커밋을 한다.
      2. 브랜치 2로 체크아웃하고 작업을 한다.
      3. 다시 브랜치 1로 되돌아 온다.
      4. 1의 작업을 이어서 마무리 짓는다.
      5. 커밋 덮어쓰기 (commit --amend)를 한다.
      6. (옵션) 필요하다면 (push --force)를 한다.

5.  4의 내용을 우선 커밋 한다.
6.  main으로 체크아웃해서 작업
7.  다시 test 브랜치로 돌아와서 작업.
8.  스테이지에 올리고(add), 커밋 메세지 작성 후 우측의 선택 바 클릭
9.  '마지막 커밋 정정(Amend last commit)' 선택 후 확인
10. 자동으로 커밋 메세지가 작성된다. (이때 그대로 사용해도 되고, 수정해도 좋다.)

        *** push --force 가 필요할 경우는 어떤 때 인가??? ***

        - 의미 없는 내용 커밋 후 푸시를 했을 때 'origin/test'가 생긴다.
        - 이 상태에서 파일 내용을 수정하고 커밋을 하면 마지막 커밋은 바뀐다.
        - 하지만, origin/test 와 최근 커밋이 가지를 이루며 두가지의 커밋이 존재한다.
        - 이때 강제 푸시를 사용하면 정상적으로 돌아온다.
        - 필요없는 브랜치는 main으로 체크아웃 후 test 브랜치를 삭제해준다.
        - 서버에 올라간 origin/test는 우클릭 후 '브랜치'
                -> '브랜치 삭제' 클릭 -> origin/test 선택 후 '브랜치 삭제' 클릭
        ----------------------------------------------------------------

    - stash를 이용해서 같은 작업 하기

      1. 'test2' 브랜치 만들기 (test2 브랜치로 체크아웃)
      2. 파일에 내용을 적고 커밋하기
      3. 같은 파일에 내용을 추가하면 올라가지 않는 파일이 생긴다.(체크아웃이 안됨.)
      4. 이때 상단에 'stash' 클릭 후 '임시 작업 1' 입력 후 확인
      5. 내용이 사라졌음을 확인할 수 있다.
      6. main 으로 체크아웃해서 작업을 다 마친 후에
      7. tast2 브랜치로 다시 체크아웃 한 후
      8. 스태시 밑에 있는 '임시 작업 1' 우클릭한 후 '스태시 적용'을 누른다.
      9. 에디터에 다시 내용이 뜨는 것을 확인할 수 있다.
      10. 작업한 후 커밋하면 된다.
          즉, 불필요한 커밋을 생성하지 않는 방법으로 stash를 사용한다.

          **_ 주의 사항 _**

          - 스테이지에 한번도 올라가지 않은 파일은 스태시 기능을 사용할 수 없다.
          - 이때, 일단 스테이지에 올린 후(add) 스태시를 사용할 수 있다.
          - 다 작업해서 불필요한 stash는 우클릭 후 '스태시 삭제' 클릭하면 삭제 시킬 수 있다.

      11. 다 사용한 test2 브랜치는 main으로 체크아웃 후 삭제해준다!
