## Основы работы с Kubernetes

### Домашняя работа № 5

### Используемый Docker образ
```shell
docker pull elenkavolodina/otus_hw5
```

### Миграции
```shell
Команда alembic upgrade head вызывается в initContainers в hw_5_chart/templates/deployment.yaml
```

### Запуск приложения
```shell
kubectl create namespace otus-hw-5-volodina
helm upgrade --install -n otus-hw-5-volodina otus-hw-5-volodina ./hw_5_chart
```

### Удаление приложения
```shell
helm uninstall otus-hw-5-volodina -n otus-hw-5-volodina
```

### Postman коллекция
```shell
newman run tests/otus_hw_5.postman_collection.json
```

```shell
newman

otus_hw_5

→ Registration user_1
  POST arch.homework/registration [200 OK, 966B, 408ms]
  ✓  Registration user_1 status code is 200

→ Registration user_2
  POST arch.homework/registration [200 OK, 966B, 321ms]
  ✓  Registration user_2 status code is 200

→ Check auth user
  GET arch.homework/auth [401 Unauthorized, 118B, 7ms]
  ✓  user not authenticated

→ Get profile not authorization user
  GET arch.homework/user/profile [401 Unauthorized, 308B, 8ms]
  ✓  Authorization required for access profile

→ Login user_1
  POST arch.homework/login [200 OK, 191B, 542ms]
  ✓  Login user_1 success

→ Check auth user_1
  GET arch.homework/auth [200 OK, 804B, 7ms]
  ✓  user_1 authenticated

→ Update authorization  user_1
  POST arch.homework/user/profile [200 OK, 1.69kB, 25ms]
  ✓  Update user_1 success

→ Delete user_1
  DELETE arch.homework/user/delete [204 No Content, 120B, 12ms]

→ Logout user_1
  GET arch.homework/logout [200 OK, 147B, 7ms]
  ✓  Logout user1

→ Login user_2
  POST arch.homework/login [200 OK, 191B, 287ms]
  ✓  Login user2 success

→ Check auth user_2
  GET arch.homework/auth [200 OK, 804B, 11ms]
  ✓  user_2 authenticated

→ Get profile user_2
  GET arch.homework/user/profile [200 OK, 1.7kB, 13ms]
  ✓  Get profile user_2

→ Delete user_2
  DELETE arch.homework/user/delete [204 No Content, 120B, 15ms]

→ Logout user_2
  GET arch.homework/logout [200 OK, 147B, 9ms]
  ✓  Logout user2

┌─────────────────────────┬────────────────────┬───────────────────┐
│                         │           executed │            failed │
├─────────────────────────┼────────────────────┼───────────────────┤
│              iterations │                  1 │                 0 │
├─────────────────────────┼────────────────────┼───────────────────┤
│                requests │                 14 │                 0 │
├─────────────────────────┼────────────────────┼───────────────────┤
│            test-scripts │                 26 │                 0 │
├─────────────────────────┼────────────────────┼───────────────────┤
│      prerequest-scripts │                 14 │                 0 │
├─────────────────────────┼────────────────────┼───────────────────┤
│              assertions │                 12 │                 0 │
├─────────────────────────┴────────────────────┴───────────────────┤
│ total run duration: 2s                                           │
├──────────────────────────────────────────────────────────────────┤
│ total data received: 4.96kB (approx)                             │
├──────────────────────────────────────────────────────────────────┤
│ average response time: 119ms [min: 7ms, max: 542ms, s.d.: 178ms] │
└──────────────────────────────────────────────────────────────────┘

```
