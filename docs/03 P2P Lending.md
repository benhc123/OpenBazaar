Peer-to-Peer Lending on *OpenBazaar*
===

![0](http://techfleece.com/wp-content/uploads/2013/02/Tyrion-Lannister-1024x567.jpg)

## Preamble

Banks are centralised institutions that, among other things, offer credit to individuals, groups and corporations. Historically, banks were a nexus of borrowers and lenders, matching the *supply* of liquidity to the *demand* for credit. The primary role of a bank was risk management in the form of the due diligence required to assess if a potential borrower was a worthwhile investment. With the advent of nation-state money printing and fractional-reserve banking, whereby money is *lent into existence* and losses are publicly subsidized by inflation and bailouts, the traditional care of risk management for loans has all but been obiliterated.

Peer-to-peer (P2P) lending has emerged as a means to decentralise the oligopolistic hold that banks possess in every category for lending. While P2P lending is still in early days, regulatory pressure is mounting making P2P lending services using fiat dollars especially vulnerable to the legacy financial/political order. Using Bitcoin, this legacy threat is largely eliminated, but introduces new problems in the traditional approach of risk management. The purpose of this article is to suggest possible solutions to these problems and how they might be executed on a pseudonymous censorship-resistant marketplace like *OpenBazaar*.

## Ricardian Loan Contracts

As with other goods and services on *OpenBazaar*, the loan is drawn up as a [Ricardian-style contract](https://github.com/OpenBazaar/OpenBazaar/blob/master/docs/Ricardian-Contracts.md) that I will refer to as the **loan contract** for the rest of the article. The loan contract is initially written by the *borrower* and distributed/published on the *OpenBazaar* network, as the borrower is trying to convince the market to purchase their unmaterialized future good (a interest markup of the original loan amount).

Let us imagine a *borrower*, Bob, and a *creditor*, Alice:

#### Step 1: Bob creates a **loan contract**
The loan contract specifies that Bob wishes to exchange **110 mBTC in 1 year** for **100 mBTC now**. The interest rate is 10% p.a. The following fields are introduced in the **loan contract**:
```
1. Loan_amount: 100 mBTC
2. Loan_term: 1 year   
3. Interest_rate: 10% p.a.
4. Repayment schedule: 10 mBTC by the end of each month
```
Bob digitally signs the contract and publishes it to the network.

**Example Loan Contract**

```
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

<?xml version="1.0"?>

<!-- Borrower NYM -->
	<nym_id> BOB-NYM-ID-HASH </nym_id>

<!-- Node_ID -->
	<node_ID> XXX-YYY-123 </node_ID>

<!-- Loan -->
	<btc_addr> 03d728ad6757d4784effea04d47baafa216cf474866c2d4dc99b1e8e3eb936e730 </btc_addr>
	<loan_amt> 100 mBTC </loan_amt>
	<loan_term> 12 months </loan_term>	
	<interest_pa> 10% </interest_pa>
	<repayment_sched> 10 mBTC/month </repayment_sched>
	
<!-- Borrower PGP Key -->
<PGP_Public_Key>
- -----BEGIN PGP PUBLIC KEY BLOCK-----
Version: Mailvelope v0.8.2
Comment: Email security by Mailvelope - http://www.mailvelope.com

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
=dDLn
- -----END PGP PUBLIC KEY BLOCK-----
</PGP_Public_Key>
-----BEGIN PGP SIGNATURE-----
Version: BCPG v1.47

iQKBBAEBAgBrBQJTiJ8LZBxEciBXYXNoaW5ndG9uIFlhbWFuZHUgU2FuY2hleiAo
MjAxNCBLZXlwYWlyIGZvciBuZXcgZW1haWwgYWRkcmVzcykgPHdhc2hpbmd0b24u
c2FuY2hlekBvdXRsb29rLmNvbT4ACgkQ4HjIrr/yMs/A4Q//dkyzWsAJ/Gnjto1y
hVz78TKbs9zzgRKzo7db2rvQZb1gezVXrGIy4FGjcFOyqPQ9DQi4udkefimSi16T
elIE1VyCE/Y5oKXlzW0/fD0cT4nY5rrXY12TJQzoiFfusXpIIA22CkyGu9nQhdRF
QAO5o+Ggd2ANb3lMGR2sfgkgnPKYgl704YmGyJ+4wxG5k4G66HOs+hiif6NnzRjw
JFJPrYpTdCVp66xLZXT77nCE0OpqgHq2evXyV+OgOShn7QIb5NrXpHjfGgT9Z2im
iClZMPjrKshKdkwVn0q96OuwSHkbAW0IWeUqcMfZMgOodCmg//pR3HxO5GiyyxcD
5xbcr7EdJ931oCFl1FadeCbGfWfoOGhpebY+KZn7QU7wBizWHMy7eszb+0Rh+eUd
yE22NZrPOUNHaoYY+ohk+p0VIhM1QfOM/3dwhTQbmE/C0+X7MrosEWtzaY41w3k8
9b1sXQHw9GmuRAC/LRyPP/IpjIOKUxIBP6Y+wLZdgCYGHbOCWV79cDv9zt68t183
QeLuE85/HWxDVOgPHontRxC8TBnG4Xs8LuSxAWfO5sSQjNCDr9Tpfr5jFJIzu+pA
MVOloAxiEwpvG0HSo6f0VoSEbgvwUsERi9uXAHnu7rFLGKv/1rv7Gmm5lS5ULhHW
iLl5b3F2atDwSOyVTwXXHHkeo34=
=Fqvr
-----END PGP SIGNATURE-----
```

The resulting filename is labelled according to the SHA1 hash of the document: ```6127dbed6e218567de94dbd26e7c5fa350de3b9c```

#### Step 2: Alice accepts the **loan contract**
Alice agrees with the contract and appends the following data:

1. A schedule of repayment bitcoin addresses (i.e. an address for January, February etc)
  - There are an estimated 12 repayment schedules in the example, so Alice attached 12 unique addresses for Bob to send each repayment
2. A bitcoin address for the funds to be lent (with a signed message from that address for verification purposes)

If Alice wants to change the terms of part of the contract, she can write, sign and send a fresh contract to Bob. If Bob disagrees, he can simply ignore the contract, or sign it if the change in terms acceptable (e.g. Alice increases the interest rate to 11% p.a., or changes the schedule to fortnightly repayments). Note that this is the only stage where this can happen as once both parties have signed the terms of the contract, it is locked-in as far as the arbiter is concerned for dispute resolution purposes.

**Example of an Accepted Loan Contract**

```
<?xml version="1.0"?>

<-- Loan Contract -->
	<Loan_offer_hash> 6127dbed6e218567de94dbd26e7c5fa350de3b9c </Loan_offer_hash>

<!-- Lender NYM -->
	<nym_id> ALICE-NYM-ID-HASH </nym_id>

<!-- Node_ID -->
	<node_ID> AAA-BBB-123 </node_ID>

<!-- Loan Repayment Addresses -->
	<repayment_addr> 1Hmv2gUMqypH5FENoJ1bXkFbWJHXpYv4mr </repayment_addr>
	<repayment_addr> 1M8Jyac6j8PAN8P2s7SL64PDpTXGuQhVs4 </repayment_addr>
	<repayment_addr> 19eUSSLSjvqYK4XN7VC3SEKYhqDaXWGW9y </repayment_addr>
	<repayment_addr> 19eUSSLSjvqYK4XN7VC3SEKYhqDaXWGW9y </repayment_addr>
	<repayment_addr> 1LBggLaYNA2pXViT3xLSRcvBp2GGMaVZrp </repayment_addr>
	<repayment_addr> 1NoErV3DqskowS5ehb2t2Ru4DsQPSS4ePm </repayment_addr>
	<repayment_addr> 179zt3Tt2QNxDZcwQ8cxNNpF7PXDGouoCJ </repayment_addr>
	<repayment_addr> 1MHhhoahdAanHJx3JXxGTMqe2s5XKxgToS </repayment_addr>
	<repayment_addr> 1DyupVxmFcLW3MPTrZ8tyUEQXNFqgNAuXf </repayment_addr>
	<repayment_addr> 1DYNcXAe7nQR5YPKhFbrz1QWEfnJQJd5zR </repayment_addr>
	
<!-- Loan Funding Verification -->
	<addr_message_sig>
-----BEGIN-SIGNATURE-BLOCK-------------------------------------
Address:    1Cpbd5tKaDiXuChctbePpYjUz1PvRzVUiq
Message:    "I control the bitcoin in this address"
PublicKey:  04b728f56bdc4aa8eb213a08ac0a3a95f8eaf4150a988d8754
            e6973e5701418422d89373eb1f2c1125315eeddb7d7557902e
            5521a900a2b71e233441a2d333e304
Signature:  f51cd1645a779c5b2db27405e21a6347a6baec3d26b1e78701
            3c9a824b9ff4e94504c3ff07a116079064ff6f7bd5a508673d
            92be1835f6f47ea824f2b960f90c
-----END-SIGNATURE-BLOCK---------------------------------------
	</addr_message_sig>
	
<!-- Lender PGP Key -->
	<PGP_Public_Key>
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: BCPG v1.47

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
=nT6N
-----END PGP PUBLIC KEY BLOCK-----
	</PGP_Public_Key>
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v2.0.22 (MingW32)

iQIcBAABAgAGBQJTiKTQAAoJEKnOFXGYSKNNIPIP+wdUnfanAe80JedgYaU0P51z
feHkRrCbHxHCG9J+GM1++QoTcfxoKKatKcA+KtlEhCeNQnn4iiuurFEyyENbRkTn
nI2QaP/WKQ9yummS3lB7m927upBN/9hIdG8y1S3HZz0Dwi8DpZOv5ZwConKGzH71
RfzBJpPojzxkhL//J2JwWr6oInUiW/gDPJuXDVKXD+gJGwdhla7cbEeolfbS+C3E
QJ1HnxQsqfnWmr7Dz5FPZiygY5DQPvYge52iv42+tNZzggbOpLPkeLu30dUHzLvG
HT6/L+JYYDeIOV9Vt3XAS3xkRvChzJXk5XOSeq+BPdJJLVmucCMX5TueEBLw5ttF
rmRgjHEd9QgfZEIUOr0m1rRk4a5mQJhI3faFEWqrVlvOI/sIOE7JjnAlocrY4WqC
DbM7dTlVEHUbMxsJb+8PXGv4nQiP3hkyzlzYY8/8yMLjQZBTNhpspsWFGv3dmX+M
Jr/yEc7Zt9WBPQjbZV6KA5hUq6UeP9DscuB+gahUBybUdwy5kWId5Tm9xCdDhTmy
X/d56+9LYmIqRaMFTt7UFJ6zX9qXKu+6Wo59sSST4Aea0QcnSgdz7B6k1nWV0iNq
jo4UD8VcWCyjNmDSwJ+J3nqDz0FtlBZHsdYtXWiBg1P6aohPbMYomDS3V1S1Pnre
bJrs0OCKxkvB+1k7DvBw
=d3YQ
-----END PGP SIGNATURE-----
```

#### Step 3: Bob accepts Alice's offer and sends to the contract to the arbiter
Bob verifies that Alice has the funds and digitally signs the contract. Bob sends the contract to Alice (signifying agreement) and to the arbiter.

#### Step 4: Funds are transferred; repayment-receipt tracking begins (last signed receipt)
Upon receiving the signed contract from Bob, Alice transfers 100 mBTC to Bob's nominated bitcoin address. To keep track of repayments and the balance of the loan, Alice appends the balance of the loan to the contract, digitally signs it, and sends it to Bob and the arbiter. 

For every repayment, Alice adjusts the balance of the outstanding loan. The contract is digitally signed sent to the borrower and arbiter. If the lender fails to issue receipts for repayments, the borrower can issue a repayment receipt to lender and arbiter with the new balance. Irrespective of who issues repayment receipts, the entire process and balance is auditable by the arbiter via the blockchain and the 'last signed receipts'.

This process can continue until the loan has been paid in full and the outstanding balance is zero.

## Risk Management

### Part 1: Credit Ratings and Collateral

The process above has thus far described how the **loan contract** is created and processed for auditing purposes by the arbiter. However, it has not dealt with how **loan contracts** will be protected from fraud by bad actors on *OpenBazaar*. Traditionally, there are two major ways to manage risk for potential loans:

1. Assess the borrower's **credit rating**
2. Require **collateral** for the loan

##### Credit Rating

> an estimate of the ability of a person or organization to fulfill their financial commitments, based on previous dealings.

As a credit rating often involves an individual disclosing their income and previous financial dealings to the creditor and other third parties, the concept of a traditional credit rating is incompatible with the goals and purpose of *OpenBazaar*. New and innovative solutions are required assess the credit-worthiness of an individual in a pseudonymous marketplace.  

##### Collateral

> something pledged as security for repayment of a loan, to be forfeited in the event of a default.

A borrower must provide *collateral* to the creditor before a loan is approved. *Collateral* can be any good belonging to the borrower that has an equivalent value to the amount being loaned. In case of a credit default, the creditor can physically possess the *collateral* to recover their losses.

### Part 2: Web of Trust

In *OpenBazaar*, reputation management of your pseudonym (nym) is managed in a number of ways. Firstly, the pseudonym can have a value ascribed to it via a [proof of burn](https://en.bitcoin.it/wiki/Proof_of_burn). Effectively, this serves two purposes:

1. Inhibits Sybil attacks by promoting trade with *valuable* identities
2. Signals the level of risk associated with trade (e.g. selling a 10 mBTC good with a 1 mBTC nym is less risky than selling it to a 0.01 mBTC nym).

On the second layer, a bitcoin-otc style of [web of trust](http://bitcoin-otc.com/newsite/trust.php) allows peers to rate each other from -10 (Bernie Madoff) to +10 (Satoshi Nakamoto). The cumulative rating on the *web of trust* is another measure of risk other parties can consider before making a trade with you. Moreover, the network of peers and their corresponding rating also is a measure of the quantity and quality of that rating. Individuals creating 20 sockpuppets can easily be identified as a closed off web by viewing their trust graph, which is a visual representation of their trust relationships. Lastly, *web of trust* ratings aren't predicated on a trade, allowing existing trust networks to be translated into the system. The *web of trust* platform can be expanded to further differentiate between free and trade-based ratings to signal more information to other parties.

In the context of peer-to-peer lending, the *web of trust* can act as a form of credit rating.

### Part 3: Web of Credit

Taking the *web of trust* concept one step further, *OpenBazaar* can facilitate peers extending lines of credit to each other. If there is a successful trade between Alice and Bob, Alice may choose to extend a 5 mBTC line of credit to Bob. Bob can borrow this money at any time according to the prescribed conditions set by Alice. The funds can be kept in a 2-of-3 multisignature address, using an arbiter as a third signature. This line of credit can be publicly disclosed and audited by other peers. The aggregate of a pseudonym's line of credit becomes a powerful and informative risk signal for other peers, with risk being inversely proportional to the sum total line of credit.

The line of credit can be considered as collateral by a potential creditor, knowing that a pseudonym's line of credit can be called upon to satisfy a renumberation of second loan. For individual extending lines of credit, they have an opportunity to invest in successful and well-regarded trade partners.

### Part 4: Collateral as User-Created Assets

In *OpenBazaar*, collateral can be transferred by digitally signing possession of a user-created asset, represented by a Ricardian contract. Briefly, Jack may posses 0.1 ounces of gold and wants to exchange it for other goods and services on *OpenBazaar*. Jack writes a contract stating that he has possession of 0.1 ounces of gold. To sign ownership of that contract to another individual, Jill, Jack can create a fresh contract with the following data:

1. A encrypted copy of the old contract using Jill's public key
2. Updated ownership details (i.e. Jill owns 0.1 ounces of gold)

The new contract is then digitally signed with Jack's private key. Now, this entire process assumes that Jack actually has 0.1 ounces of gold behind the contract and is able to physically transfer the goods or their custody (if a third party, like a vault, is holding them). The burden of proof will be on Jack to demonstrate to Jill that contract is valid. Jack can also seek other highly rated (web of trust) third parties or arbiters to sign the initial contract after they are satisfied with Jack's proof.

Outside of the Ricardian contract model in *OpenBazaar*, user-generated assets from colored coins or other sources (Mastercoin, Counterparty, OpenTransactions etc), can also be offered as *collateral* for a loan.

### Part 5: Collateral and Distributed Collateralized Trusts

What if a user like Bob is unable to provide sufficient *collateral* for the loan due to either: 1) his wealth status living in a developing country, or 2) providing *collateral* in the traditional sense would reveal his pseudonym's identity?

One possible solution is for Bob to purchase *collateral* from a **distributed collateralized trust** or **dCT**. A **dCT** is a collection of users that pool a certain value of funds in essentially a term deposit. This term deposit serves as *collateral* for a loan in the event that the borrower defaults. In return for this risk, the borrower pays each member of the trust a fee that makes up the effective interest rate of the term deposit. Using the example thus far, Bob purchases 100 mBTC collateral from a 10 member **dCT** at the price of 10 mBTC. Under this arrangement, each member of the **dCT** risks 10 mBTC for a term of 1 year for a return of 1 mBTC (or roughly 10% p.a.), paid for in advance by Bob's fee

Alternatively, Alice could forgo Bob's collateral in favor of a 10 mBTC downpayment upfront. However, Alice will not be compensated if there is a default on the loan. This option could be viable if Alice routinely lends funds to Bob and extends to him a sufficient level of trust.

dCTs however, confer a number of advantages:

1. Overall level of risk is spread
2. Multiple layers of due diligence
	- Both the creditor and the dCT will need to evaluate the profitability of lending to Bob, decreasing the chances of spurious lending
	- The dCT can also examine the track record of the creditor, Alice, for their success in picking borrowers
	- The purpose of the loan can be interrogated, and if possible, funds can incrementally be released
3. Promotes liquidity
	- The creditor has, in effect, insurance in lending
	- The level of risk that is an obstacle for the lender is now lower than the level of risk for each member of the dCT, making relatively capital-intensive loans possible

A dCT is not necessarily appropriate for small-medium sized loans, as a borrow can crowd-source the loan as the level of risk is especially low. However, it will be up to the creditor to evaluate their level of risk tolerance and what steps they take to manage that risk.

## Summary

The concepts listed in this article are possible approaches of managing the risk of P2P loans on a pseudonymous network. This proposal is meant to serve as a primer for new and more innovative approaches to manage the risk of P2P lending on *OpenBazaar*.
