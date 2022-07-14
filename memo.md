```terraform
provider "aws" {
  region     = "us-west-2"
  access_key = "my-access-key"
  secret_key = "my-secret-key"
}
```

다음과 같은 권한 부여와 관련된 기타 설정을 구성할 수 있습니다.

- profile
- shared_config_files
- shared_credentials_files

### Environment Variables

자격 증명은 `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY` 및 선택적으로 `AWS_SESSION_TOKEN` 환경 변수를 사용하여 제공할 수 있습니다. 리전은 AWS_REGION 또는 AWS_DEFAULT_REGION 환경 변수를 사용하여 설정할 수 있습니다.

### 자격 증명 얻기

Amazon Cognito를 사용하여 애플리케이션에 권한이 제한된 임시 자격 증명을 전달하면 사용자가 AWS 리소스에 액세스할 수 있습니다. 이 섹션에서는 자격 증명을 가져오는 방법과 자격 증명 풀에서 Amazon Cognito 자격 증명을 가져오는 방법을 설명합니다.

Amazon Cognito는 인증된 자격 증명과 인증되지 않은 자격 증명을 모두 지원합니다. 미인증 사용자는 자격 증명이 인증되지 않았으므로 앱 혹은 자격 증명의 인증이 중요하지 않은 경우 게스트 사용자 역할에 적합합니다. 인증받은 사용자는 타사 자격 증명 공급자(IdP)를 통해 또는 자격 증명을 인증받은 사용자 풀을 통해 애플리케이션에 로그인합니다. 미인증 사용자의 액세스 권한을 허용하지 않도록 리소스 권한 범위를 충분히 정했는지 확인하세요.

Amazon Cognito 자격 증명(identity)은 자격 증명(credential)이 아닙니다. AWS Security Token Service (AWS STS)에서 웹 자격 증명 연동 지원을 사용하여 자격 증명으로 교환되는 것입니다. 앱 사용자를 위해 AWS 자격 증명을 얻는 권장 방법은 AWS.CognitoIdentityCredentials를 사용하는 것입니다. 그러면 자격 증명 객체의 ID가 AWS STS를 사용하여 자격 증명용으로 교환됩니다.

https://docs.aws.amazon.com/ko_kr/cognito/latest/developerguide/getting-credentials.html
