# gitlabCE_management_experience
This repository is to summarise my experience working on managing gitlab ce server in UbuntuOS, known as Omnibus gitlab
#==========================================
## Setup
### Using apt-get package
- Preparation: (Install postfix is an optional if you want to use the email service)
  >> sudo apt update
  >> sudo apt install ca-certificates curl openssh-server postfix
- Add gitlab repository into your system
  >> curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.deb.sh | sudo bash
- Install the package: Check [3] for the list of versions
  >> sudo apt install gitlab-ce=<version>
- Configuration:
  - Setup external url which will be used for http/https push/fetch/clone service. If you have domain name, add it to here. If you want use gitlab at your local network, you can add your host server ip address. To configure, open /etc/gitlab/gitlab.rb and look for below param, and replace 'https://example.com' by your input.
    >> external_url 'https://example.com'
  - Setup alert email service: The system will send the alerts to this email if there is something wrong with your SSL certificate. It works only if you install postfix. I obmit this step. To configure, open /etc/gitlab/gitlab.rb and look for below param, and replace the example email by your email.
    >> letsencrypt['contact_emails'] = ['bob@example.com']
  - Update config: Save changes and close gitlab.rb. Then execute below command
    >> sudo gitlab-ctl reconfigure
### Using gitlab docker image
## Backup data
## Upgrade version
## Migrate to other host machines
## Reference:
1. [General installation guide](https://docs.gitlab.com/omnibus/installation/)
2. [On Ubuntu installation guide](https://about.gitlab.com/install/#ubuntu)
3. [Gitlab version list]
