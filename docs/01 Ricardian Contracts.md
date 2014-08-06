# The Use of Ricardian Contracts in *OpenBazaar*

## What is a Ricardian Contract

> A Ricardian Contract can be defined as a single document that is a) a contract offered by an issuer to holders, b) for a valuable right held by holders, and managed by the issuer, c) easily readable by people (like a contract on paper), d) readable by programs (parsable like a database), e) digitally signed, f) carries the keys and server information, and g) allied with a unique and secure identifier.

[Source](http://iang.org/papers/ricardian_contract.html)

The Ricardian contract is a means of tracking the liability of one party to another when selling goods to each other in *OpenBazaar*. Fundamentally, a contract represents a single unit of a good or service. Ricardian contracts should be used in *OpenBazaar* as they are means of effectively tracking legitimately signed agreements between two parties, which cannot be forged after the contract has been signed.

Ricardian contracts make use of a chain of digitally signed and checksum hashed contracts to create an unalterable record of agreement for an exchange on a peer-to-peer network.

**Digital signatures** = Proof of agreement (when you sign, you agree to the terms)  
**Hashes** = Proof of authenticity (the smallest possible change in the contract alters the hash, indicating the contract has been altered)

## Issuing a Contract: Structure

The contract is saved as an XML file, with the SHA1 hash of the file as part of the file name. Within the XML file, the contract contains the following structure:

```
1. Contract terms
	- Seller's nym
	- Contract nonce (unique identifier)
	- Seller's bitcoin pubkey (for multisig transactions)
	- Merchant Data
		- What is to be sold
		- Price per unit
		- Additional conditional detail unforseen in this proposal
	- Contract expiration date
	- Seller's PGP public key
2. All of the above is digitally signed with the seller's private PGP key
```

#### Example:

Alice wants to sell a 16 pound watermelon. She creates the contract below, signs it with her nym key (her private PGP key) and distributes/seeds it on the *OpenBazaar* network. 

```
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

<?xml version="1.0"?>

<!-- Seller's NYM -->
        <nym_id> ALICE-NYM-ID-HASH </nym_id>

<!-- Contract Nonce -->
	<contract_nonce> XXXX-YYYY-123456 </contract_nonce>

<!-- Bitcoin Pubkey -->
	<btc_addr> 03d728ad6757d4784effea04d47baafa216cf474866c2d4dc99b1e8e3eb936e730 </btc_addr>

<!-- Merchant Data -->
	<asset_name> 16 Pound Watermelon </asset_name>
	<asset_price> 0.01 BTC </asset_price>

<!-- Contract Expiration Date -->
	<contract_exp> YYYY-MM-DD TIME UTC </contract_exp>
	
<!-- Seller's PGP Key -->
<PGP_Public_Key>
- -----BEGIN PGP PUBLIC KEY BLOCK-----
Version: BCPG v1.47

mQINBFMZcEIBEADJlq0oVgLfFDdW9WOBguskPdSSeAfHe4s9w8QlmRuO/Zj548gK
fofbM84rtP3rHSOSkeOTsu5GwDt48V/md6gyJ69BTZJkJ6qmxFtGaWVRLP/UD4ma
vW4EAn3PvWY6X7Z8x36U3j2I6vknH1Ufu5Dh5qvQC3WsMliul9ZxlJQZ1/TkQE+q
I/gBPRmsMFZ/xV2VOEjMtM3qOPoemhYFzU39/ra0isk81sXrotySkvWw6zsrx8Nr
kBaw9mxhs0kumF06AfKSrBjyt/FIdbJaWtNrCdxJ+NMfzQUHmq9bzpBI2VpNJzFQ
I4WlO8eRYDS1Z88VxXOjMZchd70JfNNWcXwCUeOA/HUgHO4tWczvb/5/C5pfZRKu
DqfOLntcMEzpPxbhAbXvU+K5TK394SGgu9ioXl3rdrFj1B1EBPH2BfnOdwCiOOr5
ccWVPUHdG34i4D98ARgeqEDxq9/WZwq8FG9rgSszqkmnGQtSZxz8aoW1kU1h1SQu
mqs2ZUrEoLGACkNg16kRq2z7RBLc4MAm3/GW3ygeEFQxK0PMief0X2+l0oVo7a0A
RMLLLx4ckuoX3DIJvBegFPvlp0rO3JihdzNmCqIBTDok7D0k2NiQsm3WDJHAYB+8
G4ruHVPAOzPNxz5krF+u71jcWmZKO4FRAcXCrWTQCku7wLyzOF80sVEDlwARAQAB
tGNEciBXYXNoaW5ndG9uIFlhbWFuZHUgU2FuY2hleiAoMjAxNCBLZXlwYWlyIGZv
ciBuZXcgZW1haWwgYWRkcmVzcykgPHdhc2hpbmd0b24uc2FuY2hlekBvdXRsb29r
LmNvbT6JAjkEEwECACMFAlMZcEICGw8HCwkIBwMCAQYVCAIJCgsEFgIDAQIeAQIX
gAAKCRDgeMiuv/IyzzaGEACiYWINH5utgquhNPIGl8oPXQwi3cdHbLROXk9s8K5j
umxO3qyzrZuag+M39eKrDOgMTteLcCuJV+9sgdmSJHsLuH9o9/PPwaKHsY995C0Y
5ZRsvABRQbHoOJPsdq136gH2Z0kW/RJ2fqQfNrDiqyPJpWTkrnnRZF2XU8OlIAq+
BsyeVqxOiht1vMIz2TX/LanbP6leas7Wah1GRuzhd68+NCyCUQJ4bnBDv6cbGwXR
Vi7kOOvXYoTilCENdbSuYfGWrq7z54DrefjTP3+0Y/YTWwUQr/yvXi915UCDVU+T
6jaqCwtqmezr1VjkMrFQOOrOY7jWmYo4AwQfr4hW9iLdiggr6bPmz0YRfT83a9r9
Z+SmU4zuLWmmJXARiUGBwhXUmyqFQa1yjCVI+50uW8Wx3iDot9qiO7gSB878Zq1s
Ktt3EXolTDGgpVIxZ78do42X02wD8gwGGOdDU3Dzywjy3qcIbVWreuT8tEvCU+Wx
w0TGzeoBLcHezhLEbaAOmE5jAmKPL9EbRQBGS1nV3uwzW24vu9ftNqmseYXC2afW
DCulmUHHAQEfleJA/mKii2mYV7Yxclib81+EzkzJBPijgUJBN9A1PxqliF8ZDXF/
h/jQomASoDBAL8VWo7qwTQlc5CZKZ6xnUZGdUU9lFBmnclw0A6PrMBaZjm1zeKJr
1Q==
=7M1T
- -----END PGP PUBLIC KEY BLOCK-----
</PGP_Public_Key>
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

<?xml version="1.0"?>

<!-- Seller's NYM -->
        <nym_id> ALICE-NYM-ID-HASH </nym_id>

<!-- Contract Nonce -->
	<contract_nonce> XXXX-YYYY-123456 </contract_nonce>

<!-- Bitcoin Pubkey -->
	<btc_addr> 03d728ad6757d4784effea04d47baafa216cf474866c2d4dc99b1e8e3eb936e730 </btc_addr>

<!-- Merchant Data -->
	<asset_name> 16 Pound Watermelon </asset_name>
	<asset_price> 0.01 BTC </asset_price>

<!-- Contract Expiration Date -->
	<contract_exp> YYYY-MM-DD TIME UTC </contract_exp>
	
<!-- Seller's PGP Key -->
<PGP_Public_Key>
- - -----BEGIN PGP PUBLIC KEY BLOCK-----
Version: BCPG v1.47

mQINBFMZcEIBEADJlq0oVgLfFDdW9WOBguskPdSSeAfHe4s9w8QlmRuO/Zj548gK
fofbM84rtP3rHSOSkeOTsu5GwDt48V/md6gyJ69BTZJkJ6qmxFtGaWVRLP/UD4ma
vW4EAn3PvWY6X7Z8x36U3j2I6vknH1Ufu5Dh5qvQC3WsMliul9ZxlJQZ1/TkQE+q
I/gBPRmsMFZ/xV2VOEjMtM3qOPoemhYFzU39/ra0isk81sXrotySkvWw6zsrx8Nr
kBaw9mxhs0kumF06AfKSrBjyt/FIdbJaWtNrCdxJ+NMfzQUHmq9bzpBI2VpNJzFQ
I4WlO8eRYDS1Z88VxXOjMZchd70JfNNWcXwCUeOA/HUgHO4tWczvb/5/C5pfZRKu
DqfOLntcMEzpPxbhAbXvU+K5TK394SGgu9ioXl3rdrFj1B1EBPH2BfnOdwCiOOr5
ccWVPUHdG34i4D98ARgeqEDxq9/WZwq8FG9rgSszqkmnGQtSZxz8aoW1kU1h1SQu
mqs2ZUrEoLGACkNg16kRq2z7RBLc4MAm3/GW3ygeEFQxK0PMief0X2+l0oVo7a0A
RMLLLx4ckuoX3DIJvBegFPvlp0rO3JihdzNmCqIBTDok7D0k2NiQsm3WDJHAYB+8
G4ruHVPAOzPNxz5krF+u71jcWmZKO4FRAcXCrWTQCku7wLyzOF80sVEDlwARAQAB
tGNEciBXYXNoaW5ndG9uIFlhbWFuZHUgU2FuY2hleiAoMjAxNCBLZXlwYWlyIGZv
ciBuZXcgZW1haWwgYWRkcmVzcykgPHdhc2hpbmd0b24uc2FuY2hlekBvdXRsb29r
LmNvbT6JAjkEEwECACMFAlMZcEICGw8HCwkIBwMCAQYVCAIJCgsEFgIDAQIeAQIX
gAAKCRDgeMiuv/IyzzaGEACiYWINH5utgquhNPIGl8oPXQwi3cdHbLROXk9s8K5j
umxO3qyzrZuag+M39eKrDOgMTteLcCuJV+9sgdmSJHsLuH9o9/PPwaKHsY995C0Y
5ZRsvABRQbHoOJPsdq136gH2Z0kW/RJ2fqQfNrDiqyPJpWTkrnnRZF2XU8OlIAq+
BsyeVqxOiht1vMIz2TX/LanbP6leas7Wah1GRuzhd68+NCyCUQJ4bnBDv6cbGwXR
Vi7kOOvXYoTilCENdbSuYfGWrq7z54DrefjTP3+0Y/YTWwUQr/yvXi915UCDVU+T
6jaqCwtqmezr1VjkMrFQOOrOY7jWmYo4AwQfr4hW9iLdiggr6bPmz0YRfT83a9r9
Z+SmU4zuLWmmJXARiUGBwhXUmyqFQa1yjCVI+50uW8Wx3iDot9qiO7gSB878Zq1s
Ktt3EXolTDGgpVIxZ78do42X02wD8gwGGOdDU3Dzywjy3qcIbVWreuT8tEvCU+Wx
w0TGzeoBLcHezhLEbaAOmE5jAmKPL9EbRQBGS1nV3uwzW24vu9ftNqmseYXC2afW
DCulmUHHAQEfleJA/mKii2mYV7Yxclib81+EzkzJBPijgUJBN9A1PxqliF8ZDXF/
h/jQomASoDBAL8VWo7qwTQlc5CZKZ6xnUZGdUU9lFBmnclw0A6PrMBaZjm1zeKJr
1Q==
=7M1T
- - -----END PGP PUBLIC KEY BLOCK-----
</PGP_Public_Key>
-----BEGIN PGP SIGNATURE-----
Version: BCPG v1.47

iQKBBAEBAgBrBQJThXbMZBxEciBXYXNoaW5ndG9uIFlhbWFuZHUgU2FuY2hleiAo
MjAxNCBLZXlwYWlyIGZvciBuZXcgZW1haWwgYWRkcmVzcykgPHdhc2hpbmd0b24u
c2FuY2hlekBvdXRsb29rLmNvbT4ACgkQ4HjIrr/yMs+evQ//cYOiI7PTqe8XgDRX
hxD+udw94HD/7qXoZOI2R2NsftYpnpEBcY0A0VVp5G7pjXbwfBQjeg+5xOMk0OCK
Z+JkMSLqqIjV6lMP8dK9LzVjYbITc1f5M2KcpureOiK9GsZWVGykk1JzyuB/HIds
UNvRtaj/gwgv0O9+e/gglxj8UaeXIjaIwXocUjrRqeSCQzIjwCTv2a6uJEF8pDZ8
w65Xftwfn/gVvjBNlHetYRSJuynSKNwHG7u26tkihXbcvEnN24wOoPozQhWT2WbS
3zbjE+WjXjOGHjuAd/u5fdezTzG26BwSb0jahgvLwr+DvaOH5HX3jDtpQH5Vi8p1
ULW9dVeAX7ZHC//as0IY+6uuhLBy7+HlIzmn2ka63ML7Kqk+p9Uf1mImJ3PXmjvb
EyGYDpDtkfIKWJvM+UB6eiZKOG1VCAZjKHj9O8IgCTfT4fViu0GmjHYeOGdj+U6e
3dQzGqOYc/Ow4kXKQMM2FGpRp+85Arj9HEoUyPWNf6FDKKclbeBAKMJX99SNdwsi
ZX9YNFFPguwsoztYyWQGfhQItzUxfnsBFn4JvU6LyHI/orbzmtUSR4qFHKPpTRmI
BYDcVMMAv/u1eXOL8zd43kLcD0qp551FRjHVPhuOcu1R7tPkhdKirlZ4anbaEBMA
fdUl5j/whtLQ7afe3zsQ+9R4rpA=
=zW6Y
-----END PGP SIGNATURE-----
```

The SHA1 hash of this contract is ```4cb658abd0ed7cd1a0531a5f1e839638a8d22d93``` and can be used as the filename and/or tracking number of the contract.

## Buying a Contract on *OpenBazaar*

The process for buying a contract is summarised by the following steps (note: signing is done on the client side, following the assumption that the buyer/seller's keys are stored locally or recoverable from a seed similar to DarkWallet):

```
1. The buyer digitally signs the seller's contract and sends it back to the seller
	- The buyer appends the following data to contract before signing:
		1. Buyer's nym
		2. Contract nonce
		3. Buyer's bitcoin pubkey (for multisig transactions)
		4. Delivery address of the buyer
		4. Buyer's PGP public key
	- Filename is the hash of the contract
2. The seller agrees to the transaction by digitally signing the buyer's version of the contract and sending the contract to 1) a potential arbiter, and 2) the buyer
	- Filename is the hash of the contract
3. The arbiter agrees to mediate the transaction by digitally signing the contract AND creaties a 2-of-3 multisig address
	- The arbiter's appends the following data to the contract before signing:
		1. Arbiter nym
		2. Contract nonce
		3. Arbiter's bitcoin pubkey (for multisig transactions)
		4. Arbiter's PGP public key
		5. Generated multisig address from the buyer, seller and arbiter's pubkeys
		6. Redemption script of the multisig address
	- Filename is the hash of the contract
4. The arbiter sends the final version of the triple-signed contract, with a multisig address, to the buyer and seller
	- The triple-signed contract represents the final version of the contract that all parties have agreed to
5. The buyer sends the contractually required amount of bitcoin to the multisig address.
6. The seller packages and ships the good to the buyer's address indicated in the triple-signed contract
7. Upon successful arrival of the goods, the buyer sends a digitally signed 'closed' contract to the seller and arbiter:
	- The buyer appends the following data to the triple-signed contract before signing:
		1. Message indicating that the goods have arrived
		2. Multisignature transaction script
		3. Buyer's signed multisignature transaction script
8. The seller verifies the multisignature transaction script in the 'closed' contract, signs the script and broadcasts the transaction to the bitcoin network for release of funds to the seller's bitcoin address
```
Using this process, the terms and conditions of the contract cannot be disputed and are impossible to forge. This leaves any disputes regarding the contract concerning to: 

1) Whether the goods have arrived or not
2) Whether the multisignature transaction has been signed by the buyer (if not, the arbiter can be called upon to do this)

## Reducing Contract Size

To reduce the overall size of the contract at each stage of the process, the next individual in the contract's iteration can sign the hash of the previous version of the contract.

For example, the buyer in step (1) can format the contract the following way:

```
<?xml version="1.0"?>

<!-- Seller's Contract Hash -->
	<contract_hash> 4cb658abd0ed7cd1a0531a5f1e839638a8d22d93 </contract_hash>

<!-- Buyer's NYM -->
	<nym_id> BOB-NYM-ID-HASH </nym_id>

<!-- Contract Nonce -->
	<contract_nonce> XXXX-YYYY-123456 </contract_nonce>

<!-- Bitcoin Pubkey -->
	<btc_addr> 03d728ad6757d4784effea04d47baafa216cf474866c2d4dc99b1e8e3eb936e730 </btc_addr>

<!-- Bitcoin Pubkey -->
	<delivery_addr> 1060 W Addison St, Chicago, IL 60613, United States </delivery_addr>

<!-- Buyer's PGP Key -->
<PGP_Public_Key>
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: Mailvelope v0.8.2
Comment: Email security by Mailvelope - http://www.mailvelope.com

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
=dDLn
-----END PGP PUBLIC KEY BLOCK-----
</PGP_Public_Key>
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v2.0.22 (MingW32)

iQIcBAABAgAGBQJTgzDXAAoJEKnOFXGYSKNN1e8P/1LRDhBLB4czvFV0t7roRQyU
qAS3jCkag7rabTU5zxb2Ld2vzJrl1aCD0VLqaLdc3++1vyhgOguY2wl9t0xoBKcf
zfUxJ/H0o//DtuWajFLnaQYyXB/LBuobSgSa0Tm26dZhAgJvFXGs6sny05ZVk9le
YbnsGUQh0B/zl3X/mhT3F6iFq1QRQ4jZj1ka1U/HzMFo7scpLEG3G003vEhwQa/Z
SXlkGuCJ7s0CjJ6qRmc9HPRcd5qA/2AHsAVF5HywgYXYqze8QFscUGhn/kO3//1Z
1I0u1v8FHuHSY/r/wHDZymJ5dYgndEPgzUrzvZStbswN3NtLVNdv6DRhGi+/xFRC
tZ87ys3OD+1cFjCd/wSTamAlTj99PHJLYuxX6gMYfTnj41JJADnfUeMa2Fw/qQg9
B3wWDXKIvs/xb4TzIJHKykBIZ5jjKGMweysD4iMbHkpSN/xEaWhM8hDAQ1nU1TjO
ecERcMLNM/oTa+RleynGXONaVG+24XwkC7gyl8fWdfFI9cfaICLHpcksRFWjkTkD
Z85QRlyzCUp1xK54hn3YNUKwibeOYHBdSqj3DYtCFdFD9A6QWYS+CGqlPLKbkjQQ
fgV7t+6hJjVztSeZiUzZDLDDGn978j8yTGi/5fQJsgbxO6cdPCAf7qKMX/4vK2g3
excS0w19X3r6nX+N6/+x
=YNf7
-----END PGP SIGNATURE-----
```

For even later iterations of the contract, a running tally of the previous hashes can be made in the contract field. For example:

```
<!-- Seller's Contract Hash -->
	<contract_hash> 4cb658abd0ed7cd1a0531a5f1e839638a8d22d93 </contract_hash>
	<contract_hash> 3f295f95f4a9abb0dba2cdb026ea551f0fa91507 </contract_hash>
```

There is also some flexibility in the naming of this field for clarity and simplicity:

```
<!-- Contract Chain -->
	<seller_signed_contract_hash> 4cb658abd0ed7cd1a0531a5f1e839638a8d22d93 </seller_signed_contract_hash>
	<buyer_signed_contract_hash> 3f295f95f4a9abb0dba2cdb026ea551f0fa91507 </buyer_signed_contract_hash>
	<double_signed_contract_hash> ... </double_signed_contract_hash>
	<arbiter_signed_contract_hash> ... </arbiter_contract_hash>
	<closed_contract_signed_hash> ... </closed_contract_signed_hash>
```

## Summary

In conclusion, using Ricardian Contracts for buying and sellings goods on *OpenBazaar* is an effective means of managing risk and minimising disputes on a pseudonymous peer-to-peer market, thought its use of iterative key signing and checksum hashes at each stage of the contract's execution.
