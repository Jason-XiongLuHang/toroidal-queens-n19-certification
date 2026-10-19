# Independent domination on the 19 by 19 and 20 by 20 toroidal queens boards

Xiong Luhang, 19 October 2026.

This page collects the manuscripts, constructions, verification programs and
proof files supporting the proposed values **A279404(19) = 11** and
**A279404(20) = 10**. The sequence is
[OEIS A279404](https://oeis.org/A279404).

## Order 19

The computation excludes independent dominating sets of exactly ten queens.
Together with the previously recorded lower bound ten and Cohen's published
eleven-queen construction, this gives the value eleven. The manuscript explains
the mathematical reduction; the source package and checked DRAT refutations
allow its finite computations to be audited.

- [Current manuscript (PDF)](https://github.com/Jason-XiongLuHang/toroidal-queens-n19-certification/releases/download/v1.0.1-manuscript/manuscript-Xiong-Luhang-20261019.pdf).
- [Current LaTeX sources](https://github.com/Jason-XiongLuHang/toroidal-queens-n19-certification/releases/download/v1.0.1-manuscript/manuscript-LaTeX-Xiong-Luhang-20261019.zip).
- [Complete verification source, 280 CNFs and original manuscript](https://github.com/Jason-XiongLuHang/toroidal-queens-n19-certification/releases/download/v1.0.0-artifact/toroidal-queens-n19-code-and-manuscript.zip).
- [All four DRAT archive parts, checksums and certification record](https://github.com/Jason-XiongLuHang/toroidal-queens-n19-certification/releases/tag/v1.0.0-artifact).
- [Proof archive assembly and replay instructions](https://github.com/Jason-XiongLuHang/toroidal-queens-n19-certification/blob/main/README.md#join-and-validate-the-proof-archive).

All 280 refutations passed the separate drat-trim checker in the original local
certification. The mathematical reduction is explained and independently audited
by finite programs; it has not been formalized in a proof assistant. Later
manuscript formatting leaves the original source, CNF and proof assets unchanged.

## Order 20

An independent dominating set of ten queens has the following zero-indexed
coordinates, with all attack relations interpreted modulo 20:

```text
(0,0), (1,7), (2,15), (5,8), (7,18),
(10,5), (11,16), (12,10), (15,3), (17,13)
```

The two Python verifiers report zero attacking pairs and coverage of all 400
squares. Combined with the previously recorded lower bound ten, this construction
gives the value ten.

- [Mathematical explanation and verification instructions](https://github.com/Jason-XiongLuHang/toroidal-queens-n19-certification/releases/download/v1.1.0-n20-witness/README.md).
- [Minimal evidence package: coordinates, standard-library Python verifiers and complete coverage certificate](https://github.com/Jason-XiongLuHang/toroidal-queens-n19-certification/releases/download/v1.1.0-n20-witness/toroidal-queens-n20-minimal-evidence.zip).
- [Full computational record and checksums](https://github.com/Jason-XiongLuHang/toroidal-queens-n19-certification/releases/tag/v1.1.0-n20-witness).

After extracting the minimal package, its main check is:

```text
python verify.py witness-n20-k10.json
```

This requires no solver or third-party Python package. The positive witness
establishes an upper bound; the existing lower bound is a separate input to the
minimum-cardinality conclusion.

## Scope

These artifacts make no first-discovery, journal-acceptance or OEIS-acceptance
claim. AI assistance in code development and exposition is disclosed in the
manuscript and artifact notes. Searches and verification run locally without
language-model API calls. Refer to each versioned release for its original
checksums, provenance and licensing information.
