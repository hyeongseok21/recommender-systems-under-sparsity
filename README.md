# Recommender Systems under Sparse Marketplace Regimes

현대의 marketplace recommendation system은 **extreme sparsity** 환경에서 동작합니다.
대부분의 user는 전체 item 중 일부에만 상호작용하며 behavioral signal은 약하고, popularity effect는 강하게 나타납니다.

이 포트폴리오는 이러한 **sparse interaction regime**에서 recommender system이 어떻게 동작하는지를 두 가지 상호보완적인 관점에서 탐구합니다.

* **system-level ranking behavior in marketplace feeds**
* **model behavior in sparse sequential recommendation**

단순한 model 성능 비교를 넘어서,
**dataset regime, evaluation metric, ranking strategy가 sparse marketplace 환경에서 어떻게 상호작용하는지**를 분석하는 것이 목표입니다.

---

# Key Insights

실험 전반에서 다음과 같은 패턴이 반복적으로 관찰되었습니다.

* **Hybrid ranking**은 sparse marketplace feed에서 heuristic signal과 learned relevance를 효과적으로 균형 잡습니다.
* **Offline engagement metric**은 latent user utility와 항상 일치하지 않습니다.
* **Extreme sparsity** 환경에서는 model architecture만으로 **popularity baseline**을 안정적으로 넘기기 어렵습니다.
* behavioral signal이 약한 상황에서는 **metadata signal의 가치가 크게 증가합니다**.
* recommendation behavior는 **user regime**에 따라 크게 달라지므로 slice analysis가 중요합니다.

---

# Research Projects

이 포트폴리오는 sparse recommender systems를 **system-level**과 **model-level** 두 레벨에서 분석합니다.

## 1. System-Level Analysis

### Synthetic Marketplace Ranking Study

synthetic marketplace simulator를 구축하여 **ranking strategy behavior**를 분석합니다.

Main focus:

* heuristic vs ML vs hybrid ranking
* metric sensitivity
* marketplace health trade-off (seller exposure, diversity)
* sparsity regime에 따른 ranking behavior

Key finding:

heuristic marketplace signal이 여전히 강한 환경에서는
**Hybrid ranking strategy가 가장 안정적인 성능을 보이는 경우가 많았습니다.**

Repository
[synthetic-marketplace-ranking-study](https://github.com/hyeongseok21/synthetic-marketplace-ranking-study)

---

## 2. Model-Level Analysis

### Sequential Recommendation under Sparse Interaction Regimes

real fashion purchase dataset을 사용하여 **sequential recommendation model behavior**를 분석합니다.

Main focus:

* metadata usefulness under weak behavioral signals
* candidate frontier shift
* user regime별 slice analysis
* extreme sparsity에서의 popularity dominance

Key finding:

behavioral signal이 약할 때는 **metadata signal이 personalized recommendation을 개선할 수 있지만**,
highly sparse dataset에서는 **global popularity가 전체 성능을 여전히 지배할 수 있습니다.**

Repository
[sequential-recommendation-under-sparsity](https://github.com/hyeongseok21/sequential-recommendation-under-sparsity)

---

# Shared Experimentation Framework

두 프로젝트는 모두 recommender system 실험 루프를 구조화하기 위한
**agent-driven experimentation framework** 위에서 수행되었습니다.

이 프레임워크는 다음 단계를 자동화합니다.

* dataset construction
* model training
* evaluation
* slice analysis
* experiment reporting

이를 통해 실험을 체계적으로 반복하고 reproducible한 experiment log를 유지할 수 있었습니다.

---

# Research Theme

이 포트폴리오는 다음 질문을 탐구합니다.

**behavioral data가 극도로 sparse할 때, recommender system은 어떻게 설계되어야 하는가?**

특히 다음 요소들이 실제 marketplace 환경에서 recommender system behavior를 어떻게 결정하는지를 분석합니다.

* ranking strategy
* dataset regime
* evaluation metric
* system-level constraints
