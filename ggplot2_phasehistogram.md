### Here's how to make a circular histogram (rose plot) of phase, using R package ggplot2

*Load ggplot2*

    library(ggplot2)

*Import your data file as a CSV file, where one of the columns contains a value for the phase of each observation (e.g. gene expression). The data file has headings, with the heading for the phase column being "phase".*

    data <- read.csv("my_data.csv", header = TRUE)

*Tell ggplot2 what you want your axis breaks to be (here for a 24hr cycle)*

    breaks <- c(0,2,4,6,8,10,12,14,16,18,20,22)

*Draw the plot*

    ggplot(data, aes(data$phase)) + 
    geom_histogram(colour = "black", fill = "deeppink") + 
    coord_polar(theta = "x", direction=1 ) + 
    theme_linedraw() +
    theme(text = element_text(size = 24), axis.text.y=element_blank(), axis.ticks.y = element_blank()) + 
    scale_x_continuous(breaks = breaks, limits = c(0,23.9), name = "") + 
    scale_y_continuous(name = "") #+
    ggtitle("Phase histogram")
    
*Pick colours from the [R Color Chart](http://www.stat.columbia.edu/~tzheng/files/Rcolor.pdf).*
