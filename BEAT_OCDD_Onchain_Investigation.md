# BEAT (BEAT) OCDD On-chain Investigation

| **Date** | **Token Name** | **Token Ticker** | **Listing Status** | **Token Folder** |
|---|---|---|---|---|
| 12/06/2026 | Audiera | $BEAT | *TBC by CTL* | *TBC* |

> **Drafting note.** Preliminary L1 on-chain review built on OKX Onchain OS (holder, cluster, balance and market endpoints) and public OSINT. The triggering Bubblemaps and Ryker_Crypto X threads could not be retrieved in this environment and must be attached verbatim before escalation. Chainalysis Reactor tracing and FIU/SI account checks remain outstanding. Full addresses for manual investigation are provided in the Wallet Address Log and the Flagged Addresses table.

---

> # Summary
>
> The CTL OCDD Team's on-chain review of BEAT was initiated following an abnormal price event — BEAT reached an approximate USD 8 billion fully diluted valuation overnight (~525–630% in one week to 11 June 2026) — and public allegations by on-chain commentators Bubblemaps and Ryker_Crypto of insider supply control, drawing explicit comparison to LAB (subject of this team's 08/05/2026 OCDD investigation). This review assesses the on-chain evidence and cross-references the BEAT holder graph against the LAB and RIVER (Redici Capital) case address sets.
>
> Key findings are as follows:
>
> - **Supply is near-totally concentrated.** The top 10 on-chain holders control **84.07%** of the 1,000,000,000 BEAT supply and the top 100 control **98.05%**, with the single largest wallet holding **34.17%**. This independently corroborates the public allegation that "at least 84% of supply is team-controlled."
>
> - **A dormant TGE vault block holds ~73% of supply.** Seven of the top ten holders are plain EOAs holding round-number allocations since 26–27 September 2025 (TGE), each with zero BNB for gas and no recorded outflow. This mirrors the LAB structure (five dormant holding multisigs, 68.96% of supply, no outflow since 18 October 2025) in EOA form.
>
> - **A coordinated fresh-wallet layer was staged through CEX rails.** The mid-tier of the top 100 was distributed across batch-created wallets bearing byte-identical gas dust and round allocations, each seeded from a unique single-use funder — a funding-fragmentation technique that defeats clustering (OKX resolves all 100 top holders into single-member clusters; same-fund-source ratio 6.7% against 73% same-creation-time). Seeding traces to **Binance, Gate.io and KuCoin** hot wallets, echoing the LAB (Bitget/Ju.com) and RIVER (BitGet) staging patterns.
>
> - **Thin float, derivatives-led price action.** On-chain DEX liquidity is only ~USD 3.7m against ~USD 2.31bn market cap / ~USD 8bn FDV. Public reporting records derivatives volume +191% to USD 1.9bn, open interest +79%, and USD 8.2m short liquidations on 11 June — price formation is perp-led against a float materially thinner than the headline circulating supply.
>
> - **No direct wallet overlap with LAB or RIVER was found**, but this is not exculpatory (see below). One family-level link exists: the LAB Bitget deposit wallet still holds SKYAI, a token in the same Bubblemaps-flagged manipulation family (RAVE / SKYAI / PIPPIN / LAB).
>
> - **No OKX nexus observed.** No OKX hot wallet appears among the 51 distinct funding sources of the BEAT top-100 holders, and no tracked BEAT activity routed through OKX infrastructure. BEAT's on-chain staging is via non-OKX exchanges, in contrast to LAB (founder OKX account; OKX Ventures investment) and RIVER (Redici Capital funded by, and depositing to, OKX).
>
> The pattern-level match to the LAB playbook is strong; the wallet-level and operator-level links are unproven on current evidence. The CTL team recommends escalation for full Reactor tracing and manual address investigation.

## Recommendation

Compliance Token Listing Team's on-chain investigation concludes:

- **Preliminary material information identified** (L1: elevated market-integrity and free-float concentration risk), pending full investigation.

As such, the following steps are recommended:

- Commission Chainalysis Reactor tracing of (i) the deployer → top-10 vault distribution at TGE, (ii) the funding chain *above* the BEAT distribution wallet `0x2e2b29…a04e`, and (iii) deposit paths from the batch wallets into CEX deposit addresses, to test whether the operator entity matches the LAB multisig owner set or the RIVER / Redici entity.
- Manually investigate the **Flagged Addresses** (full strings below) against the Bubblemaps / Ryker_Crypto threads and any other OSINT, noting that these wallets may since have swapped or forwarded tokens and so may no longer hold BEAT, LAB or RIVER.
- Confirm the **OKX nexus** finding manually against the OKX hot-wallet addresses listed below (incoming and outgoing), as on-chain history beyond the holder snapshot was not available to this review.
- Notify Market Surveillance regarding BEAT perpetual activity (if listed on OKX), given perp-led price formation against a thin float.
- Escalate to the CTL Committee by way of the Periodic Review Report once Reactor and OSINT confirmation are complete.

---

## Background

On 11–12 June 2026, BEAT (Audiera — a BNB Chain Web3 music / AI "SocialFi" platform) rose from ~USD 1.16 (1 June) to an all-time high of ~USD 9.34 (11 June), briefly implying an FDV above USD 8bn on a 1,000,000,000 maximum supply, before correcting on 12 June. Public commentary (Bubblemaps; Ryker_Crypto; analyst Luke Cannon) alleged the rally was insider-driven, that ≥84% of supply is team-controlled, and that BEAT is "likely the next RAVE / LAB."

Because the Bubblemaps post references LAB, this review additionally cross-references the BEAT holder graph against the full LAB and RIVER address sets to identify common addresses or a common operator.

The relevant BSC token contract is: `0xCF3232b85B43BCa90E51D38cc06CC8bb8c8A3E36` (Beat Token, 18 decimals; 142,772 holders at review date).

---

## Wallet Address Log

Wallet labels are descriptive of each address's role in the identified structure and are used throughout the report in place of raw addresses.

| Label | Address (full) | Role / Finding |
|---|---|---|
| BEAT-Token | `0xCF3232b85B43BCa90E51D38cc06CC8bb8c8A3E36` | Audiera (BEAT) BEP-20 contract, BSC |
| BEAT-Vault-1 | `0x75552f8f6785946172527cbfef84a08086a4ede7` | **Top holder — 341,666,669 BEAT (34.17%).** EOA, 0 BNB, dormant since 27 Sep 2025 (TGE), no outflow. Publicly noted as the largest BEAT holder; honeypot indicator reported |
| BEAT-Vault-2 | `0x1830834fe3742b7e0988968dd50f321250157561` | 119,583,331 BEAT (11.96%). EOA, 0 BNB, dormant since 27 Sep 2025. Vault-1 + Vault-2 = 461,250,000 (complementary `…669`/`…331` split of one allocation) |
| BEAT-Vault-3 | `0x05b7721d66e83f8fb236d2ace995f710fd59e718` | 80,000,000 BEAT (8.00%), dormant since 27 Sep 2025 |
| BEAT-Vault-4 | `0xc6ff829cde48848b02c19b3af54b1de73c40a669` | 70,000,000 BEAT (7.00%), holding since 1 Dec 2025 |
| BEAT-Vault-5 | `0x34d5d4c15ff9a1417411787c1eb26f4c3c35149f` | 68,700,000 BEAT (6.87%), dormant since 27 Sep 2025 |
| BEAT-Vault-6 | `0x0793b14b0beb04caf55c5fd48e0e3e7358bf6bb2` | 60,000,000 BEAT (6.00%), dormant since 27 Sep 2025 |
| BEAT-Vault-7 | `0x56705ec68deb49f49daa6c6dee1eab4b1c9b2830` | 20,416,669 BEAT (2.04%) |
| BEAT-Vault-8 | `0xcaf2023e372169b89318888f3c6fecea7197c891` | 20,000,000 BEAT (2.00%), dormant since 26 Sep 2025 |
| BEAT-Vault-9 | `0x8c84616281bb4686600090a1aad58543a0e11be1` | 20,000,000 BEAT (2.00%), dormant since 27 Sep 2025 |
| BEAT-Funder-1 | `0x2e2b29d314db954ee9d8c5ced89fa5153a64a04e` | **Unattributed distribution wallet.** Gas/seed source for BEAT-Recv-1/2/3 (~51.5m BEAT ≈ 5.15% of supply, ~USD 410m, across nominally independent top-21 holders). Now near-empty (0.38 BNB). Priority Reactor target |
| BEAT-Recv-1 | `0x6f8a2e8fe3dc9867ab3ff3351fc5b2ab7fe93a7e` | 40,360,603 BEAT (4.04%), seeded by BEAT-Funder-1, holding since 1 Dec 2025 |
| BEAT-Recv-2 | `0x88ca5b88041a2bccfb7e614963196d551380c529` | 9,501,419 BEAT (0.95%), seeded by BEAT-Funder-1 |
| BEAT-Recv-3 | `0xadcecefcc0ac3776b0af1385bfff8f3162ded650` | 1,650,000 BEAT (0.17%), seeded by BEAT-Funder-1 |
| Binance-Funder | `0xe2fc31f816a9b94326492132018c3aecc4a93ae1` | Binance hot wallet; funded holder `0x365d02…95d7` (9.7m BEAT) |
| Gate-Funder | `0x0d0707963952f2fba59dd06f2b425ace40b492fe` | Gate.io hot wallet; funded `0xc882b1…f071` (12.8m BEAT) and `0x384c74…95a0` (7.9m BEAT) |
| KuCoin-Funder | `0x53f78a071d04224b8e254e243fffc6d9f2f3fa23` | KuCoin Hot Wallet 2; funded `0x8dac80…ae18`, `0x17a303…c4a8`, `0xb8e6d3…6b23` |
| testBEAT | `0xb9fbd1f37146ea92a3c1a5309902644427c0aa12` | "testBEAT" token on BSC (25,173 holders) — possible same-operator rehearsal/farm token; unverified, follow-up |

### Batch-wallet series (clustering-evasion signature)

| Series | Signature | Sample addresses (full) |
|---|---|---|
| Batch-A (~15 wallets) | Byte-identical BNB dust `0.000071833`; round allocations | `0x8bede344d7d0dbc023ab86c640fd8a895ac5c003`, `0x8b3f95d45b85782a21c151b9dcd4dc47df19f4cd`, `0x85ee81d3bb8fb8b127269f3b44c982df08e4d9fc`, `0x4a19c7e70d4297eafedb82906e59c6311e054974`, `0x458597cfaa5d92bec7b9b19b12dd75faaae5961d`, `0x21bc2d25b377b635246176e6ba5460a3d5ebaf15` |
| Batch-B (7 wallets) | Identical `999,999.114` BEAT each | `0xf71a8927ff46a3b5841069e41a302fbef1736cdb`, `0xf19f33f1af3c0450f4f9f9e5a95ade75457f57f7`, `0xe85756833633c7e42adeee47c63ca1dcacb0a211`, `0x86ef7509edd8b8ed4e27994b9910c17c52e82dd3`, `0x33206c831743818bb2df0144adc2e9b54595eb8d`, `0x20922f48b3bc3aedc8385c336f4defa771995b4f`, `0x150268b1b5133953b195c811f3cc5e008fcf8eb6` |
| Batch-C (~50 wallets) | 0.5m–1.2m BEAT each, every wallet seeded by a unique single-use funder | Full list retained in working data; representative funders: `0x9f11b05740837c1f7ddf2a78cf983bdb1e85b074`, `0xea09e6cb684fec805eadfce5678be347fe091347`, `0x1abfb4ab7c6c2ac9c2fff3d59e7a7d2259c44edd`, `0x361f25ad2d6ae57e166f5ac29bc79620490b71ec` |

---

## Details of Investigation

### 1. Public Market Context

BEAT had cross-venue access well before the price event, including a Bitget BEATUSDT perpetual (for which Bitget adjusted leverage and margin parameters). At review date, public data reported BEAT at ~USD 8.02, market cap ~USD 2.31bn, **FDV ~USD 8bn** on a 1,000,000,000 maximum supply, with reported circulating supply of ~288–290m (~29%). The rally ran from ~USD 1.16 (1 June) to an ATH of ~USD 9.34 (11 June): +525% week-on-week, +630% from 1 June, +750% over 30 days.

The material structural feature is liquidity: on-chain **DEX liquidity is only ~USD 3.67m** against the ~USD 8bn FDV, so the on-chain tradeable float is negligible and price discovery is occurring on CEX spot and perpetual venues. Public reporting records derivatives volume +191% to USD 1.9bn, open interest +79%, and USD 8.2m of short liquidations on 11 June.

### 2. Public Allegations

- **Bubblemaps** (X, 11–12 June 2026; thread not retrievable in this environment — attach verbatim) alleged insider supply control, drawing explicit comparison to **LAB**. Bubblemaps' published pattern family for this playbook covers RAVE, SKYAI, PIPPIN and LAB: large synchronized CEX inflows/outflows, abnormal on-chain movement preceding price moves, and supply fragmented into coordinated fresh wallets.
- **Ryker_Crypto** (X, 11–12 June 2026; not retrievable — attach verbatim).
- **Luke Cannon / other analysts** (public coverage): "be careful with BEAT as it's likely the next RAVE/LAB"; "at least 84% of supply is controlled by the team"; distributed wallets "had not moved and could create selling pressure," though without published proof of team ownership.

These are treated as public concerns, not proof. The purpose of this review is to assess whether available on-chain evidence supports, refines, or mitigates them.

### 3. On-chain Findings

**3.1 Supply concentration — allegation corroborated.** Top 10 holders: **84.07%**; top 100: **98.05%**; largest single wallet: **34.17%**. Only ~12.35m BEAT (1.24%) is burned. The public "84%" claim is independently confirmed.

**3.2 Dormant TGE vault block (~73% of supply).** Vaults 1–9 are plain EOAs (not contracts, not exchange-labelled) holding round-number allocations since 26–27 September 2025, each with zero BNB (cannot pay gas) and no recorded outflow. The `341,666,669 / 119,583,331 / 20,416,669` figures are complementary fragments of round allocations split across wallets at a single TGE event — the same retention structure as the LAB dormant holding multisigs.

**3.3 Coordinated fresh-wallet distribution layer.** Three batch signatures appear in the top 100 (see Batch series table): identical-dust Batch-A, identical-amount Batch-B, and uniquely-funded Batch-C. Cluster telemetry confirms the design: **73% of top holders share a creation-time window** while only **6.7% share a funding source**, and OKX clustering resolves all 100 top holders into single-member clusters — i.e., funding paths were deliberately randomised to defeat cluster analysis. This is the same source-distancing escalation documented in LAB (single-hop relays → parallel ~10-hop fresh-wallet chains) and RIVER (2,418 BitGet-withdrawn wallets, mass gas-funding).

**3.4 CEX rails and the unattributed funder.** Mid-tier holders were seeded from Binance, Gate.io and KuCoin hot wallets. The most significant unattributed node is **BEAT-Funder-1** (`0x2e2b29…a04e`): it seeded three nominally independent top-21 holders totalling ~51.5m BEAT (~5.15% of supply, ~USD 410m) and then went dormant near-empty. Its own funding source must be established in Reactor — if it traces to the BEAT deployer/treasury, project-linked control of the "distributed" mid-tier is confirmed; if it traces to a CEX withdrawal, the exchange-side account holder is the key subject.

**3.5 Price/flow structure.** As with LAB, a straightforward insider spot-dump is inconsistent with the price outcome (+630% with core supply still parked). The combination of ≥84% supply control, ~USD 3.7m DEX float, CEX-listed perpetuals and USD 1.9bn derivatives volume creates the same capacity identified in the LAB review: a party controlling the effective float can influence spot price formation on thin liquidity and let the move propagate to perpetual mark prices and liquidation cascades, without selling core supply. On-chain analysis establishes **capacity and opportunity**, not exchange-side execution.

### 4. Cross-reference Against LAB and RIVER, and OSINT Flagging

A snapshot, funding-source and cluster-membership cross-check found **no direct overlap** between the BEAT holder graph and the named LAB or RIVER addresses. **This is not exculpatory:** the flagged addresses may since have swapped or forwarded their tokens via a CEX/DEX and so need not currently hold BEAT, LAB or RIVER. The reliable test is therefore OSINT-based — whether any address has been publicly named in connection with these tokens — and manual Reactor tracing, both of which are recommended.

**OSINT status (current).** No external OSINT was found naming the specific BEAT wallets beyond holder-ranking sites identifying `0x75552f8f…ede7` as the largest holder (with a reported honeypot indicator). The Bubblemaps and Ryker_Crypto threads, which may cite specific wallets, were not retrievable here and must be checked manually against the Flagged Addresses.

#### Flagged Addresses for manual investigation (full strings)

| # | Address | Why flagged |
|---|---|---|
| 1 | `0x75552f8f6785946172527cbfef84a08086a4ede7` | Largest holder, 34.17%; publicly noted; honeypot indicator |
| 2 | `0x1830834fe3742b7e0988968dd50f321250157561` | 11.96%, dormant TGE vault |
| 3 | `0x05b7721d66e83f8fb236d2ace995f710fd59e718` | 8.00%, dormant TGE vault |
| 4 | `0xc6ff829cde48848b02c19b3af54b1de73c40a669` | 7.00% |
| 5 | `0x34d5d4c15ff9a1417411787c1eb26f4c3c35149f` | 6.87%, dormant TGE vault |
| 6 | `0x0793b14b0beb04caf55c5fd48e0e3e7358bf6bb2` | 6.00%, dormant TGE vault |
| 7 | `0x2e2b29d314db954ee9d8c5ced89fa5153a64a04e` | **Priority** — distribution/seed wallet, ~5.15% of supply, now drained |
| 8 | `0x6f8a2e8fe3dc9867ab3ff3351fc5b2ab7fe93a7e` | 4.04%, seeded by #7 |
| 9 | `0x88ca5b88041a2bccfb7e614963196d551380c529` | 0.95%, seeded by #7 |
| 10 | `0xadcecefcc0ac3776b0af1385bfff8f3162ded650` | 0.17%, seeded by #7 |
| 11 | `0xb9fbd1f37146ea92a3c1a5309902644427c0aa12` | "testBEAT" token contract — possible same-operator rehearsal |

#### LAB / RIVER addresses checked against BEAT (full strings)

| Address | Case | Label | Result vs BEAT |
|---|---|---|---|
| `0x1AB4973a48dc892Cd9971ECE8e01DcC7688f8F23` | LAB | Bitget deposit | No BEAT; still holds ~29.6k LAB + SKYAI (same family) |
| `0xEc99AB6394c3bB6E256c3DaB3147ba37C2DCd375` | LAB | Msig-2 | Not in BEAT holders/funders/clusters |
| `0x80b06923098c17C84e0564742D1A2d071D7Ee29a` | LAB | Msig-3 | Not present |
| `0x36FC85Ec486C254c9564d66de8c4210a1A20C291` | LAB | Msig-4 | Not present |
| `0xF760B38e09282B11884a26E4fFb701Eb0bD8de99` | LAB | Msig-5 | Not present |
| `0xe39F91A0dAFfc5547aDA79a09bE30b8556F7dfba` | LAB | Relay-A | Not present |
| `0x77156a0a621d2Ac7A075C0AC3172707C2e4aa191` | LAB | Relay-B | Not present |
| `0x00ad38779F49509E9B7ae3532a894dAF3629a279` | LAB | Relay-C | Not present |
| `0xD425C56F2EB64646fdE7f3c53d7584E60E62fC94` | LAB | Relay-D | Not present |
| `0xaa5e3b10e337ee1c1CCE16F6869b40BAC3B42e39` | LAB | FreshChain-1 | Not present |
| `0x7E1C38869888b89C6979095191a9f3669F76C93E` | LAB | FreshChain-2 | Not present |
| `0x1FA674198179C3B231c3f3Fd349139b29AFe555e` | RIVER | Deployer | Not present |
| `0x365b689f33f6Fe3E4aEf5057061A006A09099A54` | RIVER | Redici Capital EOA | No BEAT (BNB dust only) |
| `0x26bce225fC47Dbe32aF888c51EAdEe27ae91F93F` | RIVER | Addr3 | Not present |
| `0x00B02EFc64722eb5e83CE969E79c2C33E75Ac766` | RIVER | Addr4 | Not present |
| `0x828Ff5678bb85C7Ae0e683E7D7b931C9779443Dc` | RIVER | Team EOA | Not present |

*Partial-only LAB addresses (Msig-1 `0xA7D23…d559B`, RouterWallet `0xe0372…E21dd`, HoldingMsig A–E) could not be machine-checked — re-run with full strings from Reactor.*

### 5. OKX Nexus

No OKX nexus was identified at the level available to this review. Across the **51 distinct funding sources** of the BEAT top-100 holders, **no OKX hot wallet appears**; the CEX seeding sources are Binance, Gate.io and KuCoin only. The recent on-chain trade tracker returned no BEAT activity for the priority wallets. BEAT's on-chain staging therefore does not route through OKX, in contrast to LAB (founder OKX account; OKX Ventures investment) and RIVER (Redici Capital funded by, and depositing to, OKX).

This finding should be **confirmed manually** against the OKX hot-wallet addresses below (incoming and outgoing), as transaction history beyond the holder snapshot was not available here:

| OKX address (full) | Label |
|---|---|
| `0x7c0629bbbaf7d68ffaa393e3fedc9b633679fa5f` | OKX: Hot Wallet (BSC) |
| `0x559432e18b281731c054cd703d4b49872be4ed53` | OKX: Hot Wallet 5 |
| `0x6cc5f688a315f3dc28a7781717a9a798a59fda7b` | OKX (ETH) |
| `0x4b4e14a3773ee558b6597070797fd51eb48606e5` | OKX: Hot Wallet (ETH) |

### 6. Comparison to LAB and RIVER

| Dimension | LAB (08/05/2026) | RIVER (28/01/2026) | BEAT (this review) |
|---|---|---|---|
| Chain | BSC | BSC | BSC |
| Supply control | ~91.6% project-linked | Large, via BitGet outflows | 84.07% top-10 / 98.05% top-100 |
| Dormant vault block | 689.6m (68.96%) since Oct 2025 | — | ~730m (~73%) since Sep 2025 (TGE) |
| Fresh-wallet staging | Parallel ~10-hop chains, escalating | 2,418 wallets, mass gas-funding | Batch series + unique-funder fragmentation |
| CEX rails | Bitget; Ju.com seeding | BitGet | Binance / Gate / KuCoin seeding |
| Price event | +1,000%, violent two-sided | $19 → $85 then correction | +630% w/w then correction |
| Perp amplification | Yes (thin float) | Yes (BitGet) | Yes ($1.9bn perp vol; $8.2m short liqs; $3.7m DEX float) |
| Direct wallet overlap | — | — | **None found** (subject to OSINT/Reactor) |
| OKX nexus | Founder account; OKX Ventures | Redici funded by / deposits to OKX | **None observed** |

**Nexus assessment.** The common element across the three cases is an identical operational playbook — TGE supply parked in dormant vaults, a fragmented fresh-wallet mid-tier staged through CEX rails, thin DEX float and perp-led price discovery — matching the Bubblemaps RAVE/SKYAI/PIPPIN/LAB family, plus shared use of CEX infrastructure as the staging layer. Operator-identity overlap can only be confirmed or excluded by tracing BEAT-Funder-1 and the TGE distribution in Reactor and by exchange-side data.

---

## Conclusion

BEAT presents **elevated market-integrity and free-float concentration risk** on the same structural pattern as LAB: near-total supply control (98% in 100 wallets, 84% in 10), a dormant TGE vault block, a deliberately fragmented fresh-wallet distribution layer staged via CEX hot-wallet rails, and a derivatives-led 630% weekly price move against ~USD 3.7m of on-chain liquidity. The public allegation of 84% team control is corroborated on-chain. The alleged direct link to the LAB/RIVER actors is **not yet evidenced at wallet level**, but because flagged wallets may have swapped tokens away, this must be settled by OSINT review of the named threads and Reactor tracing of `0x2e2b29…a04e` and the TGE distribution. No OKX nexus was observed and should be manually confirmed. Escalation is recommended once these steps are complete.

---

## References

- Bubblemaps — BEAT thread: https://x.com/bubblemaps/status/2065116941224964363 *(attach verbatim)*
- Ryker_Crypto — BEAT thread: https://x.com/Ryker_Crypto/status/2065069122518761676 *(attach verbatim)*
- Internal — LAB ($LAB) OCDD On-chain Investigation, 08/05/2026 (Lark doc RGPedExsdo7lCpxFqUSlkRydgzb)
- Internal — River (RIVER) On-chain Investigation, 28/01/2026 (Lark doc FgcrdLYZGoCyuux5YUvlgptxgfc)
- BscScan — BEAT token contract: https://bscscan.com/token/0xcf3232b85b43bca90e51d38cc06cc8bb8c8a3e36
- BscScan — OKX: Hot Wallet (BSC): https://bscscan.com/address/0x7c0629bbbaf7d68ffaa393e3fedc9b633679fa5f
- BscScan — KuCoin Hot Wallet 2: https://bscscan.com/address/0x53f78a071d04224b8e254e243fffc6d9f2f3fa23
- Cryip — "BEAT Token Rises Over 525% in a Week…": https://cryip.co/beat-token-surges-525-percent-audiera-revenue-token-burns/
- CryptoTicker — "What Is Audiera? BEAT Token Explodes 380%…" (84% team-control claim): https://cryptoticker.io/en/what-is-audiera-beat-token-surge-analysis/
- news.bitcoin.com — "Audiera's BEAT Surges 60% to $9.34…" ($8.2m short liquidations): https://news.bitcoin.com/audieras-beat-surges-60-to-9-34-as-ai-partnership-fuels-fresh-buying/
- CoinGecko — Audiera: https://www.coingecko.com/en/coins/audiera
- Bubblemaps pattern family (RAVE/SKYAI/PIPPIN/LAB) coverage: https://cryptorank.io/news/feed/fe030-bubblemaps-lab-token-price-manipulation-exchanges
- Data source: OKX Onchain OS (holder, cluster, balance, market endpoints), retrieved 12/06/2026
