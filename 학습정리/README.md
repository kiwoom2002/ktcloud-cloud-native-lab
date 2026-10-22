# 내 학습 정리 — kt cloud TECH UP 클라우드 네이티브

> 이 폴더는 김민규가 kt cloud TECH UP 클라우드 네이티브 과정에서 배운 내용을 정리한 문서입니다.
> 저장소 안의 실습·미션 문서와 `lab/` 설정 파일에서 **실제로 확인되는 내용만** 적었습니다.
> 과정 원본 자료(`01-docker/` ~ `06-모니터링/`, `lab/`)는 그대로 두었습니다.

## 한 줄 요약

**컨테이너 이미지 빌드부터 쿠버네티스 배포, 보안 게이트가 있는 CI/CD, GitOps 배포·롤백, 서비스 메시 트래픽 제어, 지표·로그·트레이스 기반 장애 분석까지 클라우드 네이티브 서비스의 전체 수명주기를 직접 실습했습니다.**

같은 앱(todo: web · api · db 3티어)을 과목마다 한 단계씩 발전시키고, 마이크로서비스 11개로 된 Online Boutique로 같은 기술을 다시 적용하는 흐름으로 배웠습니다.

```
Docker            →  Kubernetes        →  클라우드 보안            →  CI/CD                   →  서비스 메시           →  모니터링
이미지·Compose       Deployment·Service   Trivy·SecurityContext       GitHub Actions·Jenkins     Linkerd·Istio            Prometheus·Grafana
볼륨·네트워크        ConfigMap·PVC·Probe  RBAC·NetworkPolicy·PSA       Argo CD(GitOps)            mTLS·카나리·재시도        Loki·Tempo·경보·SLO
                     Ingress·Helm         Kyverno·SBOM·cosign          dev 자동 / prod PR 승인    Kiali
```

## 문서

| 문서 | 내용 |
|---|---|
| [01. 과목별 학습 내용](./01-과목별-학습-내용.md) | 과목마다 실습·미션에서 무엇을 했고 무엇을 배웠는지 |
| [02. 기술 키워드별 정리](./02-기술-키워드별-정리.md) | REST API, 컨테이너, 쿠버네티스, CI/CD, GitOps, MSA, IaC, DevSecOps, 서비스 메시, 관측성 — 키워드별로 배운 것과 **현업에서 기여할 수 있는 기술** |

## 실습 환경 (lab/ 에서 확인)

| 구분 | 내용 |
|---|---|
| OS | Ubuntu 24.04 VM (본인 배정 VM에 SSH 접속) |
| 클러스터 | kind — `lite`(노드 1개), `full`(컨트롤 플레인 1 + 워커 2, 서비스 메시 과목부터) |
| 도구 | kubectl, kind, helm, kustomize, k9s (버전 고정: `lab/.mise.toml`) |
| 설치 자동화 | `lab/Makefile` — `make up / down / reset`, `make ingress`(Traefik), `make kyverno`, `make jenkins`, `make argocd`, `make monitoring / logging / tracing` |
| 실습 앱 | todo(Node.js Express API + nginx + PostgreSQL), hello, files, memo-api(Python), Online Boutique v0.10.7(Google, 서비스 11개) |
