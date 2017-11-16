# Android Programming :computer: :memo:

- ## __Android Study__ :open_file_folder:
  - ---

  ### [Animation](https://github.com/qskeksq/Animation)
    - 뷰 애니메이션
    - 프로퍼티 애니메이션
    - 액티비티 애니메이션
    - 프래그먼트 애니메이션
    - 어댑터뷰 애니메이션

  ### [CustomView](https://github.com/qskeksq/CustomView)
    - 기본 위젯 상속(extends 위젯)
    - 복합 위젯(extends 레이아웃)
    - View 상속
    - [오픈소스 변형](https://github.com/qskeksq/CustomTabIndicatorLayout)

  ### [CustomListView](https://github.com/qskeksq/AdapterView)
    - BaseAdapter 상속
    - ViewHolder 패턴 구현

  ### [ExpandingListView](https://github.com/qskeksq/ExpandingList)
    - Retrofit2로 서버에서 데이터 받아오기
    - 인터페이스를 통한 데이터 동기화
    - ServiceGenerator, IRemoteService, RemoteLib
    - SCROLL_STATE_IDLE&isLastData를 통해 추가로 데이터 세팅
    - AbsListView & onScrollListener 이해

  ### [ScrollWithRecyclerview](https://github.com/qskeksq/ScrollWithRecyclerview)
    - CoordinatorLayout 
    - AppBarLayout 
    - CollapsingToolbarLayout 
    - NestedScrollView/app:layout_behavior

  ### [ViewPager](https://github.com/qskeksq/ViewPager)
    - FragmentPager-FragmentStatePagerAdapter 
    - ViewPager-PagerAdapter
    - 탭레이아웃과 연동

  ### [Permission](https://github.com/qskeksq/Permission)
    - BaseActivty를 통한 퍼미션 구현
    - Util성 퍼미션 구현
    - checkSelfPermission()
    - onRequestPermissionsResult()

  ### [Camera & Album](https://github.com/qskeksq/Camera)
    - 누가버전에서 카메라 사용 권한 설정
      - 1. 권한 설정(Provider & Path 설정)
      - 2. 퍼미션 설정
      - 3. 저장할 파일 객체 생성
      - 4. 외부에서 파일에 접근할 수 있도록 설(FileProvider.getUriForFile)

  ### [ContentResolver](https://github.com/qskeksq/ContentResolver)
    - 권한 처리
    - 이미지 테이블/스트림/칼럼 주소
    - 썸네일 테이블/스트림/칼럼 주소
    - 연락처 테이블/스트림/칼럼 주소
    - ContentResolver 쿼리

  ### [Thread Basics](https://github.com/qskeksq/ThreadBasic)
    - 다중 스레드를 통해 화면 그리기
    - ConcurrentModificationException 해결
      - thread-safe 리스트 CopyOnWriteArrayList synchronizedArrayList = new CopyOnWriteArrayList<>();
      - List synchronizedArrayList = Collections.synchronizedList(new ArrayList()); -> synchronized(raindrop){ ... }
      - Observable 동기화

  ### [Service Basics](https://github.com/qskeksq/ServiceBasic)
    - 서비스 Basics

  ### [Dependency Injection Library](https://github.com/qskeksq/DependencyInjection)
    - 의존성 주입
    - ButterKnife
    - AndroidAnnotations

  ### [FireBase1](https://github.com/qskeksq/Firebase1)
    - NoSql 데이터 구조
    - RealTime Database 저장과 동기화

  ### [FireBase2](https://github.com/qskeksq/FireBase2)
    - 파이어베이스 로그인 인증처리
    - 이미지 파일 업로드
    - 실시간 데이터베이스
    - 클라우드 메시징

- ## __Android Library Develpment__ :open_file_folder:
  - ---

  ### [CustomTabIndicator](https://github.com/qskeksq/CustomTabIndicatorLayout)
    - setCustomView() : 뷰2개를 갈아 끼우는 형식이기 때문에 indicator가 부드럽게 움직이지 않는다
    - 상속 : extends TabLayout 할 경우 탭을 그려주는 핵심 클래스인 SlidingTabStrip이 private이기 때문에 오버라이드 불가
    - Reflection : indicator는 위젯(or 레이아웃)이 아니라 canvas에 그려지는 동적인 '그림'이다. 따라서 Reflection을 통해 declaredField, declaredMethod로 메서드나 변수에 접근한다 하더라도 indicator가 그려지는 핵심 메서드인 draw(Canvas canvas)를 시스템에서 호출하기 때문에 public으로 설정된 indicator의 속성인 높이, 두께, 색상 이외에는 커스터마이징 할 수 없다
    - 결론 : 오픈소스로 되어 있는 TabLayout을 참고하여 라이브러리를 따로 만들고, 그 중 draw()부분을 customize 해 준다


  ### [ExpandableRecyclerView](https://github.com/qskeksq/RecyclerView)
    - RecyclerView 해부
      - Adapter
      - LayoutManager
      - ItemDecorator
      - ItemAnimator
      - Swipe, Drag&Drop
        - ItemTouchHelper
        - ItemTouchHelperListener(커스텀 인터페이스)
        - ItemTouchHelper.CallBack
      - position
        - getPosition()
        - getLayoutPosition()
        - getAdapterPosition()


- ## __Android Mini Project__ :open_file_folder:
  - ---
  ### [1. 계산기1](https://github.com/qskeksq/Calculator1)
    - MVP 기초적 적용
    - 컬렉션 ConcurrentModificationException, size() 변화
    - try-catch로 연산 오류 처리
    - 정규식 사용의 이해

  ### [2. 계산기2](https://github.com/qskeksq/Calculator)
    - 인터페이스 설계  
    - MVP 세부 적용
    - 사칙연산/괄호연산 알고리즘
    - 애니메이션
    - 정규식 분리

  ### [3. LaunchPad & 피아노](https://github.com/qskeksq/CustomView)
    - View 상속 커스텀뷰
    - 뷰의 생명주기 - onAttachToView(), onDetachFromWindow(), onMeasure(), onLayout(), onDraw()
    - 터치 이벤트 - onTouchEvent()/invalidate()
    - 멀티터치 구현

  ### [4. 오픈소스앱 분석1 - BestFood](https://github.com/qskeksq/BestFood)
    - 클라이언트(Android)-서버(Nodejs)-DB(MySql) 연동 이해
    - Android
      - 기획, 설계 : 서버, DB와 연동하는 안드로이드의 Information Architectur, Data Flow 이해
      - 모듈화 : activity, fragment / item, Lib, remote / adapter, custom 분리
      - 네트워크 통신
    - Nodejs
      - 서버 생성부터 데이터베이스, 클라이언트 연동, 통신 이해
      - 서버 생성 -> (클라이언트 요청) -> 라우팅 -> RESTful -> request 분석 -> CRUD -> (DB 반영) ->response
      - formidable 이미지 통신
    - MySql
      - 클라이언트에 적합하게 데이터를 보내주기 위한 데이터베이스 설계의 이해
      - insert, select, delete, update 쿼리
      - 테이블 join
      - 다중 쿼리문

  ### [5. 뮤직 플레이어](https://github.com/qskeksq/MusicPlayer)
    - ContentResolver 쿼리
	- MediaStore 테이블 정리 - 음악, 앨범, 아티스트 분류
	- MediaPlayer의 스레드와 스레드 연동
	- Observer Design Pattern
	- Service, Foreground Service

  ### [6. Fiebase 채팅](https://github.com/qskeksq/FirebaseChat)
    - 파이어베이스를 통한 채팅 구현
    - 회원가입
    - 로그인
    - 친구추가
    - 방 추가, 친구 초개
    - 채팅하기




