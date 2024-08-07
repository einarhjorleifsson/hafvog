
<!-- README.md is generated from README.Rmd. Please edit that file -->

# hafvog

<!-- badges: start -->
<!-- badges: end -->

The goal of hafvog is to read in the hafvogs json files into R

## Installation

You can install the development version of hafvog from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("einarhjorleifsson/hafvog")
```

## The fundamental stuff

With {hafvog} you can read in the content of the hafvog zip files via:

``` r
library(hafvog)
zip_path <- system.file("zips", "A3-2024.zip", package = "hafvog")
hv_read_hafvog(zip_path, collapse_station = FALSE) |> dplyr::glimpse()
#> List of 6
#>  $ leidangrar    : tibble [1 × 11] (S3: tbl_df/tbl/data.frame)
#>   ..$ .file           : chr "A3-2024.zip"
#>   ..$ dags_byrjun     : chr "2024-02-28"
#>   ..$ dags_endir      : chr "2024-03-23"
#>   ..$ leidangursteg   : int 0
#>   ..$ synaflokkur     : int 30
#>   ..$ veidafaeri      : int 73
#>   ..$ skip            : int 2350
#>   ..$ verkefni        : chr "9113"
#>   ..$ leidangur       : chr "A3-2024"
#>   ..$ maelingamenn    : chr "Ásgeir og Lína, Anna Ragnheiður og Hjalti, Sæunn"
#>   ..$ leidangursstjori: chr "Jón Sól"
#>  $ stodvar       : tibble [51 × 26] (S3: tbl_df/tbl/data.frame)
#>   ..$ .file          : chr [1:51] "A3-2024.zip" "A3-2024.zip" "A3-2024.zip" "A3-2024.zip" ...
#>   ..$ leidangur      : chr [1:51] "A3-2024" "A3-2024" "A3-2024" "A3-2024" ...
#>   ..$ skip           : int [1:51] 2350 2350 2350 2350 2350 2350 2350 2350 2350 2350 ...
#>   ..$ dags           : Date[1:51], format: "2024-02-29" "2024-02-29" ...
#>   ..$ reitur         : int [1:51] 475 476 477 527 476 526 526 527 576 576 ...
#>   ..$ smareitur      : int [1:51] 3 4 2 4 1 4 4 2 3 3 ...
#>   ..$ kastad_v_lengd : num [1:51] -26 -26.4 -27.2 -27.1 -26.8 ...
#>   ..$ kastad_n_breidd: num [1:51] 64.5 64.7 64.9 65 65 ...
#>   ..$ hift_v_lengd   : num [1:51] -26 -26.5 -27.2 -27.2 -26.6 ...
#>   ..$ hift_n_breidd  : num [1:51] 64.6 64.8 64.9 65 65 ...
#>   ..$ dypi_kastad    : int [1:51] 207 184 377 234 203 147 231 247 201 175 ...
#>   ..$ dypi_hift      : int [1:51] 209 197 361 302 178 160 230 265 195 173 ...
#>   ..$ stod           : int [1:51] 14 15 16 17 18 19 20 21 22 23 ...
#>   ..$ tog_aths       : chr [1:51] NA NA NA NA ...
#>   ..$ synis_id       : int [1:51] 8742 8743 8744 8745 8746 8747 8748 8749 8750 8751 ...
#>   ..$ synaflokkur    : int [1:51] 30 30 30 30 30 30 30 30 30 30 ...
#>   ..$ fishing_gear_no: int [1:51] 73 73 73 73 NA 73 73 73 73 73 ...
#>   ..$ grandaralengd  : int [1:51] 35 35 35 35 35 35 35 35 45 45 ...
#>   ..$ veidarfaeri_id : chr [1:51] "5" "5" "5" "5" ...
#>   ..$ landsyni       : logi [1:51] FALSE FALSE FALSE FALSE FALSE FALSE ...
#>   ..$ maelingarmenn  : chr [1:51] "Ásgeir og Lína, Anna Ragnheiður og Hjalti, Sæunn" "Ásgeir og Lína, Anna Ragnheiður og Hjalti, Sæunn" "Ásgeir og Lína, Anna Ragnheiður og Hjalti, Sæunn" "Ásgeir og Lína, Anna Ragnheiður og Hjalti, Sæunn" ...
#>   ..$ undirstod_heiti: chr [1:51] "Varpa" "Varpa" "Varpa" "Varpa" ...
#>   ..$ medferd_afla   : int [1:51] 1 1 1 NA 1 1 1 1 1 1 ...
#>   ..$ device_id      : int [1:51] 6 6 6 6 NA 6 6 6 6 6 ...
#>   ..$ net_nr         : int [1:51] 1 1 1 1 NA 1 1 1 1 1 ...
#>   ..$ hnattstada     : int [1:51] -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 ...
#>  $ togstodvar    : tibble [51 × 13] (S3: tbl_df/tbl/data.frame)
#>   ..$ .file        : chr [1:51] "A3-2024.zip" "A3-2024.zip" "A3-2024.zip" "A3-2024.zip" ...
#>   ..$ synis_id     : int [1:51] 8742 8743 8744 8745 8746 8747 8748 8749 8750 8751 ...
#>   ..$ togbyrjun    : POSIXct[1:51], format: "2024-02-29 02:22:00" "2024-02-29 05:06:00" ...
#>   ..$ togendir     : POSIXct[1:51], format: "2024-02-29 03:24:00" "2024-02-29 06:05:00" ...
#>   ..$ togtimi      : int [1:51] 62 59 62 61 58 59 62 30 66 72 ...
#>   ..$ toghradi     : num [1:51] 3.9 4.1 3.9 3.9 4.1 4.1 3.9 4 3.6 3.3 ...
#>   ..$ toglengd     : num [1:51] 4 4 4 4 4 4 4 2 4 4 ...
#>   ..$ tognumer     : int [1:51] 12 1 11 11 12 11 12 1 13 2 ...
#>   ..$ togstefna    : int [1:51] 0 331 326 235 62 259 7 0 23 26 ...
#>   ..$ lodrett_opnun: num [1:51] 2.3 2.5 3.1 3 2.4 2.5 2.5 3 2.6 2.7 ...
#>   ..$ larett_opnun : num [1:51] 83.4 82.3 86.5 90.2 87.1 82.6 91.1 84.8 91 91.2 ...
#>   ..$ vir_uti      : int [1:51] 250 225 432 343 267 183 301 289 231 204 ...
#>   ..$ dregid_fra   : chr [1:51] "A" "A" "A" "A" ...
#>  $ umhverfi      : tibble [51 × 11] (S3: tbl_df/tbl/data.frame)
#>   ..$ .file        : chr [1:51] "A3-2024.zip" "A3-2024.zip" "A3-2024.zip" "A3-2024.zip" ...
#>   ..$ synis_id     : int [1:51] 8742 8743 8744 8745 8746 8747 8748 8749 8750 8751 ...
#>   ..$ yfirbordshiti: num [1:51] 6.6 6.5 6.8 6.7 6.6 6.1 6.6 6.6 6 5.4 ...
#>   ..$ botnhiti     : num [1:51] 5.9 5.7 6.7 6.6 5.9 5.6 6.2 6.4 6.2 5.6 ...
#>   ..$ lofthiti     : num [1:51] -0.1 0.6 -1.6 -2.2 -2.2 -4.3 -4 -0.8 -2.3 -2.4 ...
#>   ..$ vindhradi    : int [1:51] 2 4 13 9 11 11 14 11 16 16 ...
#>   ..$ loftvog      : int [1:51] 981 980 984 986 989 991 993 996 1000 1003 ...
#>   ..$ sky          : int [1:51] 8 8 8 8 8 7 8 8 8 8 ...
#>   ..$ sjor         : int [1:51] 4 3 5 3 3 3 4 5 5 5 ...
#>   ..$ vedur        : int [1:51] 7 2 6 2 2 2 2 7 7 7 ...
#>   ..$ vindatt      : int [1:51] 99 11 7 34 32 32 29 5 5 5 ...
#>  $ skraning      : tibble [19,681 × 20] (S3: tbl_df/tbl/data.frame)
#>   ..$ .file                  : chr [1:19681] "A3-2024.zip" "A3-2024.zip" "A3-2024.zip" "A3-2024.zip" ...
#>   ..$ s_synis_id             : int [1:19681] 8742 8742 8742 8742 8742 8742 8742 8742 8742 8742 ...
#>   ..$ s_maeliadgerd          : int [1:19681] 1 1 1 1 1 1 1 1 1 1 ...
#>   ..$ s_tegund               : int [1:19681] 5 5 5 5 5 5 5 5 5 5 ...
#>   ..$ s_lengd                : num [1:19681] 39 37 41 35 38 39 37 40 38 42 ...
#>   ..$ s_fjoldi               : int [1:19681] 1 1 1 1 1 1 1 1 1 1 ...
#>   ..$ s_kyn                  : int [1:19681] NA NA NA NA NA NA NA NA NA NA ...
#>   ..$ s_kynthroski           : int [1:19681] NA NA NA NA NA NA NA NA NA NA ...
#>   ..$ s_kvarnanr             : int [1:19681] NA NA NA NA NA NA NA NA NA NA ...
#>   ..$ s_nr                   : int [1:19681] 1 2 3 4 5 6 7 8 9 10 ...
#>   ..$ s_oslaegt              : num [1:19681] NA NA NA NA NA NA NA NA NA NA ...
#>   ..$ s_slaegt               : num [1:19681] NA NA NA NA NA NA NA NA NA NA ...
#>   ..$ s_magaastand           : int [1:19681] NA NA NA NA NA NA NA NA NA NA ...
#>   ..$ s_lifur                : num [1:19681] NA NA NA NA NA NA NA NA NA NA ...
#>   ..$ s_kynfaeri             : num [1:19681] NA NA NA NA NA NA NA NA NA NA ...
#>   ..$ s_tegund_as_faedutegund: int [1:19681] 5 5 5 5 5 5 5 5 5 5 ...
#>   ..$ valkvorn               : logi [1:19681] FALSE FALSE FALSE FALSE FALSE FALSE ...
#>   ..$ s_radnr                : int [1:19681] 1 2 3 4 5 6 7 8 9 10 ...
#>   ..$ s_ranfiskurteg         : int [1:19681] NA NA NA NA NA NA NA NA NA NA ...
#>   ..$ s_heildarthyngd        : num [1:19681] NA NA NA NA NA NA NA NA NA NA ...
#>  $ drasl_skraning: tibble [28 × 7] (S3: tbl_df/tbl/data.frame)
#>   ..$ .file         : chr [1:28] "A3-2024.zip" "A3-2024.zip" "A3-2024.zip" "A3-2024.zip" ...
#>   ..$ synis_id      : int [1:28] 8744 8745 8753 8755 8755 8756 8757 8783 8790 8790 ...
#>   ..$ yfirflokkur_id: int [1:28] 1 1 1 1 1 1 1 1 1 1 ...
#>   ..$ thyngd        : num [1:28] 20 4 6 16 7 9 8 4 4 10 ...
#>   ..$ flokkur_id    : int [1:28] 1 1 1 2 1 1 1 1 1 1 ...
#>   ..$ fjoldi        : int [1:28] 3 2 2 1 1 1 2 1 1 1 ...
#>   ..$ id            : int [1:28] 2621 2622 2623 2624 2625 2626 2627 2643 2644 2645 ...
```
