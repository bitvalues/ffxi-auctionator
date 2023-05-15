# ffxi-auctionator

> A discord bot written for FFXI DKP auctions.

## Features

- **DKP auctions can be easily created and automated through discord** (which makes it easier for the officers to manage)
- **Last minute "ninja" bids are prevented by a configurable, automatic timeline extension**:
  -  For example, a bid ends at 12am EST and at 11:59:59pm EST, someone tries to "snipe" the item by adding a last minute bid. The `ffxi-auctionator` bot will automatically extend the timeline for another 3 minutes (the time extension is configurable) which will allow for people to respond to the last minute bid; the bot will continue extending the auction until no bids are received in the time extension and the item's auction will be closed to the highest bidder.
-  **Unattended bidding is possible by setting player-based automatic bid maximums**. This serves the purpose of letting the `ffxi-auctionator` bot automatically bid for you (in the event you cannot be available during the time an auction will close). This is accomplished through a simple command; something like `!auctionator bid auto 90` - which will indicate to the bot that you are willing to spend up to 90 DKP on the specified item; note -- the `ffxi-auctionator` bot will only ever bid in increments of 1. Conversely, automatic bidding can be disabled through a command like `!auctionator bid auto cancel` if you decided that you want to change your mind later.
-  Bidders can lock in their bids with a simple command like `!auctionator bid 23` which will bid 23 DKP on the current thread's item; a confirmation message is created by the `ffxi-auctionator` bot if the bid is valid (higher than the previous bid). Note - this also addresses the ability to prevent last-minute deletions of bids.

## How it works

Here's an example of how this might work:

The linkshell was farming Sky one night and a `Divine Log` dropped. You, or one of the officers, wants to auction this item off in discord so the linkshell members can farely bid DKP on the item. You want the `Divine Log` to start at 1 DKP minimum. You know that linkshell members need 2 days to bid on the item and you want the auction to close @ 9pm EST.

You simply perform the following steps:

1. Pick any channel in our linkshell discord and type the following command: `!auctionator new "Divine Log" 1 2 21:00`
2. The `ffxi-auctionator` discord bot will automatically create a new auction thread for members to bid on. It will also notify linkshell members that a new item is available for bidding.
3. The bot will wait for 2 days to pass and automatically close the auction by locking the discord thread so no members can bid on the item past 9pm EST.
4. You, or one of the other officers, manually adjust their DKP accordingly.
5. The item is then distributed to the highest bidder.

## Commands

### Create a new auction (requires elevated privileges)

`!auctionator new <itemName> <startingBid> <daysOpen> <closeTime>`

| Name | Type | Description | Default |
|:----:|:----:|:------------|:-------:|
| Item Name | `String` | The name of the item being auctioned | `""` |
| Starting Bid | `Integer` | The minimum number of DKP required to bid on the item | `1` |
| Days Open | `Integer` | The number of days that the auction will be remain open. Note: the item will always close on the last day. | `3` |
| Close Time | `Integer` | The time an auction will automaticallty be closed on the last day. | `21:00` |

### Cancel an existing auction (requires elevated privileges)

`!auctionator cancel <reason>`

| Name | Type | Description | Default |
|:----:|:----:|:------------|:-------:|
| Reason | String | The reason why the auction was manually closed | `""` |

### Bid on an item

`!auctionator bid <total>`

| Name | Type | Description | Default |
|:----:|:----:|:------------|:-------:|
| Total | Integer | The number of DKP you are willing to bid on an item | `n+1` |

### Auto-bid on an item

`!auctionator bid auto <maximum>`

| Name | Type | Description | Default |
|:----:|:----:|:------------|:-------:|
| Maximum | Integer | The maximum number of DKP you are willing to automatically bid on an item | `n+1` |


### Cancel Auto-bidding on an item

`!auctionator bid auto cancel`

### Getting help on how-to use the `ffxi-auctionator` bot

`!auctionator help`
