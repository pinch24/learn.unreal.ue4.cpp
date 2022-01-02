# 언리얼 C++ 게임 개발의 정석
언리얼 C++ 게임 개발의 정석 by 이득우

# 들어가며
## 프로그래머 관점에서의 언리얼 엔진 시스템
- 언리얼 엔진의 빌드 시스템
- 언리얼 엔진의 모듈 시스템
- 언리얼 엔진의 샐행 환경(Runtime)
- 언리얼 엔진 오브젝트의 선언과 관리
- 언리얼 엔진 C++의 기능
- 
## 크리에이터 입장에서의 언리얼 엔진 시스템
- 게임 컨텐츠를 수용하는 환경(월드, World)
- 게임 컨텐츠의 기본 단위(액터, Actor)
- 게임 플레이가 진행되는 배경(레벨, Level)
- 게임 플레이어에게 부여되는 액터
- 게임의 룰과 게임 모드 액터
- 게임 제작에 필요한 보조 기능
---- 

# 1. 개발 환경 설정
```md
# Start Unreal Engine
# Unreal Project Browser
- [Third Person]
- [Blueprint]
- Starter Content: [x]
- Project Name: ["ArenaBattle"]
# [Create]
```

## Content 디렉토리
언리얼 엔진은 게임 프로젝트 에셋을 프로젝트의 Content 폴더에서 관리한다.
