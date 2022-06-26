---
layout: post
title: "Matrix Syxnapse Communication Server for the Homelab"
date: 2022-06-25 00:00:00 +0200
categories: communication
tags: communication
---

## Introduction

### What is Matrix?

Matrix is an open standard for interoperable, decentralised, real-time communication over IP.

- there exists an open standard in the form of the Matrix Specification
- it's interoperable, meaning it is designed to interoperate with other communication systems, and being an Open Standard means it's easy to see how to interoperate with it
- Matrix is decentralised, which means there is no central point - anyone can host their own server and have control over their data
- it is designed to function in real-time, which means it is ideal for building systems that require immediate exchange of data, such as Instant Messaging

### How does it work?

Each user connects to a single server, this is their homeserver. Users are able to participate in rooms that were created on any Matrix server since each server federates with other Matrix servers. This means you can talk to anyone on any server. It also means you can host your own server, giving you control over all of your data. Self hosting also gives you the ability to customize your server to fit your needs including giving you the ability to bridge to other chat networks (such as IRC, XMPP, Discord, Telegram, etc) or to host bots.

Each message that is sent in a room is synchronized to all of the other servers that participate in that room. If one server goes offline, everyone else in the room can continue talking. Once that server comes back online it will be sent all of the messages that it missed while it was down.

Did we mention it is secure? Your private conversations can be secured by end to end encryption so the server has no idea what you are talking about.
