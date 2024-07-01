# Automated CI/CD Pipeline with GitHub and Amazon S3 Integration

## Overview
This guide provides steps to set up a **Continuous Integration/Continuous Deployment (CI/CD) pipeline** using GitHub and Amazon S3. By following these steps, you can automate the deployment process of your application, ensuring that your application is always up-to-date with the latest code changes. This pipeline will help you create a secure, scalable, and full-stack application that can handle high levels of traffic.

## GitHub Repo Set Up
This section guides you through the process of setting up a GitHub repository which will be the source for your CI/CD pipeline.

1. Create a GitHub account.
2. Create a new repository where your project will live.
3. Upload all the files from your project.

## S3 Bucket Set Up
This section provides steps to set up an Amazon S3 bucket. This bucket will serve as the deployment environment for your application.

1. Open S3 on a separate tab.
2. Click on "Create Bucket".
3. Enter the following information: Bucket Name="any globally unique name or MyFirstApp123456", AWS Region="choose closest to country you'll be using it or choose US-East-1 as default". **Note**: The bucket name must be globally unique across all existing bucket names in Amazon S3.
4. Under "Block public access (bucket settings)", uncheck all options. **Note**: Unchecking these options will make your bucket publicly accessible. Be sure you want to do this.
5. Leave default settings, and click on "Create bucket".
6. Under "Buckets", choose "Properties".
7. Under "Static website hosting", click "Edit".
8. Under "Static website hosting", choose "Enable".
9. Under "Hosting type", choose "Host static website".
10. Under "Index", type "index.html".
11. Leave default settings, and click on "Save changes".
12. Under "Buckets", choose "Permission".
13. Under "Bucket Policy", click "Edit".
14. Enter the JSON policy provided in this project. If you don't have the JSON policy, you can find it [here](https://github.com/r-ramos2/Automated-CI-CD-Pipeline-with-GitHub-and-Amazon-S3-Integration/blob/main/s3_public_read_policy.json).
15. Replace "arn:aws:s3:::Bucket-Name/*" with the Bucket ARN at the top of the screen. **Note**: The Bucket ARN is a unique identifier for your bucket.
16. Click on "Save changes".

## CodePipeline Set Up
This section is the core of your CI/CD pipeline. It guides you through the process of setting up a pipeline in AWS CodePipeline, which automates the deployment process from your GitHub repository to your Amazon S3 bucket.

1. Open CodePipeline on a separate tab.
2. Click on "Create pipeline".
3. Enter the following information: Pipeline name="any name or MyPipeline123456", Pipeline type="V1", Role name="include details such as what AWS service you're using, AWS region, and original project name". **Note**: V1 type pipeline definition contains the standard pipeline, stage, and action-level parameters. V2 type pipeline extends the definition to add additional configurations sections such as triggers, and variables.
4. Check box to "Allows AWS CodePipeline to create a service role so it can be used with this new service", then click "Next".
5. Under "Source provider", choose "GitHub (Version 2)".
6. Under "Connection", click  on "Connect to GitHub".
7. Under "Create GitHub App connection", enter Connection name="any name or MyPipeline123456".
8. Click on "Connect to GitHub", then click on "Install a new app".
9. On GitHub screen, scroll down to "Repository access". 
10. Select repository to give access to, then click "Save", then click "Connect".
11. Under "Connection", click on GitHub connection you just created.
12. Under "Repository name", choose corresponding S3 Bucket.
13. Under "Pipeline trigger", choose "Push in a branch".
14. Under "Branch name", choose "main".
15. Under "Output artifact format", choose "CodePipeline default", then click "Next".
16. Under "Build - optional", choose depending on your needs or "Skip build stage", then click "Next".
17. Enter the following information: Deploy provider=Amazon S3, Region=your current region, Bucket=your S3 bucket, S3 object key=click on "Extract file before deploy", then click "Next", then click "Create pipeline".
18. Wait until the screen show green checkmarks for Source and Deploy.

## Testing Phase
This section guides you through the process of testing your CI/CD pipeline.

1. Open S3 on a separate tab.
2. Under "Buckets", choose "Properties".
3. Under "Static website hosting", click on the URL below "Bucket website endpoint".
4. Open the GitHub repository with your project, make a change and save.
5. Open CodePipeline and verify that the change is detected.
6. Refresh the URL below "Bucket website endpoint" and see the change.

## Clean Up
To avoid unnecessary costs, please double-check that no underlying resources are still running. 

Here's how you can empty and terminate the CodePipeline:
1. Navigate to the CodePipeline dashboard.
2. Click on the pipeline you want to delete.
3. Click on the "Delete" button to remove the pipeline.

Here's how you can empty and terminate the S3 Bucket:
1. Navigate to the S3 dashboard.
2. Click on the bucket you want to delete.
3. Click on the "Empty" button to remove all objects from the bucket.
4. Once the bucket is empty, click on the "Delete" button to remove the bucket.
**Note**: You may need to delete the bucket policy before you can delete the bucket.

## Conclusion
In this project, we demonstrated how to deploy up a Continuous Integration/Continuous Deployment (CI/CD) pipeline using GitHub and Amazon S3. By following these steps, we have created a fully functioning CI/CD pipeline that deploys an application to Amazon S3 bucket whenever there are changes pushed to the GitHub repository. Feel free to message me with code improvement suggestions.

## Acknowledgment
This tutorial is adapted from the [Tutorial: Create a pipeline that uses Amazon S3 as a deployment provider website](https://docs.aws.amazon.com/codepipeline/latest/userguide/tutorials-s3deploy.html) provided by Amazon Web Services. We extend our gratitude to AWS for providing this valuable resource, which served as the foundation for the "Automated CI/CD Pipeline with GitHub and Amazon S3 Integration" tutorial.

## Explore Project in More Languages

- [French](https://github.com/r-ramos2/Pipeline-automatisee-CI-CD-avec-integration-GitHub-et-Amazon-S3-French) (Français)
- [Italian](https://github.com/r-ramos2/Pipeline-Automatizzato-di-CI-CD-con-Integrazione-di-GitHub-e-Amazon-S3-Italian) (Italiano)
- [Portuguese](https://github.com/r-ramos2/Pipeline-Automatizado-de-CI-CD-com-Integracao-GitHub-e-Amazon-S3-Portuguese) (Português)
- [Spanish](https://github.com/r-ramos2/Pipeline-Automatizado-de-CI-CD-con-Integracion-de-GitHub-y-Amazon-S3-Spanish) (Español)
