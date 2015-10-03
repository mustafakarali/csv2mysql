The problem: I have a gigantic csv file with hundreds of columns (mixed types: strings and integers), and need to turn this into a queryable mysql table.

MySQL's LOAD DATA INFILE is great if the schema is already there -- but in many cases that's the majority of the problem.  You can't just create N columns of varchar(255)'s, because then your numeric columns get string sorted (0, 1, 100, 101, 2).  Additionally, LOAD DATA INFILE sucks in many circumstances and becomes an irreconcilable train wreck when it comes to matching up data into the right columns and not dropping rows (why?!).

csv2mysql generates tables with compact columns of the right type (so far just varchar and int), stealing column names from headers in the first row of the csv.