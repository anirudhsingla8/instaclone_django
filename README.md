instaclone_django
=================
This is the web app side of the instaclone ios app (https://github.com/ethanlance/instaclone_ios/blob/master/README.md).  


You Also Need:
---------
Amazon S3 account.  If you want to upload images get an account and fill this section of settings.py out:

<pre>
USE_AMAZON_S3 = True
AWS_ACCESS_KEY = 'YOU_NEED_THIS'
AWS_SECRET_KEY = 'AND_YOU_NEED_THIS'
AWS_TEMP_UPLOAD_BUCKET = 'instaclonebucket'
AWS_TEMP_UPLOAD_DIRECTORY = 'uploads/'
</pre>



Setup
-----

Set up a virtualenv 

<code>virtualenv venv --distribute</code>

<code>source venv/bin/activate</code>

Now install all the requirements (like Django and Tastypie):

<code>cd instaclone_django</code>

<code>pip install -r requirements.txt</code>

<code>cd instaclone_django/instaclone</code>

Create our sqlite3 database:

<code>python manage.py syncdb</code>
Say "NO" to creating an admin user. Or you'll get an error later on because tastypie will not have created an api_key for this user.  I let the iOS app create the 1st user.

Start the server. I'm using a Mac and Bonjour to make this work:

<code>python manage.py runserver 0.0.0.0:8000</code>
For mac (dunno about windows, sorry) go System Preferences > Sharing.  Under Computer Name click "Edit".  Copy localhost name and use it in the constants.h file where we define: #define BASE_URL @"http://lancebook.local:8000/" 

