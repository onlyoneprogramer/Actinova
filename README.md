탐지 우회를 전제로 설계된 **차세대 커널 보안 솔루션**입니다.

단순 탐지를 넘어서,  
👉 **위협을 이해하고 자동으로 대응하는 시스템**을 목표로 합니다.

---

## 🔥 Why Actinova?

| 기존 보안 | Actinova |
|----------|----------|
| User-space 중심 | Kernel + Hypervisor 기반 |
| 탐지 (Detect) | 탐지 + 대응 (Detect + Respond) |
| 이벤트 단위 분석 | 행위 시퀀스 기반 분석 |
| 사후 대응 | 실시간 자동 대응 |

> **"We don't just detect threats. We stop them."**

---

## 🏗️ Architecture


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


📌 상세 구조는 → [doc/architecture.md](doc/architecture.md)

---

## ⚙️ Core Features

- 🔍 **Kernel-level Visibility**  
  eBPF 기반 syscall 및 시스템 이벤트 추적

- 🧠 **Behavior-based Detection**  
  단일 이벤트가 아닌 행위 흐름 기반 분석

- 🛡️ **Advanced Threat Detection**  
  BPFdoor, 랜섬웨어, APT, 공급망 공격 대응

- ⚡ **Automated Response**  
  프로세스 종료, 네트워크 차단, 시스템 격리

- 🔐 **System Integrity Protection**  
  커널 및 핵심 시스템 구조 보호

---

## 🎬 Demo

실제 공격 시나리오 기반 탐지 및 대응 흐름:

👉 [BPFdoor Detection Scenario](docs/demo.md)

---

## 📚 Documentation

- [📌 Overview](docs/overview.md)
- [🏗️ Architecture](docs/architecture.md)
- [🎯 Threat Model](docs/threat-model.md)
- [🔍 Detection](docs/detection.md)
- [⚡ Response](docs/response.md)
- [🚀 Deployment](docs/deployment.md)
- [🗺️ Roadmap](docs/roadmap.md)
- [❓ FAQ](docs/faq.md)

---

## 🖥️ System Components

```bash
core/        # kernel, eBPF, VMI 핵심 로직
agent/       # 수집 및 대응 에이전트
backend/     # 분석 엔진 및 API
gui/         # 모니터링 및 관리 인터페이스
docs/        # 기술 문서