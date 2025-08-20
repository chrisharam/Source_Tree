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