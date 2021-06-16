---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "3. Install Docker Portainer Ubuntu Server"
linktitle: "3. Install Docker Portainer"
summary:
date: 2021-06-15T10:18:50+07:00
lastmod: 2021-06-15T10:18:50+07:00
toc: true  # Show table of contents? true/false
type: book # Do not modify.

# Add menu entry to sidebar.
# - Substitute `example` with the name of your course/documentation folder.
# - name: Declare this menu item as a parent with ID `name`.
# - parent: Reference a parent ID if this page is a child.
# - weight: Position of link in menu.
weight: 3
---

## **1. Install Docker**

Nguồn:

> https://docs.docker.com/engine/install/ubuntu/

1.  Update the  `apt`  package index and install packages to allow  `apt`  to use a repository over HTTPS:

    ```
    $ sudo apt-get update

    $ sudo apt-get install \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg \
        lsb-release

    ```

2.  Add Docker’s official GPG key:

    ```
    $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
    ```

3. Use the following command to set up the **stable** repository. To add the **nightly** or **test** repository, add the word `nightly` or `test` (or both) after the word `stable` in the commands below.

```
 echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
## 2. Install Docker Engine

1.  Update the  `apt`  package index, and install the  _latest version_  of Docker Engine and containerd, or go to the next step to install a specific version:

    ```
     $ sudo apt-get update
     $ sudo apt-get install docker-ce docker-ce-cli containerd.io
    ```
**

## 3. Install Portainner
**Step 1: Install Docker Compose**

To install Docker-Compose, open Putty and SSH into your server.

Then run this command:

```
sudo curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
```

Then, set the permissions:

```
sudo chmod +x /usr/local/bin/docker-compose
```

----------

**Step 2: Create Portainer Volume**

With Putty still open,  **create the Portainer volume.**

```
sudo docker volume create portainer_data
```

Then, **create the Portainer container:**

```
sudo docker run -d -p 9000:9000 -p 8000:8000 --name portainer --restart always -v /var/run/docker.sock:/var/run/docker.sock -v /srv/portainer:/data portainer/portainer
```

----------

 **Step 3: Start the Docker container.**

```
sudo docker start portainer
```
**
