
## Image resize
This is a demo application used to test automation deployment of FaaS. 

The image resize python app does exactly what it says with some limitations. It gets the image from the trigger from a bucket named `<name>` and saves resized version in the bucket named `<name>-resize`.

The \*.zip contains the whole project ready to deploy on Amazon Lambda (virtual env included).
  
### How to prepare a zip for Lambda deploy:

First you need to create a clean virtual env and activate it:

```
python3 -m venv venv-img
. venv-img/bin/activate
```
Install necessary depedencies:
```
pip install -r requirements.txt
```

Deactivate virtualenv, and zip site packages and change to starting dir: 

```
deactivate
cd venv-img/lib/python3.6/site-packages/
zip -r9 ${OLDPWD}/X-test-ImageRes.zip .
cd -
```

add the function code to a zip file:

```
zip X-test-ImageRes.zip image_resize.py
```

Now zip is prepared to be deployed on Amazon with Ansible or xOpera or anything else. If you do not have time to prepare it, one example is already available in `binary-zip` directory.