# Cryptographic algorithms <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Introduction and overview](#introduction-and-overview)
- [Hashing](#hashing)
	- [Hash functions](#hash-functions)
	- [Password hashing](#password-hashing)
- [Random numbers generation](#random-numbers-generation)
	- [Potential problems](#potential-problems)
		- [Debian OpenSSL bug](#debian-openssl-bug)
		- [Dual\_EC\_DRBG backdoor](#dual_ec_drbg-backdoor)
- [Public-key cryptography](#public-key-cryptography)
	- [RSA (Rivest–Shamir–Adleman)](#rsa-rivestshamiradleman)
	- [Diffie–Hellman key exchange](#diffiehellman-key-exchange)
- [Protocols](#protocols)
	- [TLS](#tls)

---

## Introduction and overview

:book:

- Essay 7: *Locking the barn door* – P.J.Plauger. [*Programming on purpose III: Essays on software technology*](https://www.pearson.com/us/higher-education/program/Plauger-Programming-on-Purpose-III-Essays-on-Software-Technology/PGM133229.html) (1994)

## Hashing

### Hash functions

### Password hashing

:link:

- [*Salted password hashing – Doing it right*](https://crackstation.net/hashing-security.htm) – CrackStation
- S.Ignatchenko. [*Password hashing: Why and how*](https://accu.org/journals/overload/23/129/ignatchenko_2159/) – [Overload **129**](https://accu.org/journals/overload/overload129) (2015)

---

## Random numbers generation

### Potential problems

:movie_camera:

- N.Heninger. [*Random number generation failures from Netscape to DUHK*](https://www.youtube.com/watch?v=fC6QySrAd7U) (2018)

#### Debian OpenSSL bug

:link:

- R.Cox. [*Lessons from the Debian/OpenSSL fiasco*](https://research.swtch.com/openssl) (2008)
- J.Kroll. [*The Debian OpenSSL bug: Backdoor or security accident?*](https://freedom-to-tinker.com/2013/09/20/software-transparency-debian-openssl-bug/) (2013)

#### Dual_EC_DRBG backdoor

:link:

- B.Schneier. [*Did NSA put a secret backdoor in new encryption standard?*](https://www.wired.com/2007/11/securitymatters-1115/)

:movie_camera:

- M.Pound. [*Elliptic curve back door*](https://www.youtube.com/watch?v=nybVFJVXbww) – Computerphile

:anchor:

- [*Dual_EC_DRBG*](https://en.wikipedia.org/wiki/Dual_EC_DRBG) – Wikipedia

---

## Public-key cryptography

:book:

- Essay 8: *Half a secret* – P.J.Plauger. [*Programming on purpose III: Essays on software technology*](https://www.pearson.com/us/higher-education/program/Plauger-Programming-on-Purpose-III-Essays-on-Software-Technology/PGM133229.html) (1994)

### RSA (Rivest–Shamir–Adleman)

:movie_camera:

- J.Keating. [*How does RSA cryptography work?*](https://www.youtube.com/watch?v=qph77bTKJTM)

### Diffie–Hellman key exchange

:link:

- [*Diffie–Hellman key exchange*](https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange) – Wikipedia

---

## Protocols

### TLS

:movie_camera:

- P.Bindels. [*TLS cryptography for programmers*](https://www.youtube.com/watch?v=6_9ODzckrfc) – ACCU (2022)
