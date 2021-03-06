- # I Installation in [[Windows]] Server
collapsed:: true
	- ## Installation Steps:
		- ### 1 Configuration of the computers & Installation environment
		  collapsed:: true
			- Login with full administrator rights
			- Check if your computer has a 32 or 64-bit processor
			- Create shortcuts to ODBC,services and control panel (This step is not necessary)
			- Set regional settings, decimals should be defined with dots (.)
			- Turn Wi-Fi off or disconnect the computer from internet
			- Turn Antivirus off
			- Disable Firewall
		- ### 2 Installation of MCH
		  collapsed:: true
			- Open MCHInstalacion by running INstalMCH.exe
				- ![image.png](../assets/image_1651167341473_0.png)
				- ==**Optional**== *Save in the root, to avoid long path* *No space in the name of the folder*
					- ![image.png](../assets/image_1651167790161_0.png)
				- Select English for the language
				- ==**Optional**== *Rename the shortcut if needed*
					- ![image.png](../assets/image_1651170677260_0.png)
				- Check that all parameters are good and Install
					- ![image.png](../assets/image_1651170722719_0.png)
				- Finish Installation
					- ![image.png](../assets/image_1651170757982_0.png)
		- ### 3 Installation of Additional Software
collapsed:: true
			- ==**Note**== Check the ((626acb08-5cb7-4427-b86b-bd79eae6928f)) page to find links to the additional software.
			- #### Install [gostscript.ps –32 or 64 bits](https://u.pcloud.link/publink/show?code=XZuFQxkZkp2f2KkBFJX8HGfUwsrN2hiAKGBk).
			  collapsed:: true
				- ==Note== Leave default settings (install fonts ticked)
				- ![image.png](../assets/image_1651171354553_0.png)
			- #### Install [RuntimePlus](https://u.pcloud.link/publink/show?code=XZOFQxkZChg6wHApJ57nMeVHNuiesJF1GsDX) (RunTimePlus /dBasePlusRuntimeEngine1703_EN.exe)
			  collapsed:: true
				- ![image.png](../assets/image_1651171558178_0.png)
			- #### ==**Optional**== If needed edit the **gmtenv.bat** (C:/MCH/gmtenv.bat), needed for the map environment as follows:
			  collapsed:: true
				- ![image.png](../assets/image_1651171639225_0.png)
			- #### Installation of MySQL Server 5
			  collapsed:: true
				- Download the right executable for a 32 or 64 bit system
				- Tick Configure MySQL Server now
					- ![image.png](../assets/image_1651173034789_0.png)
				- Select Detailed Configuration
					- ![image.png](../assets/image_1651173123102_0.png)
				- Select Server Machine
					- ![image.png](../assets/image_1651173147103_0.png)
				- Select Non-Transactional Database
					- ![image.png](../assets/image_1651173171176_0.png)
					- ==**Note**==: You can also select Multifunctional Database if you are already using a Transactional Database on your computer
				- Check installation path
					- ![image.png](../assets/image_1651173363263_0.png)
				- Select number of users
					- ![image.png](../assets/image_1651173380091_0.png)
				- Networking options
					- Enabling TCP/IP networking
						- Tick Enable TCP/IP Networking
						- Select port 3306
						- Tick Add firewall exception
						- Untick Enable Strict Mode
						- ![image.png](../assets/image_1651173457653_0.png)
					- Select Standard Character Set
						- ![image.png](../assets/image_1651173496955_0.png)
					- Installing as a [[Windows]] service
						- Tick Install as Windows Service
						- Select MySQL5
						- Tick Launch the MySQL server automatically
						- Tick include Bin
						- ![image.png](../assets/image_1651173761812_0.png)
				- Set MySQL Admin password
					- Tick Modify Security Settings
					- Create a password ==**Save it**==
					- Tick Enable root access from remote machines
					- ![image.png](../assets/image_1651174041892_0.png)
				- Execute
					- ![image.png](../assets/image_1651174090878_0.png)
				- Finish
				  collapsed:: true
					- ![image.png](../assets/image_1651174106691_0.png)
				- Check that the service is properly running
				  collapsed:: true
					- ==**Note**== **If it is not running check firewall exceptions**
				- Check that password is by running: **Programmes/MySQL/MySQL Server 5/MySQL Command Line Client**
				  collapsed:: true
					- ![image.png](../assets/image_1651174236674_0.png)
			- #### Install MySQL Server 5 Tools
				- Execute: [mysql-gui-tools-5.0-r12-win32.msi](https://u.pcloud.link/publink/show?code=XZ2tQxkZeBdqRJxfKlh32j6YIeNCryjRFQX7)
					- ![image.png](../assets/image_1651174469704_0.png)
				- Select the folder tools with in the folder where MySQL Server 5 has been installed
				  collapsed:: true
					- ==**Note**== If it does not exist create a new folder and rename it `«tools»`
					- ![image.png](../assets/image_1651174549959_0.png)
					- ![image.png](../assets/image_1651174589224_0.png)
				- Select Complete
				  collapsed:: true
					- ![image.png](../assets/image_1651174618500_0.png)
				- Install
					- ![image.png](../assets/image_1651174644361_0.png)
			- #### Installation of the ODBC connector
				- ==Note== Select the ODBC driver which is compatible to your system (32 or 64 bits) from the ((626acb08-5cb7-4427-b86b-bd79eae6928f))
				  collapsed:: true
					- ![image.png](../assets/image_1651175151806_0.png)
				- Select Typical
				  collapsed:: true
					- ![image.png](../assets/image_1651175172747_0.png)
				- Install
				  collapsed:: true
					- ![image.png](../assets/image_1651175204305_0.png)
		- ### 4 Connect MCH to MySQL
		  collapsed:: true
			- Upload the databases mcheng and capttemp to `C:\MySQL5\data`
			- Rename **mcheng** to **mch**
			- Run ODBC Data Source as Administrator `control panel/Administrative Tools/ODBC Data Sources`
				- You can also use:
				  collapsed:: true
					- For 32 bits: `C:\Windows\System32\odbcad32.exe`
					- For 64 bits: `C:\Windows\SysWOW64\odbcad32.exe`
				- Under System DSN click Add
					- Look for MySQL ODBC 3.51 Driver and select it
					- Fill the fields in
					- Test the  connection
					- Click OK
					- ![image.png](../assets/image_1651180514267_0.png)
					- Repeat this process for all connected databases in this case `capttemp`
					- Repeat this process for 32 and 64 bit
					- At the end you should see something like this:
						- For 64 bits
							- ![image.png](../assets/image_1651180567977_0.png)
							- ==**Note**== **In the image above you see to mch. The mch referring to the 32 bits should not be there. In addition, the capttemp should be for the 64-bit and not 32-bit.**
							- For 32-bit
								- You should see the same as for the 64-bit.
							- ==**Note**== Please, make sure to have the mch and the capttemp for 64-bit platform in both System DSN in the 32 (`C:\Windows\System32\odbcad32.exe`) and 64 bit (`C:\Windows\SysWOW64\odbcad32.exe`) Otherwise, you will have problems.
					- Edit `mch.dbn file` **(in the root folder where MCH has been installed)**
						- Lines to edit:
							- **mch DSN** (ODBC connection name)
							- **mysql5** Version of MySQL
							- **2** User interface language: 1= Spanish; 2= English; 3= French
							- **2** Database language: leave 2 (English)
							- **C:\programme files\Mozilla Firefox\firefox.exe** Path to web browser (optional)
					- Edit `MCHeng.bat file` **(in the root folder whereMCH has been installed)**
						- `MCH18.exe -DSNmch-DefBMCHtablasycampos.def -DefIMensajesMCH.def -I2 -B`
							- **MCH18.exe** : nameof MCH executable
							- **DSNmcheng**: DSN (ODBC connection name), here the ODBC connection is called mch
							- **DefBMCHtablasycampos.def and DefIMensajesMCH.def**: Definition files do not edit
							- **I2**: User interface language (1= Spanish; 2= English; 3= French)
							- **B2**: Database language: leave 2 (English)
					- Activate new modules (2018) **(in the root folder whereMCH has been installed)**
					  collapsed:: true
						- The administrator must run and close following **.exe**, the first time MCH is installed:
							- MchSecurity.exe
							- MchDefInterface.exe
							- MchDefGraf.exe
							- ==**Note**== **Just open them ven though you get error messages. However, if you get an erro message saying that the database is not found or cannot be connected. You should look if the ODBC connector and mch.dbn and MCHeng.bat has the correct name for the database.**
		- #### 5 Installation of the Apache Server **(only needed for MCH web pages)**
		  collapsed:: true
			- Install [Apache Server 2.2.11 for 32-bit](https://archive.apache.org/dist/httpd/binaries/win32/). It should be compatible with your 64-bit system if this is the case
			  collapsed:: true
				- ![image.png](../assets/image_1651248409536_0.png)
			- Network configuration
			  collapsed:: true
				- ==For local use== enter **localhost** as value
				- ==For non local use== enter **IP address** or **domain**
					- ![image.png](../assets/image_1651249404463_0.png)
			- Select Custom and click Next
			  collapsed:: true
				- ![image.png](../assets/image_1651249522814_0.png)
			- Save it in the root under **C:\Apache\Apache2.2** or directly under **C:\Apache**
			  collapsed:: true
				- ![image.png](../assets/image_1651249539775_0.png)
			- Click Next
			  collapsed:: true
				- ![image.png](../assets/image_1651249605135_0.png)
			- Install
			  collapsed:: true
				- ![image.png](../assets/image_1651249625001_0.png)
			- Finish installation
			  collapsed:: true
				- ![image.png](../assets/image_1651249637647_0.png)
			- Configuration of Apache Server
			  collapsed:: true
				- Check that **RunTimePlus/dBasePlusRuntimeEngine1703_EN.exe** is properly installed
				- Copy the files cgi-binmch, htdocsmch, graficosint from the folder **pagweb** into **Apache 2.2**
					- ==**Note**== If these files are not in the **pagweb** check the ((626acb08-5cb7-4427-b86b-bd79eae6928f)) page at the end of the document for a download URL or click [here](https://u.pcloud.link/publink/show?code=kZu93yVZHnxlib8qVRmG5WX5zWwrPXpxqye7)
					  id:: 626c16bf-e554-47df-9a47-de91b9afa682
				- Check that the files **“*.dbn”** within **Apache\cgi-binmch** folder are pointing to the correct ODBC Connection.
				- Edit Apache configuration file
				  collapsed:: true
					- Look for **httpd.conf** file : **C:\Apache\Apache2.2\conf\httpd.conf**
						- DocumentRoot"C:/Apache/htdocsmch" instead of htdocs
						- <Directory "C:/Apache/htdocsmch"> instead of htdocsAlias /icons/ "C:/Apache/icons/"
						- Alias /mchg/ "C:/Apache/cgi-binmch/"
						- Alias /graficosint/ "C:/Apache/graficosint/"
						- ScriptAlias/cgi-bin/ "C:/Apache/cgi-bin/"
						- ScriptAlias/cgibinmch/ "C:/Apache/cgi-binmch/"
						- <Directory"C:/Apache/graficosint/">
						  AllowOverride None
						  Options None
						  Order allow,deny 
						  Allow from all
						  </Directory>
						- <Directory "C:/Apache/cgi-binmch/">
						  AllowOverride None
						  Options None
						  Order allow,deny
						  Allow from all 
						  </Directory>
						- ![image.png](../assets/image_1651252466539_0.png)
						- ==**Note**== Please be aware, that this should be edited according to you configuration.
					- Compare: **C:\Apache\Apache2.2\conf\original\httpd.conf** with **C:\Apache\Apache2.2\conf\httpd.conf**
					- Copy **c:\mch\midas.dll** in the **cgi-binmch** folder in the Apache Directory **“Apache\cg-binmch**
					- Configure **mch.dbn** in **cgi-binmch** folder
						- ==**Note**== This configure the name of the OBDC connection and the MYSQL version, so be consistent with the configuration that you have at **mch.dbn** in the **mch** main folder
					- Configure **mchWeb.dbn** in **cgi-binmch** folder
						- ==**Note**== This configure the language for the interface and of the database, so be consistent with the configuration that you have at **mch.dbn** in the **mch** main folder
					- Check that the **port 80** is not blocked by firewall (Windows or antivirus firewall)
					- The maps that have to be displayed on the website should be copied in the **cgi-binmch** folder under: **C:\Apache\Apache2.2\cgi-binmch**
						- ==**Note**== You will have to open the MCH client and **georeference** a map for the data. Otherwise, you will no see the map in the web pages.
							- To georeference a map go to **Definitions/Stations/Stns on maps by 2-points geog.psn** and reference the map.
- # II Deploying MCH API in Apache WSGI and [[Windows]]
	- ## Installation Steps:
		- ### 1 Installing Apache HTTP Server
		  collapsed:: true
			- Install Apache HTTP Server on our windows machine. Can be downloaded from [here](https://www.apachelounge.com/download/)
				- ![image.png](../assets/image_1651259612475_0.png)
			- Extract the files and copy **Apache24** to **C:\Apache24** (This is the default location).The content of the directory is as follows:
				- `Apache24 dir`
				- `Readme.txt file`
				- `--Win64VC15—file`
			- Copy the Apache24 directory to the root directory of our hard drive. i
			- Install the Apache server as a Windows service, run the following command from a **DOS command
			  window**, in the **C:\Apache24\bin** directory:
				- `C:\Apache24\bin\htppd.exe –k install`
		- ### 2 Install Python 3.7
		  collapsed:: true
			- Download [[Python]]from [here](https://www.python.org/) and Install [[Python]]
				- ![image.png](../assets/image_1651260389467_0.png)
				- ==**Note**== Make sure that the python version you're using has the same architecture (32/64 bit) as your Apache version.
				- ==**Note**== **This medium article [here](https://medium.com/co-learning-lounge/how-to-download-install-python-on-windows-2021-44a707994013) can be used to install python in windows**
				- Create an environment variable called ***PYTHONHOME*** so that our application finds the version that we just installed. The environment variable **Path** should be already there once you install [[Python]]
					- ==**Note**== Add the ***PYTHONHOME*** environment variable. You should have the python home path also in the *“path”* environment variable. The ***PYTHONHOME*** and *”path”* environment variables should have the same value.
		- ### 3 Install the **[[Python]]** Requirements
collapsed:: true
			- Once in the windows CMD run the command: `pip install -r requirements.txt`
			- Run the following: `pip install itsdangerous==2.0.1`
			- **==Note==**: You can add the **itsdangerous==2.0.1** to the **requirements.txt**. However, if there is no need to not have the latest version of Flask, then we can just install the latest version of Flask. I downgraded the **itsdangerous** because it was giving errors with the other dependencies.
			- **==Note==**: If you want to isolate the dependencies you can create a virtual environment for the API. It can be with [[pip]] or [[conda]]
		- ### 4 Install [[Visual C++ Build Tools]]
collapsed:: true
			- **==Note==** Before installing **[[mod_wsgi]]**, the installation of **[[Visual C ++ Build Tools]]** is required, this application can be downloaded from the Microsoft site [here (https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)
				- You will be prompted to install vs build tools **2022**, but you need to download an older version of it. We need the **2019** version. Click on older versions.
				  collapsed:: true
					- ![image.png](../assets/image_1651281184774_0.png)
				- Now select **2019**, and press **download**. You will be prompted to create an account with microsoft or to login with your github account. You can do either one to login.
				  collapsed:: true
					- ![image.png](../assets/image_1651281280064_0.png)
				- Select the **16.11 version**
				  collapsed:: true
					- ![image.png](../assets/image_1651281343495_0.png)
				- Do not select anything, and *go to* **individual components** and *select* the **MSVS compiler**
				  collapsed:: true
					- ![image.png](../assets/image_1651281944142_0.png)
				- Download and install
					- ![image.png](../assets/image_1651282017050_0.png)
		- ### 5 Install [[Windows SDK]]  version 2104 (10.0.20348.0)
collapsed:: true
			- **==Note==** We need to install the **Windows SDK** to avoid errors when installing the **[[mod_wsgi]]** library with [[pip]]
				- you will avoid the following errors [here](https://github.com/GrahamDumpleton/mod_wsgi/issues/194)
			- Please go [here](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive/)
			- Now select the **Windows 10 SDK version 2104 (10.0.20348.0)**
collapsed:: true
				- ![image.png](../assets/image_1651282338676_0.png)
		- ### 6 Deploying API-MCH directory
collapsed:: true
			- Copy the **API-MCH** directory in the designated hard drive to contain it.
			- Configure the credentials to access the **MCH database**. This process is done in the API file with a *.py* extension in the [[mysql]] connection configuration section.
				- `app.config['MYSQL_HOST']='DSN database or IP address'`
				- `app.config['MYSQL_USER']='user'`
				- `app.config['MYSQL_PASSWORD']='password'`
				- `app.config['MYSQL_DB']='mch_database'`
		- ### 7 Configure the mch.dbn file
collapsed:: true
			- Configure the mch.dbn file located in the API directory to configure the language of the database.
				- `mch`
				- `mysql5`
				- `2`
				- `2`
				- `--------- Format of this file.`
				- `1.- DSN to the database`
				- `2.- Type of database. For now only mysql5 is accepted`
				- `3.- User interface language 1-Spanish, 2-English, 3-French, 4-Other, 5-External files are required`
				- `4.- Language of the database. 1-Spanish, 2-English, 3-French, 4-Other, 5-External files are required. NOT this should to be set automatically with a data in a table.`
				- `5.- Browser used for the help.`
		- ### 8 Installing [[mod_wsgi]]
collapsed:: true
			- Point **MOD_WSGI_APACHE_ROOTDIR** to your installation (default is C:/Apache24) *Use forward slashes:*
				- `set MOD_WSGI_APACHE_ROOTDIR=C:/Users/me/apache`
			- Open a command prompt and install with [[pip]] : `pip install mod_wsgi`
			- Create api.wsgi file
				- **==Note==** In order for the application to be correctly called by mod_wsgi, it is necessary to create a
				  file with a wsgi extension where the basic instructions to call the application can be found.
				  The file should contain the following:
					- `import sys`
					- `sys.path.insert(0,'C:/API-MCH')`
					- `from api import app as application`
		- ### 9 Configure Apache http.conf
collapsed:: true
			- **==Note==** Modifying the Apache server configuration is required to enable the use of virtual hosts,
			  which is the medium where the applications called by [[mod_wsgi]] run.
			- Get module configuration with the following command in the DOS: `mod_wsgi-express module-config`
			- Copy the output of the previous command into your [[Apache]] 's httpd.conf. This works when copied below any line containing the LoadModule directive.
				- ![image.png](../assets/image_1651510006062_0.png)
			- Modify the following line of the httpd.conf file as shown:
				- `Virtual hosts`
				- `Include conf/extra/httpd-vhosts.conf`
		- ### 10 Modify httpd-vhosts.conf
collapsed:: true
			- **==Note==** To complete the configuration of the virtual hosts, modify the httpd-vhosts.conf file,
			  located in the **<Apache24-Home>\conf\extra directory** *(example: C:\Apache24\conf\extra directory)*
				- NameVirtualHost *:5000
				- <VirtualHost *:5000>
					- ServerAdmin webmaster@dummy-host.example.com
					- DocumentRoot "c:/Apache24/htdocs"
					- ServerName dummy-host.example.com
					- ServerAlias www.dummy-host.example.com
					- ErrorLog "logs/dummy-host.example.com-error.log"
					- CustomLog "logs/dummy-host.example.com-access.log" common
				- </VirtualHost>
				- <VirtualHost *:5000>
					- WSGIScriptAlias / C:\API-MCH\api.wsgi
					- WSGIApplicationGroup %{GLOBAL}
					- DocumentRoot "C:/API-MCH"
					- ErrorLog "${SRVROOT}/logs/vhost-error.log"
					- CustomLog "${SRVROOT}/logs/vhost-access.log" combined
					- <Directory C:/API-MCH>
						- AllowOverride None
						- Options None
						- Require all granted
					- </Directory>
				- </VirtualHost>
		- ### 11 Restart [[Apache]] Server
			- Open DOS or the service window and restart the Apache server
		- ### Extra steps
			- **==Note==** This is something that I was required to do, to update to the last version of the API. This is because the older version did not have a response for the countries and availability methods of the API
			- Check that you have the correct *MySQL OBDC 3.51* for **32-bit** or **64-bit**
			- Create the **countries** and **availability** MySQL tables by running the provided scripts in the [[mysql]] command line or query browser.
			- Check that tables of the MCH [[mysql]] are **MyIsam** tables
			- Check that the **Mch.dbn** is similar to the one in the MCH client folder
			- Check **MCHtablasycampos.def** and **MensajesMCH.def** compact versions in the API folder
			- Check the **Stationgroup** table, and make sure there is station groups.
			- For the **Availability** table:
				- **==Note==** The program that calculates these data is **CalcDisponib2.exe** and requires certain parameters:
					- -g stngroup
					- -v variable
					- -t [D|T], where -t is the data type to use D - daily and T - detail.
					- Example for a station group called *DR* and variable *Precipitation*
						- **CalcDisponib2.exe -g DR -v Precipitation -t D**
				- **==Note==** It is necessary to create all the command lines in the bat file for each of the variables that are required, they can have a group with all the stations or a group for each type of station (in case they have climatological, hydrometric stations, etc. .). This program requires some definition files such as **mch.dbn** and **MCHtablasycampos.def**, so it is advisable to copy it to the directory where the MCH client has been installed.
				- **==Note==** If more station groups are created or stations are added to the station group you need to run the **CalcDisponib2.exe** You can schedule a tasks.
- # III [[Tethys Platform]] Application
	- ## Installation Steps
collapsed:: true
		- ### 1 Allow remote connection to [[mysql]] MCH database
			- Open [[mysql]] command line and run:
				- `GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '<your myqsl password>' WITH GRANT OPTION;`
				- `FLUSH PRIVILEGES;`
				- **==Note==** The command will allow remote access to the **root** user using the password that you specify at *<your myqsl password>*
		- ### 2 Install the MCH Bridge application
			- Clone the repository: `git clone https://github.com/BYU-Hydroinformatics/mch_bridge.git`
			- Run `tethys install -d`
			- In the custom settings at the following:
				- ![image.png](../assets/image_1651514138440_0.png)
- # Ref Links:
  id:: 626acb08-5cb7-4427-b86b-bd79eae6928f
	- ## MCH Client
		- MCH Version 2018 Latest version of MCH: ==**The current link has expired**==
		- Free Pascal version of MCH: ==**The current link has expired**==
		- User Manual in English: [URL](https://u.pcloud.link/publink/show?code=XZ5GzCXZViEMavhNfG403rV1X4JrMmEFuQuk) ![MCH_User_Manual_2012_EN.pdf](../assets/MCH_User_Manual_2012_EN_1651166295355_0.pdf)
		- User Manual in Spanish: [URL](https://u.pcloud.link/publink/show?code=XZlYePXZXaaDorE0MV77UpmtzFuzXfVOqiQX) ![MCH_ManualUsuario_2009.pdf](../assets/MCH_ManualUsuario_2009_1651166456931_0.pdf)
		- Steps to install MCH and the additional software [URL](https://u.pcloud.link/publink/show?code=XZLmePXZ1RmEcsQ9mQVbSQCIrOzrU0h3tIp7) ![MCH-Installation-steps-v2018-updated06-2021-opt.pdf](../assets/MCH-Installation-steps-v2018-updated06-2021-opt_1651166139074_0.pdf)
		- Additional Software needed to run MCH:
			- [Gostscript](https://u.pcloud.link/publink/show?code=XZuFQxkZkp2f2KkBFJX8HGfUwsrN2hiAKGBk)
			- [Runtime](https://u.pcloud.link/publink/show?code=XZOFQxkZChg6wHApJ57nMeVHNuiesJF1GsDX)
				- Use **dBasePlusRuntimeEngine1703_ES.exe** if the operating system is in Spanish
			- MySQL
				- [SetupMySQL5_0_51.exe](https://u.pcloud.link/publink/show?code=XZzpQxkZBtHTJr8EzvpLQQj0KsD428AIkWaV)
				- [Setupmysql-5.0.51b-winx64.exe](https://u.pcloud.link/publink/show?code=XZSpQxkZ3PH1Hltan7XnHcObDGpwNJ5Qrbqy)
			- [MySQL ODBC connectors different versions](https://u.pcloud.link/publink/show?code=kZzHQxkZxKSLxJGC36pVy6vxwT8f00UQPcUV)
			- [MySQL tools](https://u.pcloud.link/publink/show?code=XZ2tQxkZeBdqRJxfKlh32j6YIeNCryjRFQX7)
			- Databases:
				- [mcheng](https://u.pcloud.link/publink/show?code=XZnDHyXZu6bEol5aSbzyYkRgTjltoYLzFu1k)
				- [capttemp](https://u.pcloud.link/publink/show?code=XZbIQxkZF906UzMvrbjzSdcxb0R12XdhsIAX)
	- ## MCH Web Pages
		- [Apache 2.2](https://archive.apache.org/dist/httpd/binaries/win32/)
			- httpd-2.2.11-win32-x86-no_ssl.msi
			- ==**Note**== Select the lates version, if idoenot work select previous version
		- [Files to configure Apache Server 2.2](https://u.pcloud.link/publink/show?code=kZu93yVZHnxlib8qVRmG5WX5zWwrPXpxqye7) Please Download the following.
			- cgi-binmch
			- htdocsmch
			- graficosint
	- ## MCH API
		- MCH API files
	-