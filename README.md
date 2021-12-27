# 110618031林悟清  自動碩一
辛普森影像辨識作業
=====
-----
檔案說明
----------
sim.py為本次作業程式

環境說明
-------
google colab

需用到套件說明
------
![image](https://user-images.githubusercontent.com/94088141/147402850-cefd6a30-e848-4bb2-bfef-926a98f2628c.png)
Numpy
--------
NumPy是Python語言的一個擴充程式庫。支援高階大量的維度陣列與矩陣運算，此外也針對陣列運算提供大量的數學函數函式庫。\

--------------
h5py
-------
一個HDF5檔案就是一個容器，用於儲存兩類物件：datasets，類似於陣列的資料集合；groups，類似於資料夾的容器，可以儲存datasets和其它groups。當使用h5py時，最基本的準則為：\
groups類似於字典（dictionaries），dataset類似於Numpy中的陣列（arrays）。\

--------------
glob
-------
glob使用UNIX shell規則查找與一個模式匹配的文件名。只要程序需要查找文件系統中名字與某個模式匹配的一組文件，就可以使用這個模塊。 \
glob.glob（pathname), 返回所有匹配的文件路徑列表。它只有一個參數pathname，定義了文件路徑匹配規則，這裡可以是絕對路徑，也可以是相對路徑。\

----------------
os
-----
os 模組是關於作業系統操作呼叫的相關模組，對檔案進行重新命名、刪除等一系列操作，在python中可以用os模組\
os模組提供了一些系統級別的操作\

----------------
Keras
------
Keras套件包含許多實用的功能跟API可以快速讓初學者快速開發、認識機器學習。\
![image](https://user-images.githubusercontent.com/94088141/147403879-641fb661-e7fc-4938-b8df-47c15de91bf1.png)\

--------------
cv2
-------
OpenCV作為較大眾的開源庫，擁有了豐富的常用影象處理函式庫，採用C/C 語言編寫，可以執行在Linux/Windows/Mac等作業系統上，能夠快速的實現一些影象處理和識別的任務。此外，OpenCV還提供了Java、python、cuda等的使用介面、機器學習的基礎演算法呼叫，從而使得影象處理和影象分析變得更加易於上手，讓開發人員更多的精力花在演算法的設計上。\
影象資料的操作 ( 分配、釋放、複製、設定和轉換)。 影象是視訊的輸入輸出I/O （檔案與攝像頭的輸入、影象和視訊檔案輸出）等功能。\

---------------
matplotlib
-----------------
簡單來說Matpotlib是一個強大python繪圖工具，也就是它可以將資料視覺化，資料視覺化是相當重要的，當我們在查看訓練資料時，可以利用它來視覺化資料，使我們比較好觀察資料的走向或者相關度。\
Matpotlib有兩個重要的模組：\
1.Pylab:Matlab的python版本。\
2.Pyplot:呼叫NumPy的函式來做計算，再以圖形方式呈現。

-----------------

程式說明
------
掛載google drive\
![image](https://user-images.githubusercontent.com/94088141/147409254-46d81a9f-abbf-4664-beca-1c2afcd49723.png)\
建立角色字典\
![image](https://user-images.githubusercontent.com/94088141/147409262-de784ca5-b05a-41ab-94be-b719a90ba4d5.png)\
宣告圖片長寬、角色類別個數、切割資料比例、圖片路徑\
![image](https://user-images.githubusercontent.com/94088141/147409337-2b3924c3-e667-41a6-93be-9acf9e0cf908.png)\
載入圖片把圖片從原本BGE轉成RGB、修改圖片長寬。
![image](https://user-images.githubusercontent.com/94088141/147409373-90716a36-d15b-472c-a059-f7ccb2129435.png)

![image](https://user-images.githubusercontent.com/94088141/147410189-c1b4b1b8-c4c6-4de2-a555-77847cd5c7da.png)\
![image](https://user-images.githubusercontent.com/94088141/147410195-50df410a-6964-47ba-8ead-bc5a1f88d618.png)\
各角色圖片個數、訓練集與驗證集內容(張數,長寬,rgb三層)(張數,角色個數)\
![image](https://user-images.githubusercontent.com/94088141/147410205-c5a50d45-2580-443a-9606-8e3a41ffff71.png)
![image](https://user-images.githubusercontent.com/94088141/147410207-4105dd15-8786-4135-8c87-5a2e83f61566.png)\
建模\
為Sequentail序列模型\
宣告pretrain model使用ResNet50\
第一層:ResNet50，第二層:flatten，第三層:1024個神經元、激活函數:relu，第四層:512個神經元、激活函數:relu，第五層:50個神經元、激活函數:softmax\
model.compile配置模型\
優化器(optimizer):Adam\
損失函數(loss_funtion):categorical_crossentropy\
metrics(評估模型指標):accuracy(準確率)

softmax
--------

softmax 函數突出顯示最大值並抑制顯著低於最大值的值，儘管對於微小值而言並非如此。\
它將輸出歸一化，使它們的總和為 1，這樣它們就可以直接被視為輸出的機率。\
它通常用於分類器模型的最後一層，以category cross entropy作為損失函數。\
![image](https://user-images.githubusercontent.com/94088141/147456513-33463cc5-98b8-4e34-9e4c-144418a94cf1.png)\

![image](https://user-images.githubusercontent.com/94088141/147410212-899d1788-969d-48b8-81e2-e3d982edc52b.png)\
設置batch size 、epochs\
lr_schedule:當epochs次數越訓練到後面時learning rate會越小，以利學到更好的解。\
Imagedatagenerator:利用現有的資料經過旋轉、翻轉、縮放…等方式增加更多的訓練資料。\
ModelCheckpoint:存取最佳的訓練模型，EarlyStopping:如果val_accuracy連續三次沒有增加則會提早結束訓練防止overfitting。\
![image](https://user-images.githubusercontent.com/94088141/147413498-6d3ee472-a47b-47b4-b40e-28d97087bee2.png)\
視覺化\
![image](https://user-images.githubusercontent.com/94088141/147410240-5e95b8a9-0fa3-4ac3-a781-cbcdf1edb733.png)\
![image](https://user-images.githubusercontent.com/94088141/147410258-280af50e-8bb8-4790-9ddc-d783dc2b24a1.png)
讀取測試檔、資料前處理、預測、寫出為csv檔。\
![image](https://user-images.githubusercontent.com/94088141/147410264-39cd0410-1b71-4d57-b673-33ad900f9ea8.png)

Pretrained Model 介紹
-------------------------
ResNet
----------
在ResNet論文出來前，當時的網路相較於現在，都是非常淺的設計。這個原因在於當時較深的網路比較容易訓練不起來，使得更深的網路有時反而帶來更差的效果。而ResNet提出的residual learning簡單地使得深層網路更容易訓練，也開啟了各種超深網路的時代。

------------------------------
Residual / Bottleneck Block
----------------
ResNet的網路設計其實很naive，就是簡單地增加一條路線做單純的加法 (如下圖左)，而這樣組合起來的convolution layer，論文稱為一個 (building) block，方法簡單卻使的深層網路訓練變得容易許多。而在\
疊更深的網路時，ResNet設計了bottleneck (building) block，降低3x3 convolution的寬度，大幅減少了所需的運算量。\
![1-YcmhKmhvUPlxG3xI2ncyYg](https://user-images.githubusercontent.com/94088141/147437510-1d9a8f16-a788-4269-b6fc-27d9d73f4123.png)

---------------------------------
Why Residual Learning
-----------------------
聽到深層網路訓練不起來，很容易直接想到gradient vanishing。不過ResNet論文卻不這麼認為，作者認為gradient vanishing應該已經在使用batch normalization後得到了一定non-zero variances的保證。\
論文在實驗時，在一般堆疊 (plain)網路加上了batch normalization，作者透過觀察gradient確定batch normalization足夠保證forward時的non-zero variances、以及back propagation時良好的梯度。\
而實驗結果也證明了一般堆疊的網路也能收斂在一個不差的地方。\
![1-p25TC3jO4BgC-lsAE4UCqA](https://user-images.githubusercontent.com/94088141/147437574-ad20d4fa-0a76-4a92-bf04-2055af4a0d25.png)

---------------------------------------
整體架構都可以分為三大部分：
-----------------------
1.Input stem: 使用一般的convolution，並且用大的stride降低解析度。\
2.Stage block: ResNet共有4個Stage block，每個stage block都是由數個building block堆疊而成。不論是用stride或是pooling，每個stage一般都會先降低解析度並加大寬度 (channel)，再做一連串的residual learning。\
3.Output stem：依照任務，設計不同的輸出。一般來說這邊會隨著任務轉變，所以通常不算在ResNet的backbone裡。\
![1-cXaK9HVaLxBDUdaZRLAc_g](https://user-images.githubusercontent.com/94088141/147437703-432fa61b-ea33-4c30-ab04-2548f9e6cb3a.png)\
由於每個 stage第一個 building block的輸入與 residual path連接的地方解析度與網路寬度都不同，所以第一個 block會多一個 convolution，做解析度與寬度的調整。

--------------------------------
改善方法
-------------------
可以讓訓練圖片為灰階圖片下去訓練，因為此任務的圖片顏色貌似不太是分辨的重點特徵。\
使用更強大的、不同的pretrained model做測試。








