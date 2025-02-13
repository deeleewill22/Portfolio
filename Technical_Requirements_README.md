# Technical Requirements

## Description

This document outline the hardware, software, and system prerequisites needed to install, run, or use the price builder application and its corresponding services. This ensures users are aware of the necessary requirements before using the product.

## Table of Contents

1. Overview
2. Log and Project Information
3. Production Environment Information
4. API Calls
5. Data Administration

## Overview

The overview outlines the product suite for ABC including go-live dates, organizational information, and user licensing information.

| Product | Data Engineer | Status | Description | Go-live Date  | Org ID | SSO? | User Count and License Types |
|----------|----------|----------|----------|----------|----------|----------|----------|
| Pricing Builder | Denise Williams | Production | Application used to configure price build-up and manage pricing | 1/1/2024 | 00T8E00000iiFw | No    | 50 Salesforce Platform Users |
| Reporting Analytics | Denise Williams | QA | Embedded reports in Pricing Builder application that provides direct access reports in Tableau    | N/A | 00T8E00000iiFw | No   | 5 Identity Users |

## Log and Project Information

| Application | Link |
|----------|----------|
| Sharepoint | [https://abc.sharepoint.com](https://abc.sharepoint.com) |
| JIRA | [https://abc.atlassian.net/jira](https://abc.atlassian.net/jira) |
| Kibana | [us3-logs.abc.com/_plugin/kibana/app/discover](us3-logs.abc.com/_plugin/kibana/app/discover) |

## Production Environment Information

| Application | Link |
|----------|----------|
| SQL Server | [us3-prdb-abc1](us3-prdb-abc1) | 
| Salesforce | [https:/ABC.my.salesforce.com](https:/ABC.my.salesforce.com) | 
| AWS S3 | [s3://abc.us3/bc/prod](s3://abc.us3/bc/prod) |

## API Calls

| API Information | Notes |
|----------|----------|
| Integration Type    | Inbound |
| API Endpoint    | [https://api-bc.abc.com/](https://api-bc.abc.com/) |
| Estimated call per 24 hours    | 10 every 20 minutes during the business day (about 1,500 records per API call) |

## Data Administration

| # | File Name    | Subject Matter          | Delimiter | Size | Type | Code Page | Load Type |
|---|--------------|-------------------------|-----------|------|------|-----------|-----------|
| 1 | Customer.csv | Customer data           | Pipe (|)  | 1 GB | CSV  | UTF-8     | Monthly   |
| 2 | Pricing.csv  | Pricing recommendations | Pipe (|)  | 2 GB | CSV  | UTF-8     | Weekly    |

[Back to Portfolio](../README.md)
