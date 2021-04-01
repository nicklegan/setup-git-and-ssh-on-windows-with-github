# Setup Git and SSH on Windows with GitHub
Install and configure Git, PuTTY and SSH keys on Windows with GitHub

## Setup overview
- [Git for Windows](#Git-for-Windows)
- [PuTTY](#PuTTY)
  * [PuTTY Key Generator (puttygen.exe)](#PuTTY-Key-Generator-(puttygen.exe))
  * [PuTTY Authentication Agent (pageant.exe)](#PuTTY-Authentication-Agent-(pageant.exe))
  * [Plink - Command Line Connection Tool (plink.exe)](#Plink---Command-Line-Connection-Tool-(plink.exe))
- [Git global config](#Git-global-config)
- [Testing](#Testing)
- [Resources](#Resources)


## Git for Windows

- Download and install the latest [Git for Windows](https://gitforwindows.org/)

(skipped steps :point_down: can be treated having default values)

1. Select Components (default)

<img width="500" alt="Screenshot 2021-04-01 at 12 51 37" src="https://user-images.githubusercontent.com/60080580/113283788-0989e780-92e9-11eb-935f-21313f6b6a37.png">

2. Adjusting the default branch name for new repositories (main branch)

<img width="500" alt="Screenshot 2021-04-01 at 12 56 42" src="https://user-images.githubusercontent.com/60080580/113284933-a26d3280-92ea-11eb-8351-06eee1bada22.png">

3. Adjusting your PATH environment

- Git from the command line and also from 3rd party software

<img width="500" alt="Screenshot 2021-04-01 at 13 07 10" src="https://user-images.githubusercontent.com/60080580/113285937-d5fc8c80-92eb-11eb-8fe6-41116d06b6e6.png">

4. Choosing HTTPS transport backend

<img width="500" alt="Screenshot 2021-04-01 at 13 14 49" src="https://user-images.githubusercontent.com/60080580/113286283-46a3a900-92ec-11eb-9927-d04c38811c04.png">

5. Configuring the line ending conversions

<img width="500" alt="Screenshot 2021-04-01 at 13 16 58" src="https://user-images.githubusercontent.com/60080580/113286493-908c8f00-92ec-11eb-9844-be7ae29d916a.png">

6. Use MinTTY (the default terminal of MSYS2)

<img width="500" alt="Screenshot 2021-04-01 at 13 20 12" src="https://user-images.githubusercontent.com/60080580/113286859-0a247d00-92ed-11eb-933e-be38a25efaea.png">

7. Choose the default behavior of `git pull`

<img width="500" alt="Screenshot 2021-04-01 at 13 22 49" src="https://user-images.githubusercontent.com/60080580/113287113-64254280-92ed-11eb-822f-f2dc68e323d6.png">

8. Choose a credential helper

<img width="500" alt="Screenshot 2021-04-01 at 13 24 36" src="https://user-images.githubusercontent.com/60080580/113287261-a0f13980-92ed-11eb-839c-2d695060039b.png">

9. Configuring extra options

<img width="500" alt="Screenshot 2021-04-01 at 13 25 49" src="https://user-images.githubusercontent.com/60080580/113287406-d433c880-92ed-11eb-9e19-ad2f6336d39a.png">

10. Configuring experimental options

<img width="500" alt="Screenshot 2021-04-01 at 13 26 51" src="https://user-images.githubusercontent.com/60080580/113287516-fdecef80-92ed-11eb-9a94-17a32a13069b.png">

11. Completing the Git Setup Wizard

- yes, restart the computer now

<img width="500" alt="Screenshot 2021-04-01 at 13 28 26" src="https://user-images.githubusercontent.com/60080580/113287702-3391d880-92ee-11eb-93f6-4242854e3dec.png">

## PuTTY

1. Download and install the latest [PuTTY MSI Package installer](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) for Windows

:bulb: This package installer will also contain and automatically installs the required `plink.exe`, `pageant.exe` and `puttygen.exe` binaries required :point_down:.

2. Destination folder

<img width="500" alt="Screenshot 2021-04-01 at 13 50 22" src="https://user-images.githubusercontent.com/60080580/113289989-4528af80-92f1-11eb-8593-1b4dc6ec443e.png">

3. Product Features

<img width="500" alt="Screenshot 2021-04-01 at 13 55 24" src="https://user-images.githubusercontent.com/60080580/113290449-f3345980-92f1-11eb-9c9d-4d9f28c1e696.png">

4. After the installation of PuTTY has finished, create a `.ssh` folder in your logged in user folder: `C:\Users\yourusername\.ssh\` or the equivalent `%USERPROFILE%\.ssh\`

### PuTTY Key Generator (puttygen.exe)

5. Run `puttygen.exe` either from the Start menu or the direct locaation at `C:\Program Files\PuTTY\puttygen.exe`

<img width="500" alt="Screenshot 2021-04-01 at 15 18 17" src="https://user-images.githubusercontent.com/60080580/113299770-82933a00-92fd-11eb-9479-4af4632696ec.png">

6. Click `Generate`, wiggle the mouse around in the top part of the window until the progress bar is full, as the program asks you to do.

7. Enter your email address in the `Key comment` box.

8. Provide a passphrase, and repeat it in the subsequent textbox.

9. Click `Save private key`. Save the private key in the  `%USERPROFILE%\.ssh\` directory created earlier. Give the private key a personal name so it can be easily identified. This file should have a `.ppk` extension.

10. In `puttygen.exe` copy the generated Public key visible under `Public key for pasting into OpenSSH authorized keys file` to your Windows clipboard (see image :point_up:).

11. Open your browser and navigate to github.com and add a new [SSH key](https://github.com/settings/ssh/new) in your account settings. Choose a key title (e.g. your email address or computer name) and paste the public SSH key data from clipboard before pressing `Add SSH key`.

<img width="800" alt="Screenshot 2021-04-01 at 15 33 51" src="https://user-images.githubusercontent.com/60080580/113302157-1239e800-9300-11eb-9523-3ce35a04a9c2.png">

<img width="800" alt="Screenshot 2021-04-01 at 15 34 38" src="https://user-images.githubusercontent.com/60080580/113302406-4d3c1b80-9300-11eb-9612-fe63ce32de6d.png">

:bulb: If you have and need command line access to GitHub Single sign-on organizations make sure you authorize your SSH key by activating [Enable SSO](https://docs.github.com/en/github/authenticating-to-github/authorizing-an-ssh-key-for-use-with-saml-single-sign-on) for the specific GitHub organizations.

### PuTTY Authentication Agent (pageant.exe)

12. To automatically run `pageant.exe` and the loaded private key at startup copy the Pageant shortcut from:

```C:\ProgramData\Microsoft\Windows\Start Menu\Programs\PuTTY (64-bit)```

```%ProgramData%\Microsoft\Windows\Start Menu\Programs\PuTTY (64-bit)```

to

```C:\Users\your-username\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup```

```%AppData%\Microsoft\Windows\Start Menu\Programs\Startup```

13. At the new Pageant shortcut startup location, right-click the Pageant shortcut and select `Properties` from the context menu.

<img width="400" alt="Screenshot 2021-04-01 at 17 44 24" src="https://user-images.githubusercontent.com/60080580/113319618-eaec1680-9311-11eb-9e10-378c8cddb0a9.png">

14. At the Pageant Properties append the path to your private key in the `Target` field and press Apply:

```"C:\Program Files\PuTTY\pageant.exe" C:\Users\your-user-name\.ssh\your-private-key.ppk```

15. Double click the Pageant shortcut file which starts Pageant and enter your private key passphrase.

<img width="250" alt="Screenshot 2021-04-01 at 17 51 31" src="https://user-images.githubusercontent.com/60080580/113320584-f0962c00-9312-11eb-8943-2f88c8d8b90a.png">

16. On the right side of the Windows taskbar Pageant should now be running, if it was already running press `Exit` and double click the newly created startup shortcut again.

<img width="300" alt="Screenshot 2021-04-01 at 18 13 17" src="https://user-images.githubusercontent.com/60080580/113323210-fd684f00-9315-11eb-82b9-245e0a9188ca.png">

17. From the Pageant menu select `View Keys` to verify that your private key is loaded.

<img width="500" alt="Screenshot 2021-04-01 at 18 21 24" src="https://user-images.githubusercontent.com/60080580/113324271-381eb700-9317-11eb-8b10-ecaa3fe0de43.png">

## Plink - Command Line Connection Tool (plink.exe)

To automatically let Putty establish a connection for Git over SSH we have to configure Plink.

18. Nagivate to Start menu (right-click) -> System -> Advanced system settings -> Environment Variables. Add a new System Variable with the below entries:

```Variable name: GIT_SSH```


```Variable value: C:\Program Files\PuTTY\plink.exe```

<img width="600" alt="Screenshot 2021-04-01 at 19 11 38" src="https://user-images.githubusercontent.com/60080580/113330715-57b9dd80-931f-11eb-90dc-93e94b4d4d2f.png">

19. To verify if the environment variable is loaded run `Git Bash` from the Start menu (or via its absolute path: `C:\Program Files\Git\git-bash.exe`) and enter the following command: ` env | grep -i ssh` which should return the enabled `GIT_SSH` variable.

<img width="450" alt="Screenshot 2021-04-01 at 19 29 05" src="https://user-images.githubusercontent.com/60080580/113331722-93a17280-9320-11eb-96a6-7c44d2c9fb68.png">

## Git global config

Setup your [Git username](https://docs.github.com/en/github/getting-started-with-github/setting-your-username-in-git#setting-your-git-username-for-every-repository-on-your-computer) and [commit email address](https://docs.github.com/en/github/setting-up-and-managing-your-github-user-account/setting-your-commit-email-address#setting-your-commit-email-address-in-git) for your system. Open a command prompt and enter the below lines, adding your personal info.

1. `git config --global user.name "First-name Last-name"`
2. `git config --global user.email your@email-address.com`

## Testing

1. Open a Windows command prompt and test your connection and authentication using the following command: `plink.exe -v git@github.com` the result should look like :point_down:.

<img width="800" alt="Screenshot 2021-04-01 at 19 40 03" src="https://user-images.githubusercontent.com/60080580/113333610-eed46480-9322-11eb-80ea-437fd2cbe3c6.png">

2. Now try cloning a private repository using Git over SSH, when successful the expected output should look like the image :point_down: and you will be automatically authenticated.

<img width="800" alt="Screenshot 2021-04-01 at 19 51 16" src="https://user-images.githubusercontent.com/60080580/113334188-b08b7500-9323-11eb-977b-538bba8a270c.png">

<img width="650" alt="Screenshot 2021-04-01 at 19 54 22" src="https://user-images.githubusercontent.com/60080580/113334660-41625080-9324-11eb-8748-5c73f4dc13bd.png">

## Resources
- https://vladmihalcea.com/tutorials/git/windows-git-ssh-authentication-to-github/
- https://serverfault.com/questions/194567/how-do-i-tell-git-for-windows-where-to-find-my-private-rsa-key/850156#850156