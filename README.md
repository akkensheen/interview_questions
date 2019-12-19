**PS**  
Какой результат выполнения команды `get-command | get-member`  
Разница `Remove-ADUser` и `Disable-ADAccount`.
```
Get-WmiObject Win32_share -Property * | ? Name -NotLike "*$" | select Name,Path  
$date90=(Get-Date).AddDays(-90)
```
```
Get-ADUser -Filter {(LastLogonDate -le $date90)} -Properties LastLogonDate,employeetype | ? { $_.distinguishedname -notmatch 'DismissedUsers' }
```
**AD**  
Роли FSMO в Active Directory:
> Schema master. (F)  
> Domain naming master. (F)  
> RID master.  
> PDC emulator.  
> Infrastructure master  

Как работает RID мастер?  
Как происходит процесс поиска контроллера домена после включения компьютера?  
Можно ли авторизоваться на рабочей станции, если контроллер домена стал недоступен?  
Восстановление объектов в AD?  
Где хранятся GPO:  
> GPC class groupPolicyContainer System\Policies  
> GPT SYSVOL \<domainname>\Policies  

Порядок применения групповых политик?  
Как ограничить GPO на определенный круг пользователей/компьютеров?  

**Виртуализация**  
Какого цвета экран смерти в ESXi?  
Восстановление рабочей конфигурации ESXi при неудачном обновлении.  
Типы дисков для ВМ, их отличия.  
Балансировка автоматом по хранилищам/хостам.  
Отличие vDS и vSS.  
Возможна ли миграция ВМ между хостами без общего стораджа?  
Технологии отказоустойчивости в VMware.  
Что такое affinity rule?  
Как понизить версию виртуального железа?  

**Сеть**  
Принципиальное отличие протоколов udp/tcp.  
Можно ли на один хост назначить несколько ip-адресов.  
Отображение конфигурации коммутатора Cisco.  
> show run  
> show run-config  

Отличие access и trunk.  
Какие параметры можно передать с помощью протокола dhcp?  
Как обеспечить отказоустойчивость сервиса DHCP?  
What is ARP/DNS/DHCP and what is it used for?  

**Файловые сервера Windows**  
Автоматизация подключения файловых ресурсов, способы?  
Как назначить квоту на сетевую папку?  
Как запретить сохранение исполняемых файлов в сетевой папке?  
Заменяют ли теневые копии резервное копирование?  
Можно ли настроить сохранение теневых копий на выделенный том?  

**Exchange**  
Роли Exchange 2010/2013, способы обеспечения отказоустойчивости каждой из ролей.  
Для чего нужен quorum?  
По каким портам и протоколам почтовые клиенты могут подключаться к серверу Exchange 2010/2013?  
Как подключить МФУ/сетевой сканер к почтовому серверу для отправки отсканированных документов?  
Как включить openrelay для конкретного клиента?  
В чем отличие записей example.com. IN TXT "v=spf1 mx -all" и example.com. IN TXT "v=spf1 mx ~all"; для чего нужен этот тип записей?  

**SQL**  
Какие редакции SQL существуют, в чем основные отличия?  
Типы моделей восстановления в SQL, их предназначение и отличия.  
Чем отличается резервное копирование базы данных от резервного копирования журнала транзакций?  
Как предоставить доступ к базе данных служебной учетной записи?  
Что такое снимок базы данных, как работает?  
Способы обеспечения отказоустойчивости SQL.  

**Sharepoint**  
Как назначить квоту на сайт в Sharepoint?  
Как внести изменения в master-page для конкретного сайта?  
Что такое режим обслуживание веб-частей в Sharepoint?  
На каком уровне можно назначать разрешения в sharepoint?  

**IIS**  
Что такое Application Pool  
Как предоставить доступ к сайту определенной группе безопасности?  
Как разрешить доступ к сайту с определенных ip адресов?  
Как подключить сетевую папку к сайту?  

**Linux**  
*Simple*  
What command you can use in order to check utilization?  
What is the name and the UID of the administrator user?  
What Unix/Linux commands will alter a files ownership, files permissions?  
What does chmod +x FILENAME do?  
What does the permission 0750 on a file/directory  mean?  
Walk me through the steps in booting into single user mode to troubleshoot a problem.  
*Medium*  
What is the difference between & / &&  
What is the sticky bit?  
Describe a scenario when you get a "filesystem is full" error, but 'df' shows there is free space.  
Describe a scenario when deleting a file, but 'df' not showing the space being freed.  
*Hard*  
What kind of keys are in ~/.ssh/authorized_keys and what it is this file used for?  
I've added my public ssh key into authorized_keys but I'm still getting a password prompt, what can be wrong?  

**bash**  
```
touch file{1..9}.{png,jp{,e}g}
```
```
echo "Hello, World. On ${HOSTNAME}" > index.html
```
```
echo "Hello, World. On ${HOSTNAME}" 1>/dev/null
```
```
docker network inspect vNet01 1>/dev/null || exit 1
```
```
curl https://github.com/docker/compose/tags -o tags.html \
    && raw=$(cat tags.html | grep -m1 /tag/[0-9]\.[0-9][0-9]\.[0-9][^-rc0-9]) \
    && trim_left=${raw##*/} \
    && version=${trim_left%%\"*} \
    && curl -L "https://github.com/docker/compose/releases/download/$version/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose-$version \
    && chmod +x /usr/local/bin/docker-compose-$version \
    && if [[ -h /usr/bin/docker-compose ]]; then rm /usr/bin/docker-compose; fi \
    && ln -s /usr/local/bin/docker-compose-$version /usr/bin/docker-compose \
    && docker-compose --version
```

**Docker**  
как посмотреть командры сформировавшие образ без докер файла?  
как посмотреть логи контейнера?  
```
IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
6166f9cce87f        2 months ago        /bin/sh -c #(nop)  CMD ["/bin/sh" "-c" "nohu…   0B
864374282a1c        2 months ago        /bin/sh -c #(nop)  EXPOSE 8080:8080             0B
93cd0f88c3ad        2 months ago        /bin/sh -c curl -k https://busybox.net/downl…   1.02MB
805d0d13b097        2 months ago        /bin/sh -c bash web_server.sh                   30B
bbb22ef2347f        2 months ago        /bin/sh -c #(nop) COPY dir:79d33550593d3a835…   307B
9ee558ca9609        2 months ago        /bin/sh -c #(nop) WORKDIR /web                  0B
2cc07fbb5000        11 months ago       /bin/sh -c #(nop)  CMD ["/run-httpd.sh"]        0B
<missing>           11 months ago       /bin/sh -c chmod -v +x /run-httpd.sh            260B
<missing>           11 months ago       /bin/sh -c #(nop) ADD file:e079ee89bc45e39b0…   260B
<missing>           11 months ago       /bin/sh -c #(nop)  EXPOSE 80                    0B
<missing>           11 months ago       /bin/sh -c yum -y --setopt=tsflags=nodocs up…   56.2MB
<missing>           11 months ago       /bin/sh -c #(nop)  LABEL Vendor=CentOS Licen…   0B
<missing>           11 months ago       /bin/sh -c #(nop)  MAINTAINER The CentOS Pro…   0B
<missing>           12 months ago       /bin/sh -c #(nop)  CMD ["/bin/bash"]            0B
<missing>           12 months ago       /bin/sh -c #(nop)  LABEL org.label-schema.sc…   0B
<missing>           12 months ago       /bin/sh -c #(nop) ADD file:6f877549795f4798a…   202MB
```
What is the difference between docker image and container?  
What are layers?  
Can layers be writeble?  
What types of Storage Drivers you now? What's the differens  
How can you check overall docker config?  
What steps you have to take in order to configure network interaction between containers with names?  

**MySQL**  
How do you create a user?  
What is the difference between a "left" and a "right" join?  
How do you check which jobs are running?  
How would you take a backup of a MySQL database?  

**Python**  
```
from random import randint

class Die():
    
    def __init__(self, num_sides=6):
        self.num_sides=num_sides

    def roll(self):
        return randint(1, self.num_sides)
```
```
import os

os.path.abspath('folder')
```
```
import requests

response = requests.get('https://api.github.com')
json_response = response.json()
print(json_response['authorizations_url'])
```

**Other**  
What is GIT?  
What is a dynamically/statically linked file?  
What is the difference between Containers and VMs?  
What are the important aspects of a system of continuous integration and deployment?  
