---
title: Coldie auctions and NFT auction design
categories:
- crypto
- nfts
- auctions
---
  
I've heard the term "Coldie auction" mentioned in cryptoland a few times, but I didn't know much about its history. I know it best as the auction model used by [Foundation](https://foundation.app/), but it dates back to a manual process run by the artist [Coldie](https://superrare.co/coldie), who has been selling cryptoart NFTs since 2018. His preferred platform [SuperRare](https://medium.com/superrare/how-superrare-timed-auctions-work-a351058a6120) added native support for coldies in late 2020. 

The basic mechanics:

* 24-hour timed reserve auction
* Auction begins when first bid is placed
* In Coldie's original model, any bid reset the 24 hour clock.
* On Foundation, if a bid is placed in the last 15 minutes, the auction is extended by another 15 minutes

I believe this would be taxonomized as a `timed reserve auction with bid-extension` ? I'm not an auctionologist, but I do know that [constraints breed creativity](https://twitter.com/aweissman/status/1274819313556471810), and I am a sucker for overanalyzing game designs.

![Example of Coldie promoting one of his 24 hour reserve auctions](https://dl.dropboxusercontent.com/s%2Ftey7wo55bf8e1ka%2FScreen%2520Shot%25202021-03-25%2520at%252009-44-09%2520Coldie%2520on%2520Twitter%2520RESERVE%2520PRICE%2520REACHED%2520I%2520Remember%2520Live%2520Music%252001%252011%2520on%2520SuperRare%2520Current%2520bid%25208%2520ETH%2520by%2520jonathan%252024h%2526%2520.png)
_https://twitter.com/Coldie/status/1365737081012580353_

On Rarible, OpenSea and a few other NFT marketplaces, auctions are often open-ended: buyers place bids, and the auction ends whenever the owner accepts a bid. The winning bid doesn't even need to be the highest bid! Zora has expanded on that by adding [sell-on shares](https://zora.engineering/auction), which allows a bidder to offer a % of the first secondary sale along with their bid. This provides a financial mechanic that (hypothetically) increases the value of the bid, but the Zora team also recognize the social motivations that go along with explicitly choosing a buyer:

> The identity of the bidder is a meaningful factor that gets taken into account by the owner when assessing bids. There is a wide range of cultural, reputational and identity factors that change the context and provenance of a token and therefore impact value. Who you sell to matters.

Using more traditional English-style "highest bidder wins" auctions with a time limit makes sense. It removes the flexibility of the choose-the-buyer mechanic, but it helps everyone manage expectations, creates some time-based hype pressure, and it's less work and cognitive overhead for the seller. 

Reseting the clock on new bids (`extended bidding`) adds an element of surprise and delight, and counteracts last-minute bid sniping, where buyers try to sneak in a high bid in the last seconds of an auction. 

Bid sniping is nothing new, but it is especially complex on Ethereum and other blockchains. The gas fee auctions and inconsistent block formation make timing a bid unreliable. Extending the bid window ensures the seller will get the maximum amount that bidders are willing to pay, and not just the last bid that snuck in. 

![Example of bid patterns on eBay](https://dl.dropboxusercontent.com/s%2Fo2konep1zl9mxeu%2FScreen%2520Shot%25202021-03-25%2520at%252009-59-12%2520view.pdf%2520%2528page%25208%2520of%252032%2529%2520.png)
_Excerpted from "A Look at the Game Theory of Online Auctions", O'Regan 2005[1](https://dlib.bc.edu/islandora/object/bc-ir:102332)_

I assume Coldie's original "each bid extends by 24 hours" choice was in part because there weren't nearly as many NFT bidders out there as there are today, so letting an auction extend for another day made sense.

Foundation using a 15-minute bid extension creates a "nail-biter finish" which I think was beautifully captured by the [Nyan Cat auction livestream](https://www.twitch.tv/videos/947013029), in which PRguitarman and the Foundation staff were streaming for hours longer than they expected and freaking out as each new bid reset the clock:

https://dl.dropboxusercontent.com/s%2Fnq51pub35kw8wz1%2FImage_DcerrvLkEF.png

Coldie was running this all manually, which I imagine was a lot of work. In Dec 2020, SuperRare namechecks Coldie while announcing their support for [timed reserve auctions](https://medium.com/superrare/how-superrare-timed-auctions-work-a351058a6120), which is one of the first mentions of "Coldie auction" I could find on ~~Google~~ DuckDuckGo.

> The new Reserve Auction system is partly inspired by the “Coldie Method,” pioneered by artist Coldie in which a reserve price triggers a 24 hour auction, which can be extended by bids near the end of the auction. (Those that are technically-minded might even find a _Coldie_ reference on-chain somewhere in the smart contracts 😎).

And the artist seemed grateful for it! 

> Now I wont have to set an alarm for the middle of the night like I used to when doing manual Coldie Method auctions to accept a bid at the correct time!

https://twitter.com/Coldie/status/1336188554750304256

![Coldie is glad to not wake up in the middle of the night to check auctions](https://dl.dropboxusercontent.com/s%2Fai7ozf5b4o1pjc6%2FScreen%2520Shot%25202021-03-25%2520at%252009-47-59%2520Coldie%2520on%2520Twitter%2520Its%2520amazing%2520this%2520timed%2520auction%2520is%2520real.%2520Now%2520I%2520wont%2520have%2520to%2520set%2520an%2520alarm%2520for%2520the%2520middle%2520of%2520the%2520night%2520like%2520I%2520%2526%2520.png)

Lastly, using hours and minutes in a crypto auction is inherently problematic. Blockchains operate on [blocks not clocks](https://docs.helium.com/blockchain/mining/), and smart contracts have no knowledge of time. But telling people "auction ends at block #1,275,246" instead of "auction ends in 24 hours" doesn't exactly roll off the tongue.

Happy bidding!

Thanks for [Denis Nazarov](https://twitter.com/Iiterature/) for feedback and introducing me to the term originally.
