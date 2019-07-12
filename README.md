[![BuildStatus](https://travis.innovate.ibm.com/ESInnovationLab/ar-api.svg?token=y3yz3mxcSqS1APhnSgJA&branch=develop)](https://travis.innovate.ibm.com/ESInnovationLab/ar-api)

# Accounts Receivable REST API

# Table of Contents

  * [Overview](#overview)
  * [Prerequisites](#prerequisites)
  * [Add SSH Keys for Github](#add-ssh-keys-for-github)
    * [Mac OS](#mac-os)
    * [Windows](#windows)
  * [Troubleshooting](#troubleshooting)
    * [NPM install error on Windows](#npm-install-error-on-windows)
    * [Windows Virtual Machine with Virtual Box](#windows-virtual-machine-with-virtual-box)
  
# Overview

This repository exclusively contains the back-end service of the Accounts Receivable project.

# Prerequisites

1. Install [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
2. Install [Node.js v6.9.2 or higher](https://nodejs.org/en/download/)

For Windows users, see [these additional notes](#windows-additional-notes) below.

## Windows Additional Notes

In Windows, somehow you might encounter strange issues. We strongly recommend you to follow these instructions to setup your environment.  The tools used in this project require Windows 7 or higher, with these additional prerequisites:

1. Install [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git#Installing-on-Windows)
  - Use these configuration options:
    1. **Adjusting your PATH environment**: _Use Git from the Windows Command Prompt_ ![Screenshot](https://media.github.ibm.com/download/user/1226/files/ff1b2ee4-e9dd-11e5-97e7-14e0dfa59aa5)
    2. **Configuring the line ending conversions**: _Checkout as-is, commit Unix-style line endings_ ![Screenshot](https://media.github.ibm.com/download/user/1226/files/c6b5472a-e9dc-11e5-97c2-6ab971319396)
    3. **Configuring the terminal emulator to use with Git Bash**: _Use Windows' default console window_ ![Screenshot](https://media.github.ibm.com/download/user/1226/files/031e5c82-e9de-11e5-9035-66e30151fc3c)
2. Install Python v2.7.x (v3.x is not supported by `node-gyp`)
  - Download and run the [official installer](https://www.python.org/downloads/release/python-27)
  - Add the Python installation directory (default: `C:\Python27`) to the `PATH` environment variable
    1. Right click _My Computer_ and choose _Properties_
    2. Open the _Advanced_ tab and click the _Environment Variables_ button
    3. Look for the variable named `PATH`
      - If it does not exist, create it by clicking on _New..._
      - If it exists, click on _Edit..._
    4. Add the Python installation directory in its value
      - ![Screenshot](https://media.github.ibm.com/download/user/1226/files/1ebc2424-e9de-11e5-961d-94a74c7c68cd)
3. Install Microsoft Visual Studio C++ 2013 ([Express](https://www.microsoft.com/en-gb/download/details.aspx?id=44914) version works well)
  - This is needed by `node-gyp`. Read about it in the [`node-gyp` installation instructions](https://github.com/nodejs/node-gyp#installation)
  - There are alternate instructions in [this node-gyp Github issue](https://github.com/nodejs/node-gyp/issues/629#issuecomment-153196245)

# Add SSH Keys for Github

## Mac OS

1. In **MacTerminal**, paste the command below, substituting in your GitHub email address. It will create a new ssh key, using the provided email as a label.

```
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
2. When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.

```
Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]
```
3. Then at the prompt, you will be asked for a secure passphrase.

```
Enter passphrase (empty for no passphrase): [Type a passphrase]
Enter same passphrase again: [Type passphrase again]
```
4. Ensure ssh-agent is enabled by running:

```
$ eval "$(ssh-agent -s)"
```
5. Add your SSH key to the ssh-agent by running:

```
$ ssh-add ~/.ssh/id_rsa
```
6. Copy the SSH key to your clipboard by running:

```
$ pbcopy < ~/.ssh/id_rsa.pub
```
Note: If your SSH key file has a different name than the example code, modify the filename to match your current setup. When copying your key, don't add any newlines or whitespace.

7. Then log into [Github](http://github.ibm.com/). Click your profile photo (top right corner), then click Settings.

8. In the user settings sidebar (left side), click SSH keys.

9. Click Add SSH key.

10. In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal Mac, you might call this key "Personal MacBook Air".

11. Paste the previously copied key (step 6) into the "Key" field.

12. Click Add key and confirm the action.

13. Open Terminal again and enter:

```
$ ssh -T git@github.ibm.com
```
14. Verify that the fingerprint in the message you see matches the following message, then type yes:

```
Hi username! You've successfully authenticated, but GitHub does not
provide shell access.
```
It's Done! Just verify that the resulting message contains your username. 

## Windows

Note: all commands must be run in **Git Bash**

1. In **Git Bash**, paste the text below, substituting in your GitHub email address. It will create a new ssh key, using the provided email as a label.

```
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
2. When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.

```
Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]
```
3. Then at the prompt, you will be asked for a secure passphrase.

```
Enter passphrase (empty for no passphrase): [Type a passphrase]
Enter same passphrase again: [Type passphrase again]
```
4. Ensure ssh-agent is enabled by running the following:

```
$ eval "$(ssh-agent -s)"
```
5. Add your SSH key to the ssh-agent by running:

```
$ ssh-add ~/.ssh/id_rsa
```
6. Copy the SSH key to your clipboard by running:

```
$ clip < ~/.ssh/id_rsa.pub
```
Note: If your SSH key file has a different name than the example code, modify the filename to match your current setup. When copying your key, don't add any newlines or whitespace.

7. Then log into [Github](http://github.ibm.com/). Click your profile photo (top right corner), then click Settings.

8. In the user settings sidebar (left side), click SSH keys.

9. Click Add SSH key.

10. In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal Windows machine, you might call this key "Personal Windows Machine".

11. Paste the previously copied key (step 6) into the "Key" field.

12. Click Add key and confirm the action.

13. Open **Git Bash** again and enter:

```
$ ssh -T git@github.ibm.com
```
14. Verify that the fingerprint in the message you see matches the following message, then type yes:

```
Hi username! You've successfully authenticated, but GitHub does not
provide shell access.
```
It's Done! Just verify that the resulting message contains your username. 

## Developer Install

1. Checkout the source code
  - Latest and greatest is in `develop`
  - Production should use `master`
  - Select the `develop` branch as your origin. Note: The `master` branch is not for active development; it is the stable branch where only releases are tagged from.

  ```sh
  git clone -b develop git@github.ibm.com:ESInnovationLab/ar-api.git
  cd ar-api
  ```
2. Install the application's dependencies by issuing the following command from ar-api directory
  - Firtly, you have to checkout [Install and configure node-rdkafka in local machine guideline](https://github.ibm.com/ESInnovationLab/ar-web/wiki/Configure-node-rdkafka-in-local-machine)
  - Then do install dependencies
  ```sh
  npm install
  ```
3. Modify the configuration to work on local

  - Clone file `.env.example` to `.env` and update the variables to correctly use the environment as well as the dependencies resources you want.

    ```.env
    DATABASE_USERNAME=c18fc815-742b-4d3d-a25e-469fececb936-bluemix
    DATABASE_PASSWORD=[Reach out your teammate to get this password]
    JWT_SECRET=randomstring
    AUTH_JWT_SECRET=randomstring
    PUSH_NOTIFICATION_API_ENDPOINT=https://ar-push-api-dev.w3ibm.mybluemix.net
    DB2_HOST=dashdb-txn-large-yp-dal10-03.services.dal.bluemix.net
    DB2_USERNAME=engagear
    DB2_PASSWORD=[Reach out your teammate to get this password]
    DB2_DB=BLUDB
    DB2_PORT=50000
    DB2_SCHEMA=ENGAGE_AR
    EXCEPT_DB_NAME=soecustomer
    EXCEPT_DESIGN=Exception
    EXCEPT_SEARCH=custSearch
    EXCEPT_VIEW=exceptions
    ARORG_DB_NAME=arorganization_mock
    ARORG_DESIGN=arorgDesign
    ARORG_SEARCH=arorgSearch
    FACES_URL=http://faces.w3ibm.mybluemix.net/api/find/
    PROFILE_DB_NAME=profile_mock
    PROFILE_DESIGN=Profile
    PROFILE_VIEW=profile-view
    ROLES=manager2,manager1,hecpfocal,hecpadmin,hecpcollector,ccp
    FRONTEND_CALLBACK_URL=http://localhost:3000/#/auth
    SAML_ENTITY_ID=http://localhost:6002
    SAML_ASSERT_URL=http://localhost:6002/auth/assert
    SAML_SP_PRIVATE_KEY=MIIEvgIBADANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQD1zNCUjfctQgOQyyA5e3UegBX8nwLK836oHFuUw7or6o/diNl9OSiB2/hx67FzgQ4PQ7qI8EPRo8q0uHERQ9KI/5WxxCkyj7jPIzIQwLuM3IlQjmE8Fcf4mxReg9MUQ5X+jY/eEltSmGw6Q4L18OzHmnVTUjXsa5+jfNkxo4oKyGWY7sTj+lgX5kKJbJQeldR3lXY847+jTf1lhliUfiWtmX8I5/F3EvQybaCAQMcJS6dSc53A5Uf/LppGzuKd3JSA6fKswmU6sbpxBVWJEen+0KZjx25oLWh8CvxGt5XLUEiOqinx6v2TTlv41BgMuM2OOc7MfPaql0ldRhpoVRnbAgMBAAECggEAXtgRA8FjxwrZ5Vz7qjKBFqvF0BxrL3SVQrjufZConZl8uba8dR1BDBqc2xhe+HqruiggKgbLpHDXHrSsrETHUCWO1XEjlGbwoLyr7Nrxg4D1WygVTOH6r2rniTDEmeUaU4a8JKxgoJY/7JtwRQYZ10s6SlRGiltc1fCuvgCkm1PGibAnwhNMGZALTv0eE2zG2+Vck6dVOvGL+fhczleeI4Mbf7WgSNGSc6n/mQoN4+u1zDLIqhp/NR64sI8Y4TLwv/yUDNgH/EP9dvXwuHpEisar5oDRjRGkebdVZSdcZbFvX+shNBR0uqP7fC4RYIh28uv12FgrWMZ2A9ntSLwDQQKBgQD7qMNKzN5wU6Ipqlj7D25F2OHOkNYhszPoTUgVci7yPBeFdwUENIfVF/mktsMT/c6Fepogeqok6n4nhQj8UV4QxsFZWD8JU8cAhRSntTbbAFCeuLRMIcu3OF133g+4KVUDMMhkfuxtgeFY1jbyB1VaS+CXzZEGSYvo3309dSDkvQKBgQD6Ci4NybxHM4APKalKqIPb9KrSlb3/bFkupqfM/K/F6tBMolC+ygQVQDqcmLhYR2cq1WoAgT0RRH4YtOX0tiTC3hAZmWRKxS+g8qCqxB0slZbhtsUkkF8V0PYr7PC9BlitvsxMYa/Vzpq1OVsBwMYZAV4Q+COKKfR4RzMwBAk+dwKBgQDExVkl5HhMpegW4f4/F/qmHIW6yR7VLNR6X+rr8eLpPrk5fy1p81T99ogZFVoFCJ/xWEKpAKCGyt8nMWssNsbxISdPH6PyPBJOwr+6vgONS3q+EDfRi19I/IaA0h3CZnb1TrBxe5iLq1Ey8BP4PGmtd8S9jVtG6jy+MfkwE6RLlQKBgGxkIVbEzyOmhasNCmBc8NxXEf47/6NMWtTIVhGcsK4Bfs7ZxlsOw/paX44m/jL2sRh2b39MhyaHJIqdUNpmY0U+cohGYJ2xIVaKF3Avl94N8txiGNAi7bVNYonkKvAmYibfgTzTVCBBcfuBo5v872NDnn2ItA9e5KWHZ/82oLM9AoGBAJX23Fp5unMSCKAUYNMrI5SrhxwuVBtqobgQ6bUd2AawRW3KeZ66iCvfVQHklCIDNv0UL6sYQaEaAiKo2D2SLReZnr26djNiLNq+f4CoEiqaMivKxNIwf8K94tFa5uWSYwkvyx9z4ib+/2+OCyytw4CzTi0cwa2FZjNaCkGZKWXc
    SAML_SP_CERTIFICATE=MIIDnTCCAoWgAwIBAgIJAMV8aE3DbLcpMA0GCSqGSIb3DQEBCwUAMGUxCzAJBgNVBAYTAlNHMRIwEAYDVQQIDAlTaW5nYXBvcmUxEjAQBgNVBAcMCVNpbmdhcG9yZTEMMAoGA1UECgwDSUJNMQ0wCwYDVQQLDARFU0lMMREwDwYDVQQDDAhJQk0gRVNJTDAeFw0xNjA1MzAxNTIxMTdaFw0xNzA1MzAxNTIxMTdaMGUxCzAJBgNVBAYTAlNHMRIwEAYDVQQIDAlTaW5nYXBvcmUxEjAQBgNVBAcMCVNpbmdhcG9yZTEMMAoGA1UECgwDSUJNMQ0wCwYDVQQLDARFU0lMMREwDwYDVQQDDAhJQk0gRVNJTDCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAPXM0JSN9y1CA5DLIDl7dR6AFfyfAsrzfqgcW5TDuivqj92I2X05KIHb+HHrsXOBDg9DuojwQ9GjyrS4cRFD0oj/lbHEKTKPuM8jMhDAu4zciVCOYTwVx/ibFF6D0xRDlf6Nj94SW1KYbDpDgvXw7MeadVNSNexrn6N82TGjigrIZZjuxOP6WBfmQolslB6V1HeVdjzjv6NN/WWGWJR+Ja2Zfwjn8XcS9DJtoIBAxwlLp1JzncDlR/8umkbO4p3clIDp8qzCZTqxunEFVYkR6f7QpmPHbmgtaHwK/Ea3lctQSI6qKfHq/ZNOW/jUGAy4zY45zsx89qqXSV1GGmhVGdsCAwEAAaNQME4wHQYDVR0OBBYEFLjdiWRJY1R7bQr0koAxPxxh0pKgMB8GA1UdIwQYMBaAFLjdiWRJY1R7bQr0koAxPxxh0pKgMAwGA1UdEwQFMAMBAf8wDQYJKoZIhvcNAQELBQADggEBAGFM5+154Y31/hzMz361btLiAI+MLgui0lGyppkhysVOhgYwlQq9bbDEfz0T3lOSL/iEOIe4z8CCFOXb4QDpvA5gb0pWpm5l2L2L6DU7zrWdy2AMgJ4RnvergMvQ/zDICjdwn6MBt+MSuTVq0DIH8WBbYv2vP8NSzKVD0pPknhSq67AWkcrOXaDipFsWgy+Y3Hl4dSJtKqSFZAJwv5H3quVKN/FMm3dpEbOZ2zagi+8UnOXjoLjjgozCtovTUXM9XhiIDSUEYeadcTOsjIZBpksISECeM4v0JesMHzyx83dKhS08GL2Rp9TqGmT+feqTQ4o7jrTUyg+/O79D3vj5obI=
    SAML_IDP_CERTIFICATE=MIICQDCCAakCBEeNB0swDQYJKoZIhvcNAQEEBQAwZzELMAkGA1UEBhMCVVMxEzARBgNVBAgTCkNhbGlmb3JuaWExFDASBgNVBAcTC1NhbnRhIENsYXJhMQwwCgYDVQQKEwNTdW4xEDAOBgNVBAsTB09wZW5TU08xDTALBgNVBAMTBHRlc3QwHhcNMDgwMTE1MTkxOTM5WhcNMTgwMTEyMTkxOTM5WjBnMQswCQYDVQQGEwJVUzETMBEGA1UECBMKQ2FsaWZvcm5pYTEUMBIGA1UEBxMLU2FudGEgQ2xhcmExDDAKBgNVBAoTA1N1bjEQMA4GA1UECxMHT3BlblNTTzENMAsGA1UEAxMEdGVzdDCBnzANBgkqhkiG9w0BAQEFAAOBjQAwgYkCgYEArSQc/U75GB2AtKhbGS5piiLkmJzqEsp64rDxbMJ+xDrye0EN/q1U5Of+RkDsaN/igkAvV1cuXEgTL6RlafFPcUX7QxDhZBhsYF9pbwtMzi4A4su9hnxIhURebGEmxKW9qJNYJs0Vo5+IgjxuEWnjnnVgHTs1+mq5QYTA7E6ZyL8CAwEAATANBgkqhkiG9w0BAQQFAAOBgQB3Pw/UQzPKTPTYi9upbFXlrAKMwtFf2OW4yvGWWvlcwcNSZJmTJ8ARvVYOMEVNbsT4OFcfu2/PeYoAdiDAcGy/F2Zuj8XJJpuQRSE6PtQqBuDEHjjmOQJ0rV/r8mO1ZCtHRhpZ5zYRjhRC9eCbjx9VrFax0JDC/FfwWigmrW0Y0Q==
    SAML_IDP_LOGIN_URL=http://ar-mock-sso.w3ibm.mybluemix.net:80/openam/SSORedirect/metaAlias/idp
    SAML_IDP_LOGOUT_URL=http://ar-mock-sso.w3ibm.mybluemix.net:80/openam/IDPSloRedirect/metaAlias/idp
    ```
  - Add to `hosts` file if needed:
	
	```
	9.45.69.22    c18fc815-742b-4d3d-a25e-469fececb936-bluemix.cloudant.com
	```
4. Run the application with `$gulp`
5. The API can now be accessed at http://localhost:6002
  - Any file changes will automatically reload the Node.js application
  - The port number might change, depending on your local system, as it is automatically assigned per application by the [`node-ports`](https://github.com/hoodiehq/node-ports) package, used by [`node-cfenv`](https://github.com/cloudfoundry-community/node-cfenv). In order to force a specific port, you can change the port in server.js file from appEnv.port to `6002` for example.

# Troubleshooting

The following issues have been faced at our end, you you can find some recommendations here.

## NPM install error on Windows
* If you run `npm install` and get this error: `MSBUILD : error MSB3428: Could not load the Visual C++ component "VCBuild.exe".`
  - ![Screenshot](https://media.github.ibm.com/download/user/1226/files/5d8d8d50-e9de-11e5-941e-bf1bd844a45c)
  - Solution:
    1. Install Microsoft Visual Studio C++ 2013 (see notes on [Windows](#windows-additional-notes))
    2. Run `npm cache clean`
    3. Run `npm install` again
* If you need to upgrade `npm`:
  - Launch Windows PowerShell as Administrator, then run the following commands:

    ```bat
    Set-ExecutionPolicy Unrestricted -Scope CurrentUser -Force
    npm install -g npm-windows-upgrade
    npm-windows-upgrade
    ```
* If you need to reinstall or rebuild native Node.js modules:
  - You should clear your `npm` cache first:

    ```bat
    npm cache clean
    ```
* If you got a travis build failed at `gulp lint failed, exiting...` then you need to remove all node modules under /node_modules folder and then run `npm install` again due to one/some node module(s) has been published a new version.

