   docker run -v /srv --name SWIFT_DATA busybox
   
   ID=$(docker run -d -p 12345:8080 -v /home/zhaogang/app/sw:/home/app/sw --name swift -v /opt/app:/opt/app --volumes-from SWIFT_DATA -t morrisjobke/docker-swift-onlyone)
   
   获取令牌 curl -v -H 'X-Storage-User: test:tester' -H 'X-Storage-Pass: testing' 'http://127.0.0.1:12345/auth/v1.0'
   
   export URL=http://127.0.0.1:12345/v1/AUTH_test
   
   export TOKEN=AUTH_tk5399c92882a040be9384654a3167d62d
   
   查看信息 
   
   curl -v -H 'X-Auth-Token: $TOKEN' $URL
   
   创建容器 
   
   curl -X PUT -i -H "X-Auth-Token: $TOKEN" $URL/testcontainer
   
   创建对象 
   
   curl -X PUT -i -H "X-Auth-Token: $TOKEN" -T demo.txt $URL/testcontainer/testobject
   
   获取对象
   
   curl -X GET -i -H "X-Auth-Token: $TOKEN" -o get.txt $URL/testcontainer/testobject

   设置元数据
   
   curl -X PUT -i -H "X-Auth-Token: AUTH_tkbb289af7125b4b83983c946b2865fbc8" -H "X-Object-Meta-Zhao: gang" -T demo.txt http://127.0.0.1:12345/v1/AUTH_test/testcontainer/testobject

   获取元数据
   
   curl -X HEAD -i -H "X-Auth-Token: $TOKEN" $URL/testcontainer/testobject
