# QA Project Overview

## Context

This repository contains sanitized working materials from a real paid QA engagement for an AI SaaS web platform. The product combined a catalog of ready-made AI specialists, conversational workflows, a custom-agent builder, a multi-step campaign generator, and user-defined integrations.

Client and product names, domains, internal routes, and production identifiers have been removed. The public version preserves the technical QA context without exposing client traceability or proprietary production data.

## Role

**QA Engineer**

Responsibilities included preparing and executing manual checks, recording Expected vs Actual, assigning severity and priority, collecting evidence, validating dependencies, retesting fixes, and running affected regression.

## Coverage model

Testing was organized around risk and user flows:

1. public area and authentication;
2. critical AI dialog/runtime behavior;
3. state persistence and reopen behavior;
4. custom agents and integrations;
5. campaign generator through safe preview/export;
6. responsive, cross-browser, and real-device checks;
7. read-only administrative visibility.

Checks were linked to E2E scenarios, exploratory observations, defects, and fix-retest batches. A downstream check was not marked FAIL simply because an upstream prerequisite was unavailable; in those cases the dependency was recorded as BLOCKED BY BUG.

## Evidence-first approach

Every FAIL required current-run evidence appropriate to the defect: screenshot, continuous video, UI/runtime observation, network status, or console output. Supporting evidence was explicitly distinguished from direct causal evidence when necessary.

Production evidence is not copied into this repository. Public documentation describes the validation method and evidence type without exposing client artifacts.

## Final status limitation

The source snapshot represents an interim QA cycle. At that point the final regression gate had not yet been executed, so these materials must not be interpreted as blanket release approval.
