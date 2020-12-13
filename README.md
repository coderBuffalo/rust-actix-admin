<span style="color: red">注意:  全栈式 rust-admin 2.0 正在开发当中, 当前版本只进行维护, 请加微信群沟通 </span>

rust-admin 2.0 简介: 

1. 前端使用 Yew/WASM 框架开发

2. 后端使用 Actix-Web 3.x

3. UI使用付费授权版的layui 进行调整优化 (感谢网友Taro热心支持, 感谢社区)

4. 数据库调整为 postgresql, 连接池管理使用sqlx, 数据库调优

5. 前后端分离、数据传输加密

6. 先天支持分布式部署

静请期待。感谢大家支持!!!


# 基于Rust的后台管理系统

## 功能特点
#### 前端基于X-admin、layui,用户众多、易于修改。

X-Admin: http://x.xuebingsi.com/

Layui: https://www.larryms.com/

#### 后端基于actix-web开发,性能测试常年屠榜。

Actix框架: https://actix.rs/

性能测试: https://www.techempower.com/benchmarks/

#### MVC 设计模式,快速入门,方便上手。

#### Tera 模板引擎, layout、elements 等概念简化开发。 

Tera: https://tera.netlify.com/docs/

#### 基于Rust语言特性,有性能、安全保证

## 二次开发 & 技术交流
#### 微信群, 扫码备注: 'rust', 否则不会通过
![avatar](/public/wx.jpeg)


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
CREATE DATABASE rust_admin -- 创建数据库
    DEFAULT CHARSET=UTF8 
    COLLATE=UTF8_GENERAL_CI; 
GRANT ALL PRIVILEGES -- 设置用户名称密码
    ON `rust_admin`.* 
    TO 'rust_admin'@'%' 
    IDENTIFIED BY 'rust-x-lsl'; 
FLUSH PRIVILEGES;
USE rust_admin; -- 选中数据库
SOURCE scripts/init.sql; -- 导入初始化数据库(请依据实际路径)

-- 以下非必须, 只有前端使用 rust-vlog 时才会用到
CREATE DATABASE rust_vlog -- 创建vlog示例数据库
    DEFAULT CHARSET=UTF8 
    COLLATE=UTF8_GENERAL_CI; 
GRANT ALL PRIVILEGES -- 设置vlog用户名称密码
    ON `rust_vlog`.* 
    TO 'rust_vlog'@'%' 
    IDENTIFIED BY 'rust-x-lsl'; 
FLUSH PRIVILEGES;
USE rust_vlog; -- 选中vlog数据库
SOURCE scripts/example-vlog.sql; -- 导入初始化vlog数据库(请依据实际路径)
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

