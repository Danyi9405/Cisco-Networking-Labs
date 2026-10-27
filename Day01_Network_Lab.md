# Day 01 – Network Lab Report

## Network Topology
- 1 Cisco 2911 router
- 2 Cisco 2960 switches
- 4 PCs
- 2 subnets

## Connectivity Tests
- PC1 → PC2: Successful
- PC1 → PC3: Successful
- PC1 → PC4: Successful

## Simulated Fault
I changed PC3's default gateway to `192.168.20.254`. PC3 could still reach PC4, but it could no longer reach PC1.

## Solution
I restored PC3's default gateway to `192.168.20.1`.

## Technical Explanation
PC3 and PC4 could communicate within their local subnet without using the default gateway. To reach PC1 on another subnet, PC3 needed the correct gateway address. Setting an incorrect gateway prevented that communication.
