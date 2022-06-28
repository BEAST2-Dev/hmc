---
layout: site
title: BEAST 2 Help Me Choose Standard  Tip dates
tags: []
---

## Standard  template -- tip dates

By enabling tip dates, one or more taxa can be specified to have dates back in time. 
This enables estimating root dates when sampling times are sufficiently far appart (at least 10% of root height between oldest and newest taxon, but preferably more to reduce uncertainty in root height estimate).
You should use this when the taxa are not all sampled at the same time.


## `numerically as` vs `as dates with format` 

Choose `as dates with format` when you have calendar dates, which is quite common with viruses or other pathogens. Otherwise, choose `numerically`.

## Radio button `numerically` selected

Choose `Before the present` when you have node ages, e.g. when dealing with ancient DNA. All present nodes are set at height 0, and no node is supposed to have height (=age) less than zero.
Node calibrations set up in the priors panel will be interpreted as clade heights (=age) with respect to the present.

Choose `Since some time in the past` if tip dates are relative to a fixed date in the past, e.g. 0CE or 2000CE.
Node calibrations will be interpreted as clade heights (=age) with respect to that fixed date. 
Be aware that non-negative distributions like log-normal, and (inverse) gamma will be with respect to the TODO

## Radio button `as dates with format` selected

The drop down box next to the `as dates with format` radio button provides various date formats. 
This automatically puts all tip dates with respect to 0CE, and node calibrations are interpreted to be relative to 0CE.
Be aware that non-negative distributions like log-normal, and (inverse) gamma will be with respect to the TODO

If this option is selected, a format string  will be used to convert the entries in the second column of the table into heights (ages in years before the most recent sample) in the  second column.

The format string may be any combination of the following special characters 
and other delimiting characters such as '-' or '/'.

  Symbol  Meaning                     Examples
  ------  -------                     --------
   G       era                         AD; Anno Domini; A
   u       year                        2004; 04
   y       year-of-era                 2004; 04
   D       day-of-year                 189
   M/L     month-of-year               7; 07; Jul; July; J
   d       day-of-month                10

   Q/q     quarter-of-year             3; 03; Q3; 3rd quarter
   Y       week-based-year             1996; 96
   w       week-of-week-based-year     27
   W       week-of-month               4
   E       day-of-week                 Tue; Tuesday; T
   e/c     localized day-of-week       2; 02; Tue; Tuesday; T
   F       week-of-month               3

(The table above is an extract from the documentation for the DateTimeFormatter class which is used by BEAST to parse dates.)

Symbols in the above table representing numeric quantities (e.g. day-of-month  and month-of-year) may be repeated to allow for zero-padding.  For instance, the format string "d/m/y" will match dates such as "1/3/2004" while "dd/mm/y" will match "01/03/2004".  In addition, use "yy" to match the short form of the year.

Be aware that in all cases it is necessary that the format chosen be able to pinpoint a  single day in the calendar. For instance, "d/m" is not a valid format string as it doesn't allow days to be uniquely identified.

## Specifying tip dates

Tip dates can be entered in the second column, after the taxon name. 
If there are many taxa, a more efficient way is to use the `Auto configure` button that allows setting up patterns to match with taxon names.
This is useful when the taxon name contains tip date information, for example in the format `taxon|year-month-day`.

It is also possible to load tip dates from a tab delimited file via the `Auto configure` button.
The file must contain one row per taxon, with each row containing the taxon name and the trait value separated by a TAB (not a space!) character.

For instance, a file specifying the ages of three taxa named taxonA, taxonB and taxonC should contain the following:

taxonA 0.0
taxonB 0.1
taxonC 0.2

where the gap between each taxon name and its corresponding trait value must be a TAB.

