# DevOps Assignment Draft

Drafting of the Assignment collateral.

## [Contents](#contents)

- [Assessment Ideation](#assessment-ideation)
- [Summative Draft](#summative-draft)
  - [Introduction](#introduction)
  - [Technical Pipeline and Process Design](#technical-pipeline-and-process-design)
  - [Appraisal against Business Context](#appraisal-against-business-context)
  - [Appraisal of Business DevOps Integration](#appraisal-of-business-devops-integration)

## [Assessment Ideation](#contents)

### [Practical - API Idea](#contents)

**25% of marks.**


#### Current Pipeline

##### Infra

- GitHub - code repository
- DockerHub - image registry
- Dev Laptop
- Dev k0s vm on dev laptop
- proxmox vm for k0s cluster
- mini pc nodes
- pfsense
- cloudflare tunnels
- zitadel - identity provider
- tailscale tailnet
- Vault (kubuntu)

##### Tools

- git
- docker
- k0s
- Ubuntu Virtual Machine Manager
- vscode
- bash
- proxmox
- SonarQube

##### Process

1. Clone code "main" branch from remote.
1. Create or checkout branch "dev".
1. Edit "dev" code branch.
1. Run in local environment to test new feature works.
1. Merge code branch "dev" > "main".
1. Push to remote.
1. Build image.
1. Push image to remote container registry.
1. ssh into server.
1. Pull "main" branch.
1. kubectl -f . apply

**N.B.** Could separate image code from k8s deployment code.

#### Target Pipeline

**Continuous Delivery:**

![ContDel](/bpp_apprenticeship_notes/module_6-DevOps/module_content/topic_4_DevOps_CICD/ContDel.png)

##### Infra

##### Tools

- Secure Secrets Management.
- git.
- SonarQube.

##### Process

- Testing
  - Security
    - Static Application Security Testing (SAST)
    - Dynamic Application Security Testing (DAST)
    - Interactive Application Security Testing (IAST)
  - Performance
    - Load Testing
    - Stress Testing
    - Endurance Testing
    - Spike Testing
- GitOps

### [Report - Design & Implementation Appraisal, Contextual Technical Appraisal, Contextual DevOps Appraisal](#contents)

**75% of marks.**

**Report:** A written report (maximum 2000 words) that discusses DevOps pipelines as a whole and in context of the pipeline(s) you have created and your organisation:

- **Technical Design Critique:** Defend your choices for the architecture, tools, and processes for your pipeline(s) in relation to your application and best practice.
  - **Contributes to:**
    - Design and architecture (40%)
    - DevOps concepts (35%)

- **Appraisal against Business Context:** Critically appraise the pipeline(s) you have created in the context of your role or organisation and use in your organisation and industry as a whole, including an assessment of the effectiveness of the pipeline.
  - Contributes to:
    - Design and architecture (40%)
    - Reflection on DevOps practice (25%)

- **Appraisal of Business DevOps Integration:** Consider how DevOps can be, or is, integrated into your organisation and appraise the success and challenges of this.
  - **Contributes to:**
    - DevOps concepts (35%)
    - Reflection on DevOps practice (25%)

### Following DORA

<https://dora.dev/guides/dora-metrics/>

Now Five Metrics:

- Throughput
  - Change lead time - Lead time for changes
  - Deployment Frequency
  - Failed deployment recovery time - Mean Time to Restore
- Instability
  - Change fail rate
  - Deployment rework rate

#### DevOps Security and Data Privacy

See Mod-1 Lecture slides.

### [Guidance Interpretation](#contents)

  - There should be a process that has been created. How has this been automated. Would have otherwise been manual.
    - What are the steps.

### [Pipeline](#contents)

**25% of marks.**

  Pull from git.
  Dev changes.
  Push to git.

  Packaged as images, pushed to docker repo.

#### What should pipeline be comprised of?

- Codebase.
- CI/CD?
  - Automated SAST/DAST?
  - Automated Testing?
    - Unit.
    - Integration.
    - Etc.
  - QA?
  - Deployment through different Environments?
  - GitHub Actions triggers on Pull Requests etc?
- Images in Container Registry?
- Kubernetes Manifest (.yaml)?
- Build agents?
  - Terraform?
  - Ansible?
- Secrets management/vault?
- Authentication?

### [Report](#contents)

**75% of marks.**

## [Summative Draft](#contents)

**75% of marks.**

**Report:** A written report (maximum 2000 words) that discusses DevOps pipelines as a whole and in context of the pipeline(s) you have created and your organisation.

### [Introduction](#contents)

DevOps is not just about tools. It is very importantly about culture and behaviours etc.

Ownership of the working application beyond when it has been deployed. Not having the "Wall of Confusion" where software is packaged and thrown over the wall to Ops.

Shared responsibility between Ops and Dev for:

- Release
- Monitor
- Support

#### Ethics

#### Key Considerations

- Transparency: Ensuring transparency in automated processes and AI decision-making.   
- Accountability: Establishing clear lines of accountability for automated actions.
- Fairness: Mitigating biases in AI and ensuring fair outcomes.   
- Sustainability: Minimizing the environmental impact of DevOps practices.   
- Collaboration: Fostering collaboration between development, operations, and security teams.

### [Technical Pipeline and Process Design](#contents)

**Defend your choices for the architecture, tools, and processes for your pipeline(s) in relation to your application and best practice.**

- How do the tools that have been chosen enable DevOps culture?
  - Automation.
  - Enabling more distributed cross-functional team capability (Architecture As Code).
    - [Calm](https://calm.finos.org/) framework.
- This solution may not be appropriate for LBG, which is fine.
  - Provides counterpoint for last section.
- What tools are being used and why?
- What processes need to be embedded and why?
- How much is automated, and should be, and why?
- How are security concerns addressed?
  - What other factors need to be addressed?
  - Is this all being done safe?
    - Appropriate safety over speed.

### [Appraisal against Business Context](#contents)

**Critically appraise the pipeline(s) you have created in the context of your role or organisation and use in your organisation and industry as a whole, including an assessment of the effectiveness of the pipeline.**

#### CI/CD/CD Pipelines

CI - Integration (Testing, QA)
CD - Delivery (Git Repo, DockerHub, Container Registry)
CD - Deploy (Make available for end users, running on server)

#### IaC

- Infrastructure as what system will work on.
- Have somewhere to have software run.
- Provision environment and runtime dependencies etc.

### [Appraisal of Business DevOps Integration](#contents)

**Consider how DevOps can be, or is, integrated into your organisation and appraise the success and challenges of this.**

- IDP being implemented.
  - Becoming the GitOps authoritative source of the truth.
  - Use of Architecture As Code using [Calm](https://calm.finos.org/).
- Jira & jira Align.
- We do not have Continuous Deployment.
  - Heavily scheduled and orchestrated.
- Security of automated processes.
  - Increase of attack surfaces with the integration of DevOps tools, service agents, etc.
- Need for continuous change, not one-and-done.
  - Will likely need to adapt and adjust once first iteration of DevOps practices are implemented.
  - Reference to the 5 year platform change plan 1.0, 2.0, 3.0 etc.
    - Avoid Stagnation and Resistance to change.
    - Culture first, Tools second.