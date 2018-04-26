docker run -ti harisekhon/hbase

        create 'blog_user','userInfo'
        put'blog_user','001','userInfo:user_Password','gang'
        put'blog_user','001','userInfo:user_Name','zhao'

        put'blog_user','002','userInfo:user_Password','lin'
        put'blog_user','002','userInfo:user_Name','wang'

        scan 'blog_user',  {COLUMNS => ['userInfo:user_Name', 'userInfo:user_Password'], LIMIT => 10, STARTROW => '001'}

        scan 'blog_user',  {COLUMNS => ['userInfo:user_Name', 'userInfo:user_Password'], LIMIT => 10, STARTROW => '001', TIMERANGE=>[1524706357801,1524706879925]}

        scan 'blog_user',  {COLUMNS => ['userInfo:user_Name', 'userInfo:user_Password'], LIMIT => 10, STARTROW => '001', TIMESTAMP=>1524706357801}

        put'blog_user','001','userInfo:user_Password','gang2'

        get 'blog_user', '001',{COLUMNS => ['userInfo:user_Name', 'userInfo:user_Password'],VERSIONS=>2}

    https://www.cnblogs.com/Little-Li/p/7877971.html
    https://www.cnblogs.com/cxzdy/p/5583239.html
    https://blog.csdn.net/tanggao1314/article/details/51387560
    https://blog.csdn.net/pirateleo/article/details/7956965
