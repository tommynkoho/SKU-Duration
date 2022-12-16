# SKU-Duration

SELECT A.SKU_NUMBER,Cast(A.CREATE_TIMESTAMP as Date) as New_Date, A.AISLE, A.BAY,Concat(A.AISLE,"-",A.BAY) as Aisle_Bay,B.SOURCE as source, B.STORE_NUMBER as store_number

FROM `pr-store-merch-thd.STORE_BAY_INTEGRITY.SHELF_OUT` as A

Join `pr-store-merch-thd.STORE_BAY_INTEGRITY.SHELF_OUT_SESSION`  as B ON

   A.SHELF_OUT_SESSION_ID= B.SHELF_OUT_SESSION_ID

where source= "ZIPPEDI_AISLE_BY_AISLE" or source= "ZIPPEDI" and A.CREATE_TIMESTAMP between '2022-02-01' and '2022-09-01' and B.STORE_NUMBER= '0154'

order by B.STORE_NUMBER, A.SKU_NUMBER, A.CREATE_TIMESTAMP asc, A.AISLE, A.BAY;





Select distinct source

from (SELECT A.SKU_NUMBER,Cast(A.CREATE_TIMESTAMP as Date) as New_Date, A.AISLE, A.BAY, B.SOURCE as source, B.STORE_NUMBER as store_number

FROM `pr-store-merch-thd.STORE_BAY_INTEGRITY.SHELF_OUT` as A

Join `pr-store-merch-thd.STORE_BAY_INTEGRITY.SHELF_OUT_SESSION`  as B ON

   A.SHELF_OUT_SESSION_ID= B.SHELF_OUT_SESSION_ID

order by A.SKU_NUMBER, A.CREATE_TIMESTAMP asc,B.STORE_NUMBER, A.AISLE, A.BAY)

![image](https://user-images.githubusercontent.com/17092274/208141970-5407e4b8-9506-478b-aa45-84213621b07b.png)
