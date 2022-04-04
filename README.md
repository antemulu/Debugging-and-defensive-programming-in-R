# Debugging-and-defensive-programming-in-R
Module # 11 Debugging and defensive programming in R

The code below contains a 'deliberate' bug!  

tukey_multiple <- function(x) {
   outliers <- array(TRUE,dim=dim(x))
   for (j in 1:ncol(x))
    {
    outliers[,j] <- outliers[,j] && tukey.outlier(x[,j])
    }
outlier.vec <- vector(length=nrow(x))
    for (i in 1:nrow(x))
    { outlier.vec[i] <- all(outliers[i,]) } return(outlier.vec) }
    
    #The output with error
    #The code below contains a 'deliberate' bug!  
>   
>   tukey_multiple <- function(x) {
+     outliers <- array(TRUE,dim=dim(x))
+     for (j in 1:ncol(x))
+     {
+       outliers[,j] <- outliers[,j] && tukey.outlier(x[,j])
+     }
+     outlier.vec <- vector(length=nrow(x))
+     for (i in 1:nrow(x))
+     { outlier.vec[i] <- all(outliers[i,]) } return(outlier.vec) }
Error: unexpected symbol in:
"    for (i in 1:nrow(x))
    { outlier.vec[i] <- all(outliers[i,]) } return"

Find the bug and fix it.
Report on your blog the success or failure in your debugging procedure.

The error happened because of the curly brackets 
Deleting the curly brackets in this section of the code does fix the error.

The main bug is the structure of the R program was not correct. The parenthesis was not correctly setup. 
After making the correct changes on the structure of R, it showed no error.

 tukey_multiple <- function(x) 
+     {
+     
+     outliers <- array(TRUE,dim=dim(x))
+      for (j in 1:ncol(x))
+     
+     {
+       
+     outliers[,j] <- outliers[,j] && tukey.outlier(x[,j])
+     
+     }
+     outlier.vec <- vector(length=nrow(x))
+     for (i in 1:nrow(x))
+     
+     { outlier.vec[i] <- all(outliers[i,]) 
+   
+     } 
+   return(outlier.vec) 
+   
+     }

