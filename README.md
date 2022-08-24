# Converting-data-from-wide-to-tall-and-tall-to-wide-
### Converting data from wide to tall and tall to wide 


### make sure to install all the packages below. 
pacman::p_load(datasets, pacman,MASS, tidyverse)

### the housing  dataset
?housing
view(housing)

data <- housing %>% as_tibble() %>% print()
glimpse(data)
view(data)

### making the dataset wide 
data_wide <- spread(data, 
                    key = Sat, ### catergory to split into columns 
                    value = Freq) %>% ### values for each category
  print()

view(data_wide)

### Another way is to use the pivotwider 
philant.wide <- pivot_wider(data, names_from = Sat, values_from = Freq)
view(philant.wide)


### making the dataset longer 
data_long <- gather(data_wide, "Low", "Medium", "High", ### columns to be combined to 
                    key = "Sat", ### New variables for columns 
                    value = "Freq") ### Variables to hold values
view(data_long)


