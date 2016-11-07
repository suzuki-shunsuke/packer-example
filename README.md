# packer-example

## Example 1 Ansible + GCP

Google Developer Console から Service アカウントのキーをダウンロードし、
secret/gcp-account.jsonに配置

```
$ packer validate packer.json
$ packer build packer.json
```

source_imageには英数字と-しか使えないので注意

```json
{
  "builders": [{
    "type": "googlecompute",
    "account_file": "secret/gcp-account.json",
    "project_id": "gcp-project",
    "source_image": "ubuntu-1604-xenial-v20161020",
    "zone": "asia-east1-c",
    "image_name": "sample-1-0-0",
    "ssh_username": "ubuntu"
  }],
  "provisioners": [
    {
      "type": "ansible",
      "playbook_file": "./playbook.yml"
    }
  ]
}
```
