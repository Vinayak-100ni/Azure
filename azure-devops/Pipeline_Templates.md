```md

## 📌 What is a Template?

A **template** is a reusable YAML file that contains predefined pipeline logic such as steps, jobs, or stages.

> ✅ **In simple terms:** Write once, reuse everywhere.

---

## 🧱 Why Use Templates?

- Avoid duplication of pipeline code  
- Standardize CI/CD across projects  
- Easier maintenance and updates  
- Improves readability and structure  
- Enables scalable DevOps practices  

---

## 📂 Recommended Folder Structure


├── azure-pipelines.yml
└── templates/
├── steps/
│   └── build.yml
├── jobs/
│   └── build-job.yml
└── stages/
└── deploy-stage.yml

````

---

## 🔹 Types of Templates

### 1. Step Template
Reusable collection of steps.

```yaml
# templates/steps/build.yml
parameters:
  node_version: '18'

steps:
- task: NodeTool@0
  inputs:
    versionSpec: ${{ parameters.node_version }}

- script: npm install
- script: npm run build
````

---

### 2. Job Template

Reusable job definition.

```yaml
# templates/jobs/build-job.yml
parameters:
  vmImage: 'ubuntu-latest'

jobs:
- job: Build
  pool:
    vmImage: ${{ parameters.vmImage }}

  steps:
  - script: echo "Building application..."
```

---

### 3. Stage Template

Reusable stage definition.

```yaml
# templates/stages/deploy-stage.yml
parameters:
  environment: 'dev'

stages:
- stage: Deploy
  jobs:
  - job: DeployJob
    steps:
    - script: echo "Deploying to ${{ parameters.environment }}"
```

---

## 🚀 How to Use Templates

### Use Step Template

```yaml
# azure-pipelines.yml
steps:
- template: templates/steps/build.yml
  parameters:
    node_version: '20'
```

---

### Use Job Template

```yaml
jobs:
- template: templates/jobs/build-job.yml
  parameters:
    vmImage: 'ubuntu-latest'
```

---

### Use Stage Template

```yaml
stages:
- template: templates/stages/deploy-stage.yml
  parameters:
    environment: 'production'
```

---

## 🎯 Parameters in Templates

Templates support parameters for dynamic behavior.

```yaml
parameters:
  app_name: ''

steps:
- script: echo "Deploying ${{ parameters.app_name }}"
```

Usage:

```yaml
- template: deploy.yml
  parameters:
    app_name: 'my-app'
```

---

## 🔁 Template Reuse Across Repositories

You can reuse templates from another repository.

```yaml
resources:
  repositories:
  - repository: templatesRepo
    type: git
    name: ProjectName/TemplatesRepo

steps:
- template: steps/build.yml@templatesRepo
```

---

## 🔐 Conditional Execution in Templates

```yaml
steps:
- script: echo "Run only on main branch"
  condition: eq(variables['Build.SourceBranch'], 'refs/heads/main')
```

---

## 🔄 Looping with Templates

```yaml
parameters:
  environments: []

steps:
- ${{ each env in parameters.environments }}:
  - script: echo "Deploying to ${{ env }}"
```

---

## 🧪 Real-World Example (Multi-Stage Pipeline)

```yaml
# azure-pipelines.yml

trigger:
- main

stages:
- template: templates/stages/build-stage.yml

- template: templates/stages/deploy-stage.yml
  parameters:
    environment: 'staging'

- template: templates/stages/deploy-stage.yml
  parameters:
    environment: 'production'
```

---

## ⚙️ Best Practices

* Keep templates small and focused
* Use meaningful parameter names
* Avoid hardcoding values
* Store templates in a dedicated repo for large teams
* Use versioning for shared templates
* Validate templates before reuse

