# kubernetes-gitea
This is a gitea installation that will run on kubernetes

I am following these links as a guide to how to construct everything: 
- https://docs.gitea.io/en-us/install-with-docker/

# installation

- Run `./generate-manifests`
- If the script complains about `values.yaml` not existing, open the file and edit it
- The minimal values needed to edit are:
  - web.name: Set the name you want the git repository to show as the page title
  - web.domain: What is the domain you will host gitea on?
  - admin.email: This will create an initial administrator user with this email
  - admin.password: This will be the password to login to gitea after installation
  - database.password: This will first time, create a new database and setup this password
  - ssh.domain: This might be the same as `web.domain` but you can configure it yourself
  - ssh.port: Check this port is going to work on your infrastructure
- After the `values.yaml` is edited appropriately, run `./generate-manifests` script in a way similar to this:
  - Example: `./generate-manifests | kubectl apply -f -`