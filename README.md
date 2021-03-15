# Painters Dataset: Basic Data Frame Manipulation Using "dplyr" Package

## Description
The subjective assessment, on a 0 to 20 integer scale, of 54 classical painters. The painters were assessed on four characteristics: composition, drawing, colour and expression. The data is due to the Eighteenth century art critic, de Piles.

*to easily know about the dataset just type `?name_of_dataset`.

## Packages Installed

- **dplyr** is a grammar of data manipulation providing a consistent set of verbs that help you solve the most common data manipulation challenges. These are combined naturally with `group_by()` which allows you to perform any operation "by group".

        install.packages("dplyr")

After installing the **dplyr** and **readr** packages, you must call its library.

        library("dplyr")


## Accessing Painters Dataset
To access **painters** dataset we should call the **MASS Library**.

        library("MASS")

**Painters dataset**

        painters
                        Composition Drawing Colour Expression School
        Da Udine                 10       8     16          3      A
        Da Vinci                 15      16      4         14      A
        Del Piombo                8      13     16          7      A
        Del Sarto                12      16      9          8      A
        Fr. Penni                 0      15      8          0      A
        Guilio Romano            15      16      4         14      A
        Michelangelo              8      17      4          8      A
        Perino del Vaga          15      16      7          6      A
        Perugino                  4      12     10          4      A
        Raphael                  17      18     12         18      A
        F. Zucarro               10      13      8          8      B
        Fr. Salviata             13      15      8          8      B
        Parmigiano               10      15      6          6      B
        Primaticcio              15      14      7         10      B
        T. Zucarro               13      14     10          9      B
        Volterra                 12      15      5          8      B
        Barocci                  14      15      6         10      C
        Cortona                  16      14     12          6      C
        Josepin                  10      10      6          2      C
        L. Jordaens              13      12      9          6      C
        Testa                    11      15      0          6      C
        Vanius                   15      15     12         13      C
        Bassano                   6       8     17          0      D
        Bellini                   4       6     14          0      D
        Giorgione                 8       9     18          4      D
        Murillo                   6       8     15          4      D
        Palma Giovane            12       9     14          6      D
        Palma Vecchio             5       6     16          0      D
        Pordenone                 8      14     17          5      D
        Tintoretto               15      14     16          4      D
        Titian                   12      15     18          6      D
        Veronese                 15      10     16          3      D
        Albani                   14      14     10          6      E
        Caravaggio                6       6     16          0      E
        Corregio                 13      13     15         12      E
        Domenichino              15      17      9         17      E
        Guercino                 18      10     10          4      E
        Lanfranco                14      13     10          5      E
        The Carraci              15      17     13         13      E
        Durer                     8      10     10          8      F
        Holbein                   9      10     16         13      F
        Pourbus                   4      15      6          6      F
        Van Leyden                8       6      6          4      F
        Diepenbeck               11      10     14          6      G
        J. Jordaens              10       8     16          6      G
        Otho Venius              13      14     10         10      G
        Rembrandt                15       6     17         12      G
        Rubens                   18      13     17         17      G
        Teniers                  15      12     13          6      G
        Van Dyck                 15      10     17         13      G
        Bourdon                  10       8      8          4      H
        Le Brun                  16      16      8         16      H
        Le Suer                  15      15      4         15      H
        Poussin                  15      17      6         15      H

## Manipulating the Painters Dataset 

### dim() and str()
To view the basic characteristics of the dataset we can use `dim()` and `str()` functions.

        dim(painters)
        [1] 54  5
        
        
         str(painters)
        'data.frame':   54 obs. of  5 variables:
         $ Composition: int  10 15 8 12 0 15 8 15 4 17 ...
         $ Drawing    : int  8 16 13 16 15 16 17 16 12 18 ...
         $ Colour     : int  16 4 16 9 8 4 4 7 10 12 ...
         $ Expression : int  3 14 7 8 0 14 8 6 4 18 ...
         $ School     : Factor w/ 8 levels "A","B","C","D",..: 1 1 1 1 1 1 1 1 1 1 ...
         
## summary()
`summary()` function is a generic function used to produce result summaries of the results of various model fitting functions. The function invokes particular methods which depend on the class of the first argument. 

In this case we will look at the summary of **painters** dataset.

        summary(painters)
          Composition       Drawing          Colour        Expression         School  
         Min.   : 0.00   Min.   : 6.00   Min.   : 0.00   Min.   : 0.000   A      :10  
         1st Qu.: 8.25   1st Qu.:10.00   1st Qu.: 7.25   1st Qu.: 4.000   D      :10  
         Median :12.50   Median :13.50   Median :10.00   Median : 6.000   E      : 7  
         Mean   :11.56   Mean   :12.46   Mean   :10.94   Mean   : 7.667   G      : 7  
         3rd Qu.:15.00   3rd Qu.:15.00   3rd Qu.:16.00   3rd Qu.:11.500   B      : 6  
         Max.   :18.00   Max.   :18.00   Max.   :18.00   Max.   :18.000   C      : 6  
                                                                          (Other): 8  

Suppose we want to get the summary of the variable **School**.

         summary(painters$School)
         A  B  C  D  E  F  G  H 
        10  6  6 10  7  4  7  4 
       

## subset()
`subset()` function can be used to select and exclude variables and observations.

For instance, we want to access all the painters for which it holds **School == "F"**.

        painters_subset = subset(painters,School == "F")
        painters_subset
                   Composition Drawing Colour Expression School
        Durer                8      10     10          8      F
        Holbein              9      10     16         13      F
        Pourbus              4      15      6          6      F
        Van Leyden           8       6      6          4      F
                
Suppose we want to access all rows in which the variable **"school"** is "F" but restrict the data set fo the first two variables.

        subset(painters, School=="F",select=Composition:Drawing)
                   Composition Drawing
        Durer                8      10
        Holbein              9      10
        Pourbus              4      15
        Van Leyden           8       6
        

##### Contributors to this Document:

-Tristan John Girao
-Arvilyn Mellizas

        
        
