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
└── .github/workflows/deploy.yml # GitHub Actions workflow

yaml
Copy
Edit

---

##  Requirements

- Terraform ≥ 1.3
- AWS CLI or credentials
- An AWS default VPC in your chosen region
- GitHub repository with the following secrets:
  - `AWS_ACCESS_KEY_ID`
  - `AWS_SECRET_ACCESS_KEY`
  - `AWS_REGION`

---


## Outputs
RDS Endpoint – printed after deployment

Use any MySQL client (e.g., DBeaver, MySQL Workbench) to connect

## Note
This setup is for demo/testing purposes only.

 It does not:

Set up private networking or security groups

Enable automatic backups or multi-AZ failover

Store credentials securely

## Cleanup

 ## References
Terraform AWS Provider Docs

https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/db_instance

