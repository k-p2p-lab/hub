<div align="center">
  <img src="../figs/logo.png" alt="K-P2PLab logo" width="200">

  <h1>K-P2PLab Hub</h1>

  <p>
    <strong>K-P2PLab: A Centrally Orchestrated Multi-Host P2P Testbed with Per-Peer Container Isolation</strong>
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

**Broadcast performance.** Evaluate message delivery, propagation latency, and duplicate reception under different protocol configurations.

**Network dynamics.** Investigate how peer joins and departures, communication delays, and other network conditions affect connectivity and dissemination.

---

## Publications

### Platform Publications

*These papers describe K-P2PLab itself.*

**K-P2PLab v3 · Yet to be published**  

**K-P2PLab v2 · APNOMS 2025**  
[K-P2PLab: A Scalable Docker Swarm-Based Testbed for Peer-to-Peer Topology Analysis][v2-paper]  
Sungwook Lee, Hyungyeop Kim, Seungmin Kim, and Hongtaek Ju.  
*25th Asia-Pacific Network Operations and Management Symposium (APNOMS), September 2025.* · English

**K-P2PLab v1 · KNOM Review 2024**  
[K-P2PLab: Development Testbed and Analysis Platform for P2P Network Topology Analysis][v1-paper]  
Sungwook Lee and Hongtaek Ju.  
*KNOM Review, vol. 27, no. 2, pp. 40–48, December 2024.* · Korean

### Research Using K-P2PLab

Selected studies that report experiments conducted using K-P2PLab. See each paper for its experimental setup.

**Structural analysis of duplicate message reception · ICBC 2026**  
[A Node Triple-Based Structural Analysis of Duplicate Message Reception in P2P Broadcast Networks][ntcm-paper]  
Sungwook Lee, Jinhyeok Lee, Seungmin Kim, Hyungyeop Kim, and Hongtaek Ju.  
*IEEE International Conference on Blockchain and Cryptocurrency (ICBC), June 2026.*

**Network delay and churn · APNOMS 2025**  
[An Analysis of the Impact of Network Delay and Churn on Broadcast Efficiency in GossipSub-based P2P Networks][churn-paper]  
Sungwook Lee, Hyungyeop Kim, Seungmin Kim, and Hongtaek Ju.  
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
[v1-paper]: https://doi.org/10.22670/knom.2024.27.2.40
[v2-paper]: https://doi.org/10.23919/APNOMS67058.2025.11181317
[ntcm-paper]: https://doi.org/10.1109/ICBC67748.2026.11575499
[churn-paper]: https://doi.org/10.23919/APNOMS67058.2025.11181302
