# Toroidal queens on the 19 x 19 board: reproducible proof artifact

Author: Luhang Xiong (also displayed as Xiong Luhang in the frozen review draft).
Author-supplied ORCID: https://orcid.org/0009-0000-8999-2939.
Artifact publication prepared October 19, 2026 (Asia/Shanghai).

## Result and scope

The computation excludes independent dominating placements of exactly ten queens
on the 19 x 19 torus. Combined with the previously reported lower bound ten in
[OEIS A279404](https://oeis.org/A279404) and the independently verified published
eleven-queen construction, this gives i(Q_19^T)=11. The earlier lower bound is an
external mathematical input: excluding exactly ten does not exclude smaller
cardinalities on its own.

All 92,378 ten-row subsets are covered by 280 affine row orbits. All 280 direct
CNFs were refuted by native CaDiCaL 1.9.5, and all 280 DRAT refutations passed
the independent drat-trim checker during the original certification. The
reduction and encoding equivalence have ordinary mathematical proofs and
independent finite audits, not an end-to-end proof-assistant formalization.
No independent third-party review, journal acceptance, or DOI is claimed.
AI assistance in code development and exposition is disclosed in the manuscript.
The human author must review the mathematical and implementation arguments.

## Download

Use the assets in the [versioned release](https://github.com/Jason-XiongLuHang/toroidal-queens-n19-certification/releases/tag/v1.0.0-artifact).

- `manuscript-20261019.pdf` and `manuscript-latex-20261019.zip`: the later
  eight-page Springer-format review manuscript with author-supplied ORCID,
  clearer mathematical displays and unchanged mathematical conclusions.
  Their digests are in `MANUSCRIPT.sha256`. This is a preprint, not a
  journal-accepted or independently peer-reviewed article.
- `toroidal-queens-n19-code-and-manuscript.zip`: typeset six-page review draft, complete audit source, 280 CNFs/maps,
  original checker outputs, and provenance/licenses. Extract it and run
  `python -B final-source/verify_all.py` (Python 3.12+, standard library only).
- `toroidal-queens-n19-drat-certificates.zip.part001` through `.part004`: four consecutive raw byte chunks
  of the original proof ZIP, not individually extractable ZIP archives.
- `SHA256SUMS` and `ARTIFACTS.json`: exact sizes and SHA-256 digests.

The automatically generated GitHub Source code ZIP is only this landing
repository, NOT the full source/CNF artifact. Download the explicitly named
artifact ZIP above.

## Join and validate the proof archive

Put all four parts in one directory. This Python command works on Windows,
macOS and Linux and refuses to overwrite an existing output:

```python
from pathlib import Path
import hashlib
import shutil

archive = Path("toroidal-queens-n19-drat-certificates.zip")
with archive.open("xb") as output:
    for number in range(1, 5):
        with Path(f"{archive.name}.part{number:03d}").open("rb") as source:
            shutil.copyfileobj(source, output, 8 * 1024 * 1024)
with archive.open("rb") as source:
    assert hashlib.file_digest(source, "sha256").hexdigest() == "a68b6108ce29ca3b932532ccde13ecbe1dcc167f3309d5ca342266f5c8c7ad21"
```

The joined ZIP is exactly 3,692,134,027 bytes. Its SHA-256 is
`a68b6108ce29ca3b932532ccde13ecbe1dcc167f3309d5ca342266f5c8c7ad21`. The raw proof files total 13,916,789,616 bytes.

Source/model checking does not replay proofs or call a SAT solver. For an actual
selected replay, from extracted `final-source/` run:

```text
python -B verify_all.py --proof-archive /actual/path/toroidal-queens-n19-drat-certificates.zip --proof-id affine-0000
```

Replace `--proof-id affine-0000` with `--all-proofs` for a full, potentially
lengthy sequential replay. The checker needs an installed drat-trim or GCC to
compile the included unchanged C source. A timeout is not an UNSAT certificate.

The draft in v1.0.0 records its local preparation state before this upload;
this release page records the subsequent public deposition. Historical process
anomalies and the proof checker trust boundary are preserved in the artifact.
Later journal formatting does not change the frozen source/CNF/proof bytes.

## Licensing

Author-controlled audit code: MIT. Author-controlled documentation/research
data: CC BY 4.0. Third-party code retains the original licenses provided in the
artifact. See its LICENSE, DOCUMENTATION-LICENSE.md and THIRD_PARTY.md.
