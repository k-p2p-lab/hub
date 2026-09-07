<div align="center">
  <img src="../figs/logo.png" alt="K-P2PLab 로고" width="200">

  <h1>K-P2PLab Hub</h1>

  <p>
    <strong>K-P2PLab: 피어별 컨테이너 격리를 제공하는 중앙 오케스트레이션 기반 다중 호스트 P2P 테스트베드</strong>
  </p>

  <p>
    <a href="./RESEARCH.md">English</a> ·
    <b>한국어</b>
  </p>

  <p>
    <a href="../README.kr.md">개요</a> ·
    <b>연구</b> ·
    <a href="https://github.com/k-p2p-lab/v3">공개 구현체</a>
  </p>
</div>

---

## 연구 주제

**토폴로지와 연결성.** 피어 연결이 형성되고 변화하는 방식과 오버레이 구조가 통신 동작에 미치는 관계를 연구합니다.

**브로드캐스트 성능.** 다양한 설정에서 메시지 도달률, 전파 지연, 중복 수신과 프로토콜 오버헤드를 평가합니다.

**네트워크 다이나믹스.** 피어의 참가와 이탈, 통신 지연, 패킷 손실 및 기타 네트워크 조건이 연결성과 메시지 전파에 미치는 영향을 분석합니다.

---

## 실험 결과 보고 원칙

- churn 상황의 도달률을 보고할 때 수신 대상이 되는 피어 집합과 관측 시간 구간을 정의합니다.
- 도달률, 지연, 중복 수신과 프로토콜 오버헤드를 하나의 효율 값으로 합치지 않고 구분합니다.
- 텔레메트리 누락을 프로토콜 실패로 해석하지 않도록 누락되거나 불확실한 관측을 명시합니다.
- 실험을 재현하는 데 필요한 구현 버전 또는 커밋, 시나리오, 설정과 무작위화 입력을 기록합니다.

위 항목은 프로젝트 수준의 원칙입니다. 정확한 이벤트 스키마, 공식, 기본값과 내보내기 동작은 버전별 구현 계약이며, 현재 공개 구현체는 [v3 실험 지표 가이드][v3-metrics]에서 설명합니다.

---

## 논문

### 플랫폼 논문

*다음 논문은 K-P2PLab 플랫폼 자체를 설명합니다.*

**K-P2PLab v3 · 출판 예정**

**K-P2PLab v2 · APNOMS 2025**<br>
[K-P2PLab: A Scalable Docker Swarm-Based Testbed for Peer-to-Peer Topology Analysis][v2-paper]<br>
Sungwook Lee, Hyungyeop Kim, Seungmin Kim, and Hongtaek Ju.<br>
*25th Asia-Pacific Network Operations and Management Symposium (APNOMS), September 2025.* · 영어

**K-P2PLab v1 · KNOM Review 2024**<br>
[K-P2PLab: Development Testbed and Analysis Platform for P2P Network Topology Analysis][v1-paper]<br>
Sungwook Lee and Hongtaek Ju.<br>
*KNOM Review, vol. 27, no. 2, pp. 40–48, December 2024.* · 한국어

### K-P2PLab을 사용한 연구

K-P2PLab에서 수행한 실험을 보고하는 주요 연구입니다. 실험 설정은 각 논문을 참고하십시오.

**중복 메시지 수신의 구조 분석 · ICBC 2026**<br>
[A Node Triple-Based Structural Analysis of Duplicate Message Reception in P2P Broadcast Networks][ntcm-paper]<br>
Sungwook Lee, Jinhyeok Lee, Seungmin Kim, Hyungyeop Kim, and Hongtaek Ju.<br>
*IEEE International Conference on Blockchain and Cryptocurrency (ICBC), June 2026.*

**네트워크 지연과 churn · APNOMS 2025**<br>
[An Analysis of the Impact of Network Delay and Churn on Broadcast Efficiency in GossipSub-based P2P Networks][churn-paper]<br>
Sungwook Lee, Hyungyeop Kim, Seungmin Kim, and Hongtaek Ju.<br>
*25th Asia-Pacific Network Operations and Management Symposium (APNOMS), September 2025.*

---

## K-P2PLab 인용

연구에 해당하는 플랫폼 논문을 인용하고, 실험에 사용한 소프트웨어 버전 또는 커밋을 명시하십시오.

**v3**로 실험했다면 [공개 구현 저장소][v3-repo]를 참조하고 버전 또는 커밋을 기록하십시오. v1과 v2 논문은 이전 구현과 프로젝트 설계의 발전 과정을 설명하지만, v3 구현의 정확한 문서로 사용해서는 안 됩니다.

---

<div align="center">
  <sub>
    <b><a href="https://github.com/k-p2p-lab">K-P2PLab</a> · <a href="https://comnet.kmu.ac.kr">컴퓨터네트워크 연구실</a></b>, <i><a href="https://www.kmu.ac.kr">계명대학교</a>, 대한민국 대구</i>
  </sub>
</div>

[v3-repo]: https://github.com/k-p2p-lab/v3
[v3-metrics]: https://github.com/k-p2p-lab/v3/blob/master/docs/experiment-metrics.kr.md
[v1-paper]: https://doi.org/10.22670/knom.2024.27.2.40
[v2-paper]: https://doi.org/10.23919/APNOMS67058.2025.11181317
[ntcm-paper]: https://doi.org/10.1109/ICBC67748.2026.11575499
[churn-paper]: https://doi.org/10.23919/APNOMS67058.2025.11181302
