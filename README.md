# Bitground v1 · Spring

가상화폐 모의투자 서비스 Bitground v1의 백엔드입니다. 네이버클라우드 비트캠프 6인 팀 프로젝트(2025-05 ~ 07, 6주)로 만들었습니다.

> 현재 버전은 [bitground](https://github.com/lepe99/bitground)에서 혼자 다시 설계해 운영합니다. 이 저장소는 보존용이며, 당시 NCP 인프라가 없어 그대로는 실행되지 않습니다.

함께 쓰던 저장소: [react-bitground](https://github.com/lepe99/react-bitground) (화면) · [go-bitground](https://github.com/lepe99/go-bitground) (정시 스케줄러)

## 기술 스택

Java 17, Spring Boot 3.4, Spring Security(OAuth2/OIDC, JWT), JPA, MySQL, Redis, SSE·WebSocket, Jenkins, Pinpoint, Prometheus

## 제가 맡은 부분

- 소셜 로그인(OIDC) + JWT 쿠키 + 리프레시 토큰 교체(RTR)
- SSE 알림 (자동 재연결, DB 저장)
- 예약(지정가) 주문 접수·체결: Redis Sorted Set으로 체결할 주문을 찾고 List 큐로 처리
- REST API 응답 규약
- 모니터링(Prometheus·Loki·Grafana·Pinpoint)
- NCP 클라우드 인프라 설계·구축 (팀원 한 명과 공동), Jenkins 배포

시장가 매매, 투자내역·랭킹·커뮤니티·AI 기능 등은 다른 팀원이 맡았습니다.

모니터링을 붙인 뒤 Pinpoint로 다른 팀원이 만든 랭킹 툴팁 API가 느린 것을 찾아 지연 로딩과 쿼리를 고쳐 응답 시간을 900ms대에서 11ms로 줄였습니다.
