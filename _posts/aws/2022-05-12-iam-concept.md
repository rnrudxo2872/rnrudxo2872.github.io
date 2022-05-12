---
date: 2022-05-12
title: IAM, 사용자 계정 생성, 권한 부여
categories:
  - 개인공부
  - aws
tags:
  - aws
  - IAM
  - 권한
---

# 권한관리

AWS IAM
IAM(AWS Identity and Access Management)은 AWS의 권한을 관리하는 서비스 입니다. 처음 AWS에 계정을 이메일로 생성하면 모든 서비스에 접근할 수 있는 SSO(Single Sign-ON) ID가 생성되고 이를 **루트 권한**이라고 합니다.

사내에서 AWS를 이용하고자 하는 경우에 각자의 부서/팀별로 계정을 생성하여 부여합니다. 이때 IAM을 이용하여 필요한 권한을 세분화하여 Role을 부여함으로써 불필요한 접근을 막을 수 있습니다.

IAM에서는 AWS 계정 인증에 MFA(Multi Factor Authentication)를 지원합니다. 여기서 팩터(factor)란 사용자의 신원을 확인하는 방법에 따라서 지식 기반, 소유 기반, 속성 기반의 인증으로 총 3가지 방법으로 나누어 지는데, 이를 인증 팩터라고 합니다.

- 지식 기반 - ID/PW와 같이 알고 있는 인증 정보 이용
- 소유 기반 - 휴대폰 SMS인증 등 사용자가 소유한 것을 이용
- 속성 기반 - 고유의 속성을 이용하는 것으로 지문 인식, 홍체 인식 등을 이용

AWS 계정 인증이 지원하는 MFA란 보안을 강화하기 위해 사용자들에게 위의 싱글 팩터가 아닌 멀티 팩터를 지원한다는 것 입니다. 이를 2Factor 인증이라고 하고, 2Factor 인증은 두 가지의 팩터를 사용해서 인증하는 방식입니다.

IAM 에서는 크게 네가지를 구분해야 합니다.

1. IAM User - 사용자
1. IAM Group - 사용자 그룹
1. IAM Role - 권한
1. IAM Policy - 정책

**권한이 열쇠라고 가정하면 정책은 열쇠가 어떤 열쇠인지 설명한거라고 생각합니다.**

IAM Policy는 JSON 형식으로 작성합니다.

```json
{
  "Version": "2022-05-15",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::test/*",
      "Principal": {
        "AWS": "arn:aws:iam::AWS-account-ID:user/user0name"
      }
    }
  ]
}
```

Principal은 리소스에 접근 허용, 불허용 되는 보안 주체를 지정하는 것이며 이는 User, Group, Role을 넣습니다.  
Resource는 ARN이 들어가는데 이 때 ARN이란 'Amazon Resource Name'의 약자입니다.

<br>

```bash
arn:partition:service:region:account-id:resource-id
arn:partition:service:region:account-id:resource-type/resource-id
arn:partition:service:region:account-id:resource-type:resource-id
```

- partition: 지역(aws &rarr; 전체, aws-cn &rarr; 중국)
- service: 서비스명(s3)
- region: 리전(ap-northeast-2)
- account-id: AWS ID
- resource-id: 리소스 식별자
