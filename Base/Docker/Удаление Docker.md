
1. Остановить Docker-сервис

sudo systemctl stop docker

2. Удалить установленные пакеты Docker

sudo apt-get purge -y docker-ce docker-ce-cli containerd.io
sudo apt-get autoremove -y --purge

3. Удалить данные Docker

sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd

4. Удалить конфигурационные файлы

sudo rm -rf /etc/docker
sudo rm /etc/systemd/system/docker.service
sudo rm /etc/systemd/system/docker.socket

5. Перезагрузить демон systemd

sudo systemctl daemon-reload