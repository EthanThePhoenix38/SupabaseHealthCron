<div align="center">
  <img src="./banner.png" width="600px" alt="SupabaseCronHealth Banner" style="border-radius: 10px; box-shadow: 0 4px 8px rgba(0,0,0,0.5);">
  
  <br><br>
  
  [![GitHub Marketplace](https://img.shields.io/badge/Marketplace-SupabaseCronHealth-blue?style=for-the-badge&logo=github)](https://github.com/marketplace/actions/supabasecronhealth)
  [![Build Status](https://img.shields.io/badge/Health%20Checks%20Status-Scheduled%20Actions-brightgreen?style=for-the-badge)](https://github.com/ThePhoenixAgency/SupabaseCronHealth/actions)
  [![YAML](https://img.shields.io/badge/YAML-CB171E?style=for-the-badge&logo=yaml&logoColor=white)](https://github.com/ThePhoenixAgency/SupabaseCronHealth)
  [![Tests](https://img.shields.io/badge/Monitoring-Passing-green?style=for-the-badge&logo=github-actions&logoColor=white)](https://github.com/ThePhoenixAgency/SupabaseCronHealth/actions)
  [![MIT License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](https://choosealicense.com/licenses/mit/)
  
</div>

# SupabaseCronHealth

## Table of Contents
- [Overview](#overview)
- [Key Features & Philosophy](#key-features--philosophy)
- [Why This Pattern? (The Silent Guardian)](#why-this-pattern-the-silent-guardian)
- [Installation](#installation)
- [Configuration Options](#configuration-options)
- [Support This Project](#support-this-project)

**Version**: 1.0.0  
**Author**: ThePhoenixAgency  
**License**: MIT

## Overview

**SupabaseCronHealth** is an enterprise-grade GitHub Actions watchdog designed to monitor a Supabase instance using a silent monitoring philosophy. It produces no signal while the service is healthy, a single signal when a long outage is confirmed, and a single signal when the service recovers. Monitoring is based on the Supabase native `/auth/v1/health` endpoint with authentication via repository secrets.

## Key Features & Philosophy

### 1. Absolute Silence
- Health checks run every 5 minutes
- No commits while Supabase is healthy
- No commits for short transient failures
- One single commit for a confirmed long outage
- One single commit for confirmed recovery

### 2. Native Supabase Health Endpoint

\`\`\`http
GET /auth/v1/health
\`\`\`

Authentication is handled exclusively via GitHub repository secrets.

### 3. Commit-As-Alert Strategy

Git commits are used as the alerting mechanism. A commit triggers GitHub notifications without SMTP configuration, webhooks, or external services.

### 4. Clean History by Design

Automated commits are isolated on a dedicated branch (for example `health-events`). Your main branch remains silent and clean.

## Why This Pattern? (The Silent Guardian)

This workflow implements a mature self-healing SRE-grade monitoring pattern that eliminates noise, centralizes audit trails, and runs natively on GitHub Actions without external dependencies.

## Installation

1. Add workflows:
   - `.github/workflows/cron_alerte.yaml`
   - `.github/workflows/cron_recover.yaml`
2. Add required secrets:
   - `SUPABASE_BULLETIN_URL`
   - `SUPABASE_BULLETIN_ANON_KEY`
3. Ensure GitHub Actions has push permissions to the branch used for health event commits.

## Configuration Options

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| Check interval   | Cron schedule | Yes | 5 minutes |
| Outage threshold | Failure count | Yes | 72 |
| Endpoint         | Health URL path | Yes | `/auth/v1/health` |
| Alert branch     | Git branch | Yes | `health-events` |

## Support This Project

If this action helps secure or stabilize your infrastructure, support the development:

[![GitHub Sponsors](https://img.shields.io/badge/Sponsor_on-GitHub-ea4aaa?style=for-the-badge&logo=github)](https://github.com/sponsors/EthanThePhoenix38)  
[![Patreon](https://img.shields.io/badge/Support_on-Patreon-F96854?style=for-the-badge&logo=patreon)](https://patreon.com/EthanThePhoenix)  
[![PayPal](https://img.shields.io/badge/Support_via-PayPal-00457C?style=for-the-badge&logo=paypal)](https://www.paypal.com/paypalme/VanessaBernier)  
[![Ko-fi](https://img.shields.io/badge/Support_on-Ko--fi-F16061?style=for-the-badge&logo=ko-fi)](https://ko-fi.com/EthanThePhoenix)  
[![Support via Patreon](https://img.shields.io/badge/Patreon-Support%20Development-f96854?logo=patreon&logoColor=white)](https://www.patreon.com/EthanThePhoenix)

**Your support helps fund the server and AI development!**  
In exchange, I will add a link to your GitHub profile in the Contributors section.

You can also :  
- Star this repository  
- Fork it to customize for your needs  
- Report issues to help improve it

## Professional Page

http://ThePhoenixAgency.Github.io
