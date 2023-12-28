---
layout: post 
title: "Self-hosted Bitwarden with Yubikey"
date: 2022-03-20 22:20:28 -0400
categories: uncategorized
---

I have been recently migrating from Lastpass over to a self hosted version of Bitwarden for my password management.

When I went to add my Yubikey 5 NFC as my MFA token, I was getting an error after pressing the button for registration:

```
An error has occured
An unhandled server error has occured
```

It turns out that Yubico requires adding an API key to your Bitwarden instance to work. Go over to https://upgrade.yubico.com/getapikey/ and set this up by entering your email address and pressing the button on your yubico key. This will give you a Client ID and Secret key value.

In your onpremises bitwarden instance, go to your bitwarden directory and edit bwdata / env / global.override.env

There, you'll find two values that you need to replace with the ones you got from the yubico site:

```
globalSettings__yubico__clientId=REPLACE
globalSettings__yubico__key=REPLACE
```

After modifying the entries, save the file and go back to your main bitwarden directory. Then, rebuild bitwarden like so:

```
./bitwarden.sh stop
./bitwarden.sh rebuild
./bitwarden.sh start
```

After that, the registration process should work.
