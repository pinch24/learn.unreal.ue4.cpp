# Unreal C++ 게임 개발의 정석
Unreal C++ 게임 개발의 정석 by 이득우

# 들어가며
## 프로그래머 관점에서의 언리얼 엔진 시스템
- 언리얼 엔진의 빌드 시스템
- 언리얼 엔진의 모듈 시스템
- 언리얼 엔진의 샐행 환경(Runtime)
- 언리얼 엔진 오브젝트의 선언과 관리
- 언리얼 엔진 C++의 기능

## 크리에이터 입장에서의 언리얼 엔진 시스템
- 게임 컨텐츠를 수용하는 환경(월드, World)ed
- 게임 컨텐츠의 기본 단위(액터, Actor)
- 게임 플레이가 진행되는 배경(레벨, Level)
- 게임 플레이어에게 부여되는 액터
- 게임의 룰과 게임 모드 액터
- 게임 제작에 필요한 보조 기능
---- 

# 1. 개발 환경 설정
![1.1.png][image-1]

## Content 디렉토리
언리얼 엔진은 게임 프로젝트 에셋을 프로젝트의 Content 폴더에서 관리한다.
- Config: 게임 프로젝트의 설정 값을 저장한다.
- Content: 게임 프로젝트의 에셋을 저장한다.
- Intermediate: 게임 프로젝트의 관리에 필요한 임시 파일을 저장한다.
- Saved: 게임 프로젝트의 작업 중에 생성된 세이브, 스크린샷 등의 결과물을 저장한다.

## Unreal 프로젝트 파일
`ArenaBattle.uproject`
```json
{
	"FileVersion": 3,
	"EngineAssociation": "5.0EA",
	"Category": "",
	"Description": ""
}
```

## C++ 프로젝트로 확장
![1.2.1-6.gif][image-2]
<!--
![1.2.1.gif][1.2.1]
![1.2.2.gif][1.2.2]
![1.2.3.gif][1.2.3]
![1.2.4.gif][1.2.4]
![1.2.5.gif][1.2.5]
![1.2.6.gif][1.2.6]
-->

C++ 클래스가 생성되고 컴파일이 진행되면 블루프린트만 가능하던 게임 프로젝트가 C++ 프로그래밍도 가능한 프로젝트로 변경된다.
프로젝트 전환이 끝나면 프로젝트에는 Visual Studio 파일들이 생성된다.
- Binaries/: C++ 코드가 컴파일된 결과물을 임시로 저장한다.
- Source/: C++ 코드를 저장한다. 언리얼 엔진 빌드 설정을 담은 C# 파일도 저장한다.
- .sln: C++ 프로젝트를 관리하기 위한 Visual Studio 파일이다. 이 파일이 관리하는 대상은 Intermediate/ProjectFiles 폴더에 있다.
- .vs/: Visual Studio 설정을 저장한다.

## Unreal C++ 프로젝트 파일
`ArenaBattle.uproject`
```json
{
	"FileVersion": 3,
	"EngineAssociation": "5.0EA",
	"Category": "",
	"Description": "",
	"Modules": [
		{
			"Name": "ArenaBattle",
			"Type": "Runtime",
			"LoadingPhase": "Default",
			"AdditionalDependencies": [
				"Engine"
			]
		}
	]
}
```
C++ 프로젝트로 변환되면 Modules 항목이 추가된다. 언리얼 엔진 에디터가 시작될 때 Modules에 있는 내용도 함께 로딩하라는 의미로 게임 프로젝트의 Binaries/ 폴더에서 해당 모듈을 찾는다. 없으면 이 파일을 생성하기 위한 빌드를 진행하게 된다.
---- 

# Unreal C++ 개발 환경 설정
## Visual Studio 에디터 툴바 설정 변경
![1.3.1-4.gif][image-3]

## Visual Studio 빌드 구성
- DebugGame: 디버깅을 위해 최적화 안 된 EXE 빌드 생성
- DebugGame Editor: DebugGame의 에디터용 DLL 빌드 생성
- Development: 디버깅이 가능한 최적화된 EXE 빌드 생성
- Development Editor: Development의 에디터용 DLL 빌드 생성
- Shipping: 배포를 위해 최적화된 EXE 빌드 생성

Visual Studio에서 빌드한 EXE 파일은 언리얼 엔진에서 리소스와 묶인 패키지 형태로 배포되어야 한다. Visual Studio 빌드는 리소스 없이 실행 파일만 빌드한다.

[image-1]:	./Screenshots/1.1.png
[image-2]:	./Screenshots/1.2.1-6.gif
[image-3]:	./Screenshots/1.3.1-4.gif