# Getting started with IaC+ and cloud scans

{% hint style="warning" %}
**Release status** \
Snyk IaC+ is now in closed beta and is no longer accepting new customers for participation.\
See [Getting started with current IaC](https://docs.snyk.io/scan-using-snyk/snyk-iac/getting-started-with-current-iac) for details about the functionality available.
{% endhint %}

Use IaC+ to find, view, and fix issues in cloud configuration files for Terraform, Kubernetes (except Helm, coming soon), AWS CloudFormation, and Azure Resource Manager (ARM) in your Git repositories.

Use Snyk IaC cloud scans to find, view, and fix issues in deployed cloud resource configurations for AWS, Azure, and Google Cloud.

This page explains using IaC+ and cloud scans in the Snyk Web UI. For information about using IaC+ with the Snyk CLI, see [Test your IaC files](../../../snyk-cli/scan-and-maintain-projects-using-the-cli/snyk-cli-for-iac/test-your-iac-files/).

## Prerequisites for IaC+ and cloud scans

To start using IaC+ you must have the following:

* A Snyk account. For details, see [Getting started](../../../getting-started/).
* Snyk IaC on the enterprise plan.
* An existing Terraform, CloudFormation, or Azure Resource Manager environment to work in, or deployed AWS, Azure, or Google Cloud account to onboard.
* Integration with your Git repository. For details, see [Git repositories (SCMs)](../../../scm-ide-and-ci-cd-integrations/snyk-scm-integrations/).

## Import IaC+ SCM repositories

{% hint style="info" %}
IaC+ SCM integrations use the [Snyk Workspaces](../../../scm-ide-and-ci-cd-integrations/snyk-scm-integrations/introduction-to-git-repository-integrations/workspaces-for-scm-integrations.md) capability to support multi-file analysis. Use the **Integration Settings** for your Group and Organization to enable Snyk Workspaces.

If you want to scan a new SCM repository with IaC+ and you have already imported that repository, you must re-import the repository. This will not affect any of your existing Projects.
{% endhint %}

You will start by importing SCM repositories as [Projects](../../../snyk-admin/snyk-projects/) you want to scan with Snyk. In these steps, you choose repositories for Snyk to test and re-test:

1. Log in to Snyk and on your dashboard, select **Projects** from the navigation.
2. On the Projects page, from the **Add projects** dropdown, select the SCM from which to add the Projects; for example, select GitHub.
3. From the list of **Personal and Organization repositories**, select the Git repositories you want to use.
4. Click **Add selected repositories** to add the selected repositories to Snyk.\
   The import completes and the Projects page displays the Snyk Projects that have been added.

## View IaC+ SCM projects

On the [Projects](../../../snyk-admin/snyk-projects/) page, ensure **Group by targets** is selected and navigate to the Target (Git repository) that contains the files for IaC+ to test.

You will see a single **Infrastructure as Code issues** Project. IaC+ generates only one Project in each repository, unlike current IaC, which generates one Project for each configuration file.

<figure><img src="../../../.gitbook/assets/Screenshot 2023-05-07 at 3.57.30 PM.png" alt="IaC+ Project in your SCM repository"><figcaption><p>IaC+ Project in your SCM repository</p></figcaption></figure>

## Configure recurring scans (daily, weekly, or never)

By default, IaC+ SCM Projects are scheduled for weekly scans. On an IaC+ SCM Project Settings page, you can configure an IaC+ SCM Project to have recurring scans be daily, weekly, or never.

## Import cloud environments

Navigate to your **Organization** **Settings (cog icon) > Cloud environments**.

The cloud environments table displays the following information for each environment:

<figure><img src="../../../.gitbook/assets/snyk-cloud-environments-page.png" alt="The Snyk environments page in the Snyk Web UI"><figcaption><p>The Snyk environments page in the Snyk Web UI</p></figcaption></figure>

To import a cloud environment, select the **Add environment** drop-down and select the cloud provider. Follow the steps in [AWS Integration: Web UI](../cloud-platforms-integrations/aws-integration/aws-integration-web-ui/), [Google Cloud Integration: Web UI](../cloud-platforms-integrations/google-cloud-integration/google-cloud-integration-web-ui/), or [Azure Integration: Web UI](../cloud-platforms-integrations/azure-integration-for-cloud-configurations/azure-integration-web-ui/) to create the environment.&#x20;

<figure><img src="../../../.gitbook/assets/snyk-cloud-environments-page-add-env.png" alt="Add an environment in the Snyk Web UI"><figcaption><p>Add an environment in the Snyk Web UI</p></figcaption></figure>

You can also import an environment using the Snyk API:

* [AWS Integration: API](../cloud-platforms-integrations/aws-integration/aws-integration-api/)
* [Google Cloud Integration: API](../cloud-platforms-integrations/google-cloud-integration/google-cloud-integration-api/)
* [Azure Integration: API](../cloud-platforms-integrations/azure-integration-for-cloud-configurations/snyk-cloud-for-azure-api/)

## View IaC+ and cloud issues

Click on the **Infrastructure as Code Issues** Project link to open a view of the cloud issues page, filtered to include only issues from the IaC+ [environment](key-concepts-for-iac+-and-cloud.md#environments) that corresponds to your Project.

<figure><img src="../../../.gitbook/assets/Screenshot 2023-05-07 at 4.04.13 PM.png" alt=".IaC+ Issues UI, filtered to show issues from the environment for your repository"><figcaption><p>Cloud Issues page, filtered to show issues from the environment for your repository</p></figcaption></figure>

Issues are grouped by rule. Expand the rule and select an issue to open its issue card. Each issue card has information about the following:

* The **resource**, including the location, cloud platform, such as aws, a link to the SCM file for fast fixes, and the input type, such as `tf_hcl` for Terraform HCL.
* The **environment**, providing details on the IaC+ environment that corresponds to your Project.
* The **rule** that failed, including a link to the Snyk [security rules](https://security.snyk.io/rules/cloud/) for additional information, such as specific remediation steps.
* The reason why your developers should fix this misconfiguration.

<figure><img src="../../../.gitbook/assets/Screenshot 2023-05-07 at 4.09.40 PM.png" alt="IaC+ issue card"><figcaption><p>IaC+ issue card</p></figcaption></figure>
