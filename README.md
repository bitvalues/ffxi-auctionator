# ffxi-auctionator

> A discord bot written for FFXI DKP auctions.

## How it works

Here's an example of how this might work:

The linkshell was farming Sky one night and a `Divine Log` dropped. You, or one of the officers, wants to auction this item off in discord so the linkshell members can farely bid DKP on the item. You want the `Divine Log` to start at 1 DKP minimum. You know that linkshell members need 2 days to bid on the item and you want the auction to close @ 9pm EST.

You simply perform the following steps:

1. Pick any channel in our linkshell discord and type the following command: `!auctionator new "Divine Log" 1 2 21:00`
2. The `ffxi-auctionator` discord bot will automatically create a new auction thread for members to bid on. It will also notify linkshell members that a new item is available for bidding.
3. The bot will wait for 2 days to pass and automatically close the auction by locking the discord thread so no members can bid on the item past 9pm EST.
4. You, or one of the other officers, manually awards the item to the highest bidder and adjusts their DKP accordingly.
5. The item is then distributed to the highest bidder.

## Commands

### Create a new auction

`!auctionator new <itemName> <startingBid> <daysOpen> <closeTime>`

#### Arguments

| Name | Type | Description | Default |
|:----:|:----:|:------------|:-------:|
| Item Name | `String` | The name of the item being auctioned | `""` |
| Starting Bid | `Integer` | The minimum number of DKP required to bid on the item | `1` |
| Days Open | `Integer` | The number of days that the auction will be remain open. Note: the item will always close on the last day. | `3` |
| Close Time | `Integer` | The time an auction will automaticallty be closed on the last day. | `21:00` |

### Close an existing auction

`!auctionator close <reason>`

| Name | Type | Description | Default |
|:----:|:----:|:------------|:-------:|
| Reason | String | The reason why the auction was manually closed | `""` |

### Cancel an existing auction

`!auctionator cancel`
