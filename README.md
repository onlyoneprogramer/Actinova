# 🚀 Actinova

**Kernel-Level Threat Detection & Response System (eBPF 기반)**

> 탐지 우회를 전제로 설계된 **차세대 커널 보안 솔루션**

단순 이벤트 탐지를 넘어서
👉 **공격 흐름을 추적하고 실시간으로 대응하는 시스템**입니다.

---

## 🎯 What Makes It Different?

| 기존 보안         | Actinova        |
| ------------- | --------------- |
| User-space 중심 | Kernel-level 추적 |
| 단일 이벤트 분석     | 행위 시퀀스 기반 분석    |
| 탐지 중심         | 탐지 + 자동 대응      |
| 사후 대응         | 실시간 대응          |

> **"We don't just detect threats. We stop them."**

---

## 🎬 Real Detection Flow (핵심)

```text
[ 공격 실행 - BPFdoor ]
↓
[ eBPF syscall 추적 ]
↓
[ 비정상 행위 패턴 탐지 ]
↓
[ Response Engine 트리거 ]
↓
[ 프로세스 종료 / 네트워크 차단 ]
↓
[ 로그 및 알림 생성 ]
```

👉 **단순 이벤트가 아닌 공격 흐름 단위로 탐지 및 대응**

---

## 🧪 Demo (실제 동작 증명)

👉 [BPFdoor Detection Scenario](docs/demo.md)

### 📌 Demo 포함 내용

* 공격 실행 과정
* eBPF 기반 syscall 추적 로그
* 행위 기반 탐지 트리거
* 대응 결과 (프로세스 종료 / 네트워크 차단)

👉 **“이론이 아닌 실제 동작 결과”를 확인할 수 있습니다**

---

## 🏗️ Architecture

```text
[ Kernel Events ]
↓
[ eBPF / Kernel Module ]
↓
[ VMI Layer ]
↓
[ Behavior Analysis ]
↓
[ Response Engine ]
↓
[ Kill / Isolation / Logging ]
```

📌 상세 구조 → [docs/architecture.md](docs/architecture.md)

---

## ⚙️ Core Features

### 🔍 Kernel-level Visibility

* eBPF 기반 syscall / 네트워크 / 프로세스 이벤트 추적
* 커널 레벨에서 직접 행위 수집

---

### 🧠 Behavior-based Detection

* 단일 이벤트가 아닌 행위 흐름 기반 분석
* 정상/비정상 패턴 비교

---

### 🛡️ Advanced Threat Detection

* BPFdoor (커널 레벨 은닉형 백도어)
* Fileless 공격
* 랜섬웨어
* APT 공격

---

### ⚡ Automated Response

* 프로세스 강제 종료
* 네트워크 차단
* 시스템 격리

---

### 🔐 System Integrity Protection

* 커널 및 핵심 시스템 구조 보호
* 무결성 유지

---

## 🖥️ System Components

```bash
core/        # kernel, eBPF, VMI 핵심 로직
agent/       # 수집 및 대응 에이전트
backend/     # 분석 엔진 및 API
gui/         # 모니터링 및 관리 인터페이스
doc/        # 기술 문서
```

---

## 📚 Documentation

* [Overview](doc/overview.md)
* [Architecture](doc/architecture.md)
* [Threat Model](doc/threat-model.md)
* [Detection](doc/detection.md)
* [Response](doc/response.md)
* [Deployment](doc/deployment.md)
* [Roadmap](doc/roadmap.md)
* [FAQ](doc/faq.md)

---

## 🧠 Why This Matters

기존 보안 솔루션은
👉 User-space 기반 탐지 한계로 인해
👉 커널 레벨 은닉형 위협을 놓칠 수 있습니다.

Actinova는 이를 해결하기 위해
👉 **커널 레벨에서 직접 행위를 추적하고 대응하는 구조**로 설계되었습니다.

---

## 🚀 Future Work

* ML 기반 행위 분석 고도화
* Kubernetes / Cloud 환경 대응
* Hypervisor 기반 확장 (VMI 강화)

---

## 📌 Summary

Actinova는 단순한 탐지 시스템이 아닌

👉 **공격을 이해하고, 실시간으로 대응하는 커널 보안 플랫폼**입니다.
