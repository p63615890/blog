- [Creating NGINX Rewrite Rules](https://www.nginx.com/blog/creating-nginx-rewrite-rules/)
    - nginx return / rewrite comparison
- [使用Amazon CloudFront簽名URL+S3實現私有內容發佈](http://mp.weixin.qq.com/s/9_o7vSwDP95d8-dGn6xqqQ)
    - aws、cloudfront、s3
- AWS RDS 要 restore snapshot 的時候，事實上是會跑一個建立新 DB 的流程，如果想要 restore 成原本的 DB，可以先 rename 舊的 DB，再把要 restore 的 DB instance 的名稱取的一模一樣，這樣連 endpoints 都會一樣了
- AWS RDS 包含兩種備份機制
    - automatic backup: AWS RDS 會自動針對 db 和 transaction logs 進行備份，這些備份會被保存最多 35 天。可以 restore 最近 5 mins 內的資料
    - snapshot: 使用者手動備份，會持續保存，除非 user 自己 delete 它
- Cloudfront 的 origin 如果是設定 ELB 的域名時，要注意回源站的設定，最好走 80 回源，因為你走 443 回去時，你通常不會有源站 ELB 的憑證，這樣 Cloudfont 回去時就會出錯了。
- 強制拉 origin 最新的 commit 並且覆蓋掉 local 
```
git fetch origin master
git reset --hard FETCH_HEAD
git clean -df
```