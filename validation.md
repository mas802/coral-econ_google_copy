The following table provides and overview of the possible condition/validation options in the [stages file](Flow.md) (column 4 and 5) for the CORAL framework.


# Table #

| validation type  |  The validation fails if …  |  syntax  |  example  |  errors |
|:-----------------|:------------------------------|:---------|:----------|:--------|
| existence  |  … the variable has not been set yet (for string variables also when they are empty)  |  variable  |  number  |  nullOrEmpty |
| range and precision  |  … the numeric value of the variable does not fall within the provided range, or if it has a higher precision (decimal places) than the lower bound.  |  variable::lower::upper  |  number::100::999  |  nullOrEmpty, tooBig, tooSmall, noNumber, wrongPrecision |
| equals  |  ... the value of the variable does not correspond to the provided value.  |  variable==value  |  number==222  |  nullOrEmpty, notEqual |
| equates  |  … the value of the variable is different from the other variable specified.  |  variable:=variable2  |  number:=id  |  nullOrEmpty, notEqual, evalError |
| javascript  |  … the javascript evaluation of the expression does not evaluate as TRUE or produces an error.  |  name:JavaScriptExpression  |  custom:(a<b && (a+b)<100)  |  evalError, evalFalse _(note: the associated error object is $error.custom)_ |