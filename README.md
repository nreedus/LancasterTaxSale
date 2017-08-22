# LancasterTaxSale
## Step 1 - Importing data
### Found the Lancaster County Tax Sale data online as a PDF file.
### Downloaded the PDF and converted it to an .XLS using pdftoexcel.com Uploaded the .XLS document to Google Drive and then downloaded it to my laptop as a .csv file.
### Imported the Lancaster County Tax Sale data .csv file into R Studio for munging and analysis

## Step 2 - Rename colums
### Found and corrected column name mistake
```
Lancaster_Tax_Sale <-rename(Lancaster_Tax_Sale, Account_Number = X1)
Lancaster_Tax_Sale <-rename(Lancaster_Tax_Sale, Owner_Name = X2, Addess = X3, Sale_Amount = X4)
Lancaster_Tax_Sale <-rename(Lancaster_Tax_Sale, Address = Addess) 
```
## Step 3 - Change empty vectors to "NA"
```
Lancaster_Tax_Sale[is.na(Lancaster_Tax_Sale)] <- 'NA'
```
### Later discovered this was a misktake. Empty variables are already "NA" in R. I started over by re-importing the data.
##
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Sale_Year:2017"]<-NA
> View(Lancaster_Tax_Sale)
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Site Address"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Sale Year:2017"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Sale Year: 2017"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Tax Sale Parcel List"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 1 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "8/2/2017 08:44:17"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Lancaster County"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Sale Order Account Number Owner Name"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Sale Order AccountNumber Owner Name"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Sale Order Account Number Owner Name"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Sale Amount"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Copyright (C) 1997-2017 DEVNET Incorporated"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 2 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Sale Order", "Account Number"]<-NA
Error in `[<-.data.frame`(`*tmp*`, Lancaster_Tax_Sale == "Sale Order",  : 
  missing values are not allowed in subscripted assignments of data frames
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Sale Order" "Account Number"]<-NA
Error: unexpected string constant in "Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Sale Order" "Account Number""
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Sale Order"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Account Number"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Owner Name"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 3 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 4 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 5 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 6 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 6 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Sale Order Account Number Owner Name"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "et. Al"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Home"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "HOME"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 7 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 8 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 9 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 10 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 11 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 12 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 13 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 14 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 15 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 16 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 76 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 17 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 18 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 19 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 120 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 20 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 21 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 22 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 23 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 24 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 25 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 26 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 27 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 28 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 29 of 30"]<-NA
> Lancaster_Tax_Sale[Lancaster_Tax_Sale == "Page 30 of 30"]<-NA
```
##Step 4
```
lts.nona <-lts.nona[apply(lts.nona,1,function(x)any(!is.na(x))),]
```
