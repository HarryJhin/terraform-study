# Terraform Study

## 테라폼이란?

테라폼(Terraform)은 **HashiCorp**에서 개발한 오픈 소스 인프라스트럭처 자동화 도구입니다. 주요 특징은 다음과 같습니다:

1. 코드로 인프라 관리: 클라우드 및 온프레미스 리소스를 코드로 정의하고 프로비저닝할 수 있습니다.
2. 다중 클라우드 지원: AWS, Google Cloud, Azure 등 다양한 클라우드 플랫폼을 지원합니다.
3. 선언적 구성: `HCL`(HashiCorp Configuration Language)을 사용하여 원하는 인프라 상태를 선언합니다.
4. 상태 관리: 인프라의 현재 상태를 추적하고 일관성을 유지합니다.
5. 자동화된 인프라 프로비저닝: 코드 한 줄로 복잡한 인프라 환경을 신속하게 생성하고 변경할 수 있습니다.

## 테라폼 설치

### macOS

```shell
brew install terraform
```

### Windows

1. [Terraform 다운로드 페이지](https://www.terraform.io/downloads.html)에서 `Windows`용 바이너리 파일을 다운로드합니다.
2. 압축을 해제한 후 `terraform.exe` 파일을 `PATH` 환경 변수에 추가합니다.
3. 설치 확인:
    ```shell
    terraform --version
    ```

## 테라폼 기본 개념

테라폼을 사용하기 위해 알아야 하는 몇 가지 기본 개념이 있습니다.

### 1. Provider

테라폼이 인프라를 관리하는 대상을 `Provider`라고 합니다. AWS, Google Cloud, Azure 등 다양한 클라우드 플랫폼을 지원합니다.

```hcl
provider "aws" {
  region = "ap-northeast-2"
}
```

### 2. Resource

`Resource`는 인프라를 구성하는 각 요소를 정의하는 블록입니다. EC2 인스턴스, VPC, 서브넷 등이 `Resource`에 해당합니다.

```hcl
resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}
```

### 3. Module

`Module`은 특정 기능을 가진 코드 블록을 재사용하기 위한 단위입니다. 코드를 모듈로 분리하여 관리하면 코드의 가독성과 재사용성을 높일 수 있습니다.

```hcl
module "vpc" {
  source = "./modules/vpc"
}
```

### 4. State

테라폼이 관리하는 인프라의 현재 상태를 `State` 파일에 저장합니다. 이 파일은 테라폼 명령을 실행할 때 생성되며, 인프라의 변경 이력을 추적하고 일관성을 유지하는 데 사용됩니다.

```shell
terraform.tfstate
```

## 테라폼 명령어

테라폼을 사용할 때 자주 사용하는 명령어는 다음과 같습니다.

### 1. `terraform init`

테라폼 프로젝트를 초기화합니다. Provider 플러그인을 설치하고 모듈을 불러옵니다.

```shell
terraform init
```

### 2. `terraform plan`

테라폼이 실행할 변경 사항을 미리 확인합니다. 실제로 인프라를 변경하지는 않습니다.

```shell
terraform plan
```

### 3. `terraform apply`

테라폼이 변경 사항을 적용하여 인프라를 생성하거나 업데이트합니다.

```shell
terraform apply
```

### 4. `terraform destroy`

테라폼이 관리하는 인프라를 삭제합니다.

```shell
terraform destroy
```

## 참고 자료

- [Terraform 공식 문서](https://www.terraform.io/docs/index.html)
- [Terraform Tutorial](https://learn.hashicorp.com/collections/terraform/aws-get-started)
