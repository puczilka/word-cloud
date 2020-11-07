# word-cloud

Extracting and analysing Google activity data in R. Creating multiple charts in ggplot to visualise patterns of activity and creating a word cloud visualisation of the most common searched terms.

- Session info ---------------------------------------------------------
 setting  value                       
 version  R version 4.0.2 (2020-06-22)
 os       Windows >= 8 x64            
 system   x86_64, mingw32             
 ui       RStudio                     
 language (EN)                        
 collate  English_United Kingdom.1252 
 ctype    English_United Kingdom.1252 
 tz       Europe/London               
 date     2020-11-07                  

- Packages -------------------------------------------------------------
 package      * version date       lib source        
 assertthat     0.2.1   2019-03-21 [1] CRAN (R 4.0.2)
 backports      1.1.10  2020-09-15 [1] CRAN (R 4.0.3)
 blob           1.2.1   2020-01-20 [1] CRAN (R 4.0.2)
 broom          0.7.1   2020-10-02 [1] CRAN (R 4.0.2)
 cellranger     1.1.0   2016-07-27 [1] CRAN (R 4.0.2)
 cli            2.1.0   2020-10-12 [1] CRAN (R 4.0.3)
 colorspace     1.4-1   2019-03-18 [1] CRAN (R 4.0.2)
 crayon         1.3.4   2017-09-16 [1] CRAN (R 4.0.2)
 DBI            1.1.0   2019-12-15 [1] CRAN (R 4.0.2)
 dbplyr         1.4.4   2020-05-27 [1] CRAN (R 4.0.2)
 digest         0.6.25  2020-02-23 [1] CRAN (R 4.0.2)
 dplyr        * 1.0.2   2020-08-18 [1] CRAN (R 4.0.3)
 ellipsis       0.3.1   2020-05-15 [1] CRAN (R 4.0.2)
 fansi          0.4.1   2020-01-08 [1] CRAN (R 4.0.2)
 farver         2.0.3   2020-01-16 [1] CRAN (R 4.0.2)
 forcats      * 0.5.0   2020-03-01 [1] CRAN (R 4.0.2)
 fs             1.5.0   2020-07-31 [1] CRAN (R 4.0.2)
 generics       0.0.2   2018-11-29 [1] CRAN (R 4.0.2)
 ggplot2      * 3.3.2   2020-06-19 [1] CRAN (R 4.0.2)
 glue           1.4.2   2020-08-27 [1] CRAN (R 4.0.3)
 gtable         0.3.0   2019-03-25 [1] CRAN (R 4.0.2)
 haven          2.3.1   2020-06-01 [1] CRAN (R 4.0.2)
 hms            0.5.3   2020-01-08 [1] CRAN (R 4.0.2)
 httr           1.4.2   2020-07-20 [1] CRAN (R 4.0.2)
 jsonlite       1.7.0   2020-06-25 [1] CRAN (R 4.0.2)
 labeling       0.3     2014-08-23 [1] CRAN (R 4.0.0)
 lifecycle      0.2.0   2020-03-06 [1] CRAN (R 4.0.2)
 lubridate    * 1.7.9   2020-06-08 [1] CRAN (R 4.0.2)
 magrittr       1.5     2014-11-22 [1] CRAN (R 4.0.2)
 modelr         0.1.8   2020-05-19 [1] CRAN (R 4.0.2)
 munsell        0.5.0   2018-06-12 [1] CRAN (R 4.0.2)
 NLP          * 0.2-1   2020-10-14 [1] CRAN (R 4.0.3)
 pillar         1.4.6   2020-07-10 [1] CRAN (R 4.0.2)
 pkgconfig      2.0.3   2019-09-22 [1] CRAN (R 4.0.2)
 purrr        * 0.3.4   2020-04-17 [1] CRAN (R 4.0.2)
 R6             2.4.1   2019-11-12 [1] CRAN (R 4.0.2)
 RColorBrewer * 1.1-2   2014-12-07 [1] CRAN (R 4.0.0)
 Rcpp           1.0.5   2020-07-06 [1] CRAN (R 4.0.2)
 readr        * 1.4.0   2020-10-05 [1] CRAN (R 4.0.3)
 readxl         1.3.1   2019-03-13 [1] CRAN (R 4.0.2)
 reprex         0.3.0   2019-05-16 [1] CRAN (R 4.0.2)
 rlang          0.4.7   2020-07-09 [1] CRAN (R 4.0.2)
 rstudioapi     0.11    2020-02-07 [1] CRAN (R 4.0.2)
 rvest        * 0.3.6   2020-07-25 [1] CRAN (R 4.0.2)
 scales         1.1.1   2020-05-11 [1] CRAN (R 4.0.2)
 sessioninfo    1.1.1   2018-11-05 [1] CRAN (R 4.0.2)
 slam           0.1-47  2019-12-21 [1] CRAN (R 4.0.3)
 stringi        1.4.6   2020-02-17 [1] CRAN (R 4.0.0)
 stringr      * 1.4.0   2019-02-10 [1] CRAN (R 4.0.2)
 tibble       * 3.0.4   2020-10-12 [1] CRAN (R 4.0.3)
 tidyr        * 1.1.2   2020-08-27 [1] CRAN (R 4.0.3)
 tidyselect     1.1.0   2020-05-11 [1] CRAN (R 4.0.2)
 tidyverse    * 1.3.0   2019-11-21 [1] CRAN (R 4.0.2)
 tm           * 0.7-7   2019-12-12 [1] CRAN (R 4.0.3)
 utf8           1.1.4   2018-05-24 [1] CRAN (R 4.0.2)
 vctrs          0.3.4   2020-08-29 [1] CRAN (R 4.0.3)
 withr          2.3.0   2020-09-22 [1] CRAN (R 4.0.3)
 wordcloud    * 2.6     2018-08-24 [1] CRAN (R 4.0.3)
 xml2         * 1.3.2   2020-04-23 [1] CRAN (R 4.0.2)
 yaml           2.2.1   2020-02-01 [1] CRAN (R 4.0.2)
