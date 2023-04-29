---
layout: post
read_time: true
show_date: true
title: "Git,Github?"
date: 2023-04-29
img: ./assets/posts/20230416/interface.png
tags: [front-end, git,basic]
category: opinion
author: Armando Maynez
description: "Git,Github가 무엇인지 알아보고, Git Flow 개념을 이해해보자."
---
---

## 1. Github,Git이란?
- git이란 Distributed version control system이다. 즉, 직역하면 분산 버전 관리 시스템으로 분산해서 버전을 관리(변화,변경)를 하는 시스템을 말한다.
- github라는 Web Service의 주요 기능인 원격 저장소 역할을 한다.
- GoogleDrive 같은 원격 저장소와는 버전으로 관리 되어 하위 버전 이동 또는 버전 업데이트가 자유롭다.
- github는 이러한 git을 사용하여 현업과 프로젝트 버전관리등의 유용한 기능을 하는 개발자의 커뮤니티이다.

---

## 2. 그래서 버전 관리를 왜 하는데?
- 다양한 이유가 있지만 먼저 간단하게 시각적으로 보자면 아래와 같은 상황을 방지하기 위함이다.
> "조별과제_김원빈.pptx"<br>
> "조별과제_김원빈_성준수정.pptx"<br>
> "조별과제_김원빈_성준수정_최종.pptx"<br>
> "조별과제_김원빈_성준수정_최종_의최종.pptx"<br>
> "조별과제_김원빈_성준수정_최종_의최종_을철현수정.pptx"<br>
> "조별과제_김원빈_성준수정_최종_의최종_을철현수정_최종.pptx"<br>
>  . . .
- 위와 같은 방식을 버전 관리라고 한다. 즉, 과거 파일을 백업해두는 방법이다. 위 같은 방식도 작업하기엔 문제도 없고 백업 기능도 있기에 괜찮아 보일 수 있으나 큰 문제가 있다.
- 위 파일은 조별과제이다. 개인이 작업하는게 아니라 조원들이 관리하다가 너도나도 파일을 수정한다면 파일 백업 의미가 없어져 버린다.
- 아래와 같은 이유로 깃허브를 사용한다고 할 수 있다.

[팀 프로젝트 버전 관리의 문제]<br>
1) 여러 개의 파일 버전을 일관되게 관리하기 힘들다.(누가 가장 최신 파일을 가지고 있는지 모른다.<br>
2) 누가/무엇을/어떻게 변경하였는지 기록,확인,공유가 어렵다.<br>
3) 서로의 변경 내역을 덮어씌우거나 지워버려 오류가 발생할 수 있다.<br>
4) 변경 전 버전을 특정할 수 없으므로 내용을 이전 상태로 돌리기도 어렵다.<br>
![image](https://user-images.githubusercontent.com/61172021/92212736-65180200-eecd-11ea-8756-eb669f047081.png)

---
## 3. Git-Flow 개념 이해하기
- git-flow는 과거 Vincent Driessen이라는 사람의 블로그를 통해 알려진 Git 개발 방식의 방법론으로 기능적인 것이 아닌 약속의 의미를 가지고 있는 방법론이다.
- git-flow는 아래와 같이 5가지 [브랜치(branch)](#단어정리)로 나뉜다.

[Git-Flow 전략]<br>
- <b>master</b> : 기준인 역할을 하는 브랜치로 제품을 배포하는 최종 브랜치이다.<br>
- <b>develop</b> : 개발할 때의 메인 브랜치로. 구현해야할 기능이 발생하면 feature 브랜치를 생성 및 개발, 구현 완료 후 develop 브랜치로 병합한다. 다음 배포 버전까지 개발 완료 후 [QA Test](#단어정리)를위해 release 브랜치로 [머지(merge)](#단어정리)된다<br>
- <b>feature</b> : 이슈 및 기능을 구현하기 위해 생성하는 브랜치로 develop 브랜치에서 생성한다. 기능 구현이 완료되면 develop 브랜치에 머지하고 feature 브랜치는 삭제한다.<br>
- <b>release</b> : develop에 저장되어 QA를 진행하여 통과 시 master 브랜치에 머지하는 QA 진행 브랜치이다.<br>
- <b>hotfix</b> : 게임을 한 사람들에게는 익숙한 이름의 브랜치로 배포 후 release 브랜치에서 발견 못한 버그가 발생하여 긴급한 수정이 필요할 때 생성하는 브랜치이다. master에서 생성하고 수정 후 master, develop 브랜치에 머지하고 hotfix 브렌치는 삭제한다.<br>

## 4. Git-Flow 상세
- 위에 git-flow에 사용되는 브랜치를 알아봤다. 하지만 저렇게 정의를 해두는 것은 알겠지만 정의만 보고 흐름이 잘 보이지 않는다.
- 그렇다면 각 브랜치의 모습을 하나씩 보며 흐름을 이해해보자.

<b>[master branch]</b><br>
- 배포가능한 상태를 관리하는 브랜치<br>

<b>[develop branch]</b><br>
- 다음 버전을 개발하는 브랜치
- 평소 개발 시 기준이 되는 개발 브랜치이다.<br>

![image](https://lh4.googleusercontent.com/CZlG9QPr4RYMGAJ3z2ihWV6UuyJRqEmYSwm4Du3AeaFCc2-lrrEG-rWA6YkWKyFvAye_uKv0123vXLt4JY_dey_KkDk8VdPAHvDOgzLg2pwTE0k6li-dL_YUWpP-8Ck8Xrbx4ouS)

<b>[feature branch]</b><br>
- 기능을 개발하는 브랜치로 develop 브랜치에서 뻗어나와 좀 더 세부적으로 개발하기 위한 역할을 하는 보조 브랜치이다.
- feature 브랜치는 기능을 완성할 때까지 유지하며, 완료되면 develop 브랜치에 머지한다.
- 물론 기능이 별로다 싶으면 버린다. (develop에 머지하지 않았으니 영향을 미치지 않는다. 그러니 확실하다 싶으면 머지하는 것이 중요하다.)

![image](https://lh6.googleusercontent.com/J9X6SYLWwSLiLb6JAd_HBMFeTXpzwIZIMUkqtJpXZzi5cg42gIHLx3F99X-wSVIoFEc0u7NCY08yl-xTFolFlwfR0ytJWxZntoZS3-5WWq_oAlIO_MfJWKQfQYur_8ed7D_vzPF3)

<b>[release branch]</b><br>
- 필터 역할을 하는 브랜치로 develop에서 master로 머지하기 전에 최종 수정을 위해 QA하는 브랜치이다.
- 중요한 것은 release 브랜치에서 수정된 사항이 있으면 develop 브랜치에도 머지를 시켜줘야 다음 버전 개발에 꼬이지 않는다.

![image](https://lh5.googleusercontent.com/4mXmoEov9sqhCEo6vxFF8eOrvrc5hyo0SvW6YLgJMoauuejV0ketnm9yxjc1JyiUqjZnWwMCQr71JATvU1mAlxk3NPrQcglpWTpaIbIL1aiJbVXJ2e4DSocSo5eeG_I6zOQVfZ9A)

<b>[hotfix branch]</b><br>
- 배포 버전에서 긴급 수정이 필요할 때, master에서 분기하는 브랜치이다.
- 긴급 수정을 하는 동시에 develop 브랜치에서 아무러 작용없이 개발할 수 있어 나뉜 브랜치이며, 수정 후 master에 바로 머지를 한다.
- 이 또한 중요한 것은 수정 후 release 브랜치처럼 develop 브랜치에도 머지해야하는 것이다.

![image](https://lh5.googleusercontent.com/_jcNDU-WEGylP-1Z5CFOIYBDjwOmaqUi6DslzKGZ39rts9IXEEBdyq7NvF1jrlXnLg2dn_mL-tnvINUrUFSx4UOlAkOov_EpwW6eF1zRHYEK8xRB__GyG5HrpEWWFjHNa23WhF8I)

- 최종적으로 보는 흐름

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdSKdav%2FbtrCVRy7XUT%2FLKQdnMfcWPsCPf6ogKMq90%2Fimg.png)


## 단어정리
- 브랜치(branch) : 직역하면 나뭇가지란 뜻으로 직역 뜻과 같이 나뭇가지 처럼 뻗어나가는 가지 중 한가지를 말하며 Git 개발 작업에서는 이를 하나의 작업라인을 말할 때 사용한다.
- QA Test : Quality Assurance Test로 품질 보증 시험으로 소프트웨어가 개발 되었을 때, 이것이 적절한 디자인 패턴을 적재적소에 사용해 확작성이 있고 유지보수가 좋은 코드인지, 기존 소프트웨어 보다 좋은 또는 편리한 기능을 제시하는지, 기존 소프트웨어보다 성능면에서 좋은지 검증하는 단계라 볼 수 있다.
- 머지(merge) : 병합이라는 뜻을 가진 것처럼 나뭇가지로 뻗어나간 수 많은 나뭇가지 중 어떠한 나뭇가지인 작업라인을 또다른 작업라인으로 병합 시켜준다는 말이다.