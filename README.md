# 基于Rust的后台管理系统

## 功能特点
#### 前端基于X-admin、layui,用户众多、易于修改。

X-Admin: http://x.xuebingsi.com/

Layui: https://www.larryms.com/

#### 后端基于actix-web开发,性能测试常年屠榜。

Actix框架: https://actix.rs/

性能测试: https://www.techempower.com/benchmarks/

#### MVC 设计模式,快速入门,方便上手。

#### Tera 模板引擎,layout、elements等简化开发。 

Tera: https://tera.netlify.com/docs/

#### 基于Rust语言特性,有性能、安全保证,先天优于Go/Java/.Net/Php等带GC语言。

## 二次开发 & 技术交流
#### QQ群: 1036231916
#### 微信加群: 
![avatar](/public/wx.png)


## 环境要求
rust: 1.40+ / Mysql: 5.6+ / Nginx: 1.0+ (可选, 如果通过域名/80端口代理方式访问则需要)

## 目录说明
#### /public 用于设置nginx对外的网站地址
#### /scripts 用于初始化的sql脚本
#### /src rust源代码
#### /setting.toml.default 默认的配置文件, 请将复制为 setting.toml 并加入忽略
#### /templates 模板文件
#### /nginx.conf.default 设置nginx为前端代理的配置文件 (可选)

## 界面载图
#### 登录界面
![avatar](/public/static/images/login.png)

#### 后台管理
![avatar](/public/static/images/right.png)

#### 菜单管理
![avatar](/public/static/images/menus.png)

## 使用说明
#### 下载代码

```bash
git clone https://gitee.com/houhanting/rust-admin.git
cd rust-admin
```

#### 创建数据库(Mysql)并入导入数据

```sql
/* 创建数据库 */
CREATE DATABASE rust_admin DEFAULT CHARSET=UTF8 COLLATE=UTF8_GENERAL_CI; 
/* 设置用户名称密码 */
GRANT ALL PRIVILEGES ON `rust_admin`.* to 'rust_admin'@'%' IDENTIFIED BY 'rust-x-lsl'; 
FLUSH PRIVILEGES;
/* 选中数据库 */
USE rust_admin; 
/* 导入初始化数据库(请依据实际路径) */
SOURCE scripts/init.sql; 

/** 以下非必须, 只有前端使用 rust-vlog 时才会用到 **/
/* 创建vlog示例数据库 */
CREATE DATABASE rust_vlog DEFAULT CHARSET=UTF8 COLLATE=UTF8_GENERAL_CI; 
/* 设置vlog用户名称密码 */
GRANT ALL PRIVILEGES ON `rust_vlog`.* to 'rust_vlog'@'%' IDENTIFIED BY 'rust-x-lsl'; 
FLUSH PRIVILEGES;
/* 选中vlog数据库 */
USE rust_vlog; 
/* 导入初始化vlog数据库(请依据实际路径) */
SOURCE scripts/example-vlog.sql;
```

***** * 默认用户/名称: admin / qwe123

#### 设置nginx代理(非必需)

设置并生成Nginx配置文件
```bash
cp nginx.conf.default nginx.conf #复制nginx配置文件
cat "/nginx.conf" >> .git/info/exclude #忽略nginx配置文件
vim nginx.conf #修改相应的域名、目录、代理地址、端口
```

#### 运行程序

```bash
cargo run #生产模式: cargo run --release
```

## 捐助支持

欢迎各位朋友互相交流, 共同推进rust在中国的发展, 感谢支持:

![avatar](/public/static/images/wx.png) ![avatar](/public/static/images/tb.png)
