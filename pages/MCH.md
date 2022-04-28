- # Installation in [[Windows]] Server
	- ## Steps:
		- ### Configuration of the computers & Installation environment
			- Login with full administrator rights
			- Check if your computer has a 32 or 64-bit processor
			- Create shortcuts to ODBC,services and control panel (This step is not necessary)
			- Set regional settings, decimals should be defined with dots (.)
			- Turn Wi-Fi off or disconnect the computer from internet
			- Turn Antivirus off
			- Disable Firewall
		- ### Installation of MCH
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
		- ### Installation of Additional Software
			- ==**Note**== Check the ((626acb08-5cb7-4427-b86b-bd79eae6928f)) page to find links to the additional software.
			- Install [gostscript.ps –32 or 64 bits](https://u.pcloud.link/publink/show?code=XZuFQxkZkp2f2KkBFJX8HGfUwsrN2hiAKGBk).
collapsed:: true
				- ==Note== Leave default settings (install fonts ticked)
				- ![image.png](../assets/image_1651171354553_0.png)
			- Install [RuntimePlus](https://u.pcloud.link/publink/show?code=XZOFQxkZChg6wHApJ57nMeVHNuiesJF1GsDX) (RunTimePlus /dBasePlusRuntimeEngine1703_EN.exe)
collapsed:: true
				- ![image.png](../assets/image_1651171558178_0.png)
			- ==**Optional**== If needed edit the **gmtenv.bat** (C:/MCH/gmtenv.bat), needed for the map environment as follows:
collapsed:: true
				- ![image.png](../assets/image_1651171639225_0.png)
			- Installation of MySQL Server 5
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
collapsed:: true
					- Enabling TCP/IP networking
						- ![image.png](../assets/image_1651173457653_0.png)
							- 1. Tick Enable TCP/IP Networking
							  2. Select port 3306
							  3. Tick Add firewall exception
							  4. Untick Enable Strict Mode
					- Select Standard Character Set
						- ![image.png](../assets/image_1651173496955_0.png)
					- Installing as a [[Windows]] service
						- ![image.png](../assets/image_1651173761812_0.png)
							- 1. Tick Install as Windows Service
							  2. Select MySQL5
							  3. Tick Launch the MySQL server automatically
							  4. Tick include Bin
				- Set MySQL Admin password
					- Tick Modify Security Settings
					- Create a password ==**Save it**==
					- Tick Enable root access from remote machines
					- ![image.png](../assets/image_1651174041892_0.png)
				- Execute
					- ![image.png](../assets/image_1651174090878_0.png)
				- Finish
					- ![image.png](../assets/image_1651174106691_0.png)
				- Check that the service is properly running
					- ==**Note**== **If it is not running check firewall exceptions**
				- Check that password is by running: **Programmes/MySQL/MySQL Server 5/MySQL Command Line Client**
					- ![image.png](../assets/image_1651174236674_0.png)
			- Install MySQL Server 5 Tools
				- Execute: [mysql-gui-tools-5.0-r12-win32.msi](https://u.pcloud.link/publink/show?code=XZ2tQxkZeBdqRJxfKlh32j6YIeNCryjRFQX7)
					- ![image.png](../assets/image_1651174469704_0.png)
				- Select the folder tools with in the folder where MySQL Server 5 has been installed
collapsed:: true
					- ==**Note**== If it does not exist create a new folder and rename it `«tools»`
					- ![image.png](../assets/image_1651174549959_0.png)
					- ![image.png](../assets/image_1651174589224_0.png)
				- Select Complete
					- ![image.png](../assets/image_1651174618500_0.png)
				- Install
					- ![image.png](../assets/image_1651174644361_0.png)
					-
				-
- # Ref Links:
  id:: 626acb08-5cb7-4427-b86b-bd79eae6928f
	- MCH Version 2018 Latest version of MCH: ==**The current link has expired**==
	- Free Pascal version of MCH: ==**The current link has expired**==
	- User Manual in English: [URL](https://u.pcloud.link/publink/show?code=XZ5GzCXZViEMavhNfG403rV1X4JrMmEFuQuk) ![MCH_User_Manual_2012_EN.pdf](../assets/MCH_User_Manual_2012_EN_1651166295355_0.pdf)
	- User Manual in Spanish: [URL](https://u.pcloud.link/publink/show?code=XZlYePXZXaaDorE0MV77UpmtzFuzXfVOqiQX) ![MCH_ManualUsuario_2009.pdf](../assets/MCH_ManualUsuario_2009_1651166456931_0.pdf)
	- Steps to install MCH and the additional software [URL](https://u.pcloud.link/publink/show?code=XZLmePXZ1RmEcsQ9mQVbSQCIrOzrU0h3tIp7) ![MCH-Installation-steps-v2018-updated06-2021-opt.pdf](../assets/MCH-Installation-steps-v2018-updated06-2021-opt_1651166139074_0.pdf)
	- Additional Software needed to run MCH:
		- [Gostscript](https://u.pcloud.link/publink/show?code=XZuFQxkZkp2f2KkBFJX8HGfUwsrN2hiAKGBk)
		- [Runtime](https://u.pcloud.link/publink/show?code=XZOFQxkZChg6wHApJ57nMeVHNuiesJF1GsDX)
		- MySQL
			- [SetupMySQL5_0_51.exe](https://u.pcloud.link/publink/show?code=XZzpQxkZBtHTJr8EzvpLQQj0KsD428AIkWaV)
			- [Setupmysql-5.0.51b-winx64.exe](https://u.pcloud.link/publink/show?code=XZSpQxkZ3PH1Hltan7XnHcObDGpwNJ5Qrbqy)
		- [MySQL ODBC connectors different versions](https://u.pcloud.link/publink/show?code=kZzHQxkZxKSLxJGC36pVy6vxwT8f00UQPcUV)
		- [MySQL tools](https://u.pcloud.link/publink/show?code=XZ2tQxkZeBdqRJxfKlh32j6YIeNCryjRFQX7)
		- Databases:
			- [mcheng](https://u.pcloud.link/publink/show?code=XZnDHyXZu6bEol5aSbzyYkRgTjltoYLzFu1k)
			- [capttemp](https://u.pcloud.link/publink/show?code=XZbIQxkZF906UzMvrbjzSdcxb0R12XdhsIAX)
-