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

이 항목들은 연구 질문이며, 모든 버전이 구현한 지표나 프로토콜의 목록은 아닙니다. 현재 구현에서 지원하는 수단은 [v3 아키텍처 가이드][v3-architecture]와 [시나리오 레퍼런스][v3-scenarios]에서 확인하십시오.

---

## 연구 질문에서 실험으로

| 차원 | 결정하고 기록할 내용 |
| --- | --- |
| **비교** | 기준 실험, 변경할 변수, 검증할 가설입니다. 프로토콜 변경과 워크로드 또는 가용 자원 변경을 구분합니다. |
| **피어 집합과 참여 상태** | 발행·구독·참가·이탈하는 피어를 정의하고, 최초 집합을 대상으로 하는지 관측 중 계속 자격을 유지한 세션을 대상으로 하는지 명시합니다. |
| **워크로드와 조건** | 메시지 크기와 시간, 피어 활동, 부여한 네트워크 조건, 호스트 배치, 공유 자원의 제약입니다. |
| **관측** | 그래프 간선이나 이벤트의 의미, 수집 간격, 전달 마감 시점, 시계 불확실성과 보고 누락이 해석에 미치는 영향입니다. |
| **반복과 출처** | 각 반복의 소프트웨어 리비전, 입력 설정, 무작위화 입력, 실행 환경, 실행 식별자, 보존한 증거입니다. |

오버레이는 피어 사이의 프로토콜 관계를, 호스트 배치는 피어의 실행 위치를 나타내며, 물리 네트워크는 그 기반 연결성을 제공합니다. 이 관점들은 서로 다른 질문에 답합니다. 배치 그림이 프로토콜 토폴로지를 입증하지 않으며, 보고된 프로토콜 관계만으로 애플리케이션 전달을 입증할 수도 없습니다.

---

## 실험 결과 보고 원칙

- churn 상황의 도달률을 보고할 때 수신 대상이 되는 피어 집합과 관측 시간 구간을 정의합니다.
- 전달 성공 여부와 독립적으로 수신 자격을 정합니다. 생존한 피어만의 결과를 최초 피어 집합에 대한 도달률로 오해하지 않도록 이탈과 집합 커버리지를 함께 보고합니다.
- 도달률, 지연, 중복 수신과 프로토콜 오버헤드를 하나의 효율 값으로 합치지 않고 구분합니다.
- 메시지, 수신자, 수신자-메시지 쌍, RPC, 식별자 참조, 바이트 등 집계 단위와 규칙을 명시합니다. 지연이 성공한 전달만을 포함하는지도 밝힙니다.
- 직접 측정한 값, 메타정보에서 추정한 값, 모델 예측과 고정 참고자료를 구분하십시오. 추정에는 사용한 근거·가정·미분류 비율을 함께 보고하고, 상관이나 기준 실험과의 차이만으로 전파 원인이나 인과 효과를 단정하지 마십시오.
- 설정한 전송률 제한, 관측한 바이트·전송률, 물리 회선의 용량을 구분하십시오. 측정 계층과 방향을 명시하고 같은 전송의 양쪽 끝을 중복 합산하지 않도록 하십시오.
- 텔레메트리 누락을 프로토콜 실패로 해석하지 않도록 누락되거나 불확실한 관측을 명시합니다.
- 실험을 재현하는 데 필요한 구현 버전 또는 커밋, 시나리오, 설정과 무작위화 입력을 기록합니다.
- 관측 결과와 설정 목표를 구분하고, 과거 검증 기록과 현재 리비전에서 수행한 검사를 구분합니다. 입력을 반복해도 분산 실행이 같아지는 것은 아닙니다.

위 항목은 프로젝트 수준의 원칙입니다. 정확한 이벤트 스키마, 공식, 기본값과 내보내기 동작은 버전별 구현 계약입니다.

현재 v3에서 수집·추정하는 지표의 정확한 정의는 [실험 지표][v3-metrics]와 [대역폭 측정][v3-bandwidth]에 있습니다. [저장 결과 시각화][v3-visualization]는 반복 비교와 이미지·자료 내보내기 방법을, [API][v3-api]는 분석 작업과 로그 필드를 설명합니다. 비교에는 지표 이름뿐 아니라 정의 버전·모집단·단위·집계 규칙이 같은지 확인하십시오.

---

## 측정의 연구 배경

[HyParView 기술 보고서의 §2.5와 §5.2][hyparview]는 활성 노드를 기준으로 메시지 전파를 평가하고 장애 이후 동작을 살펴봅니다. 이는 살아남은 참여자 사이의 전달을 묻는 연구 질문에 배경을 제공합니다. 이 문서에서는 그러한 질문의 대상 집합을 명시해야 한다고 해석하며, 수신하지 못하고 이탈한 피어만 제외하는 근거로 사용하지 않습니다.

[Pongthawornkamol 외, ICAC 2013의 §2.2와 §3.2.2–3][icac-reliability]은 신뢰성을 이벤트 마감 전 전달과 연결하고, 발행자-구독자 흐름을 이벤트 발생률로 가중합니다. 이 모델은 브로커와 링크 장애를 다루므로 churn 상황에서 수신자의 구독 세션을 추적하는 문제와 다릅니다.

이 연구들은 측정의 배경 자료이며, K-P2PLab 논문이나 해당 프로토콜이 이곳에 구현되어 있다는 주장이 아닙니다. K-P2PLab의 구체적인 시간 구간, 세션 증거, 가중, 불확실성, 중복 집계 규칙은 구현 설계의 선택입니다. 정확한 정의와 한계는 [v3 지표 가이드][v3-metrics]에서 관리합니다.

---

## 논문

### 플랫폼 논문

*다음 논문은 K-P2PLab 플랫폼 자체를 설명합니다.*

**K-P2PLab v3 · 아직 이 목록에 등록된 플랫폼 논문 없음**

**K-P2PLab v2 · APNOMS 2025**<br>
[K-P2PLab: A Scalable Docker Swarm-Based Testbed for Peer-to-Peer Topology Analysis][v2-paper]<br>
Sungwook Lee, Hyungyeop Kim, Seungmin Kim, and Hongtaek Ju.<br>
*25th Asia-Pacific Network Operations and Management Symposium (APNOMS), September 2025.* · 영어

**K-P2PLab v1 · KNOM Review 2024**<br>
[K-P2PLab: Development Testbed and Analysis Platform for P2P Network Topology Analysis][v1-paper]<br>
Sung-wook Lee and Hong-taek Ju.<br>
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
[v3-architecture]: https://github.com/k-p2p-lab/v3/blob/master/docs/architecture.kr.md
[v3-scenarios]: https://github.com/k-p2p-lab/v3/blob/master/docs/scenario-reference.kr.md
[v3-visualization]: https://github.com/k-p2p-lab/v3/blob/master/docs/visualization.kr.md
[v3-bandwidth]: https://github.com/k-p2p-lab/v3/blob/master/docs/bandwidth.kr.md
[v3-api]: https://github.com/k-p2p-lab/v3/blob/master/docs/api.kr.md
[hyparview]: https://www.dpss.inesc-id.pt/~ler/reports/dsn07-leitao.pdf
[icac-reliability]: https://www.usenix.org/system/files/conference/icac13/icac13_pongthawornkamol.pdf
[v1-paper]: https://doi.org/10.22670/knom.2024.27.2.40
[v2-paper]: https://doi.org/10.23919/APNOMS67058.2025.11181317
[ntcm-paper]: https://doi.org/10.1109/ICBC67748.2026.11575499
[churn-paper]: https://doi.org/10.23919/APNOMS67058.2025.11181302
