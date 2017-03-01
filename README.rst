weekdays
========

Library of useful date functions, specifically relating to the working week.

Why?
----

Standard date function generally only consider dates and days as abstract concepts, but when
you are dealing with human beings there are some semantic issues that these libraries don't
cover - the concept of "Monday morning", or "next Thursday", for example.

We (YunoJuno) spend most of our time dealing with weeks, and these are some of the things we need:

* The week in which a given date exists (Mon-Sun)
* A week, as a list of dates, minus weekends
* The first day of a week containing a date (e.g. next Monday)
* A week, as a list of dates
* The last day of the week containing a date
* The last working day of the week
* The number of working days between two dates
* The number of weekend days between two dates
* A week (as a list of dates) offset from a given date (e.g. next week)
* Next week (as a list of dates)
* Last week (as a list of dates)
* Next working day
* Previous working day
* The list of dates in a given month
* The list of working days in a given month

And so on.

We currently use [python-dateutil](https://pypi.python.org/pypi/python-dateutil),
glued together with some custom functions, but it's time for an upgrade.

How?
----

The package [isoweek](https://pypi.python.org/pypi/isoweek) looks like a great start:

.. code:: python

 >>> from isoweek import Week
 >>> Week.thisweek()
 isoweek.Week(2014, 21)
 >>> Week.thisweek().monday()
 datetime.date(2014, 5, 19)
 >>> Week.thisweek().days()
 [datetime.date(2014, 5, 19),
  datetime.date(2014, 5, 20),
  datetime.date(2014, 5, 21),
  datetime.date(2014, 5, 22),
  datetime.date(2014, 5, 23),
  datetime.date(2014, 5, 24),
  datetime.date(2014, 5, 25)]

The intention is to wrap this to provide the additional functionality described above.
