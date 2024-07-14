---
layout: post
title: Blank Validated Pattern to configure MANO clusters
---

---
[hub-blank-vpattern](https://github.com/jtovarro/hub-blank-vpattern) acts as a blank papper to easily customize and apply day 2 configurations to MANO clusters using the Validated Pattern Framework. Validated patterns are living code architectures for different edge computing and hybrid cloud use cases. They're created by using Helm Charts, a collection of files that describe a set of related Kubernetes resources.

---

## Validated Patterns Onboarding

Prerequisites:
  
  1) Fork [https://github.com/jtovarro/hub-blank-vpattern](https://github.com/jtovarro/hub-blank-vpattern) in your GitHub.

Some steps are required to onboard Validated Patterns, in [hub-blank-vppatern](https://github.com/jtovarro/hub-blank-vpattern) repository you'll find a playbook in [ansible/playbooks/vpatters_onboarding.yaml](https://github.com/jtovarro/hub-blank-vpattern/blob/gmbros/ansible/playbooks/vpatterns_onboarding.yaml) that performs those steps for you:

  - Installing Validated Pattern operator.
  - Creating Pattern CRD pointing to your forked repository.

The playbook will ask you for:
  
  - Your GitHub user where the forked repository is located.
  - The path to the kubeconfig, so the k8s ansible module is able to create the kubernetes resources.

## How to start working

Review the *values-hub.yaml* file, inside this file you'll be able to declare in a descriptive way:
  
  - Creation of desired namespaces, including operator groups.
  - Installation of operators.
  - Operators configurations.
  - Custom day 2 configurations.

Inside values-hub.yaml file find some examples to easily understand how to modify it.

## Custom day 2 configurations

To add new Applications with custom configurations:

  - Go to charts/mgmt-hub/ and create or copy the example folder to follow the structure where you'll save your custom configs.
  - Then edit the values-hub.yaml, and in the Applications section add a new enty to the new folder created (add the name of the folder as application name and path to the folder).

---
### Related Links
[1] [Validated Patterns official documentation](https://validatedpatterns.io/)


<a href="https://www.buymeacoffee.com/techtovar"><img src="https://img.buymeacoffee.com/button-api/?text=Buy me a piece of fruit&emoji=🍌&slug=techtovar&button_colour=FFDD00&font_colour=000000&font_family=Cookie&outline_colour=000000&coffee_colour=ffffff" /></a>
