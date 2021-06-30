# OWASP Juice Shop


## Install Docker


* 更新軟體的最新資訊及列表 
```
sudo apt update
```
![](https://i.imgur.com/D4w5NEh.png)

* 安裝Docker
```
sudo apt install -y docker.io
```
![](https://i.imgur.com/XzShO04.png)

![](https://i.imgur.com/c29v8Ju.png)


* 啟用Docker
```
sudo systemctl enable docker --now
```
![](https://i.imgur.com/szz306Z.png)

* 測試一下docker是否成正常執行
```
docker
```
![](https://i.imgur.com/QB7K2rY.png)


## Juice Shop Docker Container
* 執行 docker pull bkimminich/juice-shop
```
docker pull bkimminich/juice-shop
```
![](https://i.imgur.com/U4l4NzG.png)

* 執行 docker run --rm -p 3000:3000 bkimminich/juice-shop
```
docker run --rm -p 3000:3000 bkimminich/juice-shop
```
![](https://i.imgur.com/Gu61jPm.png)

* 在Web Browser上 瀏覽http://localhost:3000

![](https://i.imgur.com/iBRUcmx.png)

## Information gathering

* Question #1: What's the Administrator's email address?

	* Ans：每個商品的評論，有些會顯示用戶的電子郵件地址。其中，透過點擊Apple Juice產品，可以獲得Administrator電子郵件！

	![](https://i.imgur.com/5AnuOwb.png)

* Question #2: What parameter is used for searching? 

	* Ans：點擊右上方的搜索欄，並輸入文本(例如：juice)，可以看到搜索的規則為：search?q=juice

	![](https://i.imgur.com/bSxXqVU.png)

* Question #3: What show does Jim reference in his review? 

	* Ans：可以發現Jim對Green Smoothie的產品評論中，有提到Replicator

	![](https://i.imgur.com/XJdKwUK.png)

	![](https://i.imgur.com/gKEggY2.png)

## Injection Juice!

* Question #1: Log into the administrator account!
	* Ans：
		* Step 1：點擊Account -> Login 會導向一個登入頁面
			![](https://i.imgur.com/Ja2XA4x.png)

		* Step 2：使用最簡單的 ' or 1=1 -- 語法繞過驗證 
			![](https://i.imgur.com/FO0Ozc6.png)
		* Step 3：成功登入
			![](https://i.imgur.com/G6TjZN0.png)
* Question #2: Log into the Bender account!
	* Ans：
		* Step 1：我們從Banana Juice的評論中可以得到Bender的帳號
			![](https://i.imgur.com/oVgQAeK.png)
		* Step 2：使用bender@juice-sh.op'-- 繞開驗證，至於為什麼不需要使用1=1，因為bender@juice-sh.op是有效帳號用戶，回傳值為True，因此不需要使用1=1(一般使用在帳戶或Email未知或無效時)。
		![](https://i.imgur.com/2M2sfD7.png)
		* Step 3：成功獲得Bender帳戶
		![](https://i.imgur.com/PMS605m.png)
## Password Cracker

* Question #1: Brute force the Administrator account's password!
	* Ans：
		* Step 1：儘管我們使用了SQL Injection成功繞過驗證，登入Administrator的帳戶，但我們還是不知道密碼，首先開啟Burp Suite
		* 
		
		* 
* Question #2: Reset Jim's password!
		

