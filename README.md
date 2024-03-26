# "GitLab" - Ткачев Артём

---

## Задание 1
Что нужно сделать:

1.Разверните GitLab локально, используя Vagrantfile и инструкцию, описанные в этом репозитории.

2. Создайте новый проект и пустой репозиторий в нём.

3. Зарегистрируйте gitlab-runner для этого проекта и запустите его в режиме Docker. Раннер можно регистрировать и запускать на той же виртуальной машине, на которой запущен GitLab.

Ответ:
![alt text](https://github.com/Artem-Tckachew/8-03-hw/blob/main/1.png)

---

### Задание 2
Что нужно сделать:

1.Запушьте репозиторий на GitLab, изменив origin. Это изучалось на занятии по Git.

2.Создайте .gitlab-ci.yml, описав в нём все необходимые, на ваш взгляд, этапы.

Ответ:
```
Поле для вставки кода...                            
stages:
  - test
  - build

test:
  stage: test
  image: golang:1.17
  script: 
   - go test .

build:
  stage: build
  image: docker:latest
  script:
   - docker build .
```

![alt text](https://github.com/Artem-Tckachew/8-03-hw/blob/main/2.png)
![alt text](https://github.com/Artem-Tckachew/8-03-hw/blob/main/3.png)
![alt text](https://github.com/Artem-Tckachew/8-03-hw/blob/main/5.png)


---

### Задание 3
Измените CI так, чтобы:

1.этап сборки запускался сразу, не дожидаясь результатов тестов;

2.тесты запускались только при изменении файлов с расширением *.go.

Ответ:
```
stages:
  - test
  - build

test:
  stage: test
  only:
    changes:
      - sdvps-materials/*.{go}
  image: golang:1.17
  script:
   - go test .

build:
  stage: .pre
  image: docker:latest
  script:
   - docker build .
```

![alt text](https://github.com/Artem-Tckachew/8-03-hw/blob/main/4.png)
