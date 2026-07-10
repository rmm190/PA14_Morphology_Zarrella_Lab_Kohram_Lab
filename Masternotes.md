# Making a box and whisker plot for cell length, cell width, and mean cell fluorescence

This one is used for mean cell length. Note that you'll have to adjust based on the spreadsheet labeles that you're using.
```
ggplot(data,
       aes(x = Timepoint,
           y = Length..um.)) +
  geom_boxplot() +
  theme_classic() +
  labs(
    x = "Time Point (minutes)",
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

A useful way to know how things are labeled in your spreadsheet so that you can accurately call select rows/columns of the spreadsheet for making figures. I highly recommend having a "master spreadsheet" with all of your data points in sequence with one another. You can collect data in individual spreadsheets, but then when you use R Studio, it's easier to have one big one to work with.

```
names(data)
```
To perform a one-way ANOVA, use this (but make sure to update with your specific variables and how you've labeled your spreadsheet.

```
length_anova <- aov(Length..um. ~ Timepoint, data = data)

summary(length_anova)
```

```
width_anova <- aov(Width_um ~ Timepoint, data = data)

summary(width_anova)

```
```
fluor_anova <- aov(Mean_Fluor ~ Timepoint, data = data)

summary(fluor_anova)
```

Reporting the means for different data points. As always, will need to know what the labels on your spreadsheet are.
```
aggregate(Length..um. ~ Timepoint,
          data = data,
          mean)
```

```
aggregate(Width_um ~ Timepoint,
          data = data,
          mean)
```

```
aggregate(Mean_Fluor ~ Timepoint,
          data = data,
          mean)
```
