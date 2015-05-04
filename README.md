Python planetary gear calculator
----------
DESCRIPTION
----------

Planetary gears must respect certain mathematical equations in order to work properly. One basic rule is that the number of teeth the ring gear must be equal to twice the number of teeth the planet gear have plus the number of teeth the sun gear has. 

  R = 2 * P + S

Another is that for a planetary gear ccnfiguration with an even distribution of planets (that is, planets are evenly spaced), the number of teeth of ring gear and sun gear must evenly divisible by the number of planets.

  R divides #Planets AND S divides #Planets

This calculator helps generating these possible gear configurations while calculating turn ratios in different scenarios: when ring gear is fixed, when carrier (planets  position) is fixed or when sun is fixed.

----------
EXAMPLES
----------
* Check if the following configuration is correct:
	ring gear   = 36 teeth
	planet gear = 14 teeth
	sun gear    = 8 teeth

```
> plgcalc.py 36:14:8
36:14:08
```

* Check if the following configuration is correct:
	ring gear   = 36 teeth
	planet gear = 14 teeth
	sun gear    = 7 teeth

```
> plgcalc.py 36:14:7
No results possible: invalid gear configuration
```

* Print out all data regarding the first configuration:

```
> plgcalc.py 36:14:8 --all
Gear            Tp/Ts Ratio     Tp/Tr Ratio     Ts/Tr Ratio     Angle
Configuration   Ring fixed      Sun fixed       Planets fixed   Planet-Sun
36:14:08        0.181818        0.818182        -4.500000       8.181818
```

* Check the configuration that is possible for a planetary having:
	ring gear   = 42 teeth
	planet gear = 18 teeth
	sun gear    = any

   Note: for this configuration print Planet-Ring turn ratio (sun is fixed)

```	
> plgcalc.py 42:18: --tpr
42:18:06        0.875000
```

* Print 10 possible configurations for a planetary setup that has:
	sun gear    = 12 teeth
	
   Note: for the resulting configurations print Planets-Sun turn ratio (ring is fixed)

```
> plgcalc.py ::12 -l 10 --tps --header
Gear            Tp/Ts Ratio
Configuration   Ring fixed
14:01:12        0.461538
16:02:12        0.428571
18:03:12        0.400000
20:04:12        0.375000
22:05:12        0.352941
24:06:12        0.333333
26:07:12        0.315789
28:08:12        0.300000
30:09:12        0.285714
32:10:12        0.272727
```

* Generate all possible configurations for a planetary gear set with following params:
	sun gear    = 9 teeth
	planets     = 3 (evenly distributed)

```
> plgcalc.py ::9 -l 10 -e -p 3
15:03:09
21:06:09
27:09:09
33:12:09
39:15:09
45:18:09
51:21:09
57:24:09
63:27:09
69:30:09
```

* Same as above, but also print calculated ratios:

```
> plgcalc.py ::9 -l 10 -e -p 3 --all
Gear            Tp/Ts Ratio     Tp/Tr Ratio     Ts/Tr Ratio     Angle
Configuration   Ring fixed      Sun fixed       Planets fixed   Planet-Sun
15:03:09        0.375000        0.625000        -1.666667       15.000000
21:06:09        0.300000        0.700000        -2.333333       12.000000
27:09:09        0.250000        0.750000        -3.000000       10.000000
33:12:09        0.214286        0.785714        -3.666667       8.571429
39:15:09        0.187500        0.812500        -4.333333       7.500000
45:18:09        0.166667        0.833333        -5.000000       6.666667
51:21:09        0.150000        0.850000        -5.666667       6.000000
57:24:09        0.136364        0.863636        -6.333333       5.454545
63:27:09        0.125000        0.875000        -7.000000       5.000000
69:30:09        0.115385        0.884615        -7.666667       4.615385
```

* Same as above, but use sun gear with 8 teeth, which  is an invalid configuration:

```
> plgcalc.py ::8 -l 10 -e -p 3 --all
No results possible: invalid sun configuration, planets will never be evenly spaced
```
