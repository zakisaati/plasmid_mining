## Figures

Here I show the codes used for the creation of some of the figures of the manuscript. The codes were used in R environment. The input tables can be found in the [Source Data](./Source_data) folder.

### Scatterplots
I used the following codes to create scatterplots for the following figures:

Figure 1a:
~~~
> data <- read.csv("/path-to/table_num_BGCs.csv")
~~~

~~~
> ggplot(data, aes(x = Size, y = nº.BGCs, color= TaxPhylum, fill = TaxPhylum)) + geom_point(position=position_jitter(h=0.1, w=0.1), shape = 21, alpha = 0.5, size = 3) + scale_color_manual(values=c("#2727a3", "#D95F02", "#7570B3", "#E7298A", "#66A61E", "#E6AB02", "#A6761D", "grey", "black", "#27a3a3", "red", "green")) + scale_fill_manual(values=c("#2727a3", "#D95F02", "#7570B3", "#E7298A", "#66A61E", "#E6AB02", "#A6761D", "grey", "black", "#27a3a3", "red", "green")) + theme_classic()
~~~

Figure 2a:
~~~
> data <- read.csv("/path-to/BGC_sizes-scatter.csv")
~~~

~~~
ggplot(data, aes(x = Size, y = BGC-type, color= BGC-type, fill = BGC-type)) + geom_point(position=position_jitter(h=0.1, w=0.1), shape = 21, alpha = 0.5, size = 1) + scale_color_manual(values=c("darkgreen", "grey", "#7570B3", "#D95F02", "bisque", "blue", "blueviolet")) + scale_fill_manual(values=c("darkgreen", "grey", "#7570B3", "#D95F02", "bisque", "blue", "blueviolet")) + theme_classic()
~~~

Figure 2b:
~~~
> data <- read.csv("/path-to/BGCtypse-size-scatter.csv")
~~~

~~~
> ggplot(data, aes(x = Size, y = BiG.SCAPE_class, color= BiG.SCAPE_class, fill = BiG.SCAPE_class)) + geom_point(position=position_jitter(h=0.1, w=0.1), shape = 21, alpha = 0.5, size = 1) + scale_color_manual(values=c("darkgreen", "grey", "#7570B3", "#D95F02", "bisque", "blue", "blueviolet")) + scale_fill_manual(values=c("darkgreen", "grey", "#7570B3", "#D95F02", "bisque", "blue", "blueviolet")) + theme_classic()
~~~

Supplementary figure 1:
~~~
> data <- read.csv("/path-to/table_num_BGCs-para-graficas-con-los-no-BGCs.csv")
~~~

~~~
> ggplot(data, aes(x = Size, y = nºBGCs, color= TaxPhylum, fill = TaxPhylum)) + geom_point(position=position_jitter(h=0.01, w=0), shape = 21, alpha = 0.5, size = 1) + scale_color_manual(values=c("#2727a3", "#D95F02", "#7570B3", "#E7298A", "#66A61E", "#E6AB02", "#A6761D", "grey", "black", "#27a3a3", "red", "green")) + scale_fill_manual(values=c("#2727a3", "#D95F02", "#7570B3", "#E7298A", "#66A61E", "#E6AB02", "#A6761D", "grey", "black", "#27a3a3", "red", "green")) + theme_classic()+ geom_smooth(method = "lm") + facet_wrap(~ TaxPhylum, scales = "free")
~~~

### Bubbleplots
Figure 3c:
~~~
> data <- read.csv("/path-to/orders-BGC-types-bubbleplot.csv")
~~~

~~~
> ggplot(data, aes(x = BGC.type, y = Order)) + geom_point(aes(color = BGC.type, size = num), alpha = 0.8) + scale_size(range = c(0, 6)) + theme_classic()  + scale_color_manual(values=c("darkgreen", "grey", "#7570B3", "#D95F02", "bisque", "blue", "blueviolet")) + scale_fill_manual(values=c("darkgreen", "grey", "#7570B3", "#D95F02", "bisque", "blue", "blueviolet"))
~~~

### Boxplots
Figure 2a:
~~~
> data <- read.csv("/path-to/porcentaje_plasmido_BGCs-8-phyla.csv")
~~~
~~~
> p <- ggplot(data, aes(x= Phylum, y= X.size.BGC,   fill= Phylum)) + geom_boxplot() + theme_classic() + geom_jitter(shape=16, size=0.8, position=position_jitter(0.3)) + scale_fill_manual(values=c("#2727a3", "#D95F02", "#E7298A", "#66A61E", "#E6AB02", "#A6761D", "#27a3a3", "red"))
> p + theme(axis.text.x = element_text(size = 3))
~~~

### Density plot

Figure 1a:
~~~
> data <- read.csv("/path-to/table_num_BGCs-density.csv")
~~~
~~~
> ggplot(data, aes(x=nº.BGCs, group= TaxPhylum, fill= TaxPhylum)) + geom_density(adjust=1.5) + theme_classic() + facet_wrap(~ TaxPhylum) + scale_color_manual(values=c("#2727a3", "#D95F02", "#7570B3", "#E7298A", "#66A61E", "#E6AB02", "#A6761D", "grey", "black", "#27a3a3", "red", "green")) + scale_fill_manual(values=c("#2727a3", "#D95F02", "#7570B3", "#E7298A", "#66A61E", "#E6AB02", "#A6761D", "grey", "black", "#27a3a3", "red", "green")) + theme_classic()
~~~

