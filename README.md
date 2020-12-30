# Locust

오픈소스 부하테스트 도구. 파이썬 스크립트 기반. 설치 및 사용 편리. 파이썬 스크립트 기반 테스트 시나리오 작성. 쿠버네티스 적용 용이.


## Install

```bash
// locust 설치
$ pip3 install locust
```
```bash
// locust 버전 확인
$ locust -V
```

## Quick Start
```bash
$ locust
// http://127.0.0.1:8089/ 접속
```

## Example

```python
from locust import HttpUser, TaskSet, task, between

def index(l):
    l.client.get("/")

def stats(l):
    l.client.get("/stats/requests")

class UserTasks(TaskSet):
    # one can specify tasks like this
    tasks = [index, stats]

    # but it might be convenient to use the @task decorator
    @task
    def page404(self):
        self.client.get("/does_not_exist")

class WebsiteUser(HttpUser):
    host = "http://127.0.0.1:8089"
    wait_time = between(2, 5)
    tasks = [UserTasks]
```

## Links

* Website: [locust.io](https://locust.io)
* Documentation: [docs.locust.io](https://docs.locust.io)
* Code/issues: [Github](https://github.com/locustio/locust)