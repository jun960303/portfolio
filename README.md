# 🎵 YouAreGABIA Music Platform

> K-POP 팬을 위한 음악 스트리밍 · 커뮤니티 통합 풀스택 프로젝트

[![Portfolio](https://img.shields.io/badge/Portfolio-보러가기-2563eb?style=for-the-badge&logo=github)](https://jun960303.github.io/portfolio)
[![Live Demo](https://img.shields.io/badge/Live_Demo-gapmusic.duckdns.org-00b4d8?style=for-the-badge&logo=google-chrome)](http://gapmusic.duckdns.org)

---

## 📌 프로젝트 소개

유튜브에서 곡을 듣고, 레딧에서 리뷰를 찾고, 별도 앱에서 퀴즈를 하는 **음악 활동의 파편화**를 해소하기 위해 기획한 프로젝트입니다.  
음악 감상 · AI 추천 · 커뮤니티 · 게임 · 굿즈 쇼핑까지 **하나의 플랫폼**에서 경험할 수 있습니다.

| 항목 | 내용 |
|------|------|
| **프로젝트명** | YouAreGABIA Music Platform |
| **개발 기간** | 2026.01 ~ 2026.04 (약 3개월) |
| **팀 구성** | 4인 팀 프로젝트 |
| **담당 역할** | AI 음악 추천 · 공동 플레이리스트 · AI 챗봇 · 추천 플레이리스트 리뷰 |

---

## 🛠 기술 스택

**Frontend**  
![React](https://img.shields.io/badge/React_18-61DAFB?style=flat-square&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite_7-646CFF?style=flat-square&logo=vite&logoColor=white)
![Redux](https://img.shields.io/badge/Redux_Toolkit-764ABC?style=flat-square&logo=redux&logoColor=white)

**Backend**  
![Spring Boot](https://img.shields.io/badge/Spring_Boot_3.x-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![Java](https://img.shields.io/badge/Java_17-007396?style=flat-square&logo=openjdk&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL_8.0-4479A1?style=flat-square&logo=mysql&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=flat-square&logo=jsonwebtokens&logoColor=white)

**AI / Python**  
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI_GPT--4o--mini-412991?style=flat-square&logo=openai&logoColor=white)
![FAISS](https://img.shields.io/badge/FAISS-0467DF?style=flat-square)

**Infra**  
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)

---

## ✨ 주요 기능

| 기능 | 설명 |
|------|------|
| 🔐 **회원 / 인증** | 이메일 가입, SMS 인증, Google·Kakao·Naver OAuth2, JWT, AES-256 암호화 |
| 🎵 **AI 음악 추천** | FAISS 벡터 유사도 + Last.fm API 하이브리드 추천, Min-Max 정규화, 10분 캐싱 |
| 🤖 **AI 챗봇** | Rule-based 기능 안내 + GPT-4o-mini 추천, iTunes API hallucination 검증 |
| 🎶 **개인 플레이리스트** | iTunes API 곡 검색·추가, 30초 미리듣기, 플레이리스트 공유 |
| 👥 **공동 플레이리스트** | 곡 제안(최대 5곡) + 투표(최대 3곡), 마감 시 상위 10곡 자동 선정 |
| 📝 **커뮤니티** | 게시판 3종, 대댓글, 블라인드 곡 추천, Rate Limiting |
| 🎮 **게임 / 랭킹** | 음악 퀴즈, 앨범 퀴즈, 이상형 월드컵(8~64강), 5단계 등급 시스템 |
| 🛍 **굿즈샵** | Toss Payments 결제, Sweettracker 배송 추적, 관리자 대시보드 |

---

## 🔧 트러블 슈팅

<details>
<summary><b>포인트 이중 차감 버그</b></summary>

**문제**: DB 저장보다 상태 업데이트가 먼저 실행되어 차감이 한 번 더 발생  
**해결**: 포인트 차감 → PointHistory 저장 → UserPoint 업데이트 순서로 실행 흐름 재정렬

</details>

<details>
<summary><b>유사도 점수 균일 현상</b></summary>

**문제**: 오디오 특성 벡터 유사도가 모두 75%로 동일하게 출력되어 변별력 없음  
**해결**: Min-Max 정규화로 오디오 점수를 0.5~1.0 범위로 재분포하여 변별력 확보

</details>

<details>
<summary><b>정렬 변경 시 재생 오류</b></summary>

**문제**: 정렬 순서 변경 시 PlayerContext 큐가 이전 순서 그대로 남아 다음 곡이 잘못 재생  
**해결**: onChange 핸들러에서 새 정렬 기준으로 큐를 재계산하고 현재 곡 인덱스를 찾아 play() 재호출

</details>

<details>
<summary><b>새로고침 시 로그인 풀림</b></summary>

**문제**: Redux는 메모리 상태라 페이지 새로고침 시 초기값으로 리셋됨  
**해결**: Redux-Persist 도입으로 localStorage에 인증 상태 영속화하여 새로고침 후에도 로그인 유지

</details>

---

## 👨‍💻 팀 소개

| 이름 | 역할 |
|------|------|
| **이주용** (팀장) | AI 음악 추천, 추천 플레이리스트 리뷰, 공동 플레이리스트, AI 챗봇 |
| **김형준** | 로그인/회원가입, 마이페이지, 굿즈샵, 관리자 |
| **윤기선** | 게시판, 랭킹, 미니게임, 유저 포인트 |
| **김경민** | 메인 홈페이지, 개인 플레이리스트, 이상형 월드컵 |

---

## 🔗 링크

- 📄 **포트폴리오**: https://jun960303.github.io/portfolio
- 🌐 **라이브 데모**: http://gapmusic.duckdns.org
