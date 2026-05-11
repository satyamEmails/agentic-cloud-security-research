
# Agentic Cloud Security Research
Independent security research on AI agent vulnerabilities in cloud environments.
Researcher: Satyam Kumar Singh | Brand: SatyamGenSys
Research focus: Intersection of AWS IAM, AI agent tool calling, and MCP protocol security.
Status: Active | Started: May 2026
# ACS-T-POISON-CRIT-001
**Date:** 2026-05-07  
**Researcher:** Satyam Kumar Singh | SatyamGenSys

## Classification
`ACS-T-POISON-CRIT` — Trust primitive violated via tool poisoning, critical severity.

## Finding
MCP tool descriptions carry no cryptographic integrity guarantee. An attacker who 
controls or compromises an MCP server can modify tool description text without 
changing structure or trust_level. The agent cannot distinguish the poisoned 
description from a legitimate one.

## Detection Gap
Each individual log entry appears legitimate:
- CloudTrail: valid `s3:GetObject` call
- Agent logs: valid `read_file` tool call
- No current SIEM rule detects the anomaly

## Proposed Defense
Cryptographic attestation of tool schemas at MCP server registration. 
Agent verifies signature before accepting tool definitions.  
**Status: Not implemented in any current MCP production deployment.**

## Research Significance
Open problem. No existing solution in the MCP specification.
