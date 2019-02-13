# AWS Server Setup

## Create AWS Server
* Select Location : Seoul
* Select Amazon Linux HVM
* Add Storage
* Config Security

---
## Create Elastic IP

---
## Creating Key Pair

### I. Creating Key Pair
#### Creating a Key Pair Using Amazon EC2
* https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2-key-pairs.html#having-ec2-create-your-key-pair

1. https://console.aws.amazon.com/console/home
1. service > EC2 > 네트워크 및 보안 > Key Pair > [Create Key Pair]
1. 'Key pair name' 지정 > [Create]
1. Local(PC) 에 KEY_PAIR_NAME.pem 파일 저장
1. KEY_PAIR_NAME.pem 의 퍼블릭 키 생성
    + PC 에서 Git Bash 를 이용하는 방법 ([PC용 Git Client 설치 필요](https://git-scm.com/downloads))
      ```console
      ]$ ssh-keygen -y -f /path_to_key_pair/KEY_PAIR_NAME.pem >> KEY_PAIR_NAME.pub
      ```
    + PuTTYgen 이용 하는 방법 ([PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html))

#### Creating a Key Pair Using Third-party
* TODO:

### II. Importing Your Own Public Key to Amazon EC2
* https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2-key-pairs.html#how-to-generate-your-own-key-and-import-it-to-aws

1. add New User (optional)
    ```console
    ]$ sudo adduser new_user
    ```
2. Create a .ssh directory
    ```console
    ]$ su - new_user
    ]$ cd ~
    ]$ mkdir .ssh
    ]$ chmod 700 .ssh
    ```
    
    upload KEY_PAIR_NAME.pub to .ssh directory

    ```console
    ]$ touch .ssh/authorized_keys
    ]$ chmod 600 .ssh/authorized_keys

    ]$ cd .ssh
    ]$ cat KEY_PAIR_NAME.pub >> authorized_keys
    ```

* TODO: