# Cloudflare and Terraform using VSCode

Project to test out the integration of cloudflare with terraform.

Project includes VSCode dev containers for easy development. The container includes `Terraform` and `cf-terraforming` toolset.

<https://github.com/cloudflare/cf-terraforming>

## Usage

Setup `.envrc` in your terraform project root. You can copy the example file from this repo.

Use `cf-terraforming` to pull down resources into a terraform templates. You can generate templates and import resources into terraform state file.

### Generate `cloudflare_zero_trust_access_policy` resource

```bash
cf-terraforming generate --resource-type "cloudflare_zero_trust_access_policy" --terraform-binary-path "/usr/bin/terraform" >> zt_access_policy.tf
```

## License

MIT
