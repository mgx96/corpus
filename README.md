# Corpus

Corpus is a curated database of smart contract and distributed ledger vulnerabilities, organized around the one thing that matters most when a system fails: the invariant that was broken.

Most security resources give you a pile of disconnected bug reports. Corpus does something different. It treats every vulnerability as a case study in a broken assumption, indexes it by root cause, and pairs the human reasoning with a runnable reproduction so you can see the failure happen rather than just read about it.

## Why Corpus exists

The web3 security field has an accumulation problem. Thousands of audit findings, contest submissions, and post mortems are published every year, yet the knowledge inside them stays fragmented. A researcher who wants to understand price oracle manipulation has to read fifty scattered reports, reconstruct the shared pattern by hand, and hope they did not miss the one variant that matters.

The core insight behind Corpus is that vulnerabilities are not really about the code. They are about assumptions that turned out to be false. A reentrancy bug and a cross function state desync can live in completely different codebases and still break the exact same invariant. When you index by the broken invariant instead of by the surface symptom, the patterns become visible and transferable.

Corpus is built to make that knowledge searchable, comparable, and reproducible.

## What a finding looks like

Every entry in Corpus is more than a description. A complete finding contains three parts that work together.

1. The reasoning. A clear written explanation of what the system assumed, why that assumption was wrong, and how an attacker turns the gap into value. This is the human layer. It reads like a senior researcher walking you through the case.

2. The reproduction. A runnable Foundry test that sets up the vulnerable state, executes the exploit, and asserts the broken invariant. You do not take our word for it. You run it and watch it break.

3. The benchmark. A structured record of how the finding behaves as a detection target, so tools and agents can be measured against it fairly.

The reasoning tells you why. The reproduction proves it. The benchmark makes it useful for building better detection.

## How findings are organized

Corpus uses a layered taxonomy so that the same case can be approached from several angles.

* Root cause classes. The fundamental category of the broken assumption, such as access control gaps, arithmetic and rounding errors, oracle and price manipulation, reentrancy and state ordering, and validation failures.

* System layers. Whether the vulnerability lives at the smart contract application layer or deeper in the consensus and distributed ledger layer. Corpus deliberately covers both, because the two layers share more failure patterns than most people expect.

* Niches. Finer grained context such as lending markets, automated market makers, bridges, staking systems, and account abstraction, so you can study a class of bug inside the environment where it actually shows up.

Because every finding carries the invariant it breaks, you can move across the taxonomy freely. You can start from a root cause and see every niche it touches, or start from a protocol type and see every way it has been broken.

## The two layers

Corpus covers two layers of the stack, and it treats them as one continuous field of study rather than two separate worlds.

The smart contract layer is where most published research lives today. This is application logic: the lending pools, the swaps, the vaults, the governance systems. Corpus documents the classic and the emerging patterns here with full reproductions.

The consensus and distributed ledger layer is where far less structured knowledge exists, and where the consequences are often larger. This covers the mechanics of the ledger itself: ordering, finality, validator behavior, cross chain messaging, and the economic games that secure or destabilize a network. Corpus brings the same rigor to this layer, indexed by the same invariant first approach.

## The Arena

The Arena is a benchmark built on top of the Corpus database.

Detection tools and autonomous agents claim to find vulnerabilities. The Arena turns that claim into a measurement. Each finding in Corpus can serve as a test target with a known ground truth, so an agent can be scored on whether it identifies the real broken invariant, avoids false positives, and reasons its way to the exploit path.

Because the reproductions are runnable and the invariants are explicit, the scoring is objective. The Arena is designed to become a standard yardstick for how good automated security actually is, rather than how good it claims to be.

## Who Corpus is for

* Security researchers and auditors who want to internalize patterns quickly and study variants side by side.

* Protocol engineers who want to check their designs against the invariants that have already failed in production.

* Builders of detection tools and security agents who need a rigorous, reproducible benchmark to measure and improve their systems.

* Anyone learning smart contract and distributed ledger security who learns better by running the exploit than by reading a summary of it.

## Project status

Corpus is under active development. The database, the taxonomy, and the Arena benchmark are being built out together, with an emphasis on depth and reproducibility over raw entry count. The goal is a resource where every finding is trustworthy enough to run, teach from, and benchmark against.

## Contributing

Contributions are welcome. A strong contribution follows the same shape as every finding in Corpus: clear reasoning about the broken invariant, a runnable Foundry reproduction that proves the failure, and enough structure that the case can be indexed and benchmarked. If you want to propose a finding, an improvement to the taxonomy, or an addition to the Arena, open an issue to start the conversation.

## License

Corpus is released under the MIT License. See the LICENSE file for the full text.
