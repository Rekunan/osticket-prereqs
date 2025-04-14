# osTicket - Prerequisites and Installation

This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.

## Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

## Operating Systems Used

- Windows 10 (21H2)

## List of Prerequisites

- Download link for files: https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD

## Installation Steps

- Click on the link and press download.
- Unzip the file to its own folder anywhere, here I unzipped to `C:\Users\labuser\Documents\osTicket-Installation-Files`

![The unzip location and folder of `osTicket-Installation-Files.zip` that I used here](https://safe.reku.me/ulB80ox6imMS.png)
- Go into `Control Panel -> Programs -> Turn Windows features on or off`
- Scroll down to `Internet Information Services`
- Check the box on:
	- `Web Management Tools\IIS Management Console`
	- `World Wide Web Services\Application Development Features\CGI`
	- `World Wide Web Services\Common HTTP Features`

![All the Windows Features you need to enable](https://safe.reku.me/ozOty257povP.png)
- Press `OK` and then close `Control Panel`
- You can then check by going to `127.0.0.1` in your web browser (here I used Microsoft Edge), it should look like this:

![What `127.0.0.1` should look like](https://safe.reku.me/JGu1pu28a8rw.png)
- Then go back to `osTicket-Installation-Files`
- Run `PHPManagerForIIS_V1.5.0.msi`

![The `PHP Manager for IIS` Setup Wizard](https://safe.reku.me/tCqbagooc04y.jpg)
- Keep clicking until `PHP Manager for IIS` is installed.
- Go back to `osTicket-Installation-Files`
- Run `rewrite_amd64_en-US.msi`

![The `IIS URL Rewrite Module 2` Setup](https://safe.reku.me/7RbsVWlHCL0L.png)
- Keep clicking until `Rewrite Module` is installed.
- Go back to `osTicket-Installation-Files`
- Go to `C:`
- Create the directory `C:\PHP`

![The directory `C:\PHP`](https://safe.reku.me/NUmHBqvN87pT.png)
- Go back to `osTicket-Installation-Files`
- Unzip `php-7.3.8-nts-Win32-VC15-x86.zip` to `C:\PHP`

![Unzipping `php-7.3.8-nts-Win32-VC15-x86.zip` to `C:\PHP`](https://safe.reku.me/B6FTWadmpNDj.png)
- Go back to `osTicket-Installation-Files`
- Run `VC_redist.x86.exe`

![`VC_redist.x86.exe`](https://safe.reku.me/nJHIM2aSHGNv.png)
- Keep clicking until `VC redist` is installed.
- Go back to `osTicket-Installation-Files`
- Run `mysql-5.5.62-win32.msi`

![`MySQL` Setup](https://safe.reku.me/Lx40UAD6gEuS.png)
- Click next until you get to `Setup Type`
- Click`Typical`

![`Setup Type`](https://safe.reku.me/J7TmdSN7lsva.png)
- Click next until you get to `Configuration Wizard
- Click `Standard Configuration`

![Configuration type](https://safe.reku.me/IdJ2aBBr99I6.png)
- Click next until you get to `security options`
- Click `Modify Security Settings`
- Set the `MySQL` password and save it (here I use `root`)

![`Security options`](https://safe.reku.me/m3jII95ZjSbM.png)
- Click next until configuration finishes.
- Open `Internet Information Services (IIS) Manager` as an admin.
- Click on `PHP Manager`
- Click on `Register new PHP version`
- Type or select `C:\PHP\php-cgi.exe`

![Register PHP](https://safe.reku.me/HrIGhir9NDgo.png)
- Click `OK`
- On the right side, click `Restart`

![`Restart`](https://safe.reku.me/M3y0TmrWQgRH.png)
- Go back to File Explorer
- Go back to `osTicket-Installation-Files`
- Unzip `osTicket-v1.15.8.zip` right there

![Unzipping `osTicket-v1.15.8`](https://safe.reku.me/49UAoeI19xnI.png)
- Go to `osTicket-v1.15.8`
- Copy `upload`
- Go to `c:\inetpub\wwwroot`
- Paste
- Rename `upload` to `osTicket`

![`osTicket` in `c:\inetpub\wwwroot`](https://safe.reku.me/nxRHqidrrBxu.png)
- Go back to `Internet Information Services (IIS) Manager`
- On the left side, go to `Sites` -> `Default Web Site` -> `osTicket`

![`Sites` -> `Default Web Site` -> `osTicket`](https://safe.reku.me/IyHY3lU32opx.png)
- Click `PHP Manager`
- Click `Enable or disable an extension`
- Enable:
	- `php_imap.dll`
	- `php_intl.dll`
	- `php_opcache.dll`
- All of these should be enabled:

![Enabled PHP extensions](https://safe.reku.me/qrSdSzEl6nKh.png)
- On the right side, click `Browse *:80 (http)`

![`Browse *:80 (http)`](https://safe.reku.me/pYcMszknZiBH.png)
- You will see a checklist, and it should look like this:

![osTicket checklist](https://safe.reku.me/Ov3lmsvZpJZX.png)
- Go back to File Explorer
- Go to `C:\inetpub\wwwroot\osTicket\include`
- Rename `ost-sampleconfig.php` -> `ost-config.php`

![`ost-config.php` in `C:\inetpub\wwwroot\osTicket\include`](https://safe.reku.me/RDGnBN8HGzl5.png)
- Right-click `ost-config.php`
- Click on `Properties`
- Go to `Security`
- Click on `Advanced`
- Click on `Disable inheritance`
- Click `Remove all inherited permissions from this object.`

![Removing inheritance](https://safe.reku.me/QuF7D9XTahLp.png)
- Click on `Add`
- Click `Select a principal`
- Type in `Everyone` as the object name

![Adding the `Everyone` object](https://safe.reku.me/ZeLfRmPKUsg6.png)
- Click `OK`
- Check the `Full control` box

![Checking `Full control`](https://safe.reku.me/UexCB0SFKpCe.png)
- Click `OK` until you're out of the `Properties` menu
- Go back to your browser
- Click `Continue`
- Fill out `System Settings` and `Admin User`
- Here's what I did:

![`System Settings`](https://safe.reku.me/OAF0ZoJS7QVn.png)
![`Admin User`](https://safe.reku.me/rEPq8wZiyhQd.png)
- Go back to File Explorer
- Go back to `osTicket-Installation-Files`
- Run `HeidiSQL_12.3.0.6589_Setup.exe`

![`HeidiSQL` Setup](https://safe.reku.me/35zHunB7LxRp.png)
- Keep clicking until `HeidiSQL` is installed
- Open `HeidiSQL`
- Click on `New` in the bottom right

![Session Manager](https://safe.reku.me/HZwAEsIvaUPD.png)
- Click `Session in root folder`
	- User: `root`
	- Password the `MySQL` password you saved earlier (here it's `root`)

![Session manager: `root`](https://safe.reku.me/SZuCM6C15CJf.png)
- Click `Open`
- Right-click the whitespace on the left, and click `Create new` -> `Database`

![`Create new` -> `Database`](https://safe.reku.me/dnuBiYFFACAN.png)
- Name: `osTicket`

![osTicket DB](https://safe.reku.me/X9hfbOA1D9bH.png)
- Click `OK`
- Go back to your browser
- Fill out your database settings appropriately

![`Database Settings`](https://safe.reku.me/3pKQ7zrLPPbd.png)
- Click `Install Now`
- Congratulations!

![Congratulations!](https://safe.reku.me/esF5zj15B9Tt.png)
- Check `http://localhost/osTicket/scp/login.php` to make sure it looks like this:

![`http://localhost/osTicket/scp/login.php`](https://safe.reku.me/TJW7G8GmOdeu.png)
- Check `http://localhost/osTicket` to make sure it looks like this:

![`http://localhost/osTicket`](https://safe.reku.me/RLiLu5kw1M9y.png)
- Go back to File Explorer
- Go to `C:\inetpub\wwwroot\osTicket`
- Delete `C:\inetpub\wwwroot\osTicket\setup`

![`C:\inetpub\wwwroot\osTicket\setup`](https://safe.reku.me/k2Wn1DWk4OO7.png)
- Right-click `C:\inetpub\wwwroot\osTicket\include\ost-config.php`
- Click on `Properties`
- Check `Read-only`

![`Read-only`](https://safe.reku.me/kSRNZqZOC4lD.png)
- Click `OK`

You have finished installing `osTicket` now.
