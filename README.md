# vue-
vue.js的项目的访问链接如何去掉 # 呢？ 

步骤如下：
1. 在路由定义的脚本里添加mode:
        'history'  const router = new VueRouter({   
            mode: 'history',   
            routes: [...] 
            
          }) 
          
2.以上步骤还不够，因为页面刷新会出现404错误，还需要配置服务器
Apache

<IfModule mod_rewrite.c> 
  RewriteEngine On   
  RewriteBase / 
  RewriteRule ^index\.html$ - [L] 
  RewriteCond %{REQUEST_FILENAME} !-f  
  RewriteCond %{REQUEST_FILENAME} !-d   
  RewriteRule . /index.html [L]
</IfModule> 
  
  nginx 
  
  location / {  
     try_files $uri $uri/ /index.html;
  }
  ##注：本地测试环境运行npm run dev时是不用配置的，但部署到服务器上是需要的。
  
  作者：童蒙_ 链接：http://www.jianshu.com/p/444476c37c01 來源：简书 著作权归作者所有。
