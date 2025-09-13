# RHEL SSH Container (UBI 8) Project

## Overview
RHEL UBI 8 container with user 'gurus', sudo privileges, SSH access (password + key), ready for lab.

## Build & Run
docker build -t rhel:latest .
docker run -d -p 2222:22 --name rhel-container rhel:latest

## SSH
Password login:
ssh gurus@localhost -p 2222
Password: Santhi@1481#
