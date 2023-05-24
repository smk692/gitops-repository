# Gitops 준비단계


## 1. SSH key 

```
ssh-keygen -q -t rsa -N '' -m PEM -t rsa -b 4096 -C test -f ./id_rsa <<<y >/dev/null 2>&1
```
## 2. argocd 생성 및 로드벨런서 생성
### a. argocd 설치방법
- argo-cd > scripts > setup.sh 
```
cd management/argo-cd/scripts

# argocd 설치 실행
./setup.sh

kubectl get svc -A
-> LoadBalancer 에 있는 External-ip 주소를 복사해서 접속해봅니다.
-> sh 마지막 실행 결과 값은 비밀번호입니다. ex) admin/GVpqhSEgqGM8XVuu

```

### b. 접속 시 아래와 같이 나오며 톱니바퀴를 눌러서 Repo 를 연결해 줍시다.
<img width="1723" alt="image" src="https://github.com/smk692/service-repository/assets/42338823/03122d04-e68d-4348-a7fb-e47cb3dcd65b">

### c. CONNECT REPO USING SSH 클릭
- Name : service-repositoy
- Project : default
- Repository URL : git@github.com:smk692/service-repository.git

- SSH private key data : (READMD 맨 위 참고)로컬에서 생성한 id_rsa 값을 넣어줍니다.
<img width="1705" alt="image" src="https://github.com/smk692/service-repository/assets/42338823/84ef28f1-ab3f-4c34-abf1-f696d5c2296b">

Connect 버튼 클릭 시 Succescss 가 뜨면 성공입니다.

## Argo Rollout 및 플러그인 설치 스크립트 경로

### ArgoRollout 구성
- gitops-repository > management > argo-rollout > scripts > setup.sh $ chmod +x setup.sh && ./setup.sh


