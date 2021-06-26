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
 * whereis : 원하는 실행파일의 위치를 찾아주는 명령어이다. ex) whereis ls => bin/ ls  
 * $PATH : whereis로 ls를 찾았더니 /bin/ls 즉 bin 디렉토리에 명령에 대한 프로그램이 있다고 한다.
그렇다면 저기 있는 ls는 어떻게 실행되는 걸까?  우리가 사용하는 명령어들은 사실 $PATH라는 변수가 숨겨져 실행된다. $PATH는 각 디렉토리의 경로를 담고 있고, 이 경로들에서 ls라는 명령을 찾아주는 역할을 한다고 한다고 하고 이러한 $PATH, 즉 내가 만든게 아닌 운영체제에서 갖춰져 있는 변수를 ‘환경변수’라고 일컫는다
## 프로세스와 실행
> 컴퓨터의 구조
* ssd,hdd : storage
* ram(ddr) : memory
* cpu(중앙처리장치) : processor
* storage와 memory는 둘다 저장장치인데 왜 둘이 나뉘어 있지? → storage는 용량은 많지만 속도가 느림. cpu의 정보처리 속도를 따라가지 못하는 불상사가 발생해선 안되기에 프로그램이 실행되면 storage에서 ram으로 적재 시킨다.그리고 사용되지 않는 프로그램들은 storaege에 남아있다.ram에 올라와있는 상태의 프로그램을  cpu가 읽어서 프로그램대로 동작후 데이터를 처리하는 과정으로 동작한다.프로세스는 사용자가 입력하는 명령어(mkdir,top,rm등)들은 디렉토리 안에 파일의 형태로 저장이 되어있다. 이 파일들을 storage에 저장되어 있고 storage에 저장되어있는것들을 프로그램이라고 하기 때문에 명령어 파일역시 프로그램이라고 정의한다. 즉 프로세스는 실행되고 있는 프로그램 = ram에 올라가 있는 프로그램 = cpu에게 처리 되는 상태의 프로그램 이다.
> 프로세스 모니터링
* 기본적으로 ps,top,htop이 있다.
* htop을 기준으로 초록색 row중 원하는걸 클릭하면 클릭된 컬럼을 기준으로 정렬되 배치된다.
  * cpu 컬럼은 해당 프로세스가
  * mem은 해당 프로세스가 물리적으로 메모리를 얼만큼 사용하고 있는지 표기해 준다
  * Time+은 해당 프로세스가 실행된 시간을 표기해 준다.
  * command는 해당 프로세스가 어떤 명령어로 실행되었는지 표기해 준다.
  * RES 는 해당 프로세스가 실제적으로 메모리를 얼만큼 사용하고 있는지를 표기해준다.
* 상단의 1,2,3,4는 cpu의 갯수, 4개의 코어를 가진것을 알 수 있고 각 코어가 얼만큼의 일을 하고 있는지를 표기해준다.
>  백그라운드 실행
* 일반적으로 어떤 프로그램을 사용하다. 이 상태는 그대로 하고 다른 프로그램을 사용하고 싶은 경우 ctrl+z를 누르면 터미널 상태로 돌아오게 된다. 예를 들어 nano로 파일을 만들다 저장이 잘되었는지 확인하고 싶은 경우 터미널로 잠깐 나가서 확인하는 편이 nano를 종료했다 확인하고 다시 실행하는 과정보다 훨~씬 편하기 때문이다. 이러한 경우 nano가 백그라운드 상태가 되고 터미널에서 실행된 명령어나 프로그램들이 포그라운드 상태가 된다.fg명령어를 사용해서 다시 백그라운드 상태의 프로그램을 멈춘 그 상태로 사용할 수 있고 ctrl+z로 멈춰논 프로그램들이 많은 경우 ‘jobs’라는 명령어를 통해 백그라운드 리스트를 확인할수 있으며 왼쪽 숫자가 높은것이 가장 최근 백그라운드 상태가 된 프로그램이다. 숫자옆에 +,-,공백은 +가 fg명령시 실행될 프로그램,-가 +다음 순서, 공백이 -다음순서...이런 방식이다. 스택구조로 구현한듯 하다.
> daemon의 개념
* ls,rm등 사용했던 명령어는 명령어를 입력해야 동작한다.
* daemon은 항상 켜져 있는 프로그램이라고 한다.
* 냉장고(=daemon)와 tv(=명령어)라고 생각하면 이해가 쉽다.
* Etc / init.d 디렉톨는 데몬 프로그램이 저장되는 디렉토리.
* 데몬 프로그램은 sudo service 프로그램명 start or stop 라는 명령으로 실행,종료가 가능하다. => 대부분의 데몬 프로그램은 service라는 명령어와 start,stop 으로 제어가 가능하다.
* 그렇다면 내가 데몬 프로그램을 추가해야 되는 경우 혹은 현재 구동되고 있는 데몬 프로그램들을 조회하고 싶은 경우 /etc 디렉토리의 rc3.d(CLI방식에서 사용)라는 디렉토리를 확인해보면 데몬 프로그램들의 리스트가 나오는데 [ S01데몬명 → ..디렉토리주소 ]이러한 형식을 갖춘걸 볼 수 있다.
여기서 s는 리눅스(CLI) 부팅시 데몬 프로그램을 실행해주는 의미이고 뒤의 숫자는 우선순위이다 
→ 는 링크인데 디렉토리와 해당 명령어를 링크해 실행해줬다고 당장은 이해하면 될 것 같다.
> 정기적 실행 – cron
* 시스템을 운용하다 보면 정기적, 주기적으로 해야 할 작업들이 있을것이다. 그날 작업한 내용의 백업, 특정 데이터 항상 누군가에게 전송하는등 이런 정기적으로 해야할 작업을 처리할 경우 ‘cron’이라는 것을 사용하면 해결할 수 있다.
* 터미널에서 crontab -e라는 명령어로
* cron에디터 내부 제일 밑엔  m h  dom  mon  dow     command 가 주석으로 달려 있는데
  * m : 분. 10m은 h값이 따로 없다면 매 시간 10분마다 명령을 동작한다는 의미이고 */10 은 ‘10분에 한번’ 이라는 의미 이다.
  * h : 시간. 즉 10 1 이렇게 되있으면 1시 10분에 실행된다는 의미이다.
  * dom : 한달에서 몇 일 인지. 즉 10 12 24 는 매달 24일 12시 10분에 명령을 동작한다는 의미이다.
  * mon : 년에서 무슨 달인지. 즉 10 12 24 5 는 매년 5월 24일 12시 10분에 명령을 동작한다는 의미이다.
  * dow : 요일을 의미한다.
  *  command : 시행할 작업을 입력해준다
  * 만약 */1 * * * * date >> date.log 면 1분에 한번씩 date(현재 시간 출력) 명령을 date.log파일에 입력하는 작업을 정기적 작업으로 설정해주게 되고. tail -f date.log로 date.log파일의 상태를 보고 있으면 1분마다 시간이 찍히는 것을 확인할 수 있다 또한 명령에서 에러가 발생하게 되는 경우가 있는데 에러는 오류 출력 스트림으로 출력을 볼 수 있기 때문에 date >> date.log 2>1 : 2>&1하게 되면 표준 에러를 표준 출력스트림으로  바꿔주어 에러가 표준 출력으로 리다이렉션되어 date.log에 같이 찍히게 된다.
## 사용자
> 다중 사용자
 유닉스 기반 운영체제는 기본적으로 다중사용자가 사용할 수 있도록 설계되었기 때문에 여러명이 하나의 리눅스를 사용하는 경우 어떤 장단점이 있고 어떤 위험이 있는지 정도는 숙지해야 한다고 생각한다.
* id : id를 터미널에 명령하면 id목록들이 나온다. uid라는 항목이 나의 id이다.
* who : who를 명령하면 현재 시스템이 누가 접속해 있는지 가시해준다.
> 관리자와 일반 사용자
사용자에는 super user(관리자)와 user(일반 사용자) 가 있다. 
* 일반 사용자는 sudo 명령을 사용할 수 없다.
* root 유저는 일반적으로 이름도 root일 확률이 높다. 그리고 터미널의 $표기가 되있다면 일반 유저라는 의미이다. 슈퍼유저는 #으로 되어있다. 그렇다면 슈퍼유저로 설정은 어떻게 할까?=> su – root 라고 한다면 root에 대한 패스워드만 알고 있다면 root유저를 사용할 수 있게 된다. 다만 일반적으로는 root유저는 락을 걸어 놓는게 안전하다.
* Root 유저는 기본적으로 최상위 디렉토리 밑의 /root 디렉토리가 홈디렉토리로 설정되어있다. 
> 사용자 추가
* sudo useradd -m duru :  사용자를 추가하는건 당연히 super user의 권한으로 가능하다. useradd와 -m 유저명 으로 새 유저를 생성가능하고 확인해 보려면 home 디렉토리로 가서 목록을 확인하면 위의 duru라는 사용자가 생성된 것을 볼 수 있었다.
* duru를 사용해보려 su - duru를 해도 비밀번호를 세팅하지 않았기에 사용 불가하다.
  * sudo passwd duru : passwd 유저명 으로 비밀번호를 세팅할 수 있다.
* sudo useradd -a -G sudo duru : duru 유저에게 super user의 권한으로 명령어 수행이 가능하게 하는 명령어.

## 권한
> 권한 기본
1. touch perm.txt를 만들고 ls -l perm.txt 하면 파일의 상세정보를 출력해준다.
1. => -rw-rw-r-- 1 minyoung minyoung 0  6월 16 23:55 perm.txt 이런식으로 출력되는데 echo hi > perm.txt 로 hi라는 문자를 저장해준다.
1. 이후 duru 계정으로 접속해 위의 perm.txt를 확인해 보겠다. 해당 파일을 확인후 hello라는 문자를 저장해 주려 하면 Permission denied 오류가 발생한다.즉 파일에 대한 권한이 없어 접근 불가하다는 것이다.그럼 저 파일 상세정보를 뜯어보자
1.-|rw-rw-r--| 1 | minyoung minyoung | 0 | 6월 16 23:55| perm.txt|
 - 첫번째 영역 - 는 type이다 perm.txt가 - 인건 기본 파일이라는 뜻이고 디렉토리면 d라는 알파벳으로 표기
 - 두번째 영역은 access mode라고한다. 저 9자리를 3자리씩 나누어 첫 rw-는 owner의 권한, 둘째 rw-는 group의 권한, 셋째 r-- 는 이 운영체제에 모든 사용자들의 기본 권한이다. 여기에서 r은 read를 의미,w는 write , -가 있는자리는 x가 올수 있는데 excute(실행)를 의미한다.
 - 즉 owner minyoung은 perm.txt에 대해 read,write권한은 있지만 excute권한은 없는것이다.
 - 네번째 영역은 첫 minyoung은 owner 두번째 minyoung은 group이다. owner는 해당 파일이 누구의 파일인지를 명시해준다.
> 권한 변경하는 방법 – chmod
* perm.txt파일은 전체사용자 권한이 r—이었다. 다만 perm.txt가 보안적으로 중요한 파일이라 권한이 있는 사용자만 읽게 하게해야 된다면? 이럴때 사용하는게 chmod
* chmod o-r perm.txt : perm.txt의 other의 권한중 read를 -없애고 싶다 라는 명령
* Chmod o+r perm.txt : perm.txt에 other의 권한중 read를 +추가하고 싶다.라는 명령
* 그럼 user=소유자의 권한을 막아놓을 수 있나? => 가능하다.
> 디렉토리 권한
* 똑같이 chmod로 설정하고 r은 파일의 내용 읽, w는 디렉토리내 파일을 추가,삭제,이름변경등 , x는  디렉토리에 접근에 대한 권한정보이다.추가적으로 chmod -R o+w perm 은 perm디렉토리 내의 모든 디렉토리에 o+w 설정을 적용한다는 의미이다.
> access mode

| 입력 | Permission | rwx |
|---|:---:|---:|
| 7 | read,write and execute | rwx |
| 6 | read and write | rw- |
| 5 | read and execute | r-x
| 4 | read only | r-- |
| 3 | write and execute | -wx |
| 2 | write only | -w- |
| 1 | execute only | --x |
| 0 | none | --- |
* 이러한 표를 바탕으로 chmod를 사용 해주면 전 명령들과 달리 간편하게 권한 설정이 가능하다.
 * chmod 111 perm.txt -> user,group, other에게 1,1,1의 권한을 설정하는 것으로 모두 --x|--x|--x로 설정되는 것을 확인할 수 있다.

## 웹서버
> 간단하게 웹서버는 WAS와 함께 사용한다. WAS의 부담을 덜하게 하기 위해 정적 리소스들을 웹서버에 담아두고 WAS는 DB조회, 다양한 로직을 처리하는데 집중해야 한다.
* sudo service apache2 start : 아파치를 사용하는 경우 웹서버 기동 명령어
* sudo service apache2 stop : 아파치를 사용하는 경우 웹서버 종료 명령어
* /etc/apache2/apache2.conf : 우리가 apt로 프로그램을 다운받으면 etc디렉토리 밑에 설정파일이 존재하게 된다. 여기서 웹서버의 설정파일인 apache2.conf에서 설정을 확인할 수 있다.
* /var/log/apache2/access.log : 웹서버의 접근하는 사용자의 정보 로그 파일. tail -f 를통해 해당 파일을 관제하면 접근시 사용자의 브라우저,아이피,접근결과 등의 정보가 쌓이는 것을 확인 가능하다.
* /var/log/apache2/error.log : 웹서버의 에러가 발생시 같이 로그를 쌓아주는 파일이다. 웹서버에서 에러발생시 확인해야 할 파일이다.
### ssh
> 서버나 다른 컴퓨터를 '원격제어'를 해야하는 경우 사용한다.
* 클라이언트와 서버에 각각 ssh를 사용하고 이것을 각각 ssh client, ssh server라고 한다.
* 대부분의 유닉스 계열은 ssh가 설치되어있다.
* 현재 우분트에 openssh 설치후 윈도우 cmd에서" ssh -'아이디@ip주소' " 시 비밀번호 입력후 원격제어가 가능하다.
### 포트
> 한 컴퓨터에는 포트가 0~6만5천개 정도 있다. ssh는 기본적으로 22번 포트에 연결, 웹서버는 기본적으로 80번 포트에 연결
* 대기하고 있는 포트는 sudo netstat -ntlp | grep LISTEN 로 전체 포트 중 LISTEN상태인 포트를 보는 명령어인데 LISTEN 상태가 사용대기중인 포트라는 의미이다. 위의 ssh와 웹서버도 LISTEN상태
* 포트에 대한 설정은 역시나 etc에 있다. /etc/ssh/sshd_config 파일에 ssh의 포트에 대한 설정을 포함 여러 설정들이 정의 되어 있다.
 #### 포트포워딩
 <img src = "https://media.vlpt.us/images/ssoulll/post/d9a56fc4-2ff9-4643-b3dd-1bab6ce891e5/homeserver_port_forwarding.png"/>
 > 예를 들어 오늘날 한가정에는 보통 통신사에서 할당된 public ip하나가 공유기 형태로 가정에 연결되고 이 공유기를 통해 tv,데스크탑 등이 private ip로 나눠진다. 보통 외부 사용자는 pubilc에 접근하고 private은 접근불가능하지만 private에 접근 가능하게 하는것이 포트포워딩이다
 > 만약 공유기 public ip가 211.10.10.1 이고 데스크탑 private ip가 192.10.5.11이라고 한다고 하고 211.10.10.1:9000로 사용자가 접근하면 공유기의 9000번 포트에 접근하는 것이다. 이때 9000번포트는 데스크탑 192.10.5.11에 포워딩 되어있고 80번포트에 웹서버가 설정되어있다. 이러한 경우 데스크탑의 80포트 즉  211.10.10.1:9000로 접근하면 192.19.5.11:80으로 접근할수 있다. 
* 또한 공유기와 엮인 기기들과 공우기의 내부망을 아우르는 공유기의 주소가 있는데 이것을 디폴트 게이트 웨이라고 한다.
* 디폴트 게이트웹이는 ip route 라는 명령어로 주소값을 알아 낼수 있다.
## 도메인
> google.com에 접속시 클라이언트에서 google.com을 입력시 바로 구글 서버가 아닌 DNS서버에 먼저 접근되 google.com에 대한 ip 값을 응답 받게 되고 해당 ip값으로 클라이언트에서 접근하는 원리이다.
### hosts
> DNS전엔 hosts라는 파일이 있었다고한다. hosts파일은 인터넷을 사용하는 컴퓨터마다 hosts파일이 있어서 어떤 특정 도메인으로 접속할때는 DNS서버가 없기에 DNS에 묻는게 아닌 hosts파일에 적혀있는 도메인을 보고 ip를 확인해 접근했다고 한다. 클라와 서버를 구분했지만 각각을 host라고 부르고 각 host들이 모여있는것을 network라고하고 network의 전체적인 집단을 인터넷이라고 한다.즉 hosts파일은 각각의 host의 ip의 주소를 적어놓고 사용했다는 것. /etc/hosts파일이 있다.
### DNS의 원리
> 항상 DNS에 대해 이야기 할때 DNS서버에 도메인 정보가 있어 알맞는 ip값을 반환한다라고만 알고있었다. 해당 DNS서버가 어떻게 많은 도메인 정보를 담고 있을까?

* DNS서버는 계층적구조이고 우리가 우선 DNS에 접속하는건 root DNS이다. root DNS서버는 전세계에 흩어져있고 일반적으로 google.com에 접속시 rootDNS서버를 거친다고 한다.
* ' dig +trace 도메인 ' 명령어를 터미널에 명령하면 DNS에 해당 도메인에 대한 정보를 의뢰한것.
* 명령어로 입력되어 처음 나오는 root-server.net은 모든 root DNS서버를 처음에 뒤진것이고 여기서 google.com에서 .com을 담당하는 서버를 DNS서버에서 찾고 결과를 반환한다.
