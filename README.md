This CDK app deploys an isolated network on AWS that does not have restrictive policies for limiting exfil.  It does not have flaws that would let an attacker in, but it is not configured in a hardened way that would prevent an attacker with access to the EC2 from exfil'ing data out, so read the associated blog post to be aware of the problems this has.  Blog post here: https://summitroute.com/blog/2020/03/31/isolated_networks_on_aws/

This creates an EC2 nad VPC endpoints for SSM so that Session Manager can be used to access the EC2.  It also creates VPC endpoints for SQS and S3 and creates a queue and bucket.

<img src="https://raw.githubusercontent.com/summitroute/isolated_network_experiment/master/docs/experimental_isolated_network.png"  width=30% alt="Network layout">

# Usage
## Prerequisites
- Have the CDK installed

## Deployment
```
git checkout https://github.com/SummitRoute/isolated_network_experiment.git
cd isolated_network_experiment
npm install
# Then, while in an AWS session, such as through aws-vault
cdk deploy
```

## Uninstalling
```
cdk destroy
```
