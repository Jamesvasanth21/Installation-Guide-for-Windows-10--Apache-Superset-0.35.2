# Installation-Guide-for-Windows-10---Apache-Superset-0.35.2-

Installation & Configuration for Windows
System Requirements
1.	Superset has deprecated support for Python 2.* and supports only ~=3.6 to take advantage of the newer Python features and reduce the burden of supporting previous versions. We run our test suite against 3.6, but 3.7 is fully supported as well.
2.	Microsoft Visual C++ 14.0. 
Install Microsoft Visual C++ 14.x standalone: Build Tools for Visual Studio 2019 (x86, x64, ARM, ARM64).
•	Select latest version of MSVCv142 - VS 2019 C++ x64/x86 build tools.
•	Select Windows 10 SDK
Installation Steps
1.	Open Command Prompt in Administrator Mode move to C:\
2.	Check whether your python installation contains pip package and It should be above version 20.0.2. Check version by using following cmd, 
pip -V
If not download get-pip.py, and run 
python get- pip.py 
3.	Superset stores database connection information in its metadata database. For that purpose, we use Cryptography Library. Python library to encrypt connection passwords. This library has OS level dependencies. Run this command.

pip install cryptography
4.	It is recommended to install Superset inside a virtualenv. Python 3 already ships virtualenv. But if it’s not installed in your environment for some reason, you can install it via the package for your operating systems, otherwise you can install from pip:
pip install virtualenv
5.	You can create and activate a virtualenv by:
# virtualenv is shipped in Python 3.6+ as venv instead of pyvenv.# See #https://docs.python.org/3.6/library/venv.html
python3 -m venv venv
venv\Scripts\activate
Once you activated your virtualenv everything you are doing is confined inside the virtualenv. To exit a virtualenv just type deactivate.
6.Python’s setup tools and pip
Put all the chances on your side by getting the very latest pip and setuptools libraries.:
pip install --upgrade setuptools pip
setuptools in c:\venv\lib\site-packages (46.0.0)
pip in c:\venv\lib\site-packages (20.0.2)


Superset installation and initialization
Follow these few simple steps to install Superset.:
# Install superset
(venv) C:\>pip install apache-superset

# Initialize the database
(venv) C:\>cd venv
(venv) C:\venv>py Scripts\superset db upgrade
# Create an admin user (you will be prompted to set a username, first and last name before setting a password)
(venv) C:\venv>cd ..
(venv) C:\>set FLASK_APP=superset
(venv) C:\>flask fab create-admin
(venv) C:\>cd venv
# Load some data to play with
(venv) C:\venv>py Scripts\superset load_examples
# Create default roles and permissions
(venv) C:\venv>py Scripts\superset init
# To start a development web server on port 8088, use -p to bind to another port
(venv) C:\venv>py Scripts\superset run -p 8088 --with-threads --reload –debugger
After installation, you should be able to point your browser to the right hostname:port http://localhost:8088, login using the credential you entered while creating the admin account, and navigate to Menu -> Admin -> Refresh Metadata. This action should bring in all of your datasources for Superset to be aware of, and they should show up in Menu -> Datasources, from where you can start playing with your data!
To INSTALL DATABASE DEPENDENCIES
1)	Stop server “ctrl+C”
2)	I am using MS SQL Server and based on your database select the pypi package from here https://superset.apache.org/installation.html#database-dependencies
(venv) C:\venv>cd ..
(venv) C:\>pip install pymssql
3)	(venv) C:\>cd venv
4)	(venv) C:\venv>py Scripts\superset run -p 8088 --with-threads --reload –debugger
References:
https://visualstudio.microsoft.com/visual-cpp-build-tools/
https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017
https://www.itechtics.com/microsoft-visual-c-redistributable-versions-direct-download-links/
https://github.com/apache/incubator-superset/issues/7707
https://github.com/apache/incubator-superset/issues/4479
https://github.com/apache/incubator-superset/issues/7763
https://stackoverflow.com/questions/50295010/is-there-a-way-to-create-read-only-dashboard-in-apache-superset
https://answers.microsoft.com/en-us/windows/forum/all/microsoft-visual-c-140/6f0726e2-6c32-4719-9fe5-aa68b5ad8e6d
https://gist.github.com/mark05e/d9cccae129dd11a21d7219eddd7d9923


Super - Set on Docker in Linux
Step 1:	https://linuxize.com/post/how-to-install-and-use-docker-on-ubuntu-18-04/

Step 2:	https://docs.docker.com/compose/install/
	
Step 3:	https://linuxize.com/post/how-to-install-git-on-ubuntu-18-04/

Step 4:	https://superset.incubator.apache.org/installation.html#

							
In case of Error at Step 4:	https://github.com/docker/compose/issues/4181






