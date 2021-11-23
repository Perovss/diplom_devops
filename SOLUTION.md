# Дипломная работа к профессии "DevOps-инженер"

Цели:
1. Подготовить облачную инфраструктуру на базе облачного провайдера AWS.
2. Запустить и сконфигурировать kubernetes-кластер.
3. Установить и настроить систему мониторинга.
4. Настроить и автоматизировать сборку тестового приложения с использованием Docker-контейнеров.
5. Настроить CI для автоматической сборки и тестирования.
6. Настроить CD для автоматического развёртывания приложения.

Этапы выполнения:

## Создание облачной инфраструктуры


Ожидаемые результаты:
1. Terraform сконфигурирован и создание инфраструктуры посредством terraform возможно без дополнительных ручных действий.
1. Полученная конфигурация инфраструктуры является предварительной, поэтому в ходе дальнейшего выполнения задания возможны изменения.

Установлена последняя стабильная версия [Terraform](https://www.terraform.io/).

```html
serge@notebook:~/lessons$ terraform --version
Terraform v1.0.11
on linux_amd64
```

[Cсылка на конфигурацию инфраструктуры](https://github.com/Perovss/diplom_terraform_cloud)



## Создание кубернетес кластера

Ожидаемый результат:

1. Работоспособный кубернетес кластер.
2. В файле `~/.kube/config` находятся данные для доступа к кластеру.
3. Команда `kubectl get pods --all-namespaces` отрабатывает без ошибок.

## Создание тестового приложения

Ожидаемый результат:
1. [Git репозиторий с тестовым приложением и Dockerfile.](https://gitlab.com/perov.ss/netology-diplom)
1. [Dockerhub регистр с собранным docker image.](https://gitlab.com/perov.ss/netology-diplom)

## Подготовка кубернетес конфигурации

Ожидаемый результат:
1. [Git репозиторий с конфигурационными файлами для настройки кубернетес.](https://github.com/Perovss/diplom_k8s_config/tree/main/manifests)
2. Http доступ к web интерфейсу grafana.
3. Дашборды в grafana отображающие состояние кубернет кластера.
4. Http доступ к тестову приложению

##  Установка и настройка CI/CD

Ожидаемый результат:
1. [Интерфейс ci/cd сервиса доступен по http.](https://gitlab.com/perov.ss/netology-diplom/-/pipelines)
2. При любом коммите в репозиторий с тестовым приложением происходит сборка и отправка в регистр докер образа.
3. При создании тега в репозитории происходит деплой соответсвующего докер образа.


##  Что необходимо для сдачи задания
1. [Репозиторий с конфигурационными файлами терраформа и готовность продемонстировать создание всех рессурсов с нуля.](https://github.com/Perovss/diplom_terraform_cloud)

2. Пример pull request с комментариями созданными atlantis'ом или снимки экрана из Terraform Cloud.![t2](/home/serge/lessons/diplom_devops/t2.png)

   ![t1](/home/serge/lessons/diplom_devops/t1.png)
3. Репозиторий с конфигурацией ansible, если был выбран способ создания кубернетес кластера при помощи ansible.

4. Репозиторий с Dockerfile тестового приложения и ссылка на собранный docker image.

5. Репозиторий с конфигурацией кубернетес кластера.

6. Ссылка на тестовое приложение и веб интерфейс графаны с данными доступа.



# Решение



pip3 install -r requirements.txt
ansible-playbook -i kubespray/inventory/mycluster/inventory.ini  kubespray/cluster.yml -u ubuntu --ask-pass -b --ask-become-pass 

ansible-playbook -i kubespray/inventory/diplom/inventory.ini kubespray/cluster.yml -e ansible_user=ubuntu -b --become-user=root





https://hub.docker.com/repository/docker/perovss/nginx.app



CI



https://gitlab.com/perov.ss/netology-diplom/-/jobs/1781112211
