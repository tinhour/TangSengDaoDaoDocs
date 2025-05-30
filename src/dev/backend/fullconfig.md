
# 完整配置

------------

默认可以全都注释掉，使用系统最优配置，需要配置什么就打开对应的注释

`配置采用yaml格式，如果发现配置什么都不生效，请检查缩进是否正确`

```yaml

#################### 基础配置 ####################
mode: "debug" #   运行模式 debug or release
addr: ":8090" # api监听地址
grpcAddr: "0.0.0.0:6979" # webhook grpc监听地址 给悟空IM提供的
appName: "唐僧叨叨" # 项目名称
rootDir: "" # 数据根目录
messageSaveAcrossDevice: true # 消息是否跨设备保存（换设备登录消息是否还能同步到老消息）
welcomeMessage: "欢迎使用{{appName}}" # 欢迎消息
phoneSearchOff: true # 关闭手机号搜索用户功能
onlineStatusOn: true # 开启在线状态功能
groupUpgradeWhenMemberCount: 1000 # 群组人数达到多少人时，群组自动升级为超级群组
eventPoolSize: 100 # 事件池大小

#################### 悟空IM配置 ####################
wukongIM:
  apiURL: "" # 悟空IM的api地址 格式： http://xx.xx.xx.xx:5001
  managerToken: "" # 悟空IM的管理者token 悟空IM配置了就需要填写，没配置就不需要

#################### db ####################
db:
  mysqlAddr: "root:demo@tcp(127.0.0.1:3306)/test?charset=utf8mb4&parseTime=true" # mysql连接地址
  redisAddr: "" # redis地址
  asynctaskRedisAddr: "" # 异步任务的redis地址 不写默认为RedisAddr的地址

#################### 外网配置 ####################
external: 
  ip: "" # 外网ip
  baseURL: "" # 外网访问地址 例如 http://10.2.3.1:8090
  webLoginURL: "" # web im的登录地址 例如 https://web.tangsengdaodao.com

#################### 日志配置 ####################
logger: 
  level: 0 # 日志级别 0:未配置,将根据mode属性判断 1:debug 2:info 3:warn 4:error
  dir: "./logs" # 日志目录
  lineNum: false # 是否打印行号

#################### 短信配置 ####################
smsCode: "" # 测试短信验证码， 如果不为空，则短信验证码为该值。
smsProvider: "aliyun" # 短信服务商. 例如: aliyun or unisms
aliyunSMS:
  accessKeyID: "" # 阿里云短信accessKeyID
  accessSecret: "" # 阿里云短信accessSecret
  templateCode: "" # 阿里云短信模板code
  signName: "" # 阿里云短信签名
aliyunInternationalSMS: # 阿里云国际短信，如果配置了该项，遇到国际区号的手机号，将使用该配置发送短信
  accessKeyID: "" # 阿里云国际短信accessKeyID
  accessSecret: "" # 阿里云国际短信accessSecret  
uniSMS:
  accessKeyID: "" # unisms accessKeyID
  signature: "" # unisms signature
  accessKeySecret: "" # unisms accessKeySecret 简易模式可以为空
  templateId: "" # unisms TemplateId 验证码变量名为code  

#################### 文件服务 ####################
fileService: "minio" # 文件服务 minio or aliyunOSS or seaweedFS or qiniu
minio: # minio配置
  url: "" # minio地址 格式：http://xx.xx.xx.xx:9000
  accessKeyID: "" # minio accessKeyID
  secretAccessKey: ""  # minio secretAccessKey
oss:  # aliyun oss配置
  endpoint: "" # oss endpoint 例如 oss-cn-hangzhou.aliyuncs.com
  bucketName: "" # bucketName 例如： tangsengdaodao
  bucketURL: "" # oss bucketURL 例如 https://xxxx.oss-cn-hangzhou.aliyuncs.com
  accessKeyID: "" # oss accessKeyID
  accessKeySecret: "" # oss accessKeySecret
seaweed: # seaweed配置
  url: ""   # seaweed地址 格式：http://xx.xx.xx.xx:9000
qiniu:            # 七牛云配置
  url: ""         # 七牛云对象存储请求域名，例：http://cdn.tsdaodao.com
  bucketName: ""  # 七牛云对象存储 bucket空间名称
  accessKey: ""   # 七牛云密钥 AccessKey
  secretKey: ""   # 七牛云密钥 secretKey

#################### 推送配置 ####################
push:
  contentDetailOn: true # 推送内容是否显示详情
  pushPoolSize: 100 # 推送池大小
  apns: # 苹果推送
    dev: false # 是否为开发环境
    topic: "" # topic 例如： com.xinbida.tangsengdaodao
    password: ""
    cert: "" # apns证书路径 例如：configs/push/push.p12
  hms: # 华为推送
    packageName: "" # 华为推送包名 例如：com.xinbida.tangsengdaodao  
    appID: "" # 华为推送appID
    appSecret: "" # 华为推送appSecret
  mi: # 小米推送
    packageName: "" # 小米推送包名 例如：com.xinbida.tangsengdaodao
    appID: "" # 小米推送appID
    appSecret: "" # 小米推送appSecret
    channelID: "" # 小米推送channelID
  vivo: # vivo推送
    packageName: "" # vivo推送包名 例如：com.xinbida.tangsengdaodao
    appID: "" # vivo推送appID
    appKey: "" # vivo推送appKey
    appSecret: "" # vivo推送appSecret 
  oppo: # oppo推送
    packageName: "" # oppo推送包名 例如：com.xinbida.tangsengdaodao
    appID: "" # oppo推送appID
    appKey: "" # oppo推送appKey
    appSecret: "" # oppo推送appSecret
    masterSecret: "" # oppo推送masterSecret

#################### 注册 ####################  
register:
  off: false # 是否关闭注册
  onlyChina: false # 是否只允许中国手机号注册
  stickerAddOff: false # 是否关闭注册添加表情

#################### 内置账户配置 ####################
account:
  systemUID: "u_10000" # 系统账户uid
  fileHelperUID: "fileHelper" # 文件助手uid
  systemGroupID: "g_10000" # 系统群组id
  systemGroupName: "意见反馈群" # 系统群组名称
  adminUID: "admin" # 管理员uid

#################### 头像 ####################
avatar:
  defaultBaseURL: "" # 默认头像cdn地址
  defaultCount: 900 # 默认头像数量
  partition: 100 # 头像分区数量

#################### 短号配置 ####################  
shortNo:
  numOn: false # 短号是否为纯数字
  numLen: 7 # 短号长度
  editOff: false # 是否允许修改短号

#################### 机器人配置 ####################    
robot:
  messageExpire: 7d # 机器人消息过期时间
  inlineQueryTimeout: 10s # 机器人inline query超时时间
  eventPoolSize: 100 # 事件池大小

#################### 第三方登录 ####################   
gitee:   
  oauthURL: "https://gitee.com/oauth/authorize" # gitee oauth地址
  clientID: ""  #  gitee client id
  clientSecret: "" # gitee client secret

github:
  oauthURL: "https://github.com/login/oauth/authorize" # github oauth url
  clientID: "" # github client id
  clientSecret: ""  # github client secret

#################### 缓存配置 ####################
cache: 
  tokenCachePrefix: "token:" # token缓存前缀
  tokenExpire: 30d # token过期时间
  loginDeviceCachePrefix: "login_device:" # 登录设备缓存前缀
  loginDeviceCacheExpire: 5m # 登录设备缓存过期时间
  uidTokenCachePrefix: "uidtoken:" # uid和token的缓存前缀
  friendApplyTokenCachePrefix: "friend_token:" # 好友申请token缓存前缀
  friendApplyExpire: 15d # 好友申请token过期时间
  nameCacheExpire: 7d # 名称缓存过期时间


```

## 配置转环境变量


唐僧叨叨可以通过配置环境变量来覆盖配置文件的配置。

比如配置文件里的 db.mysqlAddr 地址配置

文件的格式：

```
...

db
  mysqlAddr: "root:demo@tcp(127.0.0.1:3306)/test?charset=utf8mb4&parseTime=true"
...

```

转换为环境变量的格式：

```

TS_DB_MYSQLADDR=root:demo@tcp(127.0.0.1:3306)/test?charset=utf8mb4&parseTime=true

```

规则: TS为固定前缀，层级关系通过 "_"符号隔开，全都大写