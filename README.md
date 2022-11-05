# LinkedIn_Data_Puller
## General
* Cert and Cred data in env vars
* Run `init.py` to pull profile data and et to Firebase.

## Run the following to Deploy
* Login first with 
    * `aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 832214191436.dkr.ecr.ap-south-1.amazonaws.com`
* One time 
    * `aws ecr create-repository --repository-name linkedindatapuller`
* Build docker image with 
    * `docker build -t linkedindatapuller .`
* `docker tag linkedindatapuller:latest 832214191436.dkr.ecr.ap-south-1.amazonaws.com/linkedindatapuller:latest`
* `docker push 832214191436.dkr.ecr.ap-south-1.amazonaws.com/linkedindatapuller:latest`

## Test Image Locally
* Build image first
* Run built image with `docker run -d -p 8080:8080 linkedindatapuller`
* Test with `curl -XPOST "http://localhost:8080/2015-03-31/functions/function/invocations" -d """{id:123}""" ` in command prompt