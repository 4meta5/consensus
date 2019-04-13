# HoneyBadger BFT

* [Rob's Implementation](https://github.com/rphmeier/honeybadger)

Relative to partially synchronous BFT protocols, HoneyBadger BFT has **higher latency** and **lower throughput**, in part due to the use of expensive threshold cryptography (threshold encryption and threshold signatures).

Due to its erasure encoding library, it only supports Reed-Solomon codes

