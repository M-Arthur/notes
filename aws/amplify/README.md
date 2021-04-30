<a href="https://aws-amplify.github.io/" target="_blank">
    <img src="https://s3.amazonaws.com/aws-mobile-hub-images/aws-amplify-logo.png" alt="AWS Amplify" width="550" >
</a>

# AWS Amplify CLI

- [Tags with amplify init command](#tags-with-amplify-init-command)

## Tags with amplify init command
> This is working for amplify 4.50.0

Running `amplify init` command on a brand-new project will create three AWS resources:
- Two AWS Roles - authrole and unauthrole
- One S3 Bucket

Two default tags _user:stack_ and _user:application_ are attached to above resources.

Amplify does provide the ability to attach tags to resources created by it 
(Details please refer to https://docs.amplify.aws/cli/usage/tags).

However, it does not mention what to do to add tags when running `amplify init` for a
whole new project. Here is the solution:
1. Create _amplify_ directory under your project root direct based on the [template](https://github.com/aws-amplify/amplify-cli/tree/master/packages/amplify-cli/templates/amplify-skeleton).
    1. File _project-config.json_ should be created under _amplify/.config/_ directory
    2. File _backend-config.json_ and _tags.json_ should be created under _amplify/backend/_ directory
2. Please keep _backend/_ directory and _backend-config.json_ clean. In other words, only above *.json should be
_backend/_ directory and `{}` should be the only content inside file _backend-config.json_
3. Please add the custom tags into _tags.json_ file.

Once all of these has been set up correctly, then you are able to run `amplify init`
and have all the resources attached with specified tags including the ones only created when init for new projects.
