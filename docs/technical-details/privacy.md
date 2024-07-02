# Privacy

## Short version
**We don't collect any personal information about you besides username and email.** We don't want it, we don't need it, and we don't have any use for it. We don't want to know who you are, where you are, or what you're doing. We just want you to have fun making games.

## What is collected on editor.turnroot.com and why
We do not track you in any way. We don't use cookies, analytics, tracking pixels, etc. We don't pull in any scripts from third parties (except for Stripe, to handle your payment information). We do not practice browser fingerprinting. The Editor is not connected to anything except the schema server.

The data stored is your game data. This is stored in a local database and is only accessible to you and the Turnroot team. We don't look at your data unless you ask us to, and we don't share it with anyone else. This is handled by the schema server, which is carefully locked down to disallow all connections and access except from the Editor.

You can verify all of this yourself very easily, as both the Editor and the schema server are open source. You can see exactly what data is being sent and received by poking around in the code.

None of your information is being sent to AWS, Google Cloud, or any other cloud storage system- both databases are local and encrypted. 

### Stripe data
To use the cloud editor, you must have an account. Creating an account stores your username, email, and password in a discreet local database, after encrypting them. Additional information is stored by Stripe:
- stripeCustomerId 
- stripeSubscriptionId
- paymentMethodId

All of that data is encrypted, hashed, and obfuscated. There is no way to determine anything about you, your computer, your browser, or your payment methods from that data. 

To summarize, each registered user has the followed encrypted, hashed, and obfuscated data stored:
- username
- email
- password
- stripeCustomerId
- stripeSubscriptionId
- paymentMethodId

### Browser permissions
We don't need or ask for any, with the possible exception of playing sound (your game will have sound and music, so that's necessary.) We don't use popups, location tracking, or anything else. I don't want to know anything about you except that you're having fun.

### Your email
You must provide an email as part of the registration process. We will never send you marketing emails, and we will only email you if you have an active subscription but you haven't logged in for a while or with other critical account information. We will never share your email with anyone else. 

## My recommendation
I highly recommend add-ons like Privacy Badger, uBlock Origin, and DuckDuckGo Essentials. They will help protect your privacy on the web. Turnroot Editor isn't going to abuse your privacy or track you- most other sites do. 

## Keeping your hard work safe
Making a game in Turnroot Editor is designed to be as easy as possible, but it's still going to take a while. You deserve for your hard work to be safe from accidents and from malicious actors. Especially if you plan on selling your game, it's extremely important that the game data is secured against cracking, hacking, and altering.

We use a propietary, closed-source input/output system for the Turnroot Engine. This is to prevent people from reverse-engineering the engine and stealing or altering your game data. The .turnroot file format is closed-source, heavily encrypted, and designed to withstand intense reverse-engineering attempts. See the [Licenses](../index.md#licenses) section for more information.

On the "accidents" side of things, we have a robust database backup system in place. 