---
layout: default
---

> Monopoly - Stock Exchange is a Monopoly variant that adds stock manipulation and trading to the mix.
> Instead of only one player owning a company (property), now multiple players can own stock in it.
> The president is the player with a simple majority of stock in the company.
> Acquire the presidency in a block of companies and you've got yourself a monopoly.
>
> An electronic console keeps track of the proceedings.

Monopoly Stock Exchange, described by [boardgamegeek.com](https://boardgamegeek.com/boardgame/3065/monopoly-stock-exchange)

---

# Update dec 2020

Found it! [See here](https://warendorff.github.io/moose/data/result.md)

# About

Monopoly Stock Exchange is a boardgame accompanied with a small computer (displayed [here](https://boardgamegeek.com/image/133900/monopoly-stock-exchange)) which holds a lot of information and has to be passed around since all players want to see the status of their properties. Although this computer is not difficult to use, it fails to keep all the players informed about the game status. Entering changes and trading takes just a litle too long and therefore slows the game.

Reverse engineering the thing is the first (and most challenging) part of this problem. This page is used to explain the problem and provide information to those who can help solve this little mystery.

# The game

The board of Monopoly Stock Exchange (see [here](https://boardgamegeek.com/image/247141)) is almost the same as a regular game of Monopoly. It's the same board layout but the properties have company names, there are "Bull" and "Bear" cards (instead of "Chance" & "Community Chest"), plus taxes, free parking and the jail is still there. The first person to land on a given company can become the owner of the company by buying 5 shares (out of the 9 available). As long as he maintains a simple majority in stock he will retain presidency. If a player has presidency in all the companies of a given group/color he has formed a monopoly. With a monopoly the president is allowed to purchase offices/head offices (houses/hotels). Pretty familiar stuff.

Every company (property) is divided into 9 shares of which you receive 5 on initial acquisition. The remaining 4 can be bought by either the owner or the other players. Since rent is divided under the shareholders, it's a good idea to invest in a company you own (more income) or in a company you don't own in which case you pay less rent. The price of a share depends on:
- the company: Gillette (Mediterranean Avenue) is cheap, BT (Broadwalk) is expensive
- the amount of shares available: less available shares means more demand, so the price per share goes up
- monopoly: if all companies of the same color have the same owner, price goes up
- buildings: when you build houses, price per share goes way up!

As soon as you land on a property/company which is owned by another player, you have to pay rent. The rent you have to pay depends on:
- the company
- the amount of shares you have in this company: more shares means less rent
- monopoly
- buildings
Rent is divided equally under all shareholders, but you only collect this rent when you pass "Go".

The computer keeps track of all the shares, buildings and rent per player. By default the screen shows the streetnumber, buildings, shares available, player shares and the current share price.

# The goal

Figure out how the computer calculates the price per share and the rent to pay.

In order to do this, we need to know the variables and a lot of data (available below). Then it should be possible to reverse engineer the magic formula and we can create our own application. Instead of this little computer, each player can use a phone or tablet with a much better overview and easier control.

# What we do know

## Facts:

- Shares can be divided up to 6 players, but the amount of shares per player does not influence the value of the share. So when 6 shares are owned by 2 players, it doesn't matter if one player has 5 or 3 (and the other player 1 or also 3): the price per share is the same. Both the total amount of shares sold and the amount of players that own shares (of the same property) do influence the price though.

## Data:

An overview of the companies and their values is available [here](https://warendorff.github.io/moose/data/companies.md).

Sheets of raw data we extracted from the computer. On top there is a table representing the data-structure. For example, if we want to know the value per share of the company nr 1 with 2 buildings when 7 shares are owned by 4 people, we look (here)[https://warendorff.github.io/moose/data/1.md] and find a value of 47.

- [Company 1](https://warendorff.github.io/moose/data/1.md)
- [Company 1 (with a monopoly)](https://warendorff.github.io/moose/data/1mp.md)
- [Company 6](https://warendorff.github.io/moose/data/6.md)
- [Company 10](https://warendorff.github.io/moose/data/10.md)
- [Company 13](https://warendorff.github.io/moose/data/13.md)
- [Company 16](https://warendorff.github.io/moose/data/16.md)
- [Company 19](https://warendorff.github.io/moose/data/19.md)
- [Company 22](https://warendorff.github.io/moose/data/22.md)

# How to help

If you know the formula or have suggestion, please [create an issue](https://github.com/warendorff/moose/issues).

We found another github project called the "[MSE-Compute-Emulator](https://github.com/BenDutton/MSE-Compute-Emulator)" who tried to solve the same formula. It's a good start, but not complete. Thanks for pointing in the right direction though!

Of course, the resulting application will be available on github too.
