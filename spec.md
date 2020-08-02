---
layout: single-page-md
title: APIO 2020 Technical Specification
key: spec
---

Here is the specification of the grader system.

<b>Machine</b>

- <a href="https://www.digitalocean.com/docs/droplets/resources/choose-plan/#droplet-plans">DigitalOcean CPU-optimized dedicated droplet</a>, Intel Xeon Skylake 2 cores @ 2.7 GHz
- 4 GB RAM
- Ubuntu 18.04.3 LTS

<b>C compiler</b>

- gcc 7.5.0
- Compilation command: `gcc -std=gnu99 -o solution solution.c -O2 -lm`

<b>C++ compiler</b>

- g++ 7.5.0
- Compilation command: `g++ -std=c++11 -o solution solution.cpp -O2 -lm`

<b>Java compiler</b>

- OpenJDK javac 1.8.0_252
- Compilation command: `javac Solution.java`
