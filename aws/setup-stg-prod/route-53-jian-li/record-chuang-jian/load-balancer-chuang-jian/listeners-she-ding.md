# Listeners設定

1.調整HTTP的rule，點擊 **View/edit rules**

2.進去更改界面后，使用更改功能，調整THEN為Redirect to HTTPS 然後輸入443，按save

3.再調整HTTPS的rule，點擊 **View/edit rules**

4.進去更改界面后，使用插入功能新增條件IF（HOST header），讓DNS定向（Forward to）連接至之前建立的Target Group，按save

5.回到[Load Balancer](./)

