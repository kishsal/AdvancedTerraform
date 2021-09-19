# AdvancedTerraform

https://www.linkedin.com/learning/advanced-terraform/

### Create a PEM key
```
aws ec2 create-key-pair --key-name tf_key --query 'KeyMaterial' --output text > tf_key.pem
```

### Deploy resources in 01_05_base
  - Terraform init, plan, apply

### SSH into instance
  - Make a change to the key
  ```
  chmod 400 tf_key.pem
  ```
  - To ssh in:
  ```
  ssh -i "tf_key.pem" ec2-user@ec2-18-222-24-10.us-east-2.compute.amazonaws.com
  ```
  - If you logged in successfully, then enter `exit` to close session

### Check AWS resources
- Enter the following commands to review AWS resources
  ```
  aws ec2 describe-instances --query "Reservations[].Instances[].InstanceId" --output table
  ```
  OUTPUT:
  ```
    -------------------------
    |   DescribeInstances   |
    +-----------------------+
    |  i-07d3381a003dd27df  |
    |  i-0bb77aff0b136cbb4  |
    +-----------------------+
    ```

### Destroy Resources
- Enter the following to remove the resources:
```
terraform destroy
```