# 📚 Actinova Documentation (Final)

> 커널 레벨 위협을 탐지하고 대응하기 위한 구조적 보안 아키텍처 문서

---

# 🏗️ architecture.md

## Overview

Actinova는 **In-Guest + Out-of-Guest 하이브리드 구조**를 기반으로,
커널 내부와 외부에서 동시에 시스템을 관측하는 이중 가시성(Dual Visibility)을 제공합니다.

기존 보안 솔루션이 사용자 영역에 의존하는 반면,
Actinova는 커널 및 하이퍼바이저 레벨까지 확장된 관측 구조를 사용합니다.

---

## Architecture Flow

```
[Kernel Events]
      ↓
[eBPF / Kernel Module]
      ↓
[VMI Monitoring Layer]
      ↓
[Behavior Analysis Engine]
      ↓
[Response Engine]
      ↓
[Isolation / Kill / Logging]
```

---

## Core Components

### 1. In-Guest Layer

* eBPF 기반 syscall 추적
* 프로세스/파일/네트워크 이벤트 수집
* 커널 모듈 기반 심층 정보 확보

### 2. Out-of-Guest Layer (VMI)

* 하이퍼바이저 레벨에서 Guest OS 관측
* 커널 변조 및 루트킷 우회 탐지
* 신뢰 가능한 외부 데이터 확보

### 3. Behavior Analysis Engine

* 이벤트 단위가 아닌 **행위 시퀀스 기반 분석**
* 공격 패턴 모델링
* 정상/비정상 행위 분류

### 4. Response Engine

* 정책 기반 자동 대응
* 실시간 위협 차단 및 격리

---

## Design Philosophy

* 탐지 우회는 전제 조건
* 단일 관측은 신뢰하지 않음
* 행위 기반 분석 중심
* 탐지 이후 자동 대응 필수

---

# 🎯 threat-model.md

## Target Threats

### 1. BPFdoor (Kernel Backdoor)

#### 특징

* eBPF 기반 은닉 통신
* 포트 미노출
* 패킷 트리거 방식 실행

#### 공격 흐름

```
패킷 수신 → eBPF 필터 → 트리거 조건 만족 → 쉘 실행
```

---

### 2. Ransomware

#### 특징

* 대량 파일 암호화
* 파일 확장자 변경
* 비정상 I/O 폭증

#### 탐지 포인트

* write syscall 패턴
* entropy 증가

---

### 3. Supply Chain Attack

#### 특징

* 패키지 변조
* 악성 커널 모듈 삽입

#### 탐지 포인트

* module load 이벤트
* 파일 무결성 변화

---

### 4. APT Attack

#### 특징

* 장기 잠복
* 단계적 권한 상승
* 은닉 통신

#### Kill Chain

```
Initial Access → Persistence → Privilege Escalation → Lateral Movement → Exfiltration
```

---

## Why Existing Solutions Fail

* User-space 중심 탐지
* 커널 은닉 기법 대응 부족
* 탐지 후 대응 자동화 부족

---

# 🔍 detection.md

## Detection Strategy

### 1. Event Collection

* eBPF 기반 syscall hook
* process / file / network 이벤트 수집

예:

```c
SEC("tracepoint/syscalls/sys_enter_execve")
int trace_execve(...) {
    // process execution tracking
}
```

---

### 2. Behavior Sequence Analysis

단일 이벤트가 아닌 흐름 기반 탐지

```
fork → exec → privilege escalation → network connect
```

---

### 3. Anomaly Detection

* 정상 행위 baseline 구축
* deviation 기반 탐지

---

### 4. False Positive Reduction

* 화이트리스트
* 정상 프로세스 학습
* 정책 기반 필터링

---

# ⚡ response.md

## Response Strategy

### 1. Process Kill

* 명확한 악성 시그널 발생 시 즉시 종료

### 2. Isolation

* 네트워크 차단
* 컨테이너/VM 격리

### 3. Logging & Forensics

* 전체 이벤트 기록
* 공격 타임라인 생성

---

## Response Policy Example

| 조건    | 대응      |
| ----- | ------- |
| 의심 행위 | 로그 기록   |
| 확정 악성 | 프로세스 종료 |
| 확산 위험 | 시스템 격리  |

---

## Future Work

* 자동 롤백
* 메모리 복구
* 공격 이전 상태 복원

---

# 🚀 deployment.md

## Requirements

* Linux Kernel 5.x 이상
* KVM 지원 환경
* Root 권한

---

## Deployment Flow

```
Host (VMI)
   ↓
Guest (eBPF Agent)
   ↓
Backend (Analysis)
   ↓
GUI (Monitoring)
```

---

## Components

* VMI Monitor (Host)
* eBPF Agent (Guest)
* Analysis Backend
* GUI Console

---

# 🗺️ roadmap.md

## Phase 1 (Current)

* eBPF 이벤트 수집
* 기본 탐지 로직

## Phase 2

* 행위 기반 분석 고도화
* 정책 기반 대응 시스템 구축

## Phase 3

* GUI 완성
* 실환경 테스트

## Phase 4

* 성능 최적화
* 상용화 준비

---

# 🔥 Vision

> 탐지되지 않던 위협을 발견하는 것이 아니라,
> 탐지할 수 있는 구조를 만든다

Actinova는 단순한 보안 도구가 아니라,
**커널 레벨 위협을 구조적으로 제거하기 위한 방어 플랫폼**이다.
