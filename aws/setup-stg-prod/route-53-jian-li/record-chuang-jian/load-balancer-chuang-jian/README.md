# Load Balancer 創建

1.去到ec2內的Load Balancer

2.點擊Create Load Balancer

3.選擇HTTP與HTTPS類

4.Listeners新增HTTPS

5.Availability zone全開

6.到第二步Configure Security Settings選擇Choose a certificate from ACM \(recommended\)

7.若已有ACM不需要建立，[ACM建立](acm-jian-li.md)

8.跳回Load Balancer建立 Certificate name選擇剛剛建立或已有的ACM

9.到第三步Configure Security Groups勾選default 和 service-security

10.到第四步
