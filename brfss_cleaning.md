brfss cleaning
================
Gunnar
11/14/2021

``` r
library(tidyverse)
library(janitor)
library(haven)
```

loading dataset state 2020

``` r
library(tidyverse)
library(janitor)
library(haven)

state2020 <- read_xpt("./brfss_data/state_level_data/LLCP2020.XPT ") %>%
  clean_names()


state2020 <- state2020 %>%
  select(iyear, imonth, iday, ageg5yr, sexvar, race, state, casthm1, ltasth1, chccopd2, llcpwt, ststr, psu) %>%
  mutate(ageg5yr = na_if(ageg5yr, 14), ageg5yr = factor(ageg5yr, labels = c("18-24", "25-29", "30-34", "35-39", "40-44", "45-49", "50-54", "55-59", "60-64", "65-69", "70-74", "75-79", "80+")), sexvar = factor(sexvar, labels = c("male", "female")), race = na_if(race, 9), race = factor(race, labels = c("white", "black", "aian", "asian", "pacific islander", "other", "multiracial", "hispanic")), state = as_factor(state), casthm1 = na_if(casthm1, 9), casthm1 = factor(casthm1, labels = c("no", "yes")), ltasth1 = na_if(ltasth1, 9), ltasth1 = factor(ltasth1, labels = c("no", "yes")), chccopd2 = na_if(chccopd2, 9), chccopd2 = na_if(chccopd2, 7), chccopd2 = factor(chccopd2, labels = c("yes", "no"))) %>%
  rename(asthma_ever = ltasth1, asthma_current = casthm1, copd = chccopd2)
```

loading dataset state 2019

``` r
library(tidyverse)
library(janitor)
library(haven)

state2019 <- read_xpt("./brfss_data/state_level_data/LLCP2019.XPT ") %>%
  clean_names()

state2019 <- state2019 %>%
  select(iyear, imonth, iday, ageg5yr, sexvar, race, state, casthm1, ltasth1, chccopd2, llcpwt, ststr, psu) %>%
  mutate(ageg5yr = na_if(ageg5yr, 14), ageg5yr = factor(ageg5yr, labels = c("18-24", "25-29", "30-34", "35-39", "40-44", "45-49", "50-54", "55-59", "60-64", "65-69", "70-74", "75-79", "80+")), sexvar = factor(sexvar, labels = c("male", "female")), race = na_if(race, 9), race = factor(race, labels = c("white", "black", "aian", "asian", "pacific islander", "other", "multiracial", "hispanic")), state = as_factor(state), casthm1 = na_if(casthm1, 9), casthm1 = factor(casthm1, labels = c("no", "yes")), ltasth1 = na_if(ltasth1, 9), ltasth1 = factor(ltasth1, labels = c("no", "yes")), chccopd2 = na_if(chccopd2, 9), chccopd2 = na_if(chccopd2, 7), chccopd2 = factor(chccopd2, labels = c("yes", "no"))) %>%
  rename(asthma_ever = ltasth1, asthma_current = casthm1, copd = chccopd2)
```

loading dataset state 2018

``` r
library(tidyverse)
library(janitor)
library(haven)

state2018 <- read_xpt("./brfss_data/state_level_data/LLCP2018.XPT ") %>%
  clean_names()

state2018 <- state2018 %>%
  select(iyear, imonth, iday, ageg5yr, sex1, race, state, casthm1, ltasth1, chccopd1, llcpwt, ststr, psu) %>%
  mutate(ageg5yr = na_if(ageg5yr, 14), ageg5yr = factor(ageg5yr, labels = c("18-24", "25-29", "30-34", "35-39", "40-44", "45-49", "50-54", "55-59", "60-64", "65-69", "70-74", "75-79", "80+")), sex1 = na_if(sex1, 9), sex1 = na_if(sex1, 7), sex1 = factor(sex1, labels = c("male", "female")), race = na_if(race, 9), race = factor(race, labels = c("white", "black", "aian", "asian", "pacific islander", "other", "multiracial", "hispanic")), state = as_factor(state), casthm1 = na_if(casthm1, 9), casthm1 = factor(casthm1, labels = c("no", "yes")), ltasth1 = na_if(ltasth1, 9), ltasth1 = factor(ltasth1, labels = c("no", "yes")), chccopd1 = na_if(chccopd1, 9), chccopd1 = na_if(chccopd1, 7), chccopd1 = factor(chccopd1, labels = c("yes", "no"))) %>%
  rename(asthma_ever = ltasth1, asthma_current = casthm1, copd = chccopd1, sexvar = sex1)
```

loading dataset state 2017

``` r
library(tidyverse)
library(janitor)
library(haven)

state2017 <- read_xpt("./brfss_data/state_level_data/LLCP2017.XPT ") %>%
  clean_names()

state2017 <- state2017 %>%
  select(iyear, imonth, iday, ageg5yr, sex, race, state, casthm1, ltasth1, chccopd1, llcpwt, ststr, psu) %>%
  mutate(ageg5yr = na_if(ageg5yr, 14), ageg5yr = factor(ageg5yr, labels = c("18-24", "25-29", "30-34", "35-39", "40-44", "45-49", "50-54", "55-59", "60-64", "65-69", "70-74", "75-79", "80+")), sex = na_if(sex, 9), sex = factor(sex, labels = c("male", "female")), race = na_if(race, 9), race = factor(race, labels = c("white", "black", "aian", "asian", "pacific islander", "other", "multiracial", "hispanic")), state = as_factor(state), casthm1 = na_if(casthm1, 9), casthm1 = factor(casthm1, labels = c("no", "yes")), ltasth1 = na_if(ltasth1, 9), ltasth1 = factor(ltasth1, labels = c("no", "yes")), chccopd1 = na_if(chccopd1, 9), chccopd1 = na_if(chccopd1, 7), chccopd1 = factor(chccopd1, labels = c("yes", "no"))) %>%
  rename(asthma_ever = ltasth1, asthma_current = casthm1, copd = chccopd1, sexvar = sex)
```

loading dataset state 2016

``` r
library(tidyverse)
library(janitor)
library(haven)

state2016 <- read_xpt("./brfss_data/state_level_data/LLCP2016.XPT ") %>%
  clean_names()

state2016 <- state2016 %>%
  select(iyear, imonth, iday, ageg5yr, sex, race, state, casthm1, ltasth1, chccopd1, llcpwt, ststr, psu) %>%
  mutate(ageg5yr = na_if(ageg5yr, 14), ageg5yr = factor(ageg5yr, labels = c("18-24", "25-29", "30-34", "35-39", "40-44", "45-49", "50-54", "55-59", "60-64", "65-69", "70-74", "75-79", "80+")), sex = na_if(sex, 9), sex = factor(sex, labels = c("male", "female")), race = na_if(race, 9), race = factor(race, labels = c("white", "black", "aian", "asian", "pacific islander", "other", "multiracial", "hispanic")), state = as_factor(state), casthm1 = na_if(casthm1, 9), casthm1 = factor(casthm1, labels = c("no", "yes")), ltasth1 = na_if(ltasth1, 9), ltasth1 = factor(ltasth1, labels = c("no", "yes")), chccopd1 = na_if(chccopd1, 9), chccopd1 = na_if(chccopd1, 7), chccopd1 = factor(chccopd1, labels = c("yes", "no"))) %>%
  rename(asthma_ever = ltasth1, asthma_current = casthm1, copd = chccopd1, sexvar = sex)
```

loading dataset state 2015

``` r
library(tidyverse)
library(janitor)
library(haven)

state2015 <- read_xpt("./brfss_data/state_level_data/LLCP2015.XPT ") %>%
  clean_names()

state2015 <- state2015 %>%
  select(iyear, imonth, iday, ageg5yr, sex, race, state, casthm1, ltasth1, chccopd1, llcpwt, ststr, psu) %>%
  mutate(ageg5yr = na_if(ageg5yr, 14), ageg5yr = factor(ageg5yr, labels = c("18-24", "25-29", "30-34", "35-39", "40-44", "45-49", "50-54", "55-59", "60-64", "65-69", "70-74", "75-79", "80+")), sex = na_if(sex, 9), sex = factor(sex, labels = c("male", "female")), race = na_if(race, 9), race = factor(race, labels = c("white", "black", "aian", "asian", "pacific islander", "other", "multiracial", "hispanic")), state = as_factor(state), casthm1 = na_if(casthm1, 9), casthm1 = factor(casthm1, labels = c("no", "yes")), ltasth1 = na_if(ltasth1, 9), ltasth1 = factor(ltasth1, labels = c("no", "yes")), chccopd1 = na_if(chccopd1, 9), chccopd1 = na_if(chccopd1, 7), chccopd1 = factor(chccopd1, labels = c("yes", "no"))) %>%
  rename(asthma_ever = ltasth1, asthma_current = casthm1, copd = chccopd1, sexvar = sex)
```

loading dataset state 2014

``` r
library(tidyverse)
library(janitor)
library(haven)

state2014 <- read_xpt("./brfss_data/state_level_data/LLCP2014.XPT ") %>%
  clean_names()

state2014 <- state2014 %>%
  select(iyear, imonth, iday, ageg5yr, sex, race, state, casthm1, ltasth1, chccopd1, llcpwt, ststr, psu) %>%
  mutate(ageg5yr = na_if(ageg5yr, 14), ageg5yr = factor(ageg5yr, labels = c("18-24", "25-29", "30-34", "35-39", "40-44", "45-49", "50-54", "55-59", "60-64", "65-69", "70-74", "75-79", "80+")), sex = na_if(sex, 9), sex = factor(sex, labels = c("male", "female")), race = na_if(race, 9), race = factor(race, labels = c("white", "black", "aian", "asian", "pacific islander", "other", "multiracial", "hispanic")), state = as_factor(state), casthm1 = na_if(casthm1, 9), casthm1 = factor(casthm1, labels = c("no", "yes")), ltasth1 = na_if(ltasth1, 9), ltasth1 = factor(ltasth1, labels = c("no", "yes")), chccopd1 = na_if(chccopd1, 9), chccopd1 = na_if(chccopd1, 7), chccopd1 = factor(chccopd1, labels = c("yes", "no"))) %>%
  rename(asthma_ever = ltasth1, asthma_current = casthm1, copd = chccopd1, sexvar = sex)
```

loading dataset state 2013

``` r
library(tidyverse)
library(janitor)
library(haven)

state2013 <- read_xpt("./brfss_data/state_level_data/LLCP2013.XPT") %>%
  clean_names()

state2013 <- state2013 %>%
  select(iyear, imonth, iday, ageg5yr, sex, race, state, casthm1, ltasth1, chccopd1, llcpwt, ststr, psu) %>%
  mutate(ageg5yr = na_if(ageg5yr, 14), ageg5yr = factor(ageg5yr, labels = c("18-24", "25-29", "30-34", "35-39", "40-44", "45-49", "50-54", "55-59", "60-64", "65-69", "70-74", "75-79", "80+")), sex = na_if(sex, 9), sex = factor(sex, labels = c("male", "female")), race = na_if(race, 9), race = factor(race, labels = c("white", "black", "aian", "asian", "pacific islander", "other", "multiracial", "hispanic")), state = as_factor(state), casthm1 = na_if(casthm1, 9), casthm1 = factor(casthm1, labels = c("no", "yes")), ltasth1 = na_if(ltasth1, 9), ltasth1 = factor(ltasth1, labels = c("no", "yes")), chccopd1 = na_if(chccopd1, 9), chccopd1 = na_if(chccopd1, 7), chccopd1 = factor(chccopd1, labels = c("yes", "no"))) %>%
  rename(asthma_ever = ltasth1, asthma_current = casthm1, copd = chccopd1, sexvar = sex)
```

binding the data set

``` r
temp_df <- bind_rows("2020" = state2020, "2019" = state2019, "2018" = state2018, "2017" = state2017, "2016" = state2016, "2015" = state2015, "2014" = state2014, "2013" = state2013, .id = "brfss_year")
```
