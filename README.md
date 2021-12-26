# 110618031林悟清  自動碩一
辛普森影像辨識作業
=====
-----
各檔案說明
-------


需用到安裝包說明
------
![image](https://user-images.githubusercontent.com/94088141/147402850-cefd6a30-e848-4bb2-bfef-926a98f2628c.png)
Numpy\
NumPy是Python語言的一個擴充程式庫。支援高階大量的維度陣列與矩陣運算，此外也針對陣列運算提供大量的數學函數函式庫。\
h5py\
一個HDF5檔案就是一個容器，用於儲存兩類物件：datasets，類似於陣列的資料集合；groups，類似於資料夾的容器，可以儲存datasets和其它groups。當使用h5py時，最基本的準則為：\
groups類似於字典（dictionaries），dataset類似於Numpy中的陣列（arrays）。\
glob\
glob使用UNIX shell規則查找與一個模式匹配的文件名。只要程序需要查找文件系統中名字與某個模式匹配的一組文件，就可以使用這個模塊。 \
glob.glob（pathname), 返回所有匹配的文件路徑列表。它只有一個參數pathname，定義了文件路徑匹配規則，這裡可以是絕對路徑，也可以是相對路徑。\
os\
os 模組是關於作業系統操作呼叫的相關模組，對檔案進行重新命名、刪除等一系列操作，在python中可以用os模組\
os模組提供了一些系統級別的操作\
keras\
Keras套件包含許多實用的功能跟API可以快速讓初學者快速開發、認識機器學習。\
![image](https://user-images.githubusercontent.com/94088141/147403879-641fb661-e7fc-4938-b8df-47c15de91bf1.png)\

cv2\
OpenCV作為較大眾的開源庫，擁有了豐富的常用影象處理函式庫，採用C/C 語言編寫，可以執行在Linux/Windows/Mac等作業系統上，能夠快速的實現一些影象處理和識別的任務。此外，OpenCV還提供了Java、python、cuda等的使用介面、機器學習的基礎演算法呼叫，從而使得影象處理和影象分析變得更加易於上手，讓開發人員更多的精力花在演算法的設計上。\
影象資料的操作 ( 分配、釋放、複製、設定和轉換)。 影象是視訊的輸入輸出I/O （檔案與攝像頭的輸入、影象和視訊檔案輸出）等功能。\
matplotlib.pyplot\t
簡單來說Matpotlib是一個強大python繪圖工具，也就是它可以將資料視覺化，資料視覺化是相當重要的，當我們在查看訓練資料時，可以利用它來視覺化資料，使我們比較好觀察資料的走向或者相關度。\
Matpotlib有兩個重要的模組：\
1.Pylab:Matlab的python版本。\
2.Pyplot:呼叫NumPy的函式來做計算，再以圖形方式呈現。\

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



