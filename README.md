# linux-study
## 리눅스 학습내용을 기록해두는 용도

### 리눅스 기초
 * 디렉토리와 파일
   * 보통 아이콘을 통해 제어하는 방식으로 사용하는건 GUI방식,명령어를 통해 제어하는 방식은 CLI방식
   * pwd: 현재 디렉토리 위치 확인 명령어
   * mkdir hello_linux: 현 디렉토리 하위에 hello_linux 라는 이름의 새로운 디렉토리를 생성하는 명령어 
   * touch empty_file.txt : touch명령어 뒤에 파일명을 입력하면 비어있는 파일하나를 만들어
   * ls -l : 현 디렉토리에 있는 파일과 디렉토리를 자세하게 보여주는 명령어저렇게 ls명령어 뒤에 ㅣ,al등을 붙히는 것들을 ‘파라미터’라고 함 파라미터는 -뒤에 와야한다.
   * Cd / : 루트 디렉터리로 돌아가는 명령어
   * cd .. :  현 디렉터리의 부모 디렉토리, 즉 바로 위 상위 디렉토리로 이동하는 명령어. 현재 나의 위치에 따라서 ..의 경로가 달라지기 때문에 이런걸 ‘상대경로’라고 하고 위의 / 명령경우 어디에 있든지 바로 루트 디렉토리로 돌아가기에 ‘절대경로’라고 한다.
   * Rm empty_file.txt : 파일을 삭제하는 명령어. 디렉토리는 x
   * rm –r hello_linux : 디렉토리를 삭제하는 명령어.
 * --help와 man
   * –help : 해당 명령어에 대한 설명이 터미널에 출력된다.
   * Man : 알고 싶은 명령어에 대한 설명이 터미널에 출력된다.출력된 상태에서 무언가 단어를 검색하고 싶을땐 / 를 누르고 원하는 명령을 검색하면 해당하는 단어를 찾아주고 n키로 다음위치 보여준다.
 * Sudo
   * super user do 의 약자로 “슈퍼유저가 하는일”이라는 의미이다. = root user.
다만 평소에 root user로 평소 사용하게 된다면 위험한 명령어를 아무생각없이 사용하는경우 대참사가 일어나기 때문에 평소엔 일반 user로 사용하다가 필요할때 root user를 사용하는게 더 안전하다.
   * ex) Apt-get install git => git을 설치하는 명령언데 Permission denied가 뜨면서 설치할수가 없음. 이건 sudo명령어 즉 root user의 권한으로 명령어 수행이 가능하다는 의미임. => sudo apt-get install git 이렇게 해줘야 다운 가능.
 * nano 에디터 사용: 파일생성용이
 * 패키지 매니저
   * 쉽게말해 CLI 방식의 운영체제에서의 앱스토어, 플레이스토어라고 생각하면 편함.
리눅스의 대표적 패키지 매니저는 ‘apt’ 와 ‘yum’ 이 있는데 apt학습하면 yum도 쉽게 이해 가능
   * 우선 apt를 처음 사용시 패키지 매니저를 통해 설치할 수 있는 것의 목록을 최신화 해야함 
=> sudo apt-get update:  apt서버에 접속해 최신 상태의 소프트웨어 목록 다운 받음.’목록만.’
   * sudo apt-cache search (검색할 소프트웨어 이름): apt  
ex) sudo apt-cache search htop => htop택스트와 관련된걸 목록에서 찾아오는듯
   * sudo apt-get install htop : htop이라는 소프트웨어를 다운로드 받는 명령어.
   * sudo apt-get upgrade htop : htop의 새로운 버전으로 업데이트 하는 명령어
   * sudo apt-get remove htop : htop을 삭제하는 명령
### 쉘과 쉘스크립트
 <img src = "https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FPT6ca%2FbtqvwOh188B%2FwxRzSY8euwwyVuUvLlNFLK%2Fimg.png" width="700" height="400"> 출처 : google image
 * hardware는 기계적인 부분 = 디스크,메모리,램 등등
 * kernel : 하드웨어를 직접적으로 제어하는 운영체제의 코어가 되는 부분
 * shell : 사용자가 리눅스에서 입력한 명령은 shell에게 명령하는 것이고 이 명령을 해석해서 kernal이 이해할수 있는 방식으로 전달하고 kernal은 hardware에 해당 명령을 전달해 수행시켜 hardware가 동작하고 이 결과를 다시 kernal에게, kernal이 shell에게 shell이 사용자에게 전달하는 과정을 거친다고 한다 =>    사용자 명령→  shell  → kernal → hardware →  hardware 결과 → kernal → shell → User 
 * echo “문자열” : “”의 내용을 터미널에 출력하는 간단한 명령어
 * echo $0 : 현재 어떤 shell을 사용하는지를 출력해 준다. 일반적으로 bash를 사용한다.
 * Shell Script : 자주 반복되는 어떤 루틴을 만들때 스크립트를 짜두면 짜여진 대로 리눅스가 동작해줌
자동배포 구축할때 사용되려나..>?
 * 공부하기위해 script 디렉토리 내에 nano로 backup이란 파일을 만든다.
 * 맨 윗줄에 #!/bin/bash라고 적어야 하는데  밑에 작성되는 코드가 bin의 bash라는 프로그램으로 실행되야 한다는 의미의 명령어를 먼저 작성해준후 스크립트를 작성해줘야 한다.
 * If ! [ -d bak ];  then => 현 디렉토리에 bak라는 디렉토리가 존재하지 않는다면? 맞으면 밑 로직 실행
          mkdir bak
fi => if가 끝났다는 의미이다
cp *.log bak/  => 반드시 bak파일이 있기에 현 디렉토리의 모든 .log파일들을 bak으로 카피한다는 명령어
저장후 디렉토리에는 bakcup파일이 있고 ./backup 으로 backup파일을 실행시키면 허가거부가 뜨는데 일단 권한 파트는 아니라서 리눅스에게 파일권한을 열어주어야 한다 → chmod +x 파일명
위 명령어로 바꾸고 ls -ㅣ로 확인해보면 파일 정보 맨 앞에 drw나열에서 x가 추가된것을 볼수 있는데 이건 ‘실행가능한’이라는 의미로 파일이 실행가능한 상태에 있다는 의미이다.
*사진추가 할것!
### 디렉토리 구조
 * / : 최상위 디렉토리. root라고 한다.
 * /bin : user Binaries. 우리가 유닉스에서 사용하는 명령(=프로그램)들이 위치하고 있다
 * /sbin : System Binaries. 시스템관리계정이 사용하는 명령어들이 저장되어 있다.
 * /etc : 유닉스 내의 대부분의 프로그램들의 설정 파일 , 유닉스 자체에 대한 설정 파일, 설치한 프로그램의 설정파일 들이 저장되어 있다.
 * /var : variable files. /var 내의 파일들을 바뀔 수 있는 파일들이라고 한다. 앞의 /bin, /sbin은 프로그램들이기 때문에 바뀌지 않고 /etc 역시 설정파일이기 때문에 사용자가 변경하지 않는이상 바뀌지 않는다. 그런데 /var 내의 파일들은 특정 프로그램의 에러로그나, 사용자 접근로그등의 정보들이 저장되기 때문에 계속 변화하는 파일들이다.
 * /tmp : 임시파일들이 저장되는곳. 컴퓨터 재부팅시 tmp내의 파일들은 모두 사라짐. 중요한 파일은 tmp에 저장하면 안된다
 * /home : /home디렉토리 밑에 사용자 파일이 존재한다. → /home  /minyoung
 * /lib : /bin, sbin이 사용하는 라이브러리 들이 저장된 디렉토리
 * /opt : 어떤 소프트웨어를 설치할 때 자동으로 적절한 위치의 디렉토리에 저장이 되는데  만약 설치를 다른곳에다 하고 싶은데 장소가 마땅치 않은경우 /opt 디렉토리에 저장하면 된다는데 나중에 자세히 알아볼것.
 * /usr : 사용자가 설치하는 프로그램들은 /usr 밑에 설치가 된다.
> 파일 찾는 법 
 * find / -name “파일명”: 루트 디렉토리 부터 파일명에 해당하는 파일들의 경로를 찾는다
 * find . -name “파일명”: 현재 디렉토리 부터 파일명에 해당하는 파일들의 경로를 찾는다.
 * find .~-name “파일명”: /home 디렉토리 부터 파일명에 해당하는 파일들의 경로를 찾는다.
 * find . -type f -name “파일명” -exec rm -f {} \;  : -type f → 파일타입인 파일명에 해당하는 것들을 {}에 담고 이걸 -exec(:즉시실행) rm -f 그냥 삭제해라 라는 의미라고 한다. 

