# Verification certificate

## Claim

- a(9) = 167892639418.
- a(10) = 7287023194031.
- Replace the existing no3-results link with this repository link (queued).

## Evidence

| What | Repository path | Author and date | Coverage | Result | Independence / shared code or data |
|---|---|---|---|---|---|
| Producer | `programs/line_rows.c`; `programs/reference/n9.json`; `n10/shards-n10.tar.gz` | Athanor lab, AI assisted; n=9 on 3 Nov and n=10 on 5 Nov 2026; individual coder not identified | Row traversal and recorded profiles | n=9: total 167892639418, maximal 1861878186; n=10: 7287023194031, 56412888628 | Producer |
| Independent check | `programs/determinant_check.c`; `programs/reference/determinant-n9.json`; `n10/shards-n10.tar.gz` | Athanor lab, AI assisted; same dates; individual coder not identified | Determinant traversal, n=9 and 10 profiles | Reports agreement in each size cell; 512/512 n=10 shards each | Independently written enumeration, no shared enumerator code according to `programs/method.md`; same mathematical definition and target data, shared collection/receipt pipeline |
| Receipt and identity check | `programs/collect.py`; `n10/profile-n10.json` | Athanor lab, date and individual author not stated | Recorded n=10 outputs, shard receipts and profile identities | Complete receipts, matching profiles and totals | Reads both producers' stored data; no independent enumeration |

## Replayed for this repository

Executed on 13 Nov 2026 WITA, locally. Commands use the logged working directory; logs contain the full outputs. Wall times include process startup.

- `cc -O2 -std=c11 /Users/iwasborninbali/projects/science/oeis-A398172/programs/determinant_check.c -o /tmp/c7-A398172/determinant_check` — exit 0, 0.123 s; output: compiler produced no output [`logs/certificate-2026-11-13/build-determinant_check.log`](logs/certificate-2026-11-13/build-determinant_check.log) (SHA-256 `cbbd973faea62d5df9747df8eb0281427d29fff4856ba892ea36974f42ce9b36`).
- `cc -O2 -std=c11 /Users/iwasborninbali/projects/science/oeis-A398172/programs/line_rows.c -o /tmp/c7-A398172/line_rows` — exit 0, 0.726 s; output: compiler produced no output [`logs/certificate-2026-11-13/build-line_rows.log`](logs/certificate-2026-11-13/build-line_rows.log) (SHA-256 `acd871340d780d7530578763ae8a43713101a5b0a45e83713ea151a19fb81400`).
- `python3 -B /tmp/c7_compare.py /Users/iwasborninbali/projects/science/oeis-A398172` — exit 0, 0.041 s; output: PASS: b-file n=9,10 equals stored n=9 and n=10 totals; from pathlib import Path; import sys,json,re; r=Path(sys.argv[1]); s=r.name; load=lambda p:json.loads((r/p).read_text()); a=load('programs/reference/n9.json'); b=load('programs/reference/determinant-n [`logs/certificate-2026-11-13/data-compare.log`](logs/certificate-2026-11-13/data-compare.log) (SHA-256 `7295287b8f1526ed9d73d27248a3c4333821a2d4ecb24e7adb7309ff901370ed`).
- `/tmp/c7-A398172/determinant_check 5 0 1 2` — exit 0, 0.649 s; output: total 109536, maximal 5646; matching size profiles. [`logs/certificate-2026-11-13/n5-determinant_check.log`](logs/certificate-2026-11-13/n5-determinant_check.log) (SHA-256 `20bca7000468509d3ba79241648ff04039bf4ff3eb21717e17556997284e232a`).
- `/tmp/c7-A398172/line_rows 5 --shard 0 --shards 1 --split-rows 2` — exit 0, 1.037 s; output: total 109536, maximal 5646; matching size profiles. [`logs/certificate-2026-11-13/n5-line_rows.log`](logs/certificate-2026-11-13/n5-line_rows.log) (SHA-256 `59eba659e730221f22663b5d32773a0f14e7bf3c7edc9371409807f99c1ab5e0`).
- `python3 -I /Users/iwasborninbali/projects/science/oeis-A398172/programs/collect.py /tmp/c7-A398172/run-n10 --require-complete` — exit 0, 0.242 s; output: 512/512 shards per program; totals 7287023194031 and 56412888628; matching profiles. [`logs/certificate-2026-11-13/receipts.log`](logs/certificate-2026-11-13/receipts.log) (SHA-256 `b11589cdab40a6f4d9361463ab6c0027253d155cc0db8a1a52f286796619e344`).

The archived shards were safely extracted to `/tmp/c7-A398172` after checking paths and sizes. The collector operates on those existing results, not a fresh enumeration. Full n=10 reruns were omitted: README reports about 104 core-hours for both programs; stored n=9 reference runs report about 2635 and 4836 seconds.

## Not covered

The n=9 and n=10 enumerations were not rerun in full; n=9 profiles are stored reports and n=10 receipts authenticate outputs, not the truth of the computation. Correctness of both algorithms and their shared assumptions has not been established by this replay. Repository link availability has not been independently tested.

## Guide's independent check

pending

## Verdict

partial — The evidence and replay leave the gaps above, and the Guide's independent check is pending.
