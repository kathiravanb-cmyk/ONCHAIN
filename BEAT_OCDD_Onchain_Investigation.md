# Audiera (BEAT) OCDD On-chain Investigation — Preliminary Report

| Date | Token Name | Token Ticker | Listing Status | Token Folder |
|---|---|---|---|---|
| 12/06/2026 | Audiera | $BEAT | *TBC by CTL* | *TBC* |

> **Drafting note:** This is a preliminary on-chain review produced with OKX Onchain OS market/holder/cluster data and public OSINT. The Bubblemaps and Ryker_Crypto X threads cited as triggers could not be retrieved directly in this environment (network-restricted); their content is reflected via public media coverage and should be attached verbatim before escalation. Chainalysis Reactor tracing and FIU/SI checks remain to be performed.

---

## Summary

The CTL OCDD preliminary on-chain investigation into Audiera ($BEAT) was initiated following an abnormal price event in which BEAT reached a fully diluted valuation of approximately USD 8 billion overnight (price ~USD 8.0–9.3, ~525–630% in one week to 11 June 2026), and public commentary by Bubblemaps and Ryker_Crypto alleging insider supply control, with explicit comparison to the LAB case previously investigated by this team.

Key findings:

- **Extreme supply concentration.** The top 10 on-chain holders control **84.07%** of the 1,000,000,000 BEAT supply; the top 100 control **98.05%**. This independently corroborates the public allegation that "at least 84% of supply is controlled by the team."
- **TGE-era dormant whale block.** Seven of the top ten wallets (≈73% of total supply) are EOAs holding since **26–27 September 2025** (TGE window) with zero BNB for gas and no outflows — structurally identical to the LAB dormant holding cluster (689.6m LAB parked since 18 Oct 2025).
- **Coordinated fresh-wallet distribution layer.** The mid-tier of the top-100 holder set shows three distinct batch signatures: (i) ~15 wallets with byte-identical BNB dust balances of `0.000071833` and round allocations; (ii) 7 wallets holding an identical `999,999.114` BEAT; (iii) ~50 wallets each holding 0.5m–1.2m BEAT, each gas-seeded by a **unique, single-use funding wallet** — a deliberate funding-fragmentation technique that defeats clustering heuristics (OKX clustering resolves all 100 top holders into single-member clusters; same-fund-source ratio only 6.7% despite 73% same-creation-time).
- **CEX-seeded holders.** Top-100 holders were gas-funded/seeded by **Binance** (`0xe2fc31…3ae1`), **Gate.io** (`0x0d0707…92fe`) and **KuCoin Hot Wallet 2** (`0x53f78a…3fa23`). This mirrors the LAB post-Bitget fresh-wallet distribution (where Ju.com seeded the recipient cluster) and the RIVER BitGet withdrawal pattern.
- **Unlabeled project-linked distribution wallet.** `0x2e2b29d3…4a04e` seeded at least three top-21 holders controlling ~5.15% of supply (~USD 410m at review-date prices) and is now nearly empty — consistent with a spent distribution/ops wallet. No public attribution exists.
- **Thin effective float vs derivatives-led price action.** DEX liquidity is only ~USD 3.7m against a ~USD 2.31bn market cap and ~USD 8bn FDV; public reporting records derivatives volume +191% to USD 1.9bn with OI +79% during the surge, and USD 8.2m short liquidations on 11 June. The price formation is perp-led against a float that is materially thinner than the reported ~288m circulating supply implies.
- **Cross-reference vs LAB and RIVER: no direct wallet overlap.** None of the named LAB wallets (Msig cluster, RouterWallet relays, fresh chains, Bitget deposit `0x1AB497…8F23`) and none of the named RIVER wallets (Redici Capital EOA `0x365b68…9A54`, deployer, team EOA) appear in the BEAT top-100 holder set, its funding sources, or its cluster membership. The LAB Bitget hot wallet holds **no BEAT** (it does still hold ~USD 293k LAB and, notably, SKYAI — a token in the same publicly-alleged manipulation family). **The nexus is therefore a shared modus operandi and shared exchange rails, not shared wallets** (see §5).

The pattern-level match to the LAB playbook (and the RAVE/SKYAI/PIPPIN family flagged publicly by Bubblemaps) is strong; the wallet-level link is unproven on current evidence. The findings warrant escalation for full Reactor tracing and, if OKX exposure exists, Market Surveillance review.

---

## Recommendation

- Treat as **material market-integrity risk pending full investigation** (preliminary L1 finding: elevated).
- Commission Chainalysis Reactor tracing of: (i) the BEAT deployer → top-10 vault distribution at TGE; (ii) the funding chain *above* `0x2e2b29d3…4a04e`; (iii) deposit paths from the batch-wallet series into CEX deposit addresses, to establish whether the operator entity matches the LAB multisig owner set (Sadkov-linked) or the Redici Capital entity from the RIVER case.
- Request SI/FIU check on any OKX accounts linked to `0x2e2b29d3…4a04e` and the KuCoin/Gate/Binance-seeded top holders.
- Notify Market Surveillance re: BEAT perp activity on OKX (if listed) given perp-led price formation against thin float.
- Attach the Bubblemaps and Ryker_Crypto threads verbatim and reconcile their named wallets against the Wallet Address Log below before CTL Committee review.

---

## Background

On 11–12 June 2026, BEAT (Audiera — a BNB Chain Web3 music/AI "SocialFi" platform) rose from ~USD 1.16 (1 June) to an all-time high of ~USD 9.34 (11 June), briefly implying an FDV above USD 8bn on a 1,000,000,000 max supply, before correcting ~9% on 12 June. Public commentary (Bubblemaps; Ryker_Crypto; analyst Luke Cannon) alleged that the rally was insider-driven, that ≥84% of supply is team-controlled, and that BEAT is "likely the next RAVE/LAB."

Because the Bubblemaps post references LAB — the subject of this team's 08/05/2026 OCDD investigation (project-linked wallets routed ~226m LAB ≈ 98% of circulating supply to a single Bitget deposit address ahead of a >1,000% price move; founder Vladimir Sadkov; Garantex exposure) — this review additionally cross-references the BEAT holder graph against the full LAB and RIVER (28/01/2026, Redici Capital) address sets to identify any common addresses or common operators.

The relevant BSC token contract is: `0xCF3232b85B43BCa90E51D38cc06CC8bb8c8A3E36` (Beat Token, 18 decimals; 142,772 holders at review date).

---

## Wallet Address Log

| Label | Address | Role / Finding |
|---|---|---|
| BEAT-TokenContract | `0xCF3232b85B43BCa90E51D38cc06CC8bb8c8A3E36` | BEAT (Audiera) BEP-20 contract, BSC |
| BEAT-Vault-1 | `0x75552f8f6785946172527cbfef84a08086a4ede7` | **Top holder: 341,666,669 BEAT (34.17%)**. EOA, 0 BNB, holds only BEAT + airdrop dust, no outflow since 27 Sep 2025 (TGE). Assessed: project vault |
| BEAT-Vault-2 | `0x1830834fe3742b7e0988968dd50f321250157561` | 119,583,331 BEAT (11.96%), EOA, 0 BNB, dormant since 27 Sep 2025. Note: Vault-1 + Vault-2 = 461,250,000 (complementary `…669`/`…331` split of a 461.25m allocation) |
| BEAT-Vault-3 | `0x05b7721d66e83f8fb236d2ace995f710fd59e718` | 80,000,000 BEAT (8.00%), dormant since 27 Sep 2025 |
| BEAT-Vault-4 | `0xc6ff829cde48848b02c19b3af54b1de73c40a669` | 70,000,000 BEAT (7.00%), holding since 1 Dec 2025 |
| BEAT-Vault-5 | `0x34d5d4c15ff9a1417411787c1eb26f4c3c35149f` | 68,700,000 BEAT (6.87%), dormant since 27 Sep 2025 |
| BEAT-Vault-6 | `0x0793b14b0beb04caf55c5fd48e0e3e7358bf6bb2` | 60,000,000 BEAT (6.00%), dormant since 27 Sep 2025 |
| BEAT-Funder-1 | `0x2e2b29d314db954ee9d8c5ced89fa5153a64a04e` | **Unlabeled distribution wallet.** Gas/seed source for BEAT-Recv-1/2/3 (~51.5m BEAT ≈ 5.15% of supply across "independent" top-21 holders). Now nearly empty (0.38 BNB). No public attribution. Assessed: likely operator-controlled |
| BEAT-Recv-1 | `0x6f8a2e8fe3dc9867ab3ff3351fc5b2ab7fe93a7e` | 40,360,603 BEAT (4.04%), seeded by BEAT-Funder-1, holding since 1 Dec 2025 |
| BEAT-Recv-2 | `0x88ca5b88041a2bccfb7e614963196d551380c529` | 9,501,419 BEAT (0.95%), seeded by BEAT-Funder-1 |
| BEAT-Recv-3 | `0xadcecefcc0ac3776b0af1385bfff8f3162ded650` | 1,650,000 BEAT (0.17%), seeded by BEAT-Funder-1 |
| Binance hot wallet | `0xe2fc31f816a9b94326492132018c3aecc4a93ae1` | Funded holder `0x365d02…95d7` (9.7m BEAT) |
| Gate.io hot wallet | `0x0d0707963952f2fba59dd06f2b425ace40b492fe` | Funded holders `0xc882b1…f071` (12.8m BEAT, 32,654 BNB — exchange-flagged) and `0x384c74…95a0` (7.9m BEAT) |
| KuCoin Hot Wallet 2 | `0x53f78a071d04224b8e254e243fffc6d9f2f3fa23` | Funded holders `0x8dac80…ae18` (1.75m), `0x17a303…c4a8` (0.52m, 6,094 BNB), `0xb8e6d3…6b23` (0.51m, 9,926 BNB) |
| Batch-Series-A (~15 wallets) | e.g. `0x8bede3…c003`, `0x8b3f95…f4cd`, `0x85ee81…d9fc`, `0x4a19c7…4974`, `0x458597…961d`, `0x21bc2d…af15`, `0x72423e…d166`, `0x62f09c…6ceb`, `0x5d0aa7…2c26`, `0x3d3531…e791`, `0x6dfd51…2088`, `0x4c00c9…7b50`, `0x80008c…596d`, `0x19bee3…6a40`, `0x188d6a…5933`, `0x1616cb…ce78` | Byte-identical BNB dust `0.000071833`; round allocations (1,459,980 ×5; 1,100,000 ×3; 574,975 ×4; 950,100; 900,000; 802,000; 800,100; 800,000; 750,000). Single-operator batch creation |
| Batch-Series-B (7 wallets) | `0xf71a89…6cdb`, `0xf19f33…57f7`, `0xe85756…a211`, `0x86ef75…2dd3`, `0x33206c…eb8d`, `0x20922f…5b4f`, `0x150268…8eb6` | Identical `999,999.114` BEAT each — common distribution source |
| Batch-Series-C (~50 wallets) | cursors 33–99 of top-100 holder list (full list retained in working data) | 0.5m–1.2m BEAT each; every wallet seeded by a unique single-use funder with 0.008–0.034 BNB. Funding-fragmentation / clustering-evasion signature |
| testBEAT contract | `0xb9fbd1f37146ea92a3c1a5309902644427c0aa12` | "testBEAT" token on BSC (25,173 holders, ~$19.6m mcap) — possible same-operator rehearsal/farm token; unverified, flagged for follow-up |

### Cross-referenced (negative) — LAB / RIVER named wallets checked against BEAT

| Checked address | Source case | Result vs BEAT |
|---|---|---|
| `0x1AB4973a48dc892Cd9971ECE8e01DcC7688f8F23` (LAB-BitgetDeposit / Bitget hot wallet, 2,143 token positions) | LAB | **No BEAT held.** Still holds ~29.6k LAB (~USD 293k) and SKYAI (same alleged token family) |
| LAB-Msig-2/3/4/5, LAB-Relay-A/B/C/D, LAB-FreshChain-1/2 | LAB | Not present in BEAT top-100 holders, funders, or clusters |
| `0x365b689f33f6Fe3E4aEf5057061A006A09099A54` (Redici Capital EOA) | RIVER | **No BEAT** (BSC balance: 0.043 BNB + scam dust only) |
| RIVER deployer / Addr3 / Addr4 / Addr5 / `0xfE469C…BA57A` | RIVER | Not present in BEAT top-100 holders, funders, or clusters |

---

## Details of Investigation

### 1. Public Market Context

- Price at review: ~USD 8.02 (−9.4% 24h), market cap ~USD 2.31bn, **FDV ~USD 8bn** on 1,000,000,000 max supply; reported circulating supply ~288–290m (~29%).
- Rally: ~USD 1.16 (1 Jun) → ATH ~USD 9.34 (11 Jun); +525% w/w, +630% from 1 June; +750% over 30 days.
- **DEX liquidity only ~USD 3.67m** — the on-chain tradeable float is a rounding error against FDV; price discovery is occurring on CEX spot/perp venues.
- Derivatives: volume +191% to USD 1.9bn, OI +79% (public reporting); USD 8.2m short liquidations on 11 June; Bitget operates a BEATUSDT perpetual and adjusted leverage/margin parameters for it.
- OKX advanced-info flags: `riskControlLevel 1`, tags `dexBoost`, `smartMoneyBuy`, `dsPaid`; dev wallet holding negligible. Note these flags assess contract-level risk, not distribution risk — the concentration findings below are the material issue.

### 2. Public Allegations

- **Bubblemaps** (X, 11–12 Jun 2026; thread not directly retrievable in this environment — attach verbatim): alleges insider supply control, drawing explicit comparison to **LAB**; Bubblemaps' published pattern family for this playbook covers RAVE, SKYAI, PIPPIN and LAB — large synchronized CEX inflows/outflows, abnormal on-chain movement preceding price moves, and supply fragmented into coordinated fresh wallets.
- **Ryker_Crypto** (X, 11–12 Jun 2026; not directly retrievable — attach verbatim).
- **Luke Cannon / other analysts** (public coverage): "be careful with BEAT as it's likely the next RAVE/LAB"; "at least 84% of supply is controlled by the team"; distributed wallets "had not moved and could create selling pressure," though without published proof of team ownership.

These are treated as public concerns, not proof. The purpose of this review is to assess whether available on-chain evidence supports, refines, or mitigates them.

### 3. On-chain Findings (OKX Onchain OS)

#### 3.1 Supply concentration — allegation corroborated
Top 10 holders: **84.07%** (vs. the public "84%" claim — independently confirmed). Top 100: **98.05%**. The #1 wallet alone holds 34.17%. Burned: only ~12.35m BEAT (1.24%) at `0x…dead`.

#### 3.2 TGE-era dormant vault block (≈73% of supply)
Vaults 1–6 plus two further top-10 wallets are plain EOAs (not contracts, not exchange-labeled) holding round-number allocations since 26–27 September 2025, each with **zero BNB** (cannot even pay gas) and zero recorded outflow. The `341,666,669 / 119,583,331 / 20,416,669` figures are complementary fragments of round allocations, indicating a single allocation event split across wallets at TGE. This replicates the LAB structure (five dormant holding multisigs, 68.96% of supply, no outflow since Oct 2025) in EOA form.

#### 3.3 Coordinated fresh-wallet distribution layer
Three batch signatures in the top-100 set (see Wallet Address Log): identical-dust Series A, identical-amount Series B, and uniquely-funded Series C. Cluster telemetry confirms the design: **73% of top holders share a creation-time window** while only **6.7% share a funding source**, and OKX clustering resolves all 100 top holders into single-member clusters — i.e., the operator deliberately randomized funding paths to defeat cluster analysis. This is the same source-distancing escalation documented in LAB (single-hop relays → parallel ~10-hop fresh-wallet chains) and RIVER (2,418 BitGet-withdrawn wallets gas-funded en masse).

#### 3.4 CEX rails and the unlabeled funder
Mid-tier top-100 holders were seeded from Binance, Gate.io and KuCoin hot wallets (LAB used Bitget + Ju.com; RIVER used BitGet). The single most significant unattributed node is **BEAT-Funder-1 (`0x2e2b29d3…4a04e`)**: it seeded three nominally independent top-21 holders totalling ~51.5m BEAT (~5.15% of supply, ~USD 410m), then went dormant nearly empty. Its own funding source must be established via Reactor — if it traces to the BEAT deployer/treasury, project-linked control of the "distributed" mid-tier is confirmed; if it traces to a CEX withdrawal, the exchange-side account holder is the key subject.

#### 3.5 Price/flow structure
As with LAB, a straightforward insider spot-dump is inconsistent with the observed price outcome (+630% with supply still parked). The structure — ≥84% supply control, ~USD 3.7m DEX float, CEX-listed perps, derivatives volume of USD 1.9bn — creates the same capacity identified in the LAB review: a party controlling the effective float can influence spot price formation on thin liquidity and let the move propagate to perp mark prices and liquidation cascades, without selling core supply. The 12 June −9% reversal and USD 8.2m short-liquidation event are consistent with that mechanic. On-chain analysis establishes **capacity and opportunity**, not exchange-side execution.

### 4. Cross-reference Against LAB and RIVER Address Sets

All full addresses from the LAB OCDD report (active multisigs, relays, fresh-chain heads, Bitget deposit) and the RIVER report (deployer, Redici Capital EOA, Addr3/4/5, linked EOA) were checked against (i) the BEAT top-100 holder list, (ii) every recorded holder funding source, and (iii) all 100 BEAT holder clusters. **Result: zero direct overlap.** Reverse checks (BSC balances of LAB-BitgetDeposit and Redici EOA) found no BEAT positions. Partial-only addresses in the LAB report (LAB-Msig-1 `0xA7D23…d559B`, LAB-RouterWallet `0xe0372…E21dd`, HoldingMsig A–E) could not be machine-checked — recommend re-running the comparison with full strings from Reactor.

### 5. Nexus Assessment

| Dimension | LAB (08/05/2026) | RIVER (28/01/2026) | BEAT (this review) |
|---|---|---|---|
| Chain | BSC | BSC | BSC |
| Supply control | ~91.6% project-linked | Large, via BitGet outflows (2,418 wallets) | 84.07% top-10 / 98.05% top-100 |
| Dormant vault block | 689.6m (68.96%) since Oct 2025 | — | ~730m (≈73%) since Sep 2025 (TGE) |
| Fresh-wallet staging | Parallel ~10-hop chains, escalating | 2,418 wallets, mass gas-funding | 3 batch series + unique-funder fragmentation |
| CEX rails | Bitget (deposit), Ju.com (seeding) | BitGet | Binance / Gate / KuCoin (seeding) |
| Price event | +1,000% then violent two-sided | $19 → $85 then correction | +630% w/w then −9% |
| Perp-led amplification | Yes (Binance/Gate/Ju.com perps, thin float) | Yes (BitGet) | Yes ($1.9bn perp vol, $8.2m short liqs, $3.7m DEX float) |
| Direct wallet overlap with the other cases | — | — | **None found** |

**Conclusion on nexus:** the common addresses the public threads imply do not materialize at wallet level on current evidence. What *is* common is (a) an identical operational playbook — TGE supply parked in dormant vaults, a fragmented fresh-wallet mid-tier staged through CEX rails, thin DEX float, perp-led price discovery — matching the Bubblemaps RAVE/SKYAI/PIPPIN/LAB family; and (b) shared exchange infrastructure as the staging layer (and the LAB Bitget hot wallet's residual SKYAI position is a family-level, not case-level, link). Operator identity overlap (LAB's Sadkov-linked multisig owners; RIVER's Redici Capital) can only be confirmed or excluded by tracing BEAT-Funder-1 and the TGE distribution in Reactor plus exchange-side data.

---

## Conclusion

BEAT presents **elevated market-integrity and free-float concentration risk** on the same structural pattern as LAB: near-total supply control (98% in 100 wallets; 84% in 10), a dormant TGE vault block, a deliberately fragmented fresh-wallet distribution layer staged via CEX hot-wallet rails, and a derivatives-led 630% weekly price move against ~USD 3.7m of on-chain liquidity. The public allegation of 84% team control is corroborated on-chain; the allegation of a direct link to the LAB/RIVER actors is **not yet evidenced at wallet level** and requires Reactor tracing of `0x2e2b29d3…4a04e`, the TGE distribution, and exchange-side account data. Escalation recommended as per the Recommendation section.

---

## References

- Bubblemaps — BEAT thread: https://x.com/bubblemaps/status/2065116941224964363 *(attach verbatim)*
- Ryker_Crypto — BEAT thread: https://x.com/Ryker_Crypto/status/2065069122518761676 *(attach verbatim)*
- Internal — LAB ($LAB) OCDD On-chain Investigation, 08/05/2026 (Lark: RGPedExsdo7lCpxFqUSlkRydgzb)
- Internal — River (RIVER) On-chain Investigation, 28/01/2026 (Lark: FgcrdLYZGoCyuux5YUvlgptxgfc)
- BscScan — BEAT token contract: https://bscscan.com/token/0xcf3232b85b43bca90e51d38cc06cc8bb8c8a3e36
- Cryip — "BEAT Token Rises Over 525% in a Week…": https://cryip.co/beat-token-surges-525-percent-audiera-revenue-token-burns/
- CryptoTicker — "What Is Audiera? BEAT Token Explodes 380%…" (84% team-control claim): https://cryptoticker.io/en/what-is-audiera-beat-token-surge-analysis/
- news.bitcoin.com — "Audiera's BEAT Surges 60% to $9.34…" ($8.2m short liquidations): https://news.bitcoin.com/audieras-beat-surges-60-to-9-34-as-ai-partnership-fuels-fresh-buying/
- CoinGecko — Audiera: https://www.coingecko.com/en/coins/audiera ; CoinMarketCap — Audiera: https://coinmarketcap.com/currencies/audiera/
- BscScan — KuCoin Hot Wallet 2: https://bscscan.com/address/0x53f78a071d04224b8e254e243fffc6d9f2f3fa23
- Bubblemaps pattern family (RAVE/SKYAI/PIPPIN/LAB) coverage: https://cryptorank.io/news/feed/fe030-bubblemaps-lab-token-price-manipulation-exchanges
- Data source: OKX Onchain OS (holder, cluster, balance, market endpoints), retrieved 12/06/2026
