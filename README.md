# AWS RDS MySQL Terraform Demo

This is a minimal Terraform configuration to provision an **AWS RDS MySQL 8.0** instance for demo/testing purposes using the default VPC.

---

##  What It Does

- Provisions a single MySQL RDS instance
- Uses default AWS networking (no subnet group or security group customization)
- Designed for demo use, **not production**

---

##  Project Structure

.
├── main.tf # RDS MySQL resource
├── provider.tf # AWS provider config
├── variables.tf # Input variables
├── terraform.tfvars # Variable values
├── output.tf # Outputs RDS endpoint
├── backend.tf # (Optional) Remote state backend
└── .github/
└── workflows/
└── deploy.yml # GitHub Actions workflow
 
---

##  Required Secrets in GitHub

In your GitHub repo, go to:

**Settings → Secrets and Variables → Actions** and add:

| Secret Name              | Description        |
|--------------------------|--------------------|
| `AWS_ACCESS_KEY_ID`      | Access Key         |
| `AWS_SECRET_ACCESS_KEY`  | Secret Key         |
|                                               |

>  **How to get these:**  
> Go to the AWS Console → IAM → Users → Security Credentials → _Create access key_  
> You will receive an **Access Key ID** and **Secret Access Key**.

---

##  GitHub Actions CI/CD

The included workflow file `deploy.yml` will:

- Trigger on every push to the `main` branch
- Perform:
  1. Code checkout
  2. AWS credential setup
  3. Terraform init, validate, plan, and apply

---

##  Outputs

After successful deployment:

- RDS Endpoint will be printed in the Terraform output
- You can use tools like:
  - **DBeaver**
  - **MySQL Workbench**
  - **CLI (mysql client)**

To connect using:
```
 mysql -h <endpoint> -P 3306 -u foo -p

```

---

## Note

This setup is for demo or development use only. It does not:

Set up private networking or firewall rules

Enable backup retention or multi-AZ deployment

Manage secrets securely (like password encryption or rotation)

---

## Cleanup

To destroy all created resources:

 terraform destroy -auto-approve

---

## References

   Terraform AWS Provider Docs

   Amazon RDS Documentation

  https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/db_instance

