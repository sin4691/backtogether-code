# Back Together — 신재윤 작업 코드

최대 4명이 온라인으로 함께 플레이하는 **협동 2D 플랫포머**입니다. 팀 프로젝트로 개발했고, Steam·STOVE에 출시를 준비하고 있습니다.

![Back Together 플레이 화면](https://sin4691.github.io/assets/back-together.png)

| 장르 | 기간 | 네트워크 | 엔진 |
|---|---|---|---|
| 온라인 협동 플랫포머 | 2026.06.19 – 09.15 | Mirror · EOS P2P (서버 권위) | Unity 6 · URP 2D |

📂 자세한 설명: [포트폴리오 – Back Together](https://sin4691.github.io/#back-together)

> 상용 출시작이라 원본 프로젝트 저장소는 비공개입니다. 이 저장소에는 **제가 작성한 코드만** 원본 그대로 옮겨 두었습니다. 그래서 단독으로 실행되지는 않습니다.

## 코드

| 기능 | 파일 | 비고 |
|---|---|---|
| 서버 권위 보스 추격 | [`BossChase.cs`](Scripts/Boss/BossChase.cs) | |
| 보스 접근 경고 (붉은 비네트) | [`BossProximityVignette.cs`](Scripts/Boss/BossProximityVignette.cs) | 대상 탐색 최적화 부분(약 20줄)은 팀원 수정 |
| 보스 연출 (시선·연기) | [`BossEyeGaze.cs`](Scripts/Boss/BossEyeGaze.cs) · [`BossSmokeParticles.cs`](Scripts/Boss/BossSmokeParticles.cs) · [`BossSmokeSway.cs`](Scripts/Boss/BossSmokeSway.cs) | |
| 효과음 재생 통합 | [`PlayerSoundUtility.cs`](Scripts/Sound/PlayerSoundUtility.cs) · [`PlayerSoundLibrary.cs`](Scripts/Sound/PlayerSoundLibrary.cs) | |
| 씬별 BGM | [`BGMManager.cs`](Scripts/Sound/BGMManager.cs) | 약 10줄은 팀원 수정 |
| 점프 소리 중복 재생 수정 | [`jump-sound-duplicate.diff`](Fixes/jump-sound-duplicate.diff) | 팀원 파일에 넣은 수정이라 변경분만 담음 |

## 내가 맡은 것

- **서버 권위 보스 추격**: 서버는 각 플레이어의 화면을 알 수 없습니다. 그래서 가장 뒤처진 플레이어와의 가로 거리로 보스가 화면 안에 있는지 판단해 속도를 바꿨습니다. 보스 이동은 서버에서만 계산해 모든 플레이어에게 같은 위치로 보입니다.
- **위험 연출**: 보스가 가까워지면 화면 가장자리가 붉어지게 했습니다. 보스 시선과 연기 연출도 만들었습니다.
- **사운드**: 점프·피격·발소리마다 복사돼 있던 재생 코드를 하나로 합쳤습니다. 클립은 ScriptableObject로 모았고, 모든 효과음이 볼륨 설정을 따르게 했습니다. 씬마다 BGM을 바꾸는 매니저도 만들었습니다.
- **점프 소리 중복 재생**: 클라이언트가 미리 재생한 뒤 서버 상태가 도착하기 전에 타이머가 다시 채워지는 문제였습니다. 재생하는 순간 타이머를 소모하도록 고쳤습니다.
- **레벨 디자인·난이도**: 챕터 1~6과 Ex 1~2 맵을 만들었습니다. 플레이 테스트(약 40명)를 운영하며 난이도를 조정했습니다.
- **마케팅**: 홍보 릴스를 기획하고 제작했습니다.

## 팀원 담당

플레이어 이동 모듈, 로비·네트워크 연결, 대부분의 협동 기믹, UI·옵션, Steam·STOVE SDK 연동은 팀원이 작업했습니다.
