# lambda 掛 ip

lambda 如果要掛上ip 就需要用AWS 的 VPC（_Virtual Private Cloud_）虛擬私有雲

在掛上ip前先要理解lambda 如何透過VPC 來完成ip 的轉換。

* VPC 是虛擬雲，所以我門需要做一個map（地圖）來引導外面來的人需要怎麼進來，已經進來後我們有要怎麼出去

如下圖就是外面的人要怎麼進來的方式，

* Public： 為外來的ip來源
* Private：私有子網路ip pool
* subnet：則是子網路中的執行個體
* IGW（internet gateway）：是aws 提供的網際網路gateway管理，允許 VPC 與網際網路之間的通訊
* NAT（NAT gateway）：是aws提供的NAT gateway 管理，使私有子網路中的執行個體可以連線到 VPC 外部的服務，但外部服務無法啟動與這些執行個體的連線

![public to private](../.gitbook/assets/public_to_private.jpg)

下圖則是顯示私有子網路如何透過vpc 傳輸出去

![private to public](../.gitbook/assets/private_to_public.jpg)

所以我們先要創建子網路執行個體，分別要創建1個公用以及2個私用的子網路執行個體（AWS的vpc NAT預設必須為2個私有子網路執行個體）





