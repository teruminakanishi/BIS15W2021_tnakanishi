---
title: "Lab 3 Homework"
author: "Terumi Nakanishi"
date: "2021-01-13"
output:
  html_document: 
    theme: spacelab
    keep_md: yes
---

## Instructions
Answer the following questions and complete the exercises in RMarkdown. Please embed all of your code and push your final work to your repository. Your final lab report should be organized, clean, and run free from errors. Remember, you must remove the `#` for the included code chunks to run. Be sure to add your name to the author header above.  

Make sure to use the formatting conventions of RMarkdown to make your report neat and clean!  

## Load the tidyverse

```r
library(tidyverse)
```

## Mammals Sleep
1. For this assignment, we are going to use built-in data on mammal sleep patterns. From which publication are these data taken from? Since the data are built-in you can use the help function in R.

These are from V. M. Savage and G. B. West. A quantitative, theoretical framework for understanding mammalian sleep. Proceedings of the National Academy of Sciences, 104 (3):1051-1056, 2007.


```r
?msleep
```

```
## starting httpd help server ... done
```

2. Store these data into a new data frame `sleep`.

```r
sleep<-msleep
```

3. What are the dimensions of this data frame (variables and observations)? How do you know? Please show the *code* that you used to determine this below.  

This data frame is 11 variables and 83 observations. I know that by running the following code.


```r
dim(sleep)
```

```
## [1] 83 11
```

4. Are there any NAs in the data? How did you determine this? Please show your code.  

Yes.I know that by running the following code.


```r
anyNA(sleep)
```

```
## [1] TRUE
```

5. Show a list of the column names is this data frame.


```r
names(sleep)
```

```
##  [1] "name"         "genus"        "vore"         "order"        "conservation"
##  [6] "sleep_total"  "sleep_rem"    "sleep_cycle"  "awake"        "brainwt"     
## [11] "bodywt"
```

6. How many herbivores are represented in the data?  

The answer is 32 by running the following code.


```r
table(sleep$vore)
```

```
## 
##   carni   herbi insecti    omni 
##      19      32       5      20
```

7. We are interested in two groups; small and large mammals. Let's define small as less than or equal to 1kg body weight and large as greater than or equal to 200kg body weight. Make two new dataframes (large and small) based on these parameters.

```r
small<-subset(sleep,bodywt<=1)
hsmall<-data.frame(small)
hsmall
```

```
##                              name        genus    vore           order
## 1                      Owl monkey        Aotus    omni        Primates
## 2      Greater short-tailed shrew      Blarina    omni    Soricomorpha
## 3                    Vesper mouse      Calomys    <NA>        Rodentia
## 4                      Guinea pig        Cavis   herbi        Rodentia
## 5                      Chinchilla   Chinchilla   herbi        Rodentia
## 6                 Star-nosed mole    Condylura    omni    Soricomorpha
## 7       African giant pouched rat   Cricetomys    omni        Rodentia
## 8       Lesser short-tailed shrew    Cryptotis    omni    Soricomorpha
## 9                   Big brown bat    Eptesicus insecti      Chiroptera
## 10              European hedgehog    Erinaceus    omni  Erinaceomorpha
## 11      Western american chipmunk     Eutamias   herbi        Rodentia
## 12                         Galago       Galago    omni        Primates
## 13           Thick-tailed opposum   Lutreolina   carni Didelphimorphia
## 14               Mongolian gerbil     Meriones   herbi        Rodentia
## 15                 Golden hamster Mesocricetus   herbi        Rodentia
## 16                          Vole      Microtus   herbi        Rodentia
## 17                    House mouse          Mus   herbi        Rodentia
## 18               Little brown bat       Myotis insecti      Chiroptera
## 19           Round-tailed muskrat     Neofiber   herbi        Rodentia
## 20                           Degu      Octodon   herbi        Rodentia
## 21     Northern grasshopper mouse    Onychomys   carni        Rodentia
## 22                Desert hedgehog  Paraechinus    <NA>  Erinaceomorpha
## 23                     Deer mouse   Peromyscus    <NA>        Rodentia
## 24                 Laboratory rat       Rattus   herbi        Rodentia
## 25          African striped mouse    Rhabdomys    omni        Rodentia
## 26                Squirrel monkey      Saimiri    omni        Primates
## 27          Eastern american mole     Scalopus insecti    Soricomorpha
## 28                     Cotton rat     Sigmodon   herbi        Rodentia
## 29                       Mole rat       Spalax    <NA>        Rodentia
## 30         Arctic ground squirrel Spermophilus   herbi        Rodentia
## 31 Thirteen-lined ground squirrel Spermophilus   herbi        Rodentia
## 32 Golden-mantled ground squirrel Spermophilus   herbi        Rodentia
## 33                     Musk shrew       Suncus    <NA>    Soricomorpha
## 34      Eastern american chipmunk       Tamias   herbi        Rodentia
## 35                         Tenrec       Tenrec    omni    Afrosoricida
## 36                     Tree shrew       Tupaia    omni      Scandentia
##    conservation sleep_total sleep_rem sleep_cycle awake brainwt bodywt
## 1          <NA>        17.0       1.8          NA   7.0 0.01550  0.480
## 2            lc        14.9       2.3   0.1333333   9.1 0.00029  0.019
## 3          <NA>         7.0        NA          NA  17.0      NA  0.045
## 4  domesticated         9.4       0.8   0.2166667  14.6 0.00550  0.728
## 5  domesticated        12.5       1.5   0.1166667  11.5 0.00640  0.420
## 6            lc        10.3       2.2          NA  13.7 0.00100  0.060
## 7          <NA>         8.3       2.0          NA  15.7 0.00660  1.000
## 8            lc         9.1       1.4   0.1500000  14.9 0.00014  0.005
## 9            lc        19.7       3.9   0.1166667   4.3 0.00030  0.023
## 10           lc        10.1       3.5   0.2833333  13.9 0.00350  0.770
## 11         <NA>        14.9        NA          NA   9.1      NA  0.071
## 12         <NA>         9.8       1.1   0.5500000  14.2 0.00500  0.200
## 13           lc        19.4       6.6          NA   4.6      NA  0.370
## 14           lc        14.2       1.9          NA   9.8      NA  0.053
## 15           en        14.3       3.1   0.2000000   9.7 0.00100  0.120
## 16         <NA>        12.8        NA          NA  11.2      NA  0.035
## 17           nt        12.5       1.4   0.1833333  11.5 0.00040  0.022
## 18         <NA>        19.9       2.0   0.2000000   4.1 0.00025  0.010
## 19           nt        14.6        NA          NA   9.4      NA  0.266
## 20           lc         7.7       0.9          NA  16.3      NA  0.210
## 21           lc        14.5        NA          NA   9.5      NA  0.028
## 22           lc        10.3       2.7          NA  13.7 0.00240  0.550
## 23         <NA>        11.5        NA          NA  12.5      NA  0.021
## 24           lc        13.0       2.4   0.1833333  11.0 0.00190  0.320
## 25         <NA>         8.7        NA          NA  15.3      NA  0.044
## 26         <NA>         9.6       1.4          NA  14.4 0.02000  0.743
## 27           lc         8.4       2.1   0.1666667  15.6 0.00120  0.075
## 28         <NA>        11.3       1.1   0.1500000  12.7 0.00118  0.148
## 29         <NA>        10.6       2.4          NA  13.4 0.00300  0.122
## 30           lc        16.6        NA          NA   7.4 0.00570  0.920
## 31           lc        13.8       3.4   0.2166667  10.2 0.00400  0.101
## 32           lc        15.9       3.0          NA   8.1      NA  0.205
## 33         <NA>        12.8       2.0   0.1833333  11.2 0.00033  0.048
## 34         <NA>        15.8        NA          NA   8.2      NA  0.112
## 35         <NA>        15.6       2.3          NA   8.4 0.00260  0.900
## 36         <NA>         8.9       2.6   0.2333333  15.1 0.00250  0.104
```

```r
large<-subset(sleep, bodywt>=200)
hlarge<-data.frame(large)
hlarge
```

```
##               name         genus  vore          order conservation sleep_total
## 1              Cow           Bos herbi   Artiodactyla domesticated         4.0
## 2   Asian elephant       Elephas herbi    Proboscidea           en         3.9
## 3            Horse         Equus herbi Perissodactyla domesticated         2.9
## 4          Giraffe       Giraffa herbi   Artiodactyla           cd         1.9
## 5      Pilot whale Globicephalus carni        Cetacea           cd         2.7
## 6 African elephant     Loxodonta herbi    Proboscidea           vu         3.3
## 7  Brazilian tapir       Tapirus herbi Perissodactyla           vu         4.4
##   sleep_rem sleep_cycle awake brainwt   bodywt
## 1       0.7   0.6666667 20.00   0.423  600.000
## 2        NA          NA 20.10   4.603 2547.000
## 3       0.6   1.0000000 21.10   0.655  521.000
## 4       0.4          NA 22.10      NA  899.995
## 5       0.1          NA 21.35      NA  800.000
## 6        NA          NA 20.70   5.712 6654.000
## 7       1.0   0.9000000 19.60   0.169  207.501
```


8. What is the mean weight for both the small and large mammals?

```r
x<-hsmall[,11]
mean(x)
```

```
## [1] 0.2596667
```


```r
y<-hlarge[,11]
mean(y)
```

```
## [1] 1747.071
```

9. Using a similar approach as above, do large or small animals sleep longer on average?  

Small animals sleep longer on average. The result was by running following code.


```r
z<-hsmall[,6]
mean(z)
```

```
## [1] 12.65833
```


```r
v<-hlarge[,6]
mean(v)
```

```
## [1] 3.3
```

10. Which animal is the sleepiest among the entire dataframe?
That is Little brown bat.

```r
sleepiest_animal<-subset(sleep,sleep_total>=19)
```


```r
hsleepiest_animal<-data.frame(sleepiest_animal)
hsleepiest_animal
```

```
##                   name      genus    vore           order conservation
## 1        Big brown bat  Eptesicus insecti      Chiroptera           lc
## 2 Thick-tailed opposum Lutreolina   carni Didelphimorphia           lc
## 3     Little brown bat     Myotis insecti      Chiroptera         <NA>
##   sleep_total sleep_rem sleep_cycle awake brainwt bodywt
## 1        19.7       3.9   0.1166667   4.3 0.00030  0.023
## 2        19.4       6.6          NA   4.6      NA  0.370
## 3        19.9       2.0   0.2000000   4.1 0.00025  0.010
```

## Push your final code to GitHub!
Please be sure that you check the `keep md` file in the knit preferences.   
