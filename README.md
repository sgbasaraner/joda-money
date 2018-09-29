Joda-Money
----------

Joda-Money provides a library of classes to store amounts of money.

Joda-Money does not provide, nor is it intended to provide, monetary algorithms beyond the most basic and obvious.
This is because the requirements for these algorithms vary widely between domains.
This library is intended to act as the base layer, providing classes that should be in the JDK.

As a flavour of Joda-Money, here's some example code:

```java
// create a monetary value
Money money = Money.parse("USD 23.87");

// add another amount with safe double conversion
CurrencyUnit usd = CurrencyUnit.of("USD");
money = money.plus(Money.of(usd, 12.43d));

// subtracts an amount in dollars
money = money.minusMajor(2);

// multiplies by 3.5 with rounding
money = money.multipliedBy(3.5d, RoundingMode.DOWN);

// compare two amounts
boolean bigAmount = money.isGreaterThan(dailyWage);

// convert to GBP using a supplied rate
BigDecimal conversionRate = ...;  // obtained from code outside Joda-Money
Money moneyGBP = money.convertedTo(CurrencyUnit.GBP, conversionRate, RoundingMode.HALF_EVEN);

// use a BigMoney for more complex calculations where scale matters
BigMoney moneyCalc = money.toBigMoney();
```

Users are reminded that this software, like all open source software, is provided
on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND.

Joda-Money is licensed under the business-friendly [Apache 2.0 licence](https://www.joda.org/joda-money/licenses.html).


### Documentation
Various documentation is available:

* The [home page](https://www.joda.org/joda-money/)
* The helpful [user guide](https://www.joda.org/joda-money/userguide.html)
* The [Javadoc](https://www.joda.org/joda-money/apidocs/index.html)
* The change notes for the [releases](https://www.joda.org/joda-money/changes-report.html)


### Releases
[Release 1.0.1](https://www.joda.org/joda-money/download.html) is the current release.
This release is considered stable and worthy of the 1.x tag.
It depends on Java SE 8 or later.

Joda-Money does have a *compile-time* dependency on Joda-Convert, but this is not required at runtime
thanks to the magic of annotations.

Available in the [Maven Central repository](https://search.maven.org/search?q=g:org.joda%20AND%20a:joda-money&core=gav)


### Support
Please use GitHub issues and Pull Requests for support.


### Release process

* Update version (README.md, index.md, changes.xml)
* Commit and push
* `mvn clean release:clean release:prepare release:perform`
* `git fetch`
* Website will be built and released by Travis
