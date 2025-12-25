# FAQ TECHNIQUE - HCS-U7 POC SASSA

Questions anticipées de l'équipe Cyber1 et réponses détaillées.

---

## ARCHITECTURE & DEPLOYMENT

### Q1: Comment HCS-U7 s'intègre dans notre infrastructure Cyber1 ?

HCS-U7 se déploie comme un conteneur Docker dans votre environnement sécurisé. API REST standard, ingestion de données via CSV/JSON/SQL, output vers votre SIEM/dashboards existants.

**Spécifications techniques :**
- **Déploiement** : Docker Compose ou Kubernetes
- **APIs** : OpenAPI 3.0 spec disponible
- **Latency** : <50ms p95 (risk scoring)
- **Scalability** : 1000+ RPS capacity

```yaml
# Exemple docker-compose.yml
services:
  hcs-u7:
    image: ia-solution/hcs-u7:latest
    ports:
      - "8080:8080"
    environment:
      - MODE=offline_analysis
      - SHIELD_ENABLED=true
```

---

### Q2: Quelles données SASSA sont nécessaires ?

Minimum 6 mois de données historiques :

| Catégorie | Champs requis | Format |
|-----------|---------------|--------|
| **Beneficiary Profile** | ID (hashed), province, grant type, registration date | CSV/JSON |
| **Authentication Logs** | Timestamp, IP, device, GPS coords, success/fail | CSV/JSON |
| **Payment Transactions** | Beneficiary ID, amount, date, payment point | CSV/JSON |
| **Cell Tower Data** | LAC, CID, signal strength, handover events | CSV/JSON (optionnel) |

---

### Q3: Peut-on tester sans données production ?

**Oui**, nous fournissons un dataset synthétique SASSA-like pour demo/testing :
- 100,000 beneficiaries simulés
- 6 mois d'événements d'authentification
- Cas de fraude injectés (IMSI, GPS spoofing, impossible travel)
- Prêt à l'emploi pour validation technique

---

## SÉCURITÉ & COMPLIANCE

### Q4: Comment garantir la protection des données SASSA (POPIA) ?

**Mesures de protection :**

| Contrôle | Implémentation |
|----------|----------------|
| **Pseudonymization** | Hashing automatique des PII (SHA-256) |
| **Encryption at rest** | AES-256-GCM |
| **Encryption in transit** | TLS 1.3 |
| **Access controls** | RBAC + MFA obligatoire |
| **Audit trail** | Tous les accès loggés (HMAC-chained) |
| **Air-gapped** | Pas d'accès internet (environnement isolé) |
| **ISO 27001** | Aligné sur les contrôles A.5 à A.18 |

---

### Q5: Audit trail pour compliance ?

Tous les événements loggés de manière immutable :

```json
{
  "event_id": "uuid",
  "timestamp": "2025-01-15T09:30:00Z",
  "user_id": "analyst_001",
  "action": "VIEW_CASE",
  "resource": "beneficiary_hash_abc123",
  "result": "SUCCESS",
  "hmac_chain": "sha256_previous_event"
}
```

**Formats d'export supportés :**
- Syslog (RFC 5424)
- CEF (Common Event Format)
- LEEF (Log Event Extended Format)
- JSON (custom)

---

## SHIELD MODULE

### Q6: Comment fonctionne la détection IMSI catcher ?

Analyse multi-signaux en temps réel :

| Signal | Seuil | Points de risque |
|--------|-------|------------------|
| LAC (Location Area Code) | = 0 ou 1 | +40 (fake base station) |
| Signal strength | > -40 dBm | +20 (trop fort pour la distance) |
| Handover rate | > 5/min | +10 (switching anormal) |
| Encryption | A5/0 ou A5/1 | +30 (downgrade = MITM) |

**Scoring** : Somme pondérée → seuil ≥70 = **DANGEROUS**

```python
def detect_imsi_catcher(cell_data):
    risk = 0
    if cell_data.lac in [0, 1]: risk += 40
    if cell_data.signal_dbm > -40: risk += 20
    if cell_data.handover_rate > 5: risk += 10
    if cell_data.encryption in ['A5/0', 'A5/1']: risk += 30
    return risk
```

---

### Q7: Faux positifs Shield Module ?

**Calibration nécessaire** (paramètres ajustables) :

1. **Baseline** : 30 jours de données "normales" pour établir les seuils
2. **Tuning** : Feedback loop avec investigators (true/false positive tagging)
3. **Target POC** : <10% false positive rate

**Facteurs de réduction des faux positifs :**
- Corrélation multi-signaux (pas un seul indicateur)
- Contexte géographique (zones rurales vs urbaines)
- Historique du beneficiary (pattern habituel)

---

### Q8: Shield fonctionne sans cell tower data ?

| Données disponibles | Fonctionnalités Shield |
|---------------------|------------------------|
| **Avec cell tower data** | IMSI catcher detection complète ✅ |
| **Sans cell tower data** | Impossible travel + GPS spoofing uniquement ⚠️ |
| **Fallback** | IP-based geolocation (moins précis) |

**Recommandation** : Demander les cell tower data à SASSA si disponibles (via opérateurs mobiles ou logs d'authentification).

---

## PERFORMANCE & SCALABILITÉ

### Q9: Latency pour 18M beneficiaries ?

**Batch processing (offline POC)** :

| Métrique | Performance |
|----------|-------------|
| Ingestion | 1M records/hour |
| Full dataset (18M) | <24h processing |
| Risk scoring (real-time) | <50ms p95 |
| Report generation | <5 min |

**Architecture scalable** : Horizontal scaling via Kubernetes (ajout de pods selon la charge).

---

### Q10: Infrastructure requirements ?

**POC (minimal)** :

| Ressource | Spécification |
|-----------|---------------|
| CPU | 16 cores |
| RAM | 64 GB |
| Storage | 500 GB SSD |
| Network | 1 Gbps (internal) |

**Production (recommandé)** :

| Ressource | Spécification |
|-----------|---------------|
| CPU | 32+ cores (auto-scaling) |
| RAM | 128 GB |
| Storage | 2 TB SSD (+ backup) |
| Network | 10 Gbps |

---

## COMMERCIALS & PARTNERSHIP

### Q11: Revenue share model avec Cyber1 ?

**Proposition de base** (négociable) :

| Phase | Cyber1 | HCS-U7 |
|-------|--------|--------|
| **POC** | 60% | 40% |
| **Production** | 70% | 30% |
| **Support** | Tier L1/L2 (Cyber1) | Tier L3 (HCS-U7) |

**Modèles alternatifs possibles :**
- Fixed fee + success bonus
- Per-beneficiary pricing
- Annual license + maintenance

---

### Q12: Exclusivité Cyber1 en Afrique du Sud ?

**Proposition :**

| Secteur | Exclusivité |
|---------|-------------|
| **Gouvernement SA** (SASSA, Home Affairs, etc.) | ✅ 2 ans (renouvelable) |
| **Banking / Fintech** | ❌ Non-exclusif |
| **Autres pays Afrique** | À négocier |

**Conditions d'exclusivité :**
- Minimum 1 deal signé par an
- Co-marketing et références
- Reporting trimestriel

---

## SUPPORT & TRAINING

### Q13: Training SASSA investigators ?

**Inclus dans le POC :**

| Formation | Durée | Contenu |
|-----------|-------|---------|
| **Dashboard usage** | 1 jour | Navigation, filtres, export |
| **Case review workflow** | 1 jour | Triage, investigation, décision |
| **Documentation** | - | User manuals, video tutorials |
| **Support ongoing** | 3 mois | Email, calls, on-site si nécessaire |

---

### Q14: Handover to Cyber1 team ?

**Knowledge transfer complet :**

1. **Documentation technique**
   - Architecture diagrams
   - API specifications
   - Deployment runbooks

2. **Operational runbooks**
   - Monitoring & alerting
   - Troubleshooting guides
   - Incident response

3. **Training Cyber1 engineers**
   - 2 jours hands-on
   - Certification interne

4. **Support post-POC**
   - 3 mois support inclus
   - SLA L3 (4h response time)

---

## NEXT STEPS

### Q15: Timeline pour démarrer POC ?

**Si décision cette semaine :**

| Semaine | Activité |
|---------|----------|
| Week 1-2 | Contract + MOU signature |
| Week 3 | Environment setup (Cyber1 infra) |
| Week 4 | POC kickoff (data ingestion) |
| Week 5-8 | Analysis & detection |
| Week 9-12 | Validation & reporting |

**Total : 90 jours du kickoff au rapport final**

---

### Q16: Qui contacter pour questions techniques ?

**Contact principal :**

**Benjamin BARRÈRE** (CTO)
- 📧 Email: benjamin@ia-solution.fr
- 📞 Disponible pour calls (FR/EN)
- 🕐 Timezone: CET (Paris)
- 💬 Response time: <24h

**Support technique :**
- Documentation: https://docs.hcs-u7.io (à venir)
- API sandbox: Disponible sur demande

---

## QUESTIONS ADDITIONNELLES

### Q17: Quelle est la maturité du produit HCS-U7 ?

| Aspect | Status |
|--------|--------|
| **Core platform** | Production-ready (v2.x) |
| **Shield Module** | Production-ready (v1.x) |
| **Patents** | 3 brevets INPI (FR2514274, FR2514546, FR2515560) |
| **Clients existants** | POCs en cours (EU) |
| **Certifications** | ISO 27001 alignment (certification en cours) |

---

### Q18: Comment gérer les mises à jour pendant le POC ?

- **Versioning** : Semantic versioning (major.minor.patch)
- **Updates** : Coordonnées avec Cyber1 (pas de mise à jour surprise)
- **Rollback** : Procédure documentée (<1h)
- **Changelog** : Fourni pour chaque release

---

### Q19: Quid de la propriété intellectuelle des modèles ML ?

| Composant | Propriété |
|-----------|-----------|
| **HCS-U7 core algorithms** | IA Solution (licensed) |
| **SASSA-specific models** | Co-ownership (négociable) |
| **Training data** | SASSA (never leaves their control) |
| **Insights & reports** | SASSA (full ownership) |

---

### Q20: Support multi-langue ?

| Langue | Dashboard | Documentation | Support |
|--------|-----------|---------------|---------|
| **English** | ✅ | ✅ | ✅ |
| **French** | ✅ | ✅ | ✅ |
| **Afrikaans** | ⚠️ Roadmap | ❌ | ❌ |
| **Zulu** | ⚠️ Roadmap | ❌ | ❌ |

**Note** : Localisation SA possible en Phase 2 (production).

---

*Document confidentiel - Cyber1 Partnership | Décembre 2025*
