# hello git

## git 명령어 요약

- clone : 원격 저장소 복사
- add : 스테이지 영역에 작업 파일 추가
- commit : 세이브, 스테이지 영역의 파일들을 가지고 커밋(=세이브) 를 만들 수 있다.
- push : 원격 저장소에 커밋을 업로드한다.

### 코드 뭉치 버리기(Discard hunk) \_ 변경 사항 취소하기

- 이미 ctrl + s 해버린 작업한 내용이 마음에 들지 않아서 돌아가고 싶을때,
  즉, 이미 Sourcetree 'Uncommitted changes' 가 나타났을 경우
  가장 마지막 커밋으로 돌아가고자 할때

1. Uncommitted changes 클릭
2. Unstaged files 밑에 있는 파일 클릭
   (이때 내가 수정한 내용을 확인 할 수 있다.)
3. 우측 상단에 'Discard hunk' 클릭
4. 'OK' 클릭
