# cursov
ШАГ 1:

В операционной системе Ubuntu ввести следующие команды в терминале (ctrl+alt+t), нажимая в случае необходимости y (да):
(В случае если docker уже установлен пропустить команды вплоть до sudo docker run -d --name postgres-container...)

sudo apt-get update

sudo apt-get install ca-certificates curl

sudo install -m 0755 -d /etc/apt/keyrings

sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc

sudo chmod a+r /etc/apt/keyrings/docker.asc
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  
sudo apt-get update


sudo docker run -d  --name postgres-container -e POSTGRES_USER=ME  -e POSTGRES_PASSWORD=123  -e POSTGRES_DB=DATA  -p 5433:5432  postgres

ШАГ 2:

в случае если не установлено ifconfig ввести команду:

sudo apt install net-tools

ввести команду: ifconfig

найти ip-адрес Вашей виртуальной машины в предложенном списке: например 192.168.32.132

ШАГ 3:

на основной операционной системе в файле cursov.ipynb в первом блоке кода в строке:

DATABASE_URL = "postgresql://ME:123@192.168.32.132:5433/DATA"

вместо 192.168.32.132 введите ip-адрес Вашей виртуальной машины, найденный в шаге 2

Выберите в правом верхнем углу kernel venv(python 3.10.11)




