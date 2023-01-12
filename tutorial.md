# this is the main repo for code samples of workflows



[E1 - GitHub Actions: Write your first workflow with GitHub APIs || Beginner friendly tutorial](https://www.youtube.com/watch?v=-hVG9z0fCac&list=PLArH6NjfKsUhvGHrpag7SuPumMzQRhUKY&index=1)

# how the CI works

when PR is created, need do:
1. automatic the build
2. execute tests
3. linting
4. security scanning
5. deploy to test env (e.g. staging) (option)


# generate ssh-keygen rsa
`ssh-keygen -t rsa -b 4096 -C "ec2@aws" -f ~/.ssh/tmp/id_sample_server`

- -t: type
- -b: size
- -C: user
- -f: file name with path

# run docker 
1. `docker run -tid ubuntu:latest bash`
2. `docker ps`
3. `docker exec -it containerID/Name /bin/bash`

# install terraform
1. install terraform and dependencies
`apt install -y gnupg software-properties-common`
2. install gpg key
```bash
wget -O- https://apt.releases.hashicorp.com/gpg | \
    gpg --dearmor | \
    sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
```
3. verify the key's fingerprint
```bash
gpg --no-default-keyring \
    --keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg \
    --fingerprint
```

4. add repo

Official
```bash
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] \
    https://apt.releases.hashicorp.com focal main" |      tee /etc/apt/sources.list.d/hashicorp.list
```    

5. install terraform
```bash
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] \
    https://apt.releases.hashicorp.com $(lsb_release -cs) main" | \
    tee /etc/apt/sources.list.d/hashicorp.list
```
6. add the public key local/variables.tfvars.example and rename to variables.tfvars

7. `terraform init`

8. `terraform validate` to validate the configures for terraform

9. validate the variable file `terraform plan --var-file=variables.tfvars` to run this command, you need to set up aws access key, please follow: `to use aws-cli` and `get aws access key ID` section. `terraform plan` command will reveal what terraform plan going to create/modify/destory....
10. using `terraform apply --var-file=variables.tfvars` to execute the plan


>Destroy: 
>
> `terraform destroy --var-file=variables.tfvars`

WS Access Key ID [None]: AKIAYE7AL5WDZDRQ7WXK
AWS Secret Access Key [None]: *****


## to use aws-cli
1. install python and pip
2. `pip install awscli --force-reinstall --upgrade`

## to configure aws
1. run command `aws configure`
2. for the `AWS Access Key ID [None]:` see below:

## get aws access key ID:
1. go to aws, then user/security credentials
2. click `users`
3. click `add users`
4. put user name as `ferraform-cli` and tick `Access-key - programmatic access` in the select AWS credential type, then NEXT
5. select or create proper permissions and add tag and create the user
6. then you be able to get access key and secret access key 


