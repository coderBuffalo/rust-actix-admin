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

**\*** \* 默认用户/名称: admin / qwe123

#### 设置 nginx 代理(非必需)

设置并生成 Nginx 配置文件

```bash
cp nginx.conf.default nginx.conf #复制nginx配置文件
cat "/nginx.conf" >> .git/info/exclude #忽略nginx配置文件
vim nginx.conf #修改相应的域名、目录、代理地址、端口
```

#### 运行程序

```bash
cargo run #生产模式: cargo run --release
```
