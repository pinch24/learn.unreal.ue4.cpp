# 언리얼 C++ 게임 개발의 정석
언리얼 C++ 게임 개발의 정석 by 이득우

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
![][image-1]

## Content 디렉토리
언리얼 엔진은 게임 프로젝트 에셋을 프로젝트의 Content 폴더에서 관리한다.
- Config: 게임 프로젝트의 설정 값을 저장한다.
- Content: 게임 프로젝트의 에셋을 저장한다.
- Intermediate: 게임 프로젝트의 관리에 필요한 임시 파일을 저장한다.
- Saved: 게임 프로젝트의 작업 중에 생성된 세이브, 스크린샷 등의 결과물을 저장한다.

## 언리얼 프로젝트 파일
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
![][image-2]
![][image-3]
![][image-4]
![][image-5]
![][image-6]
![][image-7]

## 언리얼  C++ 프로젝트 파일
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


[image-1]:	https://github.com/pinch24/learn.unreal/blob/main/01.%20Unreal%20C%2B%2B/Screenshots/1.1.png
[image-2]:	https://github.com/pinch24/learn.unreal/blob/main/01.%20Unreal%20C%2B%2B/Screenshots/1.2.1.png
[image-3]:	https://github.com/pinch24/learn.unreal/blob/main/01.%20Unreal%20C%2B%2B/Screenshots/1.2.2.png
[image-4]:	https://github.com/pinch24/learn.unreal/blob/main/01.%20Unreal%20C%2B%2B/Screenshots/1.2.3.png
[image-5]:	https://github.com/pinch24/learn.unreal/blob/main/01.%20Unreal%20C%2B%2B/Screenshots/1.2.4.png
[image-6]:	https://github.com/pinch24/learn.unreal/blob/main/01.%20Unreal%20C%2B%2B/Screenshots/1.2.5.png
[image-7]:	https://github.com/pinch24/learn.unreal/blob/main/01.%20Unreal%20C%2B%2B/Screenshots/1.2.6.png