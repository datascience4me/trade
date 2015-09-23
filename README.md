trade: Tools For Stock Trading Applications.
============================================
Copyright (c) 2015 Rafael da Silva Rocha  
rocha.rafaelsilva@gmail.com  
http://github.com/rochars/trade


What is it?
-----------
trade is a Python module with simple functions and classes for the
development of investment applications in Python. It provides basic notions
of assets, trades, daytrades, cost deduction and functions related to
processing stock trading data.

You may use the trade module as a framework to create applications that
implement specific rules of stock markets around the world or use it "as is"
in any  application that requires the notion of buying stuff, selling stuff
and controlling how much you spent to buy and how much you profited from the
trades.


How can I install trade?
------------------------------
>> pip install trade


How can I use it?
-----------------
A basic example of trade in action:

```python
import trade

# create the asset that we are going to trade
asset = trade.Asset('Some asset')

# create the accumulator to accumulate trades with the asset
accumulator = trade.Accumulator(asset)


print accumulator.asset.name
#>> Some asset

print accumulator.quantity
#>> 0

print accumulator.price
#>> 0

print accumulator.results
#>> {'trades': 0}


# create a trade buying the asset
purchase = trade.Trade(asset=asset, quantity=10, price=2, date='2015-09-22')

# accumulate the trade
accumulator.accumulate_trade(purchase)


print accumulator.quantity
#>> 10

print accumulator.price
#>> 2.0

print accumulator.results
#>> {'trades': 0}


# create a new trade selling the asset
sale = trade.Trade(asset=asset, quantity=-5, price=3, date='2015-09-23')

# accumulate the new trade
accumulator.accumulate_trade(sale)


print accumulator.quantity
#>> 5

print accumulator.price
#>> 2.0

print accumulator.results
#>> {'trades': 5.0}
```

You may also use only the Accumulator and ignore everything else:
```python
import trade

# create the accumulator to accumulate trades with the asset
accumulator = trade.Accumulator('Some asset')


print accumulator.asset
#>> Some asset

print accumulator.quantity
#>> 0

print accumulator.price
#>> 0

print accumulator.results
#>> {'trades': 0}


# accumulate trade data
accumulator.accumulate(quantity=10, price=2, date='2015-09-22')


print accumulator.quantity
#>> 10

print accumulator.price
#>> 2.0

print accumulator.results
#>> {'trades': 0}


# accumulate new trade data
accumulator.accumulate(quantity=-5, price=3, date='2015-09-23')


print accumulator.quantity
#>> 5

print accumulator.price
#>> 2.0

print accumulator.results
#>> {'trades': 5.0}
```

Trade objects may include taxes and comissions that are considered by the
accumulator when calculating results.

The Accumulator can also log the accumulated trades and their specific
results.

There are more features, like rating and applying discounts automatically
to a group of trades, separating daytrades from common trades in a group of
trades, calculating the resulting position from a group of trades and so
on. Check the documentation and the examples for more information on how to
use the trade module.


What about compatibility?
-------------------------
the trade module is compatible with Python 2.7 and on, including Python 3.x.


License
-------
This software is licensed under the MIT license: https://opensource.org/licenses/MIT


Copyright (c) 2015 Rafael da Silva Rocha

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
