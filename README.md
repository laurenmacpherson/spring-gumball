# spring-gumball ci/cd example


## CI Workflow
Here is my CI working successfully. After uploading the provided code, I had no issues with this portion. 

![Successful CI workflow run](/images/cd_workflow1.png)

## CD Workflow

Here is my service account and key.

![Service account I used](/images/2_serviceaccounts.png)

![Key from Spring Gumball](/images/3_key.png)

I received some errors while building. Some were based on an issue with the secrets I added, some were permissions that I needed on the service account I used. 

![Unexpected Token](/images/4_error.png)

![Failed permissions](/images/5_error.png)

![Added permissions](/images/6_permissions.png)

Used Cluster Viewer and Cluster Admin based off advice from [this post](https://serverfault.com/questions/1044638/sudden-permissions-denied-for-service-account) and storage admin based on [this](https://cloud.google.com/container-registry/docs/access-control) documentation.

I just iteratively added new permissions as needed and searched for what was missing based on the error messages I was receiving. For the following error: 

![Deployment Error](/images/7_error.png)

I searched [this list](https://cloud.google.com/iam/docs/understanding-roles?hl=da) for what role was needed to grant that access. 

These were the roles/permissions that ran successfully:
![Final Roles](/images/8_permissions_final.png)

![Successful Build](/images/9_success.png)

Here are my workflows, including some releases I added due to a misunderstanding on how to re-run the build. 
![Workflows](/images/workflows.png)

Then I added the ingress as instructed. 

![Creating the Ingress](/images/9_ingress.png)

After a short while, it ran and I was able to open up the webpage. 

![Ingress Running](/images/10_running.png)

![Webpage](/images/11_web.png)

## Some Questions

1. Does a new release need to be made every time you redo something for the build? When I was having trouble with the keys, it was unclear if I needed to make a new release every time. My assumption was no, because the 'secrets' acted more like variables, but I made various releases just in case. 

*Answer*: Not necessary, use the dropdown menu just above the window and 're-run' 
