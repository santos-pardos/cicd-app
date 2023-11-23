# cicd-app
## Setting up a Node.js Application
'''
.github/workflows

name: Node.js CI/CD

on:
  push:
    branches: [ "main" ]

jobs:
  build:
    runs-on: self-hosted
    strategy:
      matrix:
        node-version: [18.x]
        # See supported Node.js release schedule at https://nodejs.org/en/about/releases/
    steps:
    - uses: actions/checkout@v3
    - name: Use Node.js ${{ matrix.node-version }}
      uses: actions/setup-node@v3
      with:
        node-version: ${{ matrix.node-version }}
        cache: 'npm'
    - run: npm ci
    - run: npm test
    - run: pm2 restart backendserver
'''

## Download GitHub Actions Runner to Ubuntu
'''
sudo ./svc.sh install
sudo ./svc.sh start
'''

## Setting up a Node.Js Application Environment on an AWS EC2 Instance
'''
sudo apt update
curl -sL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt-get install -y nodejs
sudo npm install -g pm2
cd ~
cd /home/ubuntu/actions-runner/_work/cicd-app/cicd-app
pm2 start src/index.js --name=backendserver
'''

## Upgrade V1 to V2 and see the result in the publib-ip:3000

## Links
https://reflectoring.io/tutorial-cicd-github-actions-pm2-nodejs-aws-ec2/
