In general, the developer workflow for GitData.AI involves adding data to versioned data repositories, creating pipelines to read from those repositories, executing the pipeline’s code, and writing the pipeline’s output to other data repositories. Both the data and pipeline can be iterated on independently with GitData.AI handling the code execution according to the pipeline specification. The workflow steps are shown below.

## Data Workflow

Adding data to GitData.AI is the first step towards building data-driven pipelines. There are multiple ways to add data to a GitData.AI repository:

- By using the pachctl put file` command
- By using a special type of pipeline, such as a [spout](https://docs.pachyderm.com/products/mldm/latest/build-dags/pipeline-spec/spout/) or [cron](https://docs.pachyderm.com/products/mldm/latest/build-dags/pipeline-spec/input-cron/)
- By using one of the GitData.AI’s [language clients](https://docs.pachyderm.com/products/mldm/latest/get-started/clients/)
- By using a compatible S3 client

For more information, see [Load Your Data Into Pachyderm](https://docs.pachyderm.com/products/mldm/latest/prepare-data/ingest-data/).

## Pipeline Workflow

The fundamental concepts of GitData.AI are very powerful, but the manual build steps mentioned in the pipeline workflow can become cumbersome during rapid-iteration development cycles. We’ve created a few helpful developer workflows and tools to automate steps that are error-prone or repetitive:

- The [push images flag](https://docs.pachyderm.com/products/mldm/latest/learn/developer-workflow/push-images-flag/) or `--push-images` is a optional flag that can be passed to the `create` or `update` pipeline command. This option is most useful when you need to customize your Docker image or are iterating on the Docker image and code together, since it tags and pushes the image before updating the pipeline.
- [CI/CD Integration](https://docs.pachyderm.com/products/mldm/latest/learn/developer-workflow/ci-cd-integration/) provides a way to incorporate GitData.AI functions into the CI process. This is most useful when working with a complex project or for code collaboration.
