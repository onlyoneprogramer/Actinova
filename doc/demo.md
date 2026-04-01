# 🎬 BPFdoor Detection Scenario

> Actinova는 커널 레벨에서 발생하는 위협을 **행위 기반으로 탐지하고 자동 대응**합니다.
> 본 데모는 BPFdoor 공격 시나리오를 기반으로 실제 탐지 및 대응 흐름을 보여줍니다.

---

## 🧨 1. 공격 시나리오

* 공격자는 BPFdoor를 이용하여 커널 레벨 백도어 실행
* 특정 네트워크 패킷(매직 패킷)을 통해 원격 제어 활성화
* 프로세스를 은닉하여 일반적인 보안 솔루션 회피 시도

---

## ⚙️ 2. 공격 실행

```bash
$ sudo ./bpfdoor -i eth0 -p 4444

[+] BPFdoor activated
[+] Listening for magic packet
```

👉 공격자는 커널 레벨에서 은닉된 상태로 대기

---

## 🔍 3. eBPF 기반 이벤트 추적

```bash
[Actinova - eBPF Trace]

PID: 3241
Process: bpfdoor
Event: bpf_program_load
Status: suspicious

PID: 3241
Process: bpfdoor
Event: socket_connect
Destination: 192.168.0.10:4444

PID: 3241
Process: bpfdoor
Event: process_hidden_attempt
Result: detected
```

👉 커널 레벨 이벤트를 직접 추적하여 **비정상 행위 식별**

---

## 🧠 4. 행위 기반 분석

```text
[Behavior Analysis Engine]

Detected Pattern:
- 커널 BPF 프로그램 로드
- 비정상 네트워크 연결 시도
- 프로세스 은닉 시도

Correlation Result:
→ Threat Score: HIGH
→ Classification: BPFdoor-like behavior
```

👉 단일 이벤트가 아닌 **행위 시퀀스 기반 분석 수행**

---

## ⚡ 5. 자동 대응

```bash
[Response Engine]

Action: Kill Process
Target PID: 3241
Result: SUCCESS

Action: Block Network
Target: 192.168.0.10:4444
Result: SUCCESS

Action: Alert Generated
Level: CRITICAL
```

👉 탐지 후 즉시 자동 대응 수행

---

## 📊 6. 최종 결과

* 공격 프로세스 종료 완료
* C2 통신 차단
* 시스템 정상 상태 유지
* 관리자 알림 생성

---

## 🧪 Reproducibility

**Test Environment**

* OS: Ubuntu 22.04
* Kernel: 5.x (eBPF 지원)
* Privilege: Root 권한 필요

**Execution**

```bash
# Actinova 실행
$ sudo ./actinova-agent

# 공격 시뮬레이션
$ sudo ./bpfdoor -i eth0 -p 4444
```

---

## 📌 Summary

Actinova는 단순 이벤트 탐지가 아닌

👉 **행위 기반 분석을 통해 커널 레벨 위협을 탐지하고**
👉 **실시간으로 자동 대응하는 보안 시스템입니다.**
