# AWS

In-premisis vs AWS tech stack

![](<.gitbook/assets/image (4).png>)

![](<.gitbook/assets/image (8).png>)





To create IAM user and Access Keys:

{% embed url="https://tntdrive.com/where-do-i-get-my-access-keys.aspx" %}

```
$ docker run --rm -ti -v ~/.aws:/root/.aws amazon/aws-cli configure
AWS Access Key ID [None]: A*************J
AWS Secret Access Key [None]: T******************b
Default region name [None]: ap-south-1
Default output format [None]: json


$ docker run --rm -ti -v ~/.aws:/root/.aws amazon/aws-cli iam get-user
{
    "User": {
        "Path": "/",
        "UserName": "full-access-user-jai",
        "UserId": "A*************J",
        "Arn": "arn:aws:iam::07********8:user/full-access-user-jai",
        "CreateDate": "2020-07-26T20:18:29+00:00"
    }
}

$ docker run --rm -ti -v ~/.aws:/root/.aws amazon/aws-cli s3 ls
```

[https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-docker.html](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-docker.html)





