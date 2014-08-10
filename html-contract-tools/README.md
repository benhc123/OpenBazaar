# HTML contract tools

The goal of the **HTML contract tools** is to create a multi platform, offline interface to build, read and manage OpenBazaar contracts.  At this stage during testing, we are relying on some CDN's for Bootstrap files for simplicity, though this will change in the future

Kudos to the guys at http://openpgpjs.org/ for the javascript to manage the PGP keys, etc.

## Usage
Download the entire contents of this directory, and run the index.html file.  This should open in your preferred browser, though it is recommended you run this in Chrome or Firefox due to compatibility issues with the OpenPGPJS javascript.


## Some of the workings.

As the definition of what a contract in OpenBazaar should contain is still fairly fluid, this interface has been and is being built to be able to adapt to future needs of contracts.  With this in mind, we plan to create many small functions in javascript to run the application, so that as the scope of openBazaar contracts change, the application can adapt relativly easily.

All fields in contracts are specified in a javascript array, with options for minimum length, maximum length, and regular expression validation to confirm the values a user inputs is valid data for the particular field.  For example, in the BTC address field, the regular expression *^[13][a-zA-Z0-9]{26,33}$* forces the user to enter a valid Bitcoin Address.
