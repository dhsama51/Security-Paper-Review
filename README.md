# Security-Paper-Review

Recent IEEE S&P / USENIX Security 논문을 읽고 정리한 분석 자료 모음입니다. 프로토콜/시스템 보안 취약점을 실증적으로 검증하는 연구 방법론을 익히기 위해, 매 논문마다 배경 지식 → 공격 구조 → 위협 모델 → 실험 결과 → 한계 → 관심 있는 후속 논문 순으로 정리했습니다.

## Contents

| Date | Paper | Venue | Focus |
|---|---|---|---|
| 26.08 | [DNS Cache Poisoning Like it's 2006](./analysis_dns_cache_poisoning_2026.pdf) | USENIX Security'26 | BIND 9의 Xoshiro128** PRNG state를 TXID/RRset-order 관측만으로 복구해, TXID와 UDP source port 랜덤화를 동시에 무력화하는 공격 |
| 26.09 | [Adversarial Hubness in Multi-Modal Retrieval](./analysis_adversarial_hubness_2026.pdf) | IEEE S&P'26 | 멀티모달 검색 시스템에서 자연 발생 hubness를 의도적으로 만들어, 소수 쿼리로 최적화한 이미지/오디오를 수천 개의 무관한 쿼리에 반복 검색되게 만드는 공격 |
| 26.09 | [Opossum Attack: Application Layer Desynchronization using Opportunistic TLS](./analysis_opossum_attack_2026.pdf) | USENIX Security'26 | 하나의 서버가 implicit TLS와 opportunistic TLS를 동시 지원할 때, 핸드셰이크 이후 "누가 먼저 말하는가"의 차이를 이용해 암호를 깨지 않고 순수 중계만으로 request desynchronization을 일으키는 공격 |

## About Each Analysis

각 슬라이드는 다음 구조를 공통으로 따릅니다.

1. **Background** — 논문이 다루는 시스템/프로토콜의 기본 동작과 관련 선행 연구(Related Work)
2. **Attack Structure** — 공격의 핵심 아이디어와 단계별 진행 과정
3. **Threat Model** — 공격자가 가정하는 접근 권한과 목표
4. **Experiments and Evaluation** — 논문이 제시한 실험 결과와 수치
5. **Existing Defense Mechanisms** — 기존 방어 기법과 그 한계
6. **Challenges / Contributions / Limitations** — 논문이 해결한 문제, 기여한 바, 스스로 인정한 한계
7. **More Interested Papers** — 같은 흐름에서 다음에 읽고 싶은 논문 목록

## Motivation

정보보안암호수학과에서 프로토콜 취약점 재현·검증 연구(TLS, 5G NAS)를 하며 익힌 "공격을 재현하고, 그 가정이 실제 환경에서도 성립하는지 실험으로 확인한다"는 방법론을, 최근 top-tier 보안 학회 논문을 스스로 소화하는 데도 그대로 적용해보고 있습니다. 이 중 [Adversarial Hubness in Multi-Modal Retrieval](./analysis_adversarial_hubness_2026.pdf) 분석은 이후 직접 재현·확장 실험으로 이어졌고, 그 결과는 [adversarial-hubness-reproduction](https://github.com/dhsama51/adversarial-hubness-reproduction) 레포에 별도로 정리되어 있습니다.

## Related

- [adversarial-hubness-reproduction](https://github.com/dhsama51/adversarial-hubness-reproduction) — Adversarial Hubness 논문의 재현 및 확장 실험
