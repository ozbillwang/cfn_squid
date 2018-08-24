# Overview

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Overview](#overview)
- [Validate the Template](#validate-the-template)
- [Create a SquidProxy in a Given Region](#create-a-squidproxy-in-a-given-region)
- [Testing SquidProxy](#testing-squidproxy)
- [Local test](#local-test)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Forked from https://github.com/cloudavail/snippets/tree/master/squid/basic_squid

The CloudFormation file `basic_squid_infrastructure.json` in this directory will:

1. Create a Squid Proxy in a given AWS Region

# Validate the Template

`aws cloudformation validate-template --template-body file://basic_squid_infrastructure.json`

# Create a SquidProxy in a Given Region

```
keyname=squid
region=us-west-2

aws cloudformation create-stack --stack-name SquidProxy --template-body file://basic_squid_infrastructure.json --parameters ParameterKey=SquidProxyKeyName,ParameterValue=$keyname --region $region
```

# Testing SquidProxy

1. Get public IP, for example, `52.19.230.151`
2. Curl IP as proxy  with web request

    curl --proxy http://52.19.230.151:3128 http://www.squid-cache.org/

# Local test

Test with vagrant

```
vagrant up

curl --proxy http://localhost:3128 http://www.squid-cache.org/
```
