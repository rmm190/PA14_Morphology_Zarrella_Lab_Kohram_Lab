# Making a box and whisker plot for cell length, cell width, and mean cell fluorescence

This one is used for mean cell length. Note that you'll have to adjust based on the spreadsheet labeles that you're using.
```
library(ggplot2)

ggplot(data,
       aes(x = Timepoint (min),
           y = Length..um.)) +
  geom_boxplot() +
  theme_classic() +
  labs(
    x = "Time Point",
    y = "Cell Length (µm)"
  )
```

This can be used as a more informative plot that shows every cell measurement in addition to the box plots.
```
ggplot(data,
       aes(x = Timepoint,
           y = Length..um.)) +
  geom_boxplot(outlier.shape = NA) +
  geom_jitter(width = 0.2, alpha = 0.4) +
  theme_classic() +
  labs(
    x = "Time Point",
    y = "Cell Length (µm)"
  )
```
