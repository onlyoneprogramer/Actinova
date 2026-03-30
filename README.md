# 🚀 Actinova

> 커널 레벨에서 위협을 탐지하고, 즉시 대응까지 수행하는 **차세대 능동형 보안 솔루션**

---

## 📌 Overview

**Actinova**는 고급 커널 및 시스템 위협으로부터 엔터프라이즈 환경을 보호하기 위해 개발 중인 보안 플랫폼입니다.

단순한 탐지 중심의 기존 보안 솔루션과 달리,
Actinova는 **탐지 → 분석 → 자동 대응 → 무결성 복구**까지 이어지는
**Full-cycle 방어 체계**를 제공합니다.

---

## 🎯 Motivation

현대 보안 환경은 다음과 같은 특징을 가집니다:

* 커널 레벨에서 동작하는 은닉형 백도어 증가
* eBPF 기반 공격과 같이 탐지 난이도가 높은 위협 등장
* 공급망 공격 및 APT 공격의 고도화
* 기존 보안 솔루션의 사용자 영역(User-space) 중심 한계

이러한 환경에서는 단순 탐지로는 충분하지 않습니다.

👉 **문제의 핵심은 "보이지 않는 레벨에서의 위협"과 "탐지 이후의 대응 부재"입니다.**

---

## 💡 Solution

Actinova는 다음과 같은 방식으로 문제를 해결합니다:

### 1. 커널 레벨 가시성 확보

* eBPF 및 커널 모듈을 활용한 심층 행위 추적

### 2. VMI 기반 외부 관측

* 커널 내부 조작을 우회하여 신뢰 가능한 관측 수행

### 3. 행위 기반 탐지

* 시그니처가 아닌 **행위 시퀀스 기반 분석**

### 4. 자동 대응 체계

* 공격 발생 시 즉각적인 차단 및 격리 수행

### 5. 무결성 유지

* 시스템 핵심 구조 보호 및 변조 탐지

---

## 🏗️ Architecture

```text
[Kernel / System Events]
          ↓
[eBPF + Kernel Module]
          ↓
[VMI Monitoring Layer]
          ↓
[Behavior Analysis Engine]
          ↓
[Response Engine]
          ↓
[Isolation / Kill / Logging]
```

### 핵심 구조

* **In-Guest Layer**: eBPF + Kernel Module 기반 실시간 이벤트 수집
* **Out-of-Guest Layer**: VMI 기반 신뢰 가능한 외부 관측
* **Analysis Engine**: 공격 패턴 및 행위 분석
* **Response Engine**: 자동 대응 및 시스템 보호 수행

---

## ⚙️ Core Features

### 🔍 BPFdoor 탐지 및 대응

* eBPF 기반 은닉형 백도어 실시간 추적 및 차단

### 🛡️ 랜섬웨어 방어

* 파일 암호화 패턴 및 비정상 I/O 행위 탐지

### 📦 공급망 공격 방어

* 커널 모듈 및 패키지 변조 탐지

### 🎯 APT 공격 대응

* 장기적 공격 시퀀스 분석 및 자동 격리

### 🔐 시스템 무결성 보호

* 커널 구조 및 핵심 데이터 영역 검증

### ⚡ 자동 대응 시스템

* 프로세스 종료
* 네트워크 차단
* 시스템 격리
* 로그 및 포렌식 데이터 생성

---

## 🛠️ Tech Stack

* **KVM 기반 VMI (Virtual Machine Introspection)**
* **Linux Kernel Module (C/C++)**
* **eBPF 기반 이벤트 수집**
* **Dual-Agent Architecture**
* **Python / Qt 기반 GUI**

---

## 🚧 Current Status

Actinova는 현재 **개발 진행 중**인 프로젝트입니다.

* PoC 개발 진행 중
* 커널 레벨 탐지 로직 구현 중
* 자동 대응 시스템 설계 및 테스트 단계

> ⚠️ 현재는 배포용 바이너리 또는 설치 파일은 제공되지 않습니다.

---

## 🔥 Vision

> "탐지되지 않던 위협을 발견하는 것이 아니라,
> 탐지할 수 있는 구조를 만든다"

Actinova는 단순한 보안 솔루션이 아니라,
**커널 레벨 위협을 구조적으로 제거할 수 있는 새로운 방어 패러다임**을 목표로 합니다.

---

## 🤝 Contribution

해당 프로젝트는 현재 내부 개발 중심으로 진행되고 있습니다.

향후 오픈소스 또는 협업이 가능해질 경우 별도 공지 예정입니다.

---

## 📄 License

TBD
