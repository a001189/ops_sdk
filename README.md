## 功能
### logs
```python
from opssdk.logs import Log
### 日志路径
log_path = '/log/yunwei/%s.log' % (os.path.basename(__file__))
### 添加日志标识
log_ins = Log('yunwei', log_path)
### 写日志 （'debug', 'info', 'warning', 'error', 'critical'）
log_ins.write_log('info', 'ceshi')
```
### operate
- exec_shell 执行shell命令
```python
from opssdk.operate import exec_shell
recode,stdout = exec_shell('ls')
recode 为0 则代表成功，stdout 内容 为列表格式 半月逗号分隔
recode 非0 则代表失败，stdout 内容 字符串格式
```
- exclusiveLock  脚本锁,防止脚本重复执行
```python
from opssdk.operate import exclusiveLock
exclusiveLock(脚本名称)
```
- MyCrypt  加密解密模块
```python
from opssdk.operate import MyCrypt
mc = MyCrypt()                  # 实例化
mc.my_encrypt('ceshi')          # 对字符串ceshi进行加密
mc.my_decrypt('')               # 对密文进行解密
```
- now_time 获取当前时间 '%Y-%m-%d-%H-%M-%S'格式
```python
from opssdk.operate import now_time
print(now_time())
```
- is_ip 判断是否是IP ,True代表是，False代表不是
```python
from opssdk.operate import is_ip
print(is_ip('192.168.1.11')
```
### mysql 操作
```python
from opssdk.operate.mysql import MysqlBase
mysql_dict = {"host": "172.16.0.223", "port": 3306, "user": "root", "passwd": "ljXrcyn7", "db": "zhi"}
mb = MysqlBase(**mysql_dict)
### 查询 返回查询值
mb.query(sql)
### 增删改 返回影响行
mb.change(sql)
```

### 其他依赖安装

```
pip3 install pycrypto      --index-url http://mirrors.aliyun.com/pypi/simple/ --trusted-host mirrors.aliyun.com
```