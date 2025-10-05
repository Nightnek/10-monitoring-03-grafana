# Домашнее задание к занятию 14 «Средство визуализации Grafana»

### Задание 1

1. Используя директорию [help](./help) внутри этого домашнего задания, запустите связку prometheus-grafana.
1. Зайдите в веб-интерфейс grafana, используя авторизационные данные, указанные в манифесте docker-compose.
1. Подключите поднятый вами prometheus, как источник данных.
1. Решение домашнего задания — скриншот веб-интерфейса grafana со списком подключенных Datasource.

<img width="1214" height="575" alt="image" src="https://github.com/user-attachments/assets/5f62091e-8115-407b-8b11-de76b6b84d24" />


## Задание 2

Изучите самостоятельно ресурсы:

1. [PromQL tutorial for beginners and humans](https://valyala.medium.com/promql-tutorial-for-beginners-9ab455142085).
1. [Understanding Machine CPU usage](https://www.robustperception.io/understanding-machine-cpu-usage).
1. [Introduction to PromQL, the Prometheus query language](https://grafana.com/blog/2020/02/04/introduction-to-promql-the-prometheus-query-language/).

Создайте Dashboard и в ней создайте Panels:

- утилизация CPU для nodeexporter (в процентах, 100-idle);
    > 100-(avg by (instance) (rate(node_cpu_seconds_total{job="nodeexporter",mode="idle"}[1m]))*100)
- CPULA 1/5/15;
    > node_load1
    > node_load5
    > node_load15
- количество свободной оперативной памяти;
    > node_memory_MemFree_bytes/(1024*1024)
- количество места на файловой системе.
    > node_filesystem_size_bytes{mountpoint="/",fstype!="rootfs"}/(1024*1024)
    > node_filesystem_avail_bytes{mountpoint="/",fstype!="rootfs"}/(1024*1024)

Для решения этого задания приведите promql-запросы для выдачи этих метрик, а также скриншот получившейся Dashboard.

<img width="1219" height="727" alt="image" src="https://github.com/user-attachments/assets/1cf2c692-2b47-4f4f-8457-bd33f5deb383" />


## Задание 3

1. Создайте для каждой Dashboard подходящее правило alert — можно обратиться к первой лекции в блоке «Мониторинг».
1. В качестве решения задания приведите скриншот вашей итоговой Dashboard.

## Задание 4

1. Сохраните ваш Dashboard.Для этого перейдите в настройки Dashboard, выберите в боковом меню «JSON MODEL». Далее скопируйте отображаемое json-содержимое в отдельный файл и сохраните его.
1. В качестве решения задания приведите листинг этого файла.

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
