# student_mlproject
# Machine_Learning_Project

1. [Github](www.github.com/)
2. [Render](https://render.com/) 

## Creating conda environment

```
conda create -p venv python==3.8 -y
```
_-p create venv in the project files._
```
conda activate venv/
```
## Installing requirements
```
pip install -r requirements.txt
```
### _Tells you the status of the file in the folder_
```
git status
```
### _Add a specific file to git_
```
git add <filename>
```
### _Add all the file into git_
```
git add .                                                  # turn U to A in VSCode
```

### _To check all the commited versions in git._
```
git log
``` 
To ignore file or folder from git we can wrtie name of file/folder in .gitignore file
### _To commit with comment_
```
git commit -m "message"  
```
### _To send version/changes to github_
```
git push origin main
```
### _To check remote url_
```
git remote -v
```

### _TO setup CI/CD pipleline in Render we  need 3 information_
1. RENDER_EMAIL = sheiphanshaijan@gmail.com
2. RENDER_API = rnd_wbWvEr1rkX2QW2ZVneAEev6X1ziV
3. RENDER_APP_NAME = ml-regression-app

### _BUILD DOCKER IMAGE_
```
docker build -t <image_name>:<tagname> .
```
> Note : Image should always be in small letters

### _To list docker images_
```
docker images
```
### _To Run docker image_
```
docker run -p 5000:5000 -e PORT=5000 <IMAGE ID>
```

name: Trigger Render Deployment
on:
  push:
    branches:
      - main
jobs:
  main:
    name: Deploy to Render
    runs-on: ubuntu-latest
    steps:
      - name: Trigger deployment
        uses: sws2apps/render-deployment@main #consider using pin for dependabot auto update
        with:
          serviceId: ${{ secrets.RENDER_SERVICE_ID }}
          apiKey: ${{ secrets.RENDER_API_KEY }}
          multipleDeployment: false #optional, default true