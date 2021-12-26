# 110618031林悟清  自動碩一
辛普森影像辨識作業
=====
-----
各檔案說明
-------


需用到安裝包說明
------
![image](https://user-images.githubusercontent.com/94088141/147402850-cefd6a30-e848-4bb2-bfef-926a98f2628c.png)
#########Numpy
NumPy是Python語言的一個擴充程式庫。支援高階大量的維度陣列與矩陣運算，此外也針對陣列運算提供大量的數學函數函式庫。
h5py

glob

程式說明
------
![image](https://user-images.githubusercontent.com/94088141/143763858-6c2184cf-cb5a-45ac-9b4b-8d9d33f1f1ce.png)\
此處檔案路徑須更變為你train-v3.csv所放置檔案位置\
![image](https://user-images.githubusercontent.com/94088141/143763935-ed05381b-a4fc-4865-917e-53cc35818ce3.png)\
此處檔案路徑須更變為你valid-v3.csv所放置檔案位置\
![image](https://user-images.githubusercontent.com/94088141/143763941-4e620bac-74dd-4897-8185-296139bcb934.png)\
此處檔案路徑須更變為你test-v3.csv所放置檔案位置

訓練集、驗證集跟測試集把相關度低的特徵移除不加入訓練:(id、zipcode、sale_yr、sale_month、sale_day、yr_renovated)\
![image](https://user-images.githubusercontent.com/94088141/143765610-58153fa4-187b-4440-a264-7836c3ae8f32.png)
![image](https://user-images.githubusercontent.com/94088141/143765620-8921c94f-68b0-430c-87d3-81a3d34be349.png)
![image](https://user-images.githubusercontent.com/94088141/143765630-8f71de2d-b6a5-4955-b0dd-d5624153200c.png)


資料正規化\
![image](https://user-images.githubusercontent.com/94088141/143765638-3b7db877-391c-404b-8f84-d0ac0e553488.png)

建模\
kerenel_initializer = RandomNormale\
activation = relu\
epoch = 400 \
batch_size = 128\
中間會經過dropout(0.2)把20%神經元輸出丟掉減少過擬和\
![image](https://user-images.githubusercontent.com/94088141/143765642-deb05f57-ec32-4e5e-a495-3981a94cf240.png)


查看model層數與各層參數數量、總參數資訊
![image](https://user-images.githubusercontent.com/94088141/143765649-aa33d335-5a23-4e6a-99ea-568f1b7a4114.png)

開始訓練
![image](https://user-images.githubusercontent.com/94088141/143765657-3b3d74cd-6b26-4a67-9e21-bfbf24dd294d.png)

繪出訓練loss、validation_loss\
![image](https://user-images.githubusercontent.com/94088141/143765666-931eff39-d776-43f0-8b2d-17635796135e.png)

儲存model、對測試資料做預測並寫出目標變數price
![image](https://user-images.githubusercontent.com/94088141/143765671-c04a270a-e918-4f2d-b8c3-bb71f1e5e139.png)



