# Nextcloud

Runs nextcloud via the nginx-proxy


* add your settings to .env
* create docker volumes 'nextcloud-html' 'nextcloud-db'
* sudo docker-compose up -d
* clean up the installation with:

'''
sudo docker exec --user www-data nextcloud_app_1 php occ maintenance:mode --on
sudo docker exec --user www-data nextcloud_app_1 php occ db:convert-filecache-bigint
sudo docker exec --user www-data nextcloud_app_1 php occ db:add-missing-indices
'''

* edit config.php so that collabora is linked through https to avoid browser mixed content errors.
'''
+ 'overwriteprotocol' => 'https',
- 'overwrite.cli.url' => 'http://yourhostname',
+ 'overwrite.cli.url' => 'https://yourhostname',
'''
* and it's ready:
'''
sudo docker exec --user www-data nextcloud_app_1 php occ maintenance:mode --off
'''

If you're using collabora, install the collabora app in nextcloud, and give it the address of your collabora instance.
