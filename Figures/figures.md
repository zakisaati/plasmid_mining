## Figures

Here I show the codes used for the creation of some of the figures of the manuscript. The codes were used in R environment

### Scatterplots
I used the following codes to create scatterplots for the following figures:

Figure 1a:
~~~
> ggplot(data, aes(x = Size, y = nº.BGCs, color= TaxPhylum, fill = TaxPhylum)) + geom_point(position=position_jitter(h=0.1, w=0.1), shape = 21, alpha = 0.5, size = 3) + scale_color_manual(values=c("#2727a3", "#D95F02", "#7570B3", "#E7298A", "#66A61E", "#E6AB02", "#A6761D", "grey", "black", "#27a3a3", "red", "green")) + scale_fill_manual(values=c("#2727a3", "#D95F02", "#7570B3", "#E7298A", "#66A61E", "#E6AB02", "#A6761D", "grey", "black", "#27a3a3", "red", "green")) + theme_classic()
~~~

Figure 2a:
~~~
> data <- read.csv("/path-to/BGC_sizes-sin-saccharide.csv")
~~~

~~~
ggplot(data, aes(x = Size, y = BGC-type, color= BGC-type, fill = BGC-type)) + geom_point(position=position_jitter(h=0.1, w=0.1), shape = 21, alpha = 0.5, size = 1) + scale_color_manual(values=c("darkgreen", "grey", "#7570B3", "#D95F02", "bisque", "blue", "blueviolet")) + scale_fill_manual(values=c("darkgreen", "grey", "#7570B3", "#D95F02", "bisque", "blue", "blueviolet")) + theme_classic()
~~~

Figure 2b:
~~~
> data <- read.csv("/path-to/BGCtypse-size-sin-saccharides.csv")
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

