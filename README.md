# Test_R
Prueba Condor
# Paquetes ----
pacman::p_load(tidyverse, lubridate, openxlsx, readxl, janitor)
# Data ----
Table <- tibble(date = as_date(c("2020-12-18", "2020-12-17", "2020-12-16", "2020-12-15",
                           "2020-12-14", "2020-12-13", "2020-12-12", "2020-11-30", 
                           "2020-11-29", "2020-10-18", "2020-10-17")),
                  associate_stores = c(1200, 1150, 1143, 1142, 1100, 1057, 999, 857,
                                       850, 900, 860))


Final_result <- Table %>% filter(date %in% as_date(c("2020-12-18", "2020-11-30", "2020-10-18"))) %>% 
  mutate(percentage = 0) %>% arrange(date)


 for(i in 1:(nrow(Final_result) - 1)){
   Final_result$percentage[i + 1] <- ((Final_result$associate_stores[i + 1] - Final_result$associate_stores[i])/Final_result$associate_stores[i])*100
 }


Final_result <- Final_result %>% mutate(percentage = str_c(round(percentage, 2),"%", sep = " "))

#Edgar Romero f
#25957579
