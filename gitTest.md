1. 저장소로 쓸 위치로 이동한다.
  $ git config --global user.name "yhay"
  $ git config --global user.email "y83422918@gmail.com"

2. $ git init
   $ git add README.md #추가할 파일 "add"

   $ git status #추가할 파일리스트를 보기 위한 명령어
   $ git commit -m "first commit" #파일 추가할 때 메모할 commit ment

   $ git remote add origin https://github.com/YHAY/{project_name}.git #origin으로 쓸 곳을 작성
   $ git push -u origin master #origin master 입장으로 push하겠다.
