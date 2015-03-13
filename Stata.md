# The following is a prototype for a .do file to read in and clean the data #

<pre>
clear<br>
set more off<br>
<br>
cd /* to the folder with all the raw files */<br>
<br>
// make a local with individual session idenifiers<br>
local sessions "Session1" "Session_2"<br>
<br>
foreach session of local sessions {<br>
<br>
// Read in the raw data with names and case intact<br>
import delimited export_`session'.raw, case(preserve) delimiters(";") clear<br>
<br>
drop if _valid == "false"<br>
<br>
/*<br>
this is a good place for initial data cleaning, droping subjects<br>
*/<br>
<br>
//<br>
// deal with round level variables (if you have rounds)<br>
//<br>
<br>
// make a local with all individual level variables<br>
local individualvars /* e.g. age ... */<br>
<br>
// replace instances of missing (e.g. -99)<br>
foreach var of varlist `individualvars' {<br>
<br>
cap replace `var' = . if `var' == -99<br>
<br>
}<br>
<br>
// use harmby to match them accross individual<br>
// ssc install harmby<br>
harmby `individualvars', by(_collection)<br>
<br>
//<br>
// deal with round level variables (if you have rounds)<br>
//<br>
<br>
sort _collection _id<br>
<br>
// make sure your round indicator variable is filled in properly<br>
replace round = round[_n-1] if mi(round) & _collection == _collection[_n-1]<br>
<br>
// make a local with all individual level variables<br>
local roundvars /* e.g. decision contribution ... */<br>
<br>
// replace instances of missing (e.g. -99)<br>
foreach var of varlist `individualvars' {<br>
cap replace `var' = . if `var' == -99<br>
}<br>
<br>
// use harmby to match them accross individual<br>
// ssc install harmby<br>
harmby `roundvars', by(_collection round)<br>
<br>
keep _collection `individualvars' `roundvars'<br>
<br>
// this is a good place to deal with timing<br>
<br>
// use duplicates drop to get rid of auxilliary variables<br>
// ssc install duplicates<br>
duplicates drop<br>
<br>
gen session = `session'<br>
<br>
save data_`session'.dta<br>
}<br>
<br>
// clear and append all data to a big data file<br>
clear<br>
<br>
foreach session of local sessions {<br>
append using data_`session'.dta<br>
}<br>
<br>
save all_data.dta<br>
</pre>