# Git 명령어
#### 디렉토리 이동
|명령어|기능|
|:--:|--|
| cd [디렉토리명] | 선택한 디렉토리로 이동 |
| pwd | 현재 위치 확인 |
| mkdir [디렉토리명] | 새 디렉토리 만들기 |
| ls | 디렉토리 내용 출력(ls -al로 합쳐서 사용 가능) |
| ls -a | 디렉토리의 숨김 파일과 디렉토리까지 출력 |
| ls -l | 디렉토리안에 있는 폴더 상세 정보 출력 |
  
### Git commit 명령어  
|명령어|기능|
|:--:|--|
| git init | 현재 지역 저장소에 초기화하기 |
| git add | stage area에 파일 추가(commit하기 전 준비 단계) |
| git status | 현재 깃의 상태 확인 |
| git commit | stage area에 있는 파일을 커밋 |
| git commit -m "커밋메세지" | 커밋 메세지와 동시에 커밋하기 |
| git push origin master | origin master브랜치에 푸쉬 |
#### 발생 에러 : error: failed to push some refs to  
- 원격 저장소와 로컬 저장소의 상태가 달라서 나는 에러  
시도 1 - 검색하다 ```git push -f origin```명령어를 발견하고 시도해봄  
-> 기존에 올려놨던 파일이 전부 날라감...  
시도 2 - ```git pull origin main --allow-unrelated-histories```명령어 사용  
        서로 관련없는 두 프로젝트를 병합할 때 예외를 주는 방법으로 해결  




