================================================================================
HCS-U7 POC PROPOSAL — SASSA FRAUD INTELLIGENCE
================================================================================

[Dual Value Proposition] [Offline Architecture] [90-Day POC] [Risk Intelligence + Shield]

--------------------------------------------------------------------------------
SLIDE 1 — EXECUTIVE SUMMARY
--------------------------------------------------------------------------------

**Problem Statement**
SASSA faces R200+ billion in annual grant disbursements with:
- Massive identity theft (deceased beneficiaries, loaned IDs)
- Sophisticated attacks (IMSI catchers, GPS spoofing)
- Agent corruption (syndicated fraud networks)
- Limited investigative capacity

**Our Solution : Dual Value Proposition**
1. **Fraud Intelligence** : Behavioral anomaly detection (offline)
2. **Shield Module** : State-level threat protection (UNIQUE au marché)

**POC Scope : 90 Days, Offline, Zero Production Risk**
- Ingest historical data (6 months beneficiary behavior)
- Generate risk dashboards + investigative leads
- Identify fraud clusters post-payment
- Quantify potential savings

**Success Metrics**
- 500+ high-risk cases flagged for investigation
- 40% reduction in manual review time
- R50M+ fraud identified (post-payment recovery)
- Zero production system disruption


--------------------------------------------------------------------------------
SLIDE 2 — THE SASSA FRAUD LANDSCAPE
--------------------------------------------------------------------------------

**Scale of the Problem**
- R200+ billion annual disbursements
- 18 million beneficiaries
- 10,000+ payment points nationwide
- Estimated 5-15% fraud/leakage (R10-30B/year)

**Fraud Typologies**
1. **Identity Misuse**
   - Deceased beneficiaries (ghost payouts)
   - Loaned IDs (proxy collection)
   - Synthetic identities

2. **Agent Corruption**
   - Collusion with criminal networks
   - IMSI catcher usage (SMS interception)
   - GPS spoofing (fake locations)

3. **Beneficiary Fraud**
   - Multiple claims (different provinces)
   - False eligibility documentation
   - Address manipulation

**Current Gaps**
- Reactive investigation (post-complaint)
- Limited behavioral analytics
- No state-level threat detection
- Manual review bottlenecks


--------------------------------------------------------------------------------
SLIDE 3 — WHY EXISTING SOLUTIONS FAIL
--------------------------------------------------------------------------------

**Comparison : Traditional Fraud Detection vs. HCS-U7**

| Capability | Experian | FICO Falcon | SAS Fraud | HCS-U7 |
|------------|----------|-------------|-----------|--------|
| **Behavioral Biometrics** | ⚠️ Basic | ⚠️ Basic | ⚠️ Basic | ✅ Advanced (6 tests) |
| **IMSI Catcher Detection** | ❌ | ❌ | ❌ | ✅ Shield Module |
| **Impossible Travel** | ⚠️ IP-based | ⚠️ IP-based | ⚠️ IP-based | ✅ GPS + Haversine |
| **GPS Spoofing Detection** | ❌ | ❌ | ❌ | ✅ Shield Module |
| **Cognitive Testing** | ❌ | ❌ | ❌ | ✅ 6 validated tests |
| **Post-Quantum Crypto** | ❌ | ❌ | ❌ | ✅ Dilithium3 + Kyber768 |
| **Offline POC Risk** | High | High | High | Zero |

**Key Differentiator**
HCS-U7 Shield Module detects state-level threats that bypass ALL traditional solutions.


--------------------------------------------------------------------------------
SLIDE 4 — DUAL VALUE PROPOSITION
--------------------------------------------------------------------------------

**Value Stream 1 : Fraud Intelligence (Offline)**

🔍 **Anomaly Detection**
- Behavioral pattern clustering (ML-based)
- Statistical outlier identification
- Temporal analysis (access timing, frequency)
- Geospatial correlation (beneficiary movements)

📊 **Investigative Leads**
- Top 100 high-risk cases (ranked by score)
- Cluster analysis (syndicated networks)
- Historical trend analysis
- Evidence packages for prosecution

⏱️ **Efficiency Gains**
- 40% reduction in manual review time
- Automated triage (high/medium/low risk)
- Prioritized case allocation
- Real-time dashboards

**Value Stream 2 : Shield Module (UNIQUE)**

📡 **IMSI Catcher Detection**
- LAC analysis (suspicious Location Area Codes)
- Signal strength anomalies (>-40 dBm = too strong)
- Handover rate monitoring (>5/min = suspicious)
- Encryption downgrade detection (A5/3 → A5/0)

→ **Use Case** : Detect corrupt agents using Stingray devices to intercept beneficiary SMS OTPs

📍 **Impossible Travel Detection**
- Haversine distance calculation
- Time-based plausibility (>900 km/h = impossible)
- Multi-location correlation (same beneficiary, 3 provinces, 2 hours)

→ **Use Case** : Identify syndicated identity theft (1 ID used in Johannesburg, Cape Town, Durban simultaneously)

🛰️ **GPS Spoofing Detection**
- Round coordinate analysis (lat/lon % 1 === 0)
- Impossible accuracy (<5m suspicious for mobile GPS)
- Historical pattern deviation

→ **Use Case** : Detect fake geolocation for eligibility fraud (rural address requirement)


--------------------------------------------------------------------------------
SLIDE 5 — POC ARCHITECTURE (OFFLINE, ZERO RISK)
--------------------------------------------------------------------------------

**Data Flow**

```
┌─────────────────────────────────────────────────────┐
│  SASSA Production Systems (UNTOUCHED)               │
│  ├─ Grant disbursement database                     │
│  ├─ Beneficiary authentication logs                 │
│  ├─ Payment transaction history                     │
│  └─ Geolocation data (if available)                 │
└────────────┬────────────────────────────────────────┘
             │
             │ Batch export (daily, historical 6 months)
             │ Format: CSV / JSON / Database dump
             ▼
┌─────────────────────────────────────────────────────┐
│  Cyber1 Analytics Platform (Secure Environment)     │
│  ├─ Data ingestion pipeline                         │
│  ├─ HCS-U7 Risk Engine (Docker container)           │
│  ├─ Shield Module analysis (cell tower + GPS data)  │
│  └─ Anomaly detection ML models                     │
└────────────┬────────────────────────────────────────┘
             │
             │ Risk scores + Investigative leads
             ▼
┌─────────────────────────────────────────────────────┐
│  SASSA Fraud Investigation Dashboard                │
│  ├─ Top 100 high-risk beneficiaries                 │
│  ├─ Cluster visualization (network graphs)          │
│  ├─ Evidence packages (audit trail)                 │
│  └─ Export to case management system                │
└─────────────────────────────────────────────────────┘
             │
             │ Manual investigation
             ▼
┌─────────────────────────────────────────────────────┐
│  SASSA Fraud Recovery & Prosecution                 │
│  ├─ Case review and validation                      │
│  ├─ Recovery actions (grant suspension)             │
│  └─ Legal proceedings (evidence)                    │
└─────────────────────────────────────────────────────┘
```

**Security & Compliance**
- ✅ Air-gapped environment (Cyber1 secure infrastructure)
- ✅ Data anonymization (PII pseudonymization)
- ✅ POPIA compliance (SA data protection)
- ✅ ISO 27001 aligned (Cyber1 + HCS-U7)
- ✅ Audit trail (all data access logged)


--------------------------------------------------------------------------------
SLIDE 6 — POC DELIVERABLES (90 DAYS)
--------------------------------------------------------------------------------

**Phase 1 : Setup & Data Ingestion (Days 1-30)**

Week 1-2: Environment Setup
- Cyber1 secure analytics environment provisioned
- HCS-U7 Docker containers deployed
- Data ingestion pipeline configured
- Access controls and audit logging enabled

Week 3-4: Historical Data Load
- 6 months beneficiary behavioral data
- Authentication logs (login times, locations, devices)
- Payment transaction history
- Cell tower data (if available)
- GPS coordinates (authentication events)

**Phase 2 : Analysis & Model Training (Days 31-60)**

Week 5-6: Baseline Establishment
- Normal behavior profiling
- Statistical thresholds calibration
- ML model training (anomaly detection)
- Shield Module parameter tuning

Week 7-8: Anomaly Detection
- Run HCS-U7 risk engine on historical data
- Generate behavioral anomaly scores
- Identify impossible travel cases
- Flag IMSI catcher / GPS spoofing signals

**Phase 3 : Validation & Reporting (Days 61-90)**

Week 9-10: Case Validation
- SASSA investigators review top 100 cases
- True positive / false positive analysis
- Feedback loop for model refinement
- Evidence package generation

Week 11-12: Final Report & Metrics
- POC results presentation
- ROI calculation (fraud identified vs. cost)
- Production roadmap (if approved)
- Handover to SASSA IT team


--------------------------------------------------------------------------------
SLIDE 7 — SUCCESS METRICS & KPIs
--------------------------------------------------------------------------------

**Primary Metrics**

| KPI | Target | Measurement |
|-----|--------|-------------|
| **High-Risk Cases Flagged** | 500+ | Beneficiaries scored >70/100 risk |
| **Fraud Identified (Value)** | R50M+ | Post-payment fraud confirmed |
| **Investigative Time Reduction** | 40% | Hours saved per case review |
| **True Positive Rate** | >60% | Flagged cases confirmed fraud |
| **False Positive Rate** | <10% | Flagged cases legitimate |
| **Shield Alerts** | 50+ | IMSI catcher / GPS spoofing detected |

**Secondary Metrics**
- Cluster detection accuracy (syndicated networks)
- Model performance (precision, recall, F1 score)
- Dashboard usability (investigator feedback)
- Data processing latency (<24h batch)


--------------------------------------------------------------------------------
SLIDE 8 — SHIELD MODULE USE CASES (SASSA-SPECIFIC)
--------------------------------------------------------------------------------

**Use Case 1 : Corrupt Agent Detection**

**Scenario**
SASSA agent in rural KwaZulu-Natal colluding with fraud syndicate.
Uses IMSI catcher (Stingray device) to intercept beneficiary SMS OTPs.

**Shield Detection**
- LAC = 0 (fake base station) → +40 risk points
- Signal strength = -35 dBm (too strong for distance) → +20 points
- Handover rate = 8/minute (abnormal) → +10 points
- Risk score = 70 → **DANGEROUS**

**Outcome**
Alert SASSA security → Investigate agent → Confirm corruption → Prosecution

**Impact**
- 1 corrupt agent = 200+ fraudulent grants/month
- Recovery: R2M+ annually
- Deterrence: Signal to other potential bad actors

---

**Use Case 2 : Syndicated Identity Theft**

**Scenario**
Criminal network uses stolen IDs to claim grants in 3 provinces simultaneously.
Same beneficiary ID authenticated in Johannesburg, Cape Town, Durban within 2 hours.

**Shield Detection**
- Location 1: Johannesburg (09:00 AM)
- Location 2: Cape Town (10:30 AM) → 1,400 km in 1.5h = **933 km/h**
- Location 3: Durban (11:00 AM) → 900 km in 1.5h = **600 km/h**
- Impossible travel detected → +50 risk points
- Risk score = 90 → **CRITICAL**

**Outcome**
Suspend grant immediately → Investigate syndicate → Recover funds → Legal action

**Impact**
- 1 syndicate = 500+ stolen IDs
- Recovery: R15M+ annually

---

**Use Case 3 : GPS Spoofing for Eligibility Fraud**

**Scenario**
Urban beneficiary spoofs GPS to claim rural disability grant (higher amount + relaxed verification).

**Shield Detection**
- GPS coordinates: -28.000000, 24.000000 (perfectly round = suspicious)
- Accuracy: 2m (impossible for mobile GPS in rural area)
- Historical pattern: Always urban locations, suddenly rural
- GPS spoofing detected → +40 risk points

**Outcome**
Flag for verification → Physical inspection → Confirm fraud → Grant revoked

**Impact**
- Prevents R5,000/month differential (urban vs. rural)
- R60,000/year per case


--------------------------------------------------------------------------------
SLIDE 9 — CYBER1 ROLE & VALUE ADD
--------------------------------------------------------------------------------

**Why Cyber1 is the Ideal Partner**

✅ **Trusted Government Advisor**
- 28 years cybersecurity experience
- Existing SASSA relationship (SOC services)
- Government sector expertise
- Security clearance and compliance

✅ **Infrastructure & Integration**
- Secure analytics environment (air-gapped)
- SIEM / SOAR platform (data ingestion)
- ISO 27001 certified
- 24/7 SOC operations

✅ **Risk Intelligence Expertise**
- Fraud investigation support
- Anomaly detection experience
- Incident response workflows
- Reporting and dashboards

**Cyber1 Responsibilities in POC**
- Prime integrator and project manager
- Secure environment provisioning
- Data pipeline setup
- SASSA stakeholder management
- Final deliverables and reporting

**HCS-U7 Responsibilities**
- Risk engine deployment (Docker containers)
- Shield Module configuration
- Model training and tuning
- Technical support and documentation
- Knowledge transfer to Cyber1 team


--------------------------------------------------------------------------------
SLIDE 10 — RISK MITIGATION
--------------------------------------------------------------------------------

**Technical Risks**

| Risk | Probability | Mitigation |
|------|-------------|------------|
| Data quality issues | Medium | Data profiling upfront, fallback logic |
| False positive rate too high | Low | Model tuning, investigator feedback loop |
| Performance bottlenecks | Low | Scalable architecture, batch processing |
| Integration complexity | Low | Standard APIs, Docker deployment |

**Operational Risks**

| Risk | Probability | Mitigation |
|------|-------------|------------|
| SASSA stakeholder resistance | Medium | Offline POC, zero production impact |
| Investigator capacity constraints | Medium | Automated triage, prioritized leads |
| Budget delays | Medium | Phased approach, quick wins |
| Political pressure to go live fast | High | Clear POC scope, governance framework |

**Security Risks**

| Risk | Probability | Mitigation |
|------|-------------|------------|
| Data breach | Very Low | Air-gapped, encrypted, access controls |
| Compliance violation (POPIA) | Very Low | Pseudonymization, audit trail, legal review |
| Unauthorized access | Very Low | MFA, role-based access, monitoring |


--------------------------------------------------------------------------------
SLIDE 11 — BUDGET & INVESTMENT
--------------------------------------------------------------------------------

**POC Investment (90 Days)**

| Item | Cost | Notes |
|------|------|-------|
| **HCS-U7 Licensing** | €50,000 | 3-month POC license |
| **Cyber1 Services** | €80,000 | Integration, infrastructure, PM |
| **Data Engineering** | €30,000 | Pipeline setup, ETL, validation |
| **Training & Support** | €20,000 | SASSA investigator training, documentation |
| **Contingency (15%)** | €27,000 | Unforeseen issues |
| **TOTAL POC** | **€207,000** | (~R4.5M at 22 ZAR/EUR) |

**Post-POC Production (Annual)**

| Item | Annual Cost | Notes |
|------|-------------|-------|
| **HCS-U7 SaaS** | €300,000 | Per-beneficiary pricing (18M users) |
| **Cyber1 Managed Services** | €200,000 | 24/7 SOC support, maintenance |
| **SASSA IT Resources** | €100,000 | 2 FTEs (investigators, analysts) |
| **TOTAL Year 1** | **€600,000** | (~R13.2M) |

**ROI Projection**
- Fraud identified: R50M (POC) → R200M+ (Year 1)
- Cost: R4.5M (POC) + R13.2M (Year 1) = R17.7M
- **Net savings: R182M+ (10x ROI)**


--------------------------------------------------------------------------------
SLIDE 12 — TIMELINE & MILESTONES
--------------------------------------------------------------------------------

**POC Timeline : 90 Days**

```
Month 1: Setup & Ingestion
├─ Week 1: Kickoff, environment setup
├─ Week 2: Data pipeline configuration
├─ Week 3: Historical data load (6 months)
└─ Week 4: Data validation, baseline

Month 2: Analysis & Detection
├─ Week 5: Model training (anomaly detection)
├─ Week 6: Shield Module parameter tuning
├─ Week 7: Run analysis, generate risk scores
└─ Week 8: Cluster detection, network analysis

Month 3: Validation & Reporting
├─ Week 9: SASSA investigator case review
├─ Week 10: True positive validation, feedback
├─ Week 11: Final report preparation
└─ Week 12: Executive presentation, decision
```

**Post-POC Production Roadmap (if approved)**

```
Q2 2026: Production Deployment (Months 4-6)
├─ Real-time ingestion pipeline
├─ Investigator dashboard go-live
├─ Training program (100+ investigators)
└─ SLA agreement finalized

Q3 2026: Scale & Optimization (Months 7-9)
├─ Nationwide rollout
├─ Model refinement (feedback loop)
├─ Additional use cases (child grants, disability)
└─ Integration with case management system

Q4 2026: Advanced Features (Months 10-12)
├─ Predictive analytics (fraud forecasting)
├─ Real-time alerting (high-risk transactions)
├─ Mobile app for field investigators
└─ API for third-party integration
```


--------------------------------------------------------------------------------
SLIDE 13 — GOVERNANCE & DECISION FRAMEWORK
--------------------------------------------------------------------------------

**Steering Committee**

| Role | Responsibility | Stakeholder |
|------|----------------|-------------|
| **Executive Sponsor** | Budget approval, strategic alignment | SASSA CEO / CIO |
| **Project Owner** | Day-to-day decisions, UAT sign-off | SASSA Fraud Prevention Head |
| **Technical Lead** | Architecture, security, compliance | SASSA IT Director |
| **Prime Integrator** | Delivery, risk management | Cyber1 Program Manager |
| **Solution Provider** | HCS-U7 deployment, support | IA Solution CTO |

**Go/No-Go Decision Criteria (End of POC)**

✅ **GO to Production if:**
- True positive rate >60%
- Fraud identified >R50M
- Investigator satisfaction >80%
- Zero security incidents
- Budget approval secured

❌ **NO-GO if:**
- True positive rate <40%
- Operational disruption
- Compliance violations
- Cost overruns >30%


--------------------------------------------------------------------------------
SLIDE 14 — COMPETITIVE POSITIONING
--------------------------------------------------------------------------------

**Why HCS-U7 vs. Alternatives?**

| Vendor | Strengths | Weaknesses | SASSA Fit |
|--------|-----------|------------|-----------|
| **Experian** | Global scale, credit data | No state-level threat detection | ⚠️ Medium |
| **FICO Falcon** | Mature ML, banking focus | Payment-centric, not grants | ⚠️ Medium |
| **SAS Fraud** | Enterprise analytics | Complex, expensive, long deployment | ❌ Low |
| **Local vendors (SA)** | Local presence, compliance | Limited innovation, basic analytics | ⚠️ Medium |
| **HCS-U7** | Shield Module (unique), offline POC, flexible | New to SA market | ✅ **High** |

**Unique Differentiators**
1. ✅ **Shield Module** : Only solution detecting IMSI catchers, GPS spoofing
2. ✅ **Offline POC** : Zero production risk, fast validation
3. ✅ **Cognitive Biometrics** : 6 validated tests, behavioral patterns
4. ✅ **Post-Quantum Ready** : Dilithium3 + Kyber768 (future-proof)
5. ✅ **3 Patents** : FR2514274, FR2514546, FR2515560 (defensible IP)


--------------------------------------------------------------------------------
SLIDE 15 — NEXT STEPS
--------------------------------------------------------------------------------

**Immediate Actions (Week 1-2)**

1. **SASSA Stakeholder Alignment**
   - Present POC proposal to Fraud Prevention Head
   - Secure executive sponsor buy-in
   - Confirm data availability and access

2. **Cyber1 Partnership Formalization**
   - Sign MOU (Memorandum of Understanding)
   - Define roles and responsibilities
   - Agree on commercials (revenue share)

3. **Technical Readiness**
   - Data schema documentation
   - Security requirements validation
   - Infrastructure sizing (compute, storage)

**Decision Point : Go/No-Go POC (Week 3)**

If approved:
- Contract signature (SASSA + Cyber1 + HCS-U7)
- Budget release (R4.5M)
- Project kickoff (Week 4)

**Contact Information**

**IA Solution (HCS-U7)**
- Benjamin BARRÈRE, Founder & CTO
- Email: benjamin@ia-solution.fr
- Phone: [à remplir]

**Cyber1 Solutions (Maidar Secure)**
- [Contact Cyber1 à remplir]


--------------------------------------------------------------------------------
SLIDE 16 — APPENDIX : Technical Architecture (Deep Dive)
--------------------------------------------------------------------------------

**HCS-U7 Docker Container Specifications**

```yaml
services:
  hcs-u7-risk-engine:
    image: ia-solution/hcs-u7:latest
    resources:
      limits:
        cpus: '8'
        memory: 32G
    environment:
      - MODE=offline_analysis
      - SHIELD_ENABLED=true
      - LOG_LEVEL=info
    volumes:
      - ./data:/app/data
      - ./output:/app/output
```

**API Endpoints**

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/v1/ingest` | POST | Batch data ingestion |
| `/api/v1/analyze` | POST | Trigger risk analysis |
| `/api/v1/scores` | GET | Retrieve risk scores |
| `/api/v1/shield/alerts` | GET | Shield Module alerts |
| `/api/v1/reports` | GET | Generate reports |

**Security Controls**
- Encryption at rest: AES-256-GCM
- Encryption in transit: TLS 1.3
- Authentication: OAuth 2.0 + MFA
- Authorization: RBAC (Role-Based Access Control)
- Audit logging: HMAC-chained, immutable


--------------------------------------------------------------------------------
SLIDE 17 — APPENDIX : Shield Module Technical Details
--------------------------------------------------------------------------------

**IMSI Catcher Detection Algorithm**

```python
def detect_imsi_catcher(cell_data):
    risk_score = 0
    
    # LAC Analysis (Location Area Code)
    if cell_data.lac in [0, 1]:
        risk_score += 40  # Fake base station indicator
    
    # Signal Strength Analysis
    if cell_data.signal_strength > -40:  # dBm
        risk_score += 20  # Too strong for distance
    
    # Handover Rate Analysis
    if cell_data.handover_rate > 5:  # per minute
        risk_score += 10  # Abnormal switching
    
    # Encryption Downgrade Detection
    if cell_data.encryption in ['A5/0', 'A5/1']:
        risk_score += 30  # Weak/no encryption
    
    return risk_score
```

**Impossible Travel (Haversine Formula)**

```python
from math import radians, sin, cos, sqrt, atan2

def haversine_distance(lat1, lon1, lat2, lon2):
    R = 6371  # Earth radius in km
    
    dlat = radians(lat2 - lat1)
    dlon = radians(lon2 - lon1)
    
    a = sin(dlat/2)**2 + cos(radians(lat1)) * cos(radians(lat2)) * sin(dlon/2)**2
    c = 2 * atan2(sqrt(a), sqrt(1-a))
    
    return R * c  # Distance in km

def detect_impossible_travel(events):
    for i in range(1, len(events)):
        distance = haversine_distance(
            events[i-1].lat, events[i-1].lon,
            events[i].lat, events[i].lon
        )
        time_diff = (events[i].timestamp - events[i-1].timestamp).total_seconds() / 3600
        speed = distance / time_diff if time_diff > 0 else float('inf')
        
        if speed > 900:  # km/h (faster than commercial aircraft)
            return True, speed
    
    return False, 0
```

**GPS Spoofing Detection**

```python
def detect_gps_spoofing(gps_data):
    risk_score = 0
    
    # Round coordinate detection
    if gps_data.lat % 1 == 0 or gps_data.lon % 1 == 0:
        risk_score += 30  # Perfectly round = suspicious
    
    # Impossible accuracy
    if gps_data.accuracy < 5:  # meters
        risk_score += 20  # Too accurate for mobile GPS
    
    # Historical pattern deviation
    if gps_data.location_type != gps_data.historical_pattern:
        risk_score += 20  # Sudden change (urban → rural)
    
    return risk_score
```


--------------------------------------------------------------------------------
SLIDE 18 — APPENDIX : Sample Dashboard Mockups
--------------------------------------------------------------------------------

**Investigator Dashboard - Case List View**

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  SASSA FRAUD INVESTIGATION DASHBOARD                    [Logout] [Settings] │
├─────────────────────────────────────────────────────────────────────────────┤
│  📊 Overview    📋 Cases    🛡️ Shield Alerts    📈 Analytics    📄 Reports  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  HIGH-RISK CASES (Top 100)                              Filter: [All ▼]    │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                             │
│  │ # │ Beneficiary ID │ Risk Score │ Flags           │ Status    │ Action │
│  ├───┼────────────────┼────────────┼─────────────────┼───────────┼────────┤
│  │ 1 │ SA-8501-****   │ 95 🔴      │ IMSI, Travel    │ New       │ [View] │
│  │ 2 │ SA-7203-****   │ 88 🔴      │ GPS Spoof       │ New       │ [View] │
│  │ 3 │ SA-9012-****   │ 82 🟠      │ Cluster #47     │ Review    │ [View] │
│  │ 4 │ SA-6504-****   │ 78 🟠      │ Travel          │ New       │ [View] │
│  │ 5 │ SA-8811-****   │ 75 🟠      │ Behavior        │ Assigned  │ [View] │
│  │...│ ...            │ ...        │ ...             │ ...       │ ...    │
│                                                                             │
│  Showing 1-20 of 100 cases                        [◀ Prev] [Next ▶]        │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

**Network Graph - Syndicate Detection**

```
                    ┌─────────┐
                    │ Agent X │
                    │ (Hub)   │
                    └────┬────┘
           ┌─────────────┼─────────────┐
           │             │             │
      ┌────▼────┐   ┌────▼────┐   ┌────▼────┐
      │ ID #123 │   │ ID #456 │   │ ID #789 │
      │ (Stolen)│   │ (Stolen)│   │ (Stolen)│
      └────┬────┘   └────┬────┘   └────┬────┘
           │             │             │
    ┌──────┴──────┐     ...      ┌─────┴─────┐
    │             │              │           │
┌───▼───┐    ┌───▼───┐      ┌───▼───┐  ┌───▼───┐
│Payout1│    │Payout2│      │Payout5│  │Payout6│
│ R2,000│    │ R2,000│      │ R2,000│  │ R2,000│
└───────┘    └───────┘      └───────┘  └───────┘

Legend: 🔴 High Risk  🟠 Medium Risk  🟢 Low Risk
Total Fraud Value: R156,000 (78 payouts)
```


--------------------------------------------------------------------------------
SLIDE 19 — APPENDIX : Data Requirements
--------------------------------------------------------------------------------

**Minimum Data Requirements (6 Months Historical)**

| Data Category | Fields Required | Format | Volume Estimate |
|---------------|-----------------|--------|-----------------|
| **Beneficiary Profile** | ID (hashed), province, grant type, registration date | CSV/JSON | 18M records |
| **Authentication Logs** | Timestamp, IP, device fingerprint, GPS coords, success/fail | CSV/JSON | 500M+ events |
| **Payment Transactions** | Beneficiary ID, amount, date, payment point, method | CSV/JSON | 100M+ records |
| **Cell Tower Data** | Timestamp, LAC, CID, signal strength, handover events | CSV/JSON | Optional |

**Data Schema Example**

```json
{
  "beneficiary_auth_event": {
    "event_id": "uuid",
    "beneficiary_id_hash": "sha256_hash",
    "timestamp": "2025-01-15T09:30:00Z",
    "ip_address": "102.x.x.x",
    "device_fingerprint": "hash",
    "gps_latitude": -26.2041,
    "gps_longitude": 28.0473,
    "gps_accuracy_meters": 15,
    "auth_result": "success",
    "cell_tower": {
      "lac": 12345,
      "cid": 67890,
      "signal_dbm": -75,
      "network_type": "4G"
    }
  }
}
```

**Data Transfer Options**
1. **Secure FTP** : Encrypted file transfer (daily batch)
2. **API Integration** : REST API pull (if available)
3. **Database Dump** : PostgreSQL/Oracle export (one-time historical)
4. **Air-Gapped Transfer** : Physical media (highest security)


--------------------------------------------------------------------------------
SLIDE 20 — APPENDIX : Legal & Compliance
--------------------------------------------------------------------------------

**POPIA Compliance (Protection of Personal Information Act)**

| Requirement | HCS-U7 Implementation |
|-------------|----------------------|
| **Lawful Processing** | Fraud prevention = legitimate interest |
| **Purpose Limitation** | Data used only for fraud detection |
| **Minimization** | Only necessary fields ingested |
| **Accuracy** | Validated against source systems |
| **Storage Limitation** | Retention policy (12 months default) |
| **Security** | Encryption, access controls, audit trail |
| **Data Subject Rights** | Pseudonymization, no direct PII access |

**ISO 27001 Alignment**

| Control Domain | Implementation |
|----------------|----------------|
| **A.5 Information Security Policies** | Documented security policies |
| **A.6 Organization of Information Security** | Defined roles and responsibilities |
| **A.8 Asset Management** | Data classification and handling |
| **A.9 Access Control** | RBAC, MFA, least privilege |
| **A.10 Cryptography** | AES-256, TLS 1.3, post-quantum ready |
| **A.12 Operations Security** | Logging, monitoring, change management |
| **A.13 Communications Security** | Network segmentation, encryption |
| **A.18 Compliance** | POPIA, GDPR equivalence |

**Audit Trail Requirements**

All data access and processing events logged with:
- Timestamp (UTC)
- User identity (authenticated)
- Action performed (read, analyze, export)
- Data scope (beneficiary IDs accessed)
- Result (success/failure)
- HMAC chain (tamper-evident)

**Data Retention Policy**
- POC data: Deleted 30 days after POC completion (unless production approved)
- Production data: 12 months rolling (configurable)
- Audit logs: 7 years (compliance requirement)


================================================================================
END OF PITCH DECK
================================================================================

**Document Information**
- Version: 1.0
- Date: December 2025
- Author: IA Solution (HCS-U7)
- Classification: Confidential - Cyber1 Partnership

**Conversion to PDF**
```bash
pandoc POC-SASSA-Pitch-Deck.md -o POC-SASSA-Pitch-Deck.pdf \
  --pdf-engine=xelatex \
  -V geometry:margin=1in \
  -V fontsize=11pt
```
