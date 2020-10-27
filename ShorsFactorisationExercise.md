                                                                   GP/PARI CALCULATOR Version 2.11.4 (released)
                                                           i386 running darwin (x86-64/GMP-6.2.0 kernel) 64-bit version
                                                      compiled: May 14 2020, Apple clang version 11.0.0 (clang-1100.0.33.17)
                                                                             threading engine: single
                                                                  (readline v8.0 enabled, extended help enabled)

                                                                      Copyright (C) 2000-2018 The PARI Group

parisize = 8000000, primelimit = 500000
? \\ Worked example of Shor's algorithm using GPari
? \\ Factoring an N=21
? \\ Using candidate number a=11
? N=21
%1 = 21
? a=11
%2 = 11
? \\ Next we begin our quantum algorithm, finding the periodicity of a^x mod N
? for(x = 1, 10, print(x, " ", Mod(a^x,N)))
1 Mod(11, 21)
2 Mod(16, 21)
3 Mod(8, 21)
4 Mod(4, 21)
5 Mod(2, 21)
6 Mod(1, 21)
7 Mod(11, 21)
8 Mod(16, 21)
9 Mod(8, 21)
10 Mod(4, 21)
? \\ We can see a pattern here, notice results 1 & 7, 2 & 8 respectively. We can see 11, 16 repeated after a period=6
? \\ Therefore, period of a^x is 6
? \\ We will now denote period as r
? r=6
%4 = 6
? \\ IF, r IS odd --> Find new value for 'a' --> until 'r' (period) is no longer odd
? \\ Here our r=6, which is even so we proceed
? Mod(r,2)
%5 = Mod(0, 2)
? \\ IF a^(r/2) == -1 (equivalent to -1) --> Find new value for 'a'
? Mod(a^(r/2), N)
%6 = Mod(8, 21)
? \\ We can see our above result is not equivalent to -1
? \\ Therefore, we can find the factors of our N from GCD by calculating.. gcd(a^(r/2) +/- 1, N)
? gcd(a^(r/2) +1,N)
%7 = 3
? gcd(a^(r/2) -1,N)
%8 = 7
? \\ *We have successfully factored N, finding 3 && 7 as the prime factors using Shor's algorithm*
