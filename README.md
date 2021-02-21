# icloudpd
- source:  

~~https://github.com/shuixin536/icloud_photos_downloader~~

~~https://github.com/shuixin536/pyicloud~~

~~https://github.com/ndbroadbent/pyicloud~~

`https://github.com/icloud-photos-downloader/icloud_photos_downloader`

需要直接安装即可

`pip install icloudpd`

- use:  
`docker pull shuixin536/icloudpd`

- volume:  
`/data`

- env:  

| key | value |
| ------ | ------ |
| USERNAME | uuuuuu |
| PASSWORD | pppppp | 
| TZ | Asia/Shanghai | 
| CRON | 0 */6 * * * | 
| RECENT | 500 | 
| ALBUM | All Photos 或者 Favorites 或者 某个文件夹的名字 | 
| FOLDERSTRUCTURE | {:%Y/%m/%d} 或者 {:%Y/%m} | 




# 注意
测试下载全部照片会报错。

如果报错
```
folder['fields']['albumNameEnc']['value']).decode('utf-8')
KeyError: 'albumNameEnc'
```
需要升级icloudpd
`pip install icloudpd==1.7.2`

查找icloudpd版本号
`pip install icloudpd==`

# 操作
```
docker ps
列出 容器id

CONTAINER ID        IMAGE                        COMMAND             CREATED             STATUS              PORTS               NAMES
aeaebc726f51        shuixin536/icloudpd:latest   "/home/entry.sh"    19 months ago       Up 13 hours                             icloudpd_fav

docker exec -it 容器id /bin/sh

aa@DiskStation:~# docker exec -it aeaebc726f51 /bin/sh
/ # vi /home/icloud.sh

ps -ef

/home/icloud.sh
vi /home/icloud.sh

#!/bin/sh                                                                                                                                                              
icloudpd --directory /data --username ${USERNAME} --password ${PASSWORD} --size original --recent ${RECENT} --album ${ALBUM} --folder-structure ${FOLDERSTRUCTURE} 
icloudpd的参数参考 https://github.com/icloud-photos-downloader/icloud_photos_downloader#usage
```
