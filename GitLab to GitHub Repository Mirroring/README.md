#  GitLab to GitHub Repository Mirroring (Automatic Sync)

##  Project Overview

This project demonstrates how to automatically mirror a GitLab repository to GitHub using GitLab’s built-in **Repository Mirroring** feature.

In this setup:

- GitLab is the **primary repository** (source of truth)
- GitHub is the **mirror repository**
- Code is pushed **only to GitLab**
- GitLab automatically syncs the same code to GitHub
- No manual push to GitHub is required

This approach is commonly used for:

- Backup repositories  
- Open-source publishing  
- Multi-platform version control  
- Enterprise Git workflows  

---

##  Architecture Overview

![](./img/ChatGPT%20Image%20Feb%208,%202026,%2010_46_04%20AM.png)



##  STEP 1: Authenticate GitLab with GitHub

GitLab needs permission to push code into GitHub.  
This is done using a **GitHub Personal Access Token (PAT)**, which acts as a password.

###  Create GitHub Personal Access Token

1. Login to **GitHub**
2. Go to **Settings**
3. Open **Developer settings**
4. Click **Personal access tokens**
5. Select **Tokens (classic)**
6. Click **Generate new token**
7. Fill the details:
   - **Note:** GitLab Repository Mirroring
   - **Expiration:** Optional
   - **Scopes:**
     - ✅ `repo` (mandatory)
8. Click **Generate token**
9. Copy and securely save the token

 **Important:**
- This token will be used as the **password** in GitLab
- You will **not be able to view it again**

![](./img/Screenshot%202026-02-08%20093108.png)

---

##  STEP 2: Create Repositories on GitLab and GitHub

###  Create Repository on GitLab (Source Repository)

1. Login to **GitLab**
2. Click **New Project**
3. Choose **Blank Project**
4. Enter:
   - Project Name
   - Visibility (Private / Public)
5. Click **Create Project**

![](./img/Screenshot%202026-02-08%20093551.png)

---

###  Create Repository on GitHub (Mirror Repository)

1. Login to **GitHub**
2. Click **New Repository**
3. Enter:
   - Repository name 
   - Visibility (Public / Private)
4. Click **Create Repository**

![](./img/Screenshot%202026-02-08%20093656.png)

---

##  STEP 3: Configure Repository Mirroring in GitLab

Now we connect **GitLab → GitHub** using mirroring.

###  Steps to Add Mirror Repository

1. Open your **GitLab project**
2. Go to **Settings → Repository**
3. Scroll down to **Mirroring repositories**
4. Click **Add new mirror**

---

###  Fill Mirror Configuration

- **Git repository URL**  
https://github.com/aftab0045/github-mirroring-demo.git


- **Mirror direction**
- ✅ Push

- **Authentication Method**
- **Username:** Your GitHub username
- **Password:** GitHub Personal Access Token

- ✅ Enable **Mirror repository**

Click **Mirror repository**

![](./img/Screenshot%202026-02-08%20094212.png)

![](./img/Screenshot%202026-02-08%20094231.png)  

---

##  STEP 4: Clone GitLab Repository Locally

Now we work only with **GitLab**.

```bash
git clone https://gitlab.com/aftab0045/gitlab-mirroring-demo.git
cd gitlab-mirroring-demo
```
![](./img/Screenshot%202026-02-08%20102259.png)
## STEP 5: Add a File, Commit, and Push to GitLab
1. Create a Test File : index.html

2. Add content 
3. Commit Changes
  ```
  git add .
  git commit -m "Initial commit via GitLab"
  ```
4. Push to GitLab

  ```
  git push origin main
  ```
  ![](./img/Screenshot%202026-02-08%20102451.png)

## STEP 6: Verify Repository on GitLab and GitHub
 ### Verify on GitLab

1. Open GitLab repository

2. Confirm:

- index.html file exists

- Commit is visible
![](./img/Screenshot%202026-02-08%20102622.png)







### Verify on GitHub

1. Open GitHub repository

2. Refresh the page

3. Confirm:

  - Same file appears
  - Same commit message and history

![](./img/Screenshot%202026-02-08%20102603.png)

## Conclusion

This project demonstrates a real-world Git repository mirroring solution using GitLab’s native mirroring feature with GitHub authentication.

It ensures:

- Centralized development

- Automatic synchronization

- Reliable multi-platform version control  