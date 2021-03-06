# CI/CD Workflow

## Portfolio
My portfolio [hay-kot.dev](https://hay-kot.dev) is built on Nuxt. It uses Github actions to build and publish to my Linode server on push to the `master` branch. GitHub actions will then SSH into my server, pull down the latest changes from GitHub and deploy the site using docker. During docker build the site is built and deployed as a static site behind a Caddy web server that is then proxies by another Caddy web server. Having a separate server allows changes to occur on the portfolio without effecting other services.

## Wiki
This wiki is built on Mkdocs, a beautiful and easy to use documentation platform. It uses GitHub actions to build and publish to my Linode server on push to the `master` branch. Similar to the Portfolio, it uses SSH to pull down the changes from github and build the site and deploy behind a Caddy server to host the static files. 

## Ansible
Currently, I have no Ansible CI/CD... But it's on the list! 