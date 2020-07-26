---
layout: single-page-md
title: APIO 2020 Competition Rules
key: rules
---

These Competition Rules cover General, Problem Scoring, Contestant Scoring, Grading System, and Clarifications in APIO 2020.
Delegation Leaders have the responsibility of ensuring that all members of their delegation fully understand these rules and abide by them.

<span style="color:red">**Please do not share the problems after the contest within 2 days since the competition is not held within the same time range.**</span>

<br>

### A. General

* APIO 2020 consists of **1 practice problemset** and **1 competition day**.
* Result of the practice problemset **does not** affect scoring.
* There will be **3 (three) problems** on the competition day to be solved in **5 (five) hours**.
* Each contestant may submit up to **50 submissions** for each problem.
* The supported programming languages are **C++** and **Java**.
* During the competition, each contestant can only see their own scores.

<br>

### B. Problem Scoring

* There are two types of scoring: **standard** and **creative**.
* Creative problems will be stated explicitly in the problem description.

* **Standard** scoring:
  * For batch and interactive problems:
    * A problem consists of **multiple subtasks** with various points.
    * A subtask consists of **multiple test cases** that are grouped into some **test groups**.
    * A submission gets a subtask's points if it solves **all of its test groups**.
    * To solve a test group, a submission has to solve **all of its test cases**.
  * For output-only problems:
    * A problem consists of **multiple test cases** with various points.
    * A submission gets the test case's points if it produces the correct output.

* **Creative** scoring:
  * The scoring formula will vary for each problem and will be explicitly stated in the problem description.

<br>

### C. Contestant Scoring

* For batch and interactive problems:
  * On creative scoring, for each submission, the score of a subtask is the minimum score among all its test cases.
  * A subtask final score is the **maximum of its score** among all submissions.
  * Contestant's score for a problem is the sum of all its subtasks final score.

  For example, if the first submission got 30 points for the first subtask and 0 points for the second subtask, and the second submission got 0 points for the first subtask and 40 points for the second subtask, then the contestant's score for the problem is 70 points.
* For output-only problems:
  * A test case final score is the **maximum of its score** among all submissions.
  * A contestant's score on a problem is the sum of all its test cases final score.
* A contestant's total score is the sum of **all of problems score**.
* Contestants will be ranked by the total score (descending).
* Two contestants with **the same** total score will achieve **the same** rank.
* Submission time **will not affect** contestant rank at all.

<br>

### D. Grading System

* Grading system similar to the public site [TLX](https://tlx.toki.id) will be used.
* Source code limit for each submission is **300 KB**.
* Contestants will get full feedback for each submission.
* For each test case, the grader will output one of:
  * **AC** (Accepted): program solved the problem within the given time and memory limits.
  * **WA** (Wrong Answer): program stopped within given time and memory limits, but produced the wrong output.
  * **RTE** (Runtime Error): program crashed or exceeded the memory limit.
  * **TLE** (Time Limit Exceeded): program exceeded the time limit.
  * Skipped: test case is not graded because there was a test case in the same subtask that was not solved.

<br>

### E. Clarification

* A contestant can submit a clarification request in English during the competition.
* Clarification requests will be answered only in English with one of the following:
   * “YES”
   * “NO”
   * “ANSWERED IN TASK DESCRIPTION (EXPLICITLY OR IMPLICITLY)” – The task description contains sufficient information. The contestant should read it again carefully.
   * “INVALID QUESTION” – The question is most likely not phrased so that a yes/no answer would be meaningful. The contestant is encouraged to rephrase the question.
   * “NO COMMENT” – The contestant is asking for information that the Scientific Committee cannot give.

<br>

### F. Submission and Access

* All submission from each contestant must be written by the contestant.
* Each contestant is allowed to use any code written before the competition, as long as the code is written by the contestant.
* Each contestant is prohibited to talk or discuss anything related to the content of the competition with anyone, including other contestants, except to the committee of the competition using the clarification request explained in the earlier section.
* Each contestant is allowed to use any sources of information on the Internet, as long as the contestant does not violate the previous rule. In particular, it is forbidden to copy-paste somebody else's code on the internet, or posting anything related to the content of the competition in an online forum.
* For the sake of respecting fairness of this newly-introduced online contest format, each contestant is expected to show good sportsmanship by following the above rules honestly. Any violation of the rules can be subject to disqualification.
