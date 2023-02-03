# Skylark 

## Installation

### Edit  `values.local.yaml`

1. Set imageCredentials for image pulling

```yaml
# values.local.yaml

imageCredentials: 
  registry: registry.cn-hangzhou.aliyuncs.com
  username: deploy-man@skylark
  password: changeit
```

2. Set image info for image pulling

```yaml
# values.local.yaml

image:
  repository: skylark/production
  tag: "latest"
  pullPolicy: IfNotPresent
```

3. Set host for app

```yaml
# values.local.yaml

# Application
slpHost: skylark.localhost
```

4. Set environments for app

```yaml
# values.local.yaml

# skylark environment variable
env:
  SETTING_ROOT_IDS: # 空间管理员ID号，如：[1]
  SETTING_QINIU_BUCKET: # 文件存储bucket名称
  SETTING_QINIU_DOMAIN: # 文件存储访问域名
  SETTING_QINIU_ACCESS_KEY: # 七牛提供的access key
  SETTING_QINIU_SECRET_KEY: # 七牛提供的secret key
  SETTING_QINIU_ATTACHMENT_BUCKET: # 附件存储bucket名称
  SETTING_QINIU_ATTACHMENT_DOMAIN: # 附件存储访问域名
  SETTING_QINIU_ATTACHMENT_SIZE: "100" # 附件大小，单位M
  SETTING_QINIU_EXPORTABLE_FILE_BUCKET: # 文件导出存储bucket名称
  SETTING_QINIU_EXPORTABLE_FILE_DOMAIN: # 文件导出访问域名
  SETTING_QINIU_MATERIAL_IMAGE_BUCKET: # 素材存储bucket名称
  SETTING_QINIU_MATERIAL_IMAGE_DOMAIN: # 素材存储访问域名
  SETTING_QINIU_MATERIAL_IMAGE_SIZE: "50" # 素材大小，单位M
  SETTING_APP_DOMAIN: https://skylarkly.com # 应用服务器访问域名：带http/https的完整访问域名
  SETTING_APP_IP: # 服务器访问互联网的出口IP
  SETTING_APP_DEFAULT_SITE_NAME: Skylark # 默认站点名称，后台可修改
  SETTING_APP_WELCOME_PAGE: # 修改通过域名访问服务时默认打开的页面地址
  SETTING_AMAP_JS_KEY: # 高德地图提供的JS KEY
  SETTING_AMAP_WEB_KEY: # 高德地图提供的WEB KEY
  SETTING_ALIYUN_ACCESS_KEY_ID: # 阿里云提供的KEY ID
  SETTING_ALIYUN_ACCESS_KEY_SECRET: # 阿里云提供的KEY SECRET
  SETTING_ALIYUN_SMS_SIGN_NAME: # 短信签名
  SETTING_ALIYUN_SMS_TEMPLATE_CODE_VERIFY_CODE: # 阿里云提供的短信模板ID
  REDIS_HOST: redis # redis地址
  CHEWY_HOST: elasticsearch:9200 # elasticsearch地址与端口
  POSTGRES_HOST: postgres-postgresql-helm-chart # postgres 地址
  POSTGRES_USER: postgres # postgres 用户名
  POSTGRES_PASSWORD: "123456" # postgres 密码
  RAILS_CACHE_STORE_URL: memcached:11211 # memcached地址与端口
  ...
```

### Install

```bash
# set release-name install
helm install -f values.local.yaml release-name ./
```

## HowTo

### Setup TLS

```yaml
# values.local.yaml

slpTLSSecret:
  certificate: certificate-filepath
  key: key-filepath
```

### Uninstall

```bash
helm uninstall release-name
```

### Upgrade

```bash
helm upgrade -f values.local.yaml release-name ./
```

