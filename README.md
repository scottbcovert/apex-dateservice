# Apex DateService
This utility class was built to provide the same date literal values that Salesforce built for SOQL queries in generic Apex.

The class supports all date literals found in the [old documentation](https://help.salesforce.com/apex/HTViewHelpDoc?id=custom_dates.htm&language=en) (screnshots below), which includes all those in the [new documentation](https://developer.salesforce.com/docs/atlas.en-us.soql_sosl.meta/soql_sosl/sforce_api_calls_soql_select_dateformats.htm) as well as a few others. In addition, I've added support for half years & fiscal half years.

![DateLiterals](https://cloud.githubusercontent.com/assets/524857/17267057/36a070e2-55b6-11e6-89c2-3373515bb2a0.png)

![DateLiterals2](https://cloud.githubusercontent.com/assets/524857/17267058/3c82a278-55b6-11e6-808e-89f7dd8a1a61.png)

![DateLiterals3](https://cloud.githubusercontent.com/assets/524857/17267059/40d1d3bc-55b6-11e6-88fb-05168f5b8c6d.png)

The boundaries returned by DateService are an inclusive representation of given date literals and can be used like so:

```
Map<String,DateTime> tomorrowBoundaryByDateTime = DateService.dateLiteralToDateTimeMap(DateLiteral.TOMORROW);
DateTime lastTwoMonthsStartBoundary = DateService.dateLiteralToStartDateTime(DateLiteral.LAST_N_MONTHS,2);
Date endSevenFiscalYearsBoundary = DateService.dateLiteralToEndDate(DateLiteral.NEXT_N_FISCAL_YEARS,7);
System.assertEquals( endSevenFiscalYearsBoundary, DateService.dateLiteralToDateMap(DateLiteral.NEXT_N_FISCAL_YEARS,7).get(DateService.END_KEY) );
```

[Documentation](http://scottbcovert.github.io/apex-dateservice/) was created using ApexDocs (originally developed by Aslam Bari and later improved by Steve Cox) and has been included in the project

Happy Coding!