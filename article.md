---
author: "Kyle Jones"
date_published: "October 18, 2024"
date_exported_from_medium: "November 10, 2025"
canonical_link: "https://medium.com/@kyle-t-jones/migrating-to-aws-cdk-for-infrastructure-as-code-7ac8d02490ca"
---

# Migrating to AWS CDK for Infrastructure as Code Migrating to the AWS CDK allows developers to manage cloud resources
using popular programming languages like TypeScript, JavaScript...

### Migrating to AWS CDK for Infrastructure as Code 

Migrating to the AWS CDK allows developers to manage cloud resources using popular programming languages like TypeScript, JavaScript, Python, and Java rather than dealing directly with CloudFormation YAML or JSON templates or learning domain-specific languages like Terraform's HCL. This shift modernizes how developers handle infrastructure as code, making automating, maintaining, and scaling deployments easier.

### Moving from CloudFormation to CDK
Migrating from AWS CloudFormation to CDK is a natural progression for teams looking to leverage the power of programming languages to define their infrastructure. Since CDK is built on top of CloudFormation, it generates CloudFormation templates under the hood, which ensures compatibility with existing AWS infrastructure and services. However, moving from static CloudFormation templates to the dynamic flexibility of CDK requires some planning and restructuring.

[**Infrastructure as Code with CloudFormation on AWS**\ *Introduction to AWS CloudFormation*medium.com](https://medium.com/@kylejones_47003/infrastructure-as-code-with-cloudformation-on-aws-1a5b2323b96a "https://medium.com/@kylejones_47003/infrastructure-as-code-with-cloudformation-on-aws-1a5b2323b96a")[](https://medium.com/@kylejones_47003/infrastructure-as-code-with-cloudformation-on-aws-1a5b2323b96a)
#### **Why Migrate from CloudFormation to CDK?**
CloudFormation is a robust tool, but it has limitations. Writing complex CloudFormation templates can become tedious, especially as applications scale and grow more sophisticated. CDK provides several key advantages over traditional CloudFormation:

**Programming constructs:** With CDK, you can use loops, conditionals, functions, and variables to create modular and reusable infrastructure. This is particularly helpful for large projects with multiple environments or stacks.

**Improved readability:** CloudFormation templates can become large and difficult to read, especially with deeply nested resources. CDK simplifies this by abstracting many details and providing concise, human-readable code.

**Code reuse:** With CDK, you can create reusable constructs for common patterns, which reduces redundancy and simplifies infrastructure management.

#### **Key Differences in Moving to CDK**
While CloudFormation and CDK ultimately both use AWS CloudFormation under the hood to provision resources, there are significant differences

**Declarative vs. Imperative**: CloudFormation is declarative, meaning you define the end state of your infrastructure, and AWS figures out how to achieve it. CDK is imperative, allowing you to describe infrastructure programmatically with logic, loops, and conditions.

**Maintainability:** In CDK, you can organize your infrastructure code into classes and functions, making it easier to maintain and update over time. This is a significant improvement over the flat structure of CloudFormation templates.

**Testing:** CDK code can be tested like any other codebase. Using common testing libraries, you can write unit tests for infrastructure, which is not quickly done with raw CloudFormation templates.

### Step-by-Step Migration Process
Migrating from CloudFormation to CDK involves re-writing CloudFormation templates into CDK code. Still, it's not as daunting as it sounds because of the high overlap between AWS resources in both systems.

#### Step 1: Analyze the Current CloudFormation Templates
Start by understanding the structure of your CloudFormation templates. Identify which resources are defined, their properties, and their dependencies. Make note of any complicated logic or conditions you may need to replicate in CDK, such as nested stacks, outputs, and parameter usage.

#### Step 2: Set Up Your CDK Project
CDK uses standard folder structures and configuration files. You will first need to initialize a CDK project using the following command:

``` 
cdk init app - language typescript
```

This creates a boilerplate project with the necessary dependencies. From here, you can start translating your CloudFormation templates into CDK constructs.

#### Step 3: Translate Resources into CDK Code
Take each resource in your CloudFormation template and rewrite it as a CDK construct. For example, if your CloudFormation template defines an S3 bucket, you would translate it into TypeScript like so:

CloudFormation Template

CDK Code

For more complex resources with conditions or parameters, CDK allows you to simplify logic using standard programming techniques like if statements or loops.

#### Step 4: Test the Migrated Stack
Once your resources are translated into CDK, run a test deployment in a non-production environment to ensure the stack is correctly set up. Use the cdk deploy command to launch the stack and verify that all resources are created successfully.

#### Step 5: Iterate and Optimize
As you migrate more templates, you'll find opportunities to optimize your CDK code by creating reusable components. For example, if you frequently use similar IAM policies across different resources, encapsulate them in a reusable construct to simplify your stack.

#### Step 6: Full Rollout
Once you're confident the migration is complete, roll out the CDK stack in production. This can be done gradually by running both the CloudFormation and CDK-managed environments side-by-side and shifting progressively traffic to the CDK version.
