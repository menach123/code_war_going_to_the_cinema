
### <a href = https://www.codewars.com/kata/562f91ff6a8b77dfe900006e/train/python>Going to the cinema</a>

My friend John likes to go to the cinema. He can choose between system A and system B.
```
System A : he buys a ticket (15 dollars) every time
System B : he buys a card (500 dollars) and a first ticket for 0.90 times the ticket price, 
then for each additional ticket he pays 0.90 times the price paid for the previous ticket.
```
#Example: If John goes to the cinema 3 times:
```
System A : 15 * 3 = 45
System B : 500 + 15 * 0.90 + (15 * 0.90) * 0.90 + (15 * 0.90 * 0.90) * 0.90 ( = 536.5849999999999, no rounding for each ticket)
```
John wants to know how many times he must go to the cinema so that the final result of System B, when rounded up to the next dollar, will be cheaper than System A.

The function movie has 3 parameters: card (price of the card), ticket (normal price of a ticket), perc (fraction of what he paid for the previous ticket) and returns the first n such that
```
ceil(price of System B) < price of System A.
```
More examples
```
movie(500, 15, 0.9) should return 43 
    (with card the total price is 634, with tickets 645)
movie(100, 10, 0.95) should return 24 
    (with card the total price is 235, with tickets 240)
```


```python
from math import ceil

def movie(card, ticket, perc):
    tickets = card//ticket + 1
    check = tickets* ticket <= ceil(card + sum([ticket* (perc**(i+ 1)) for i in range(tickets)]))
    while check:
        tickets += 1
        check = tickets* ticket <= ceil(card + sum([ticket* (perc**(i+ 1)) for i in range(tickets)]))
    return tickets
```


```python
card, ticket, perc = 500, 15, 0.9
```


```python
start = card//ticket + 1

```


```python
check = start* 15 <= 500 + sum([ticket* (perc**(i+ 1)) for i in range(start)])
```


```python
while check:
    start+= 1
    check = start* 15 <= 500 + sum([ticket* (perc**(i+ 1)) for i in range(start)])
start
```




    43




```python
movie(100, 10, 0.95)
```




    24




```python
movie(500, 15, 0.9)
```




    43




```python

```
