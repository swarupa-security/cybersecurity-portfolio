# Lab: SQL Injection - Login Bypass
Platform: PortSwigger
Date: June 2025

## Objective
Bypass admin login without password.

## Steps
1. Entered ' OR 1=1-- in username field
2. Password field was bypassed
3. Got access to admin panel

## Tool Used
Burp Suite

## What I Learned
SQL Injection possible due to missing
input validation.
