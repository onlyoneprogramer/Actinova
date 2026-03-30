# 🔍 Detection

## Strategy

### Event Collection
- eBPF 기반 syscall 추적

```c
SEC("tracepoint/syscalls/sys_enter_execve")
int trace_execve(...) {
}
Behavior Analysis
fork → exec → privilege escalation → network connect
Anomaly Detection
정상 패턴 기반 이상 탐지
False Positive Reduction
whitelist
정책 기반 필터링

---

# ⚡ docs/response.md

```md
# ⚡ Response

## Strategy

### Process Kill
- 악성 판단 시 즉시 종료

### Isolation
- 네트워크 차단
- 시스템 격리

### Logging
- 포렌식 데이터 저장

---

## Policy

| 조건 | 대응 |
|------|------|
| 의심 | 로그 |
| 악성 | 종료 |
| 확산 | 격리 |

---

## Future

- 롤백
- 자동 복구