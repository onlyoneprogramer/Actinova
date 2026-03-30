# 🏗️ Architecture

## Overview

Actinova는 In-Guest + Out-of-Guest 구조를 결합한 하이브리드 보안 아키텍처를 사용합니다.

---

## Flow


[Kernel Events]
↓
[eBPF / Kernel Module]
↓
[VMI Layer]
↓
[Behavior Analysis]
↓
[Response Engine]


---

## Components

### In-Guest
- eBPF syscall 추적
- process / file / network 이벤트 수집

### Out-of-Guest (VMI)
- 커널 변조 우회 관측
- 루트킷 대응

### Analysis Engine
- 행위 시퀀스 분석
- 공격 패턴 탐지

### Response Engine
- 자동 대응
- 격리 / 종료 수행

---

## Philosophy

- 탐지 우회는 전제
- 단일 관측은 신뢰하지 않음
- 탐지 + 대응 필수