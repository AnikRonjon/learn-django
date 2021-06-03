### As a testing server you can ignore migrations file `0*.py

```
# Django #
*.log
*.pot
*.pyc
__pycache__
db.sqlite3
media

# Backup files # 
*.bak 

# Python # 
*.py[cod] 
*$py.class 

# Distribution / packaging 
.Python build/ 
develop-eggs/ 
dist/ 
downloads/ 
eggs/ 
.eggs/ 
lib/ 
lib64/ 
parts/ 
sdist/ 
var/ 
wheels/ 
*.egg-info/ 
.installed.cfg 
*.egg 
*.manifest 
*.spec 

# Installer logs 
pip-log.txt 
pip-delete-this-directory.txt 

# Unit test / coverage reports 
htmlcov/ 
.tox/ 
.coverage 
.coverage.* 
.cache 
.pytest_cache/ 
nosetests.xml 
coverage.xml 
*.cover 
.hypothesis/ 

# Jupyter Notebook 
.ipynb_checkpoints 

# pyenv 
.python-version 

# celery 
celerybeat-schedule.* 

# SageMath parsed files 
*.sage.py 

# Environments 
.env 
.venv 
env/ 
venv/ 
ENV/ 
env.bak/ 
venv.bak/ 

# mkdocs documentation 
/site 

# mypy 
.mypy_cache/ 

# Sublime Text # 
*.tmlanguage.cache 
*.tmPreferences.cache 
*.stTheme.cache 
*.sublime-workspace 
*.sublime-project 

# sftp configuration file 
sftp-config.json 

# Package control specific files Package 
Control.last-run 
Control.ca-list 
Control.ca-bundle 
Control.system-ca-bundle 
GitHub.sublime-settings 

# If you are using PyCharm # 
.idea/**/workspace.xml 
.idea/**/tasks.xml 
.idea/dictionaries 
.idea/**/dataSources/ 
.idea/**/dataSources.ids 
.idea/**/dataSources.xml 
.idea/**/dataSources.local.xml 
.idea/**/sqlDataSources.xml 
.idea/**/dynamic.xml 
.idea/**/uiDesigner.xml 
.idea/**/gradle.xml 
.idea/**/libraries 
*.iws /out/ 

# Visual Studio Code # 
.vscode/* 
!.vscode/settings.json 
!.vscode/tasks.json 
!.vscode/launch.json 
!.vscode/extensions.json 
.history
```
> Does Django database migration file need to be uploaded?
>
> The database migration files are located in the migrations folder of each app folder. These files record the creation and changes of the model. Every time you create a model or modify the model fields, and then run the python manage.py makemigrations command, a new migration file will be generated. The official Django documentation specifically states that these migration files are a very important part of the Django project code and should not be deleted or ignored, so uploading is recommended. However, in actual project development, different people may make different or even opposite changes to the same model. If they are all submitted to the same code base, it is easy to cause migration file conflicts. Based on previous discussions on stackoverflow, the editor summarized the answer to whether Django database migration files need to be uploaded.

> Development environment
>
> If the project is still under development, you can choose to submit or not to submit. Every time you create a model or make changes to the model, you can use it directlypython manage.py makemigrations according to models.pyRegenerate the migration file without retaining the previous version of the migration file.If you don't have a migration file from the clone project on github, you can use the same command to produce the migration file, and then use python manage.py migrate to make changes to the tables in the database.

> Production Environment
>
> If the project is already in a production environment, then the migration files generated by the local changes to the model also need to be submitted. However, please remember that on a production environment machine, do not use python manage.py makemigrations to generate the migration file again, but use it directlypython manage.py migrate makes changes to the tables in the database according to the submitted migration file.

> Why need to ignore .pyc file
>
> Python will always compile your code to byte code. This is saved in the .pyc files. You can't do much with that and we don't need it, python will create them anyway. It's best to just ignore them through .gitignore.