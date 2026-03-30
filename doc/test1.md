# 🎯 Threat Model

## 1. BPFdoor

### 특징
- eBPF 기반 은닉 통신
- 포트 미노출

### 흐름

packet → eBPF → trigger → shell


---

## 2. Ransomware

### 특징
- 대량 파일 암호화
- I/O 급증

---

## 3. Supply Chain

- 패키지 변조
- 커널 모듈 삽입

---

## 4. APT

### Kill Chain

Initial → Persistence → Privilege → Lateral → Exfiltration


---

## Limitations of Existing Security

- user-space 중심
- 커널 은닉 대응 부족
- 자동 대응 부재