<<Git 수업 버전 관리 파일>>

<명령어>
1. commit 하기 전 상태의 파일 삭제
discard

2. 이전의 버전은 (삭제)하면서, 돌아가고 싶은 버전으로 돌아가기
reset

hard 모드: 이전 버전 뿐만 아니라 working file도 삭제
mixed 모드: 이전 버전 commit된 것만 삭제 & working file은 남김

3. 해당 버전은 (취소)하면서도, 이전 버전으로 돌아가 수정할 수 있도록.
resert(reserve commit)
-------------------------------------------------------------
<브랜치>
같은 파일을 다른 버전으로 관리하기 위함
--> master branch(main)으로 가서 병합하고자 하는 브랜치를 merge

1. Conflict 같은 코드 부분을 두 브랜치가 수정 --> 충돌 --> 사람이 해결해야 함
(코드상은 아래)
<<<<<<< HEAD
			<li>Branch</li>	// head부분이 수정한 부분
=======		// 를 기준
			<li>브랜치</li>	// 실험2가 수정한 부분
>>>>>>> 실험2

Resolved Conflicts - Marked Resolved 를 체크하여, Git에게 충돌 해결을 알림

2. Conflict를 예방할 수 있는 방법 == 실험 브랜치가 끊임없이 master브랜치를 동기화!

3. origin/master인 부분 VS master인 부분

	: 실제로 서버에 반영			: 서버에 반영되지 않고 로컬에서 추가한 부분

4. 협업
push의 갯수 : 원격 저장소와 local의 버전을 일치시킨후, 원격 저장소에 몇 개가 추가되었는지.
1) 원격 저장소의 내용을 pull하여 자신의 local 환경과 동기화한다.
2) 동기화를 마친 후, 자신의 코드를 Push한다.
(만약 상대가 원격 저장소에 올린 상태 --> 자신이 pull하지 않고 바로 push한다면, git이 오류를 냄 = pull 먼저 하고, 자신의 것을 push.)

add: 변경된 파일을 곧 커밋할 영역에 올림
commit: 로컬에 변경사항 저장(확정 및 기록)
pull: 원격 저장소의 최신 변경사항을 가져와서, 로컬 브랜치에 병합
push: 로컬 저장소의 커밋들을 원격 저장소에 업로드

"pull --> work --> commit --> pull --> push"
+)Work-->pull후 Commit할 경우: 로컬의 변경사항을 확정짓지 않은 상태에서 병합=충돌 발생

3) conflict 발생시(같은 내용을 두 사람이 2번째의 pull없이 push하는 경우)
--> 나중에 push하는 사람 혹은 diff를 사용하여 코드를 해결해야 함 
--> 코드 해결 후, Resolved conflict - Marked resolved를 체크 
--> push하기
(1) 로컬안에서 브랜치 간의 충돌
(2) 로컬과 원격 저장소 간의 충돌 

4) diff로 conflict 해결하기
Resolved conflict-launch external merge tools
Base: 공통된 부모
local: 현재의 브랜치
Remoe: 다른 브랜치

5) stash : Commit하지 않은 작업들을, 안전한 장소(stash)에 보관
--> 버그들이 속출할 때, 유용

6) tag : 별도로 기록해야 하는 것들이 있을 때
--> 실제로, commit한 것들 or 브랜치에 붙일 수 있음.

이전에 만든 버전의 브랜치에도, 태그를 붙일 수 있음(브랜치의 specified에 태그를 넣음)


