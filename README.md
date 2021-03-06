jqm-calendar
============

Simple iOS-style calendar plugin for jQuery Mobile for both showing activities or picking dates. Events are showed with a bullet point on the date, and when the date is picked, the date appears with its summary in the list below.  

The options Object for the jqmCaldender takes several attributes, all of which are *optional*.

* `events` : An Array of Objects, which represent the events in the calendar. Events should have a `summary`, `begin` and `end`. The attributes names can be changed if needed, by setting creating an attribute: `settings.summary = "mySummaryIdentifier"`. You can let this point to another array in your program or access this array later on to inject new events to the calendar. Be sure to call a refresh when doing so.
* `months` : Labels for the months, this might be useful for using the jqm-calendar in other languages. The English values are set by default, so there is no need to set them.
* `days` : Same as for months
* `startOfWeek` : integer from 0 to 6 to tell jqm-calendar at which day to start painting the week (eg. sunday)
* `weeksInMonth` : How many weeks to show in a month. Normally this varies between 4 and 6, depending on the given start of the week and the start of the month. You can fix the amount of weeks by setting this attribute. Additional days will be filled with dates from the month before and after.

Some example that sets some attributes:

```js
$("#calendar").jqmCalendar({
   events : [ { "summary" : "Test event", "begin" : new Date(), "end" : new Date() } ],
   months : ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"],
   days : ["Su", "Mo", "Tu", "We", "Th", "Fr", "Sa"],
   startOfWeek : 0
}); 
```

Dates should be given as JavaScript `Date` Object, which takes several arguments:

```js
new Date();  // now
new Date(value); // Integer value of milliseconds since 1 January 1970 00:00:00 UTC
new Date(dateString); // Date string RFC/ISO
new Date(year, month [, day, hour, minute, second, millisecond]);
```

Listen to changes via the event:
```js
$("#calendar").bind('change', function(event, date) {
   console.log(date);
});
```

Change the current month by calling refresh:
```js
$("#calendar").trigger('refresh');
// or :
$("#calendar").trigger('refresh', new Date("2013-01-01"));
```
