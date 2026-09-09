<div align="center">
  <img src="../figs/logo.png" alt="K-P2PLab logo" width="200">

  <h1>K-P2PLab Hub</h1>

  <p>
    <strong>K-P2PLab: A Centrally Orchestrated Multi-Host P2P Testbed with Per-Peer Container Isolation</strong>
  </p>

  <p>
    <b>English</b> ·
    <a href="./RESEARCH.kr.md">한국어</a>
  </p>

  <p>
    <a href="../README.md">Overview</a> ·
    <b>Research</b> ·
    <a href="https://github.com/k-p2p-lab/v3">Public Implementation</a>
  </p>
</div>

---

## Research Focus

**Topology and connectivity.** Examine how peer connections form and evolve, and how overlay structure relates to communication behavior.

**Broadcast performance.** Evaluate message delivery, propagation latency, duplicate reception, and protocol overhead under different configurations.

**Network dynamics.** Investigate how peer joins and departures, communication delays, packet loss, and other network conditions affect connectivity and dissemination.

These are research questions, not a list of measurements or protocols implemented by every version. Use the [v3 architecture guide][v3-architecture] and [scenario reference][v3-scenarios] to establish which mechanisms the current implementation supports.

---

## From Research Question to Experiment

| Dimension | What to decide and record |
| --- | --- |
| **Comparison** | The baseline, the variable being changed, and the hypothesis being evaluated. Separate a protocol change from a change in workload or available resources. |
| **Population and membership** | Which peers publish, subscribe, join, and depart; whether the question concerns the initial population or sessions that remain eligible during observation. |
| **Workload and conditions** | Message size and timing, peer activity, imposed network conditions, host placement, and shared-resource constraints. |
| **Observation** | The meaning of a graph edge or event, the collection interval, the delivery deadline, and how clock uncertainty and missing reports affect interpretation. |
| **Repetition and provenance** | Software revision, input configuration, randomization inputs, execution environment, run identifiers, and retained evidence for each repetition. |

An overlay describes protocol relationships between peers. Host placement describes where those peers execute, and the physical network provides their underlying connectivity. These views answer different questions: a placement diagram does not establish a protocol topology, and a reported protocol relationship does not by itself prove application delivery.

---

## Experimental Reporting Principles

- Define the eligible receiver population and observation window when reporting delivery under churn.
- Choose eligibility independently of delivery success. Report departures and population coverage so a survivor-only result is not mistaken for delivery to the original population.
- Distinguish delivery, latency, duplicate reception, and protocol overhead rather than combining them into one efficiency value.
- State the unit and aggregation rule: per message, receiver, receiver-message pair, RPC, identifier reference, or byte. Identify whether latency includes only successful deliveries.
- Distinguish direct measurements, metadata estimates, model predictions, and fixed reference data. Report evidence, assumptions, and unclassified coverage with estimates; correlation or a baseline difference alone does not establish a forwarding cause or causal effect.
- Distinguish a configured rate limit, observed bytes/throughput, and physical link capacity. State the measurement layer and direction, including whether both endpoints of one transfer are counted.
- Report missing or uncertain observations explicitly so telemetry gaps are not interpreted as protocol failure.
- Record the implementation version or commit, scenario, configuration, and randomization inputs needed to reproduce an experiment.
- Separate an observed result from a configured target and a historical validation record from a check performed on the current revision. Repeated inputs do not guarantee identical distributed execution.

These are project-level principles. Exact event schemas, formulas, defaults, and export behavior are versioned implementation contracts.

For current v3 measurements and estimates, use [experiment metrics][v3-metrics] and [bandwidth measurement][v3-bandwidth]. [Saved-result visualization][v3-visualization] describes repeat comparisons and image/data exports; [API][v3-api] defines analysis jobs and log fields. Check definition version, population, units, and aggregation before comparing values with the same metric name.

---

## Measurement Background

The [HyParView technical report, §2.5 and §5.2][hyparview] evaluates dissemination in terms of active nodes and examines behavior after failures. It provides context for asking about delivery among surviving participants. Our interpretation is that such a question must state its population explicitly; it does not justify excluding only departed receivers that failed to receive.

[Pongthawornkamol et al., ICAC 2013, §2.2 and §3.2.2–3][icac-reliability] connect reliability with delivery before an event deadline and weight publisher-subscriber flows by event rates. Their model concerns broker and link failures, which differs from tracking receiver subscription sessions under churn.

These works provide measurement context; they are not K-P2PLab publications or claims that those protocols are implemented here. K-P2PLab's particular window, session-evidence, weighting, uncertainty, and duplicate-counting rules are implementation design choices. The [v3 metrics guide][v3-metrics] owns their exact definitions and limitations.

---

## Publications

### Platform Publications

*These papers describe K-P2PLab itself.*

**K-P2PLab v3 · No platform publication listed here yet**

**K-P2PLab v2 · APNOMS 2025**<br>
[K-P2PLab: A Scalable Docker Swarm-Based Testbed for Peer-to-Peer Topology Analysis][v2-paper]<br>
Sungwook Lee, Hyungyeop Kim, Seungmin Kim, and Hongtaek Ju.<br>
*25th Asia-Pacific Network Operations and Management Symposium (APNOMS), September 2025.* · English

**K-P2PLab v1 · KNOM Review 2024**<br>
[K-P2PLab: Development Testbed and Analysis Platform for P2P Network Topology Analysis][v1-paper]<br>
Sung-wook Lee and Hong-taek Ju.<br>
*KNOM Review, vol. 27, no. 2, pp. 40–48, December 2024.* · Korean

### Research Using K-P2PLab

Selected studies that report experiments conducted using K-P2PLab. See each paper for its experimental setup.

**Structural analysis of duplicate message reception · ICBC 2026**<br>
[A Node Triple-Based Structural Analysis of Duplicate Message Reception in P2P Broadcast Networks][ntcm-paper]<br>
Sungwook Lee, Jinhyeok Lee, Seungmin Kim, Hyungyeop Kim, and Hongtaek Ju.<br>
*IEEE International Conference on Blockchain and Cryptocurrency (ICBC), June 2026.*

**Network delay and churn · APNOMS 2025**<br>
[An Analysis of the Impact of Network Delay and Churn on Broadcast Efficiency in GossipSub-based P2P Networks][churn-paper]<br>
Sungwook Lee, Hyungyeop Kim, Seungmin Kim, and Hongtaek Ju.<br>
*25th Asia-Pacific Network Operations and Management Symposium (APNOMS), September 2025.*

---

## Citing K-P2PLab

Please cite the platform publication relevant to your work and identify the software version or commit used in your experiments.

For experiments using **v3**, reference the [public implementation repository][v3-repo] and record the version or commit. The v1 and v2 papers document earlier implementations and may also be cited for the project's design history; they should not be treated as documentation of the exact v3 implementation.

---

<div align="center">
  <sub>
    <b><a href="https://github.com/k-p2p-lab">K-P2PLab</a> · <a href="https://comnet.kmu.ac.kr">Computer Network Laboratory</a></b>, <i><a href="https://www.kmu.ac.kr">Keimyung University</a>, Daegu, Republic of Korea</i>
  </sub>
</div>

[v3-repo]: https://github.com/k-p2p-lab/v3
[v3-metrics]: https://github.com/k-p2p-lab/v3/blob/master/docs/experiment-metrics.md
[v3-architecture]: https://github.com/k-p2p-lab/v3/blob/master/docs/architecture.md
[v3-scenarios]: https://github.com/k-p2p-lab/v3/blob/master/docs/scenario-reference.md
[v3-visualization]: https://github.com/k-p2p-lab/v3/blob/master/docs/visualization.md
[v3-bandwidth]: https://github.com/k-p2p-lab/v3/blob/master/docs/bandwidth.md
[v3-api]: https://github.com/k-p2p-lab/v3/blob/master/docs/api.md
[hyparview]: https://www.dpss.inesc-id.pt/~ler/reports/dsn07-leitao.pdf
[icac-reliability]: https://www.usenix.org/system/files/conference/icac13/icac13_pongthawornkamol.pdf
[v1-paper]: https://doi.org/10.22670/knom.2024.27.2.40
[v2-paper]: https://doi.org/10.23919/APNOMS67058.2025.11181317
[ntcm-paper]: https://doi.org/10.1109/ICBC67748.2026.11575499
[churn-paper]: https://doi.org/10.23919/APNOMS67058.2025.11181302
