## revert 를 이용해 여러 커밋 되돌리기 (GUI)

1.  브랜치 생성, test 브랜치 만들기
    브랜치를 생성해서 실험을 하면 좋은 점은 쉽게 되돌리고 없앨 수 있다. <br/>
    삭제하면 해당 브랜치에서 작업한 내용은 다 사라진다.

    오늘은 commit 1 의 내용까지 되돌리고 싶다고 가정하고 작업한다.

2.  test.md 파일 만들고 내용 작성

        # test

        - commit 1

    이후 커밋 메세지 commit 1 작성 후 커밋

        - commit 2

    이후 커밋 메세지 commit 2 작성 후 커밋

        - commit 3

    이후 커밋 메세지 commit 3 작성 후 커밋

이때, commit 1으로 돌아가고 싶다고 commit 2 우클릭 후 '커밋 되돌리기(reverse commit)' 클릭하면 충돌이 일어난다. <br/>
이때 에디터에서 '수신 변경 사항 수락' 누르면 commit 1 내용이 있어서 잘 실행된 듯 보여지지만 <br/>
결론적으로 이것은 잘못된 방법!!!! <br/>
이 상황에서 충돌없이 되돌리기하려면 최신 커밋부터 순서대로 revert 를 반복 적용하면 됩니다. (commit 1으로 돌아가고 싶다면, commit2까지 '커밋 되돌리기(reverse commit)'를 하면 된다.)

3.  commit 3 우클릭 후 '커밋 되돌리기(reverse commit)' 클릭
4.  ' Revert "commit 3" ' 내용의 커밋이 생긴 것을 확인할 수 있다. <br/>
    ( commit 2 의 내용과 같다. commit 3과 Revert "commit 3" 은 한 쌍으로 없어진 것과 마찬가지이다.)
5.  commit 2 우클릭 후 '커밋 되돌리기(reverse commit)' 클릭
    ( commit 1 의 내용과 같다. commit 2 와 Revert "commit 2" 는 한 쌍!)
6.  에디터를 확인해 보면 commit 1 의 내용과 같은 것을 확인할 수 있다.

#### 터미널로 해결해보기 (CLI)

1.  터미널로 해결 해보기 위해 "commit 3" 우클릭 후
2.  '이 커밋까지 현재 브랜치를 초기화' 선택 후 'hard' 클릭
3.  이 상태에서 터미널 열고
4.  git revert HEAD ('가장 최근 커밋을 되돌려라' 라는 뜻의 명령어)
    HEAD~1

        HEAD 는 최신 , HEAD~1  는 HEAD의 아빠라는 뜻,
        HEAD 와 HEAD~1 두개를 순서대로 되돌리라는 뜻

        터미널에
        git revert HEAD HEAD~1
        입력 후 적용이 되었다는 내용이 터미널에 떴을 때 빠져나가려면
        :wq  (' revert "commit 3" '에 대한 내용이 완료되었다는 창을 빠져나오기 위해)

        :wq  (' revert "commit 2" '에 대한 내용이 완료되었다는 창을 빠져나오기 위해)

5.  끝!
    소스트리에서 revert 내용이 적용되었나 확인해보기
    commit 3 과 commit 2의 내용이 잘 되돌아갔나 확인해보기

###### 브랜치를 생성해서 테스트한 내용을 다 없애려면 ...

        1. master 로 체크아웃 한 후,
        2. test 브랜치 우클릭 후,
        3. 'test 삭제' 클릭
        4. '강제 삭제' 체크한 후 확인
