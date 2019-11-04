---
layout: post
title:      "OAuth vs SAML"
date:       2019-11-04 00:48:29 +0000
permalink:  oauth_vs_saml
---


If you've ever been given the option to log on via Facebook or Google rather than creating an account from scratch, then you've experience OAuth.  OAuth stands for Open Authentication and is a common method for verifying a users existence by piggybacking off of some of the worlds most frequently visited websites instead of creating the verification from scratch.  Why do we do this?  One of the main reasons is the quality of the authentication.  The worlds most frequently visited platforms (such as Facebook or Google) have invested a lot of time, money, and resources into creating a lock tight authentication system.  Any authentication system we could build out from scratch would pale in comparison to the authentication performed by say Google.  Armed with this knowledge, we can utilize OAuth to theoretically "handshake" an authentication provider; I ask the provider for access to log on via their authentication system, and the authentication system tells me whether I have been verified.  This communication happens via OAuth.

Knowing this, let's look into SAML.  SAML stands for Security Assertion Markup Language, and "provides us with a standard for exchanging and exchanging authentication and authorization data between parties, in particular, between an identity provider and a service provider" (Wikipedia).  This is a little more vague than our previously discussed OAuth.

What is the difference?  In short, SAML is an umbrella standard that encompasses how to achieve SSO (Single Sign On).  OAuth is specifically the open authorization of resources (like a users account information).  From what I gather, not all SAMLs are OAuths, but all OAuths are SAMLS...

What is the main difference if I choose to use SAML over Oauth?  The biggest difference in my opinion is the data transfer.  OAuth transfers data via JSON, whereas SAML transfers data via XML.
