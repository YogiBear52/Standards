# Local Dev Environment

- Easy and Fast to build
- Put you project's dependencies inside your repo
  - Specific version of NodeJs? Java JDK? put it in the repo.
  - Try to avoid global dependencies.
    - Use npx instead of npm so you can use "global" libraries but install them locally.
- Make a nice ReadMe about how to contribute to the project. This doc will include the small details of how to build a local env of your project.
- Choose a local OS as close to your servers OS.
  - Mac,Linux Desktop --> Linux servers
  - Windows -> Windows
- Run local dockers so you can even simulate the services specific OS. Infra as a Code
  - Using a DataBase? Run it with Dockers too.
    - Use local-mini K8S to simulate complex local services.
  - It may take a lot of RAM.
    - Buy a better computer :P
    - When you have many Micro-Services, you probably can run only some of them to develop your next feature.
- Another options, which is still not production ready is to use Cloud K8S for every developer.
  - Every developer has it's own K8S cluster. Compile the code and it immediately deploy on cloud instead of in local computer.
  - [How to do it with Azure](https://koukia.ca/faster-build-and-deploy-by-using-kubernetes-and-azure-dev-spaces-within-visual-studio-bc850ecd9810)
