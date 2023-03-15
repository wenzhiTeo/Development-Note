# Set Up WSL2 (Linux) Development Environment 

### Micosoft Official tutorial 
- WSL2 Setup: https://docs.microsoft.com/en-us/windows/wsl/setup/environment
- VS Code with WSL Setup: https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-vscode 
Just follow the tutorial setup the visual, normally it will not have any surprise exception.

---

### Github SSH
As using the Linux development clone SSH will be better
SSH Setup: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
**Able to use Github to track the changes easier with GUI, but Github 2.9.10 not support the discard changes for Network Drive(WSL2)**

---

### Docker issue
If using docker some container might facing `java.lang.outofmemoryerror: java heap space` just increase the size of `JAVA_OPTS` 
eg:
```yml
zipkin:
  image: openzipkin/zipkin
  container_name: zipkin
  ports:
    - 9411:9411
  environment:
    - STORAGE_TYPE=elasticsearch
    - ES_HOSTS=elasticsearch:9200
    - JAVA_OPTS=-Xms512m -Xmx1g
  depends_on:
    - elasticsearch
```

