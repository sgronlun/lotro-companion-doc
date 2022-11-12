# Installation Guide for running under *Wine*
**NOTE:** This guide requires familiarity with using the `Terminal` application and Unix file pathing.

It is assumed you already have the Lotro Client application downloaded, installed and running under the *Wine* distribution included
with the client installation package available from the [official download site](https://www.lotro.com/guides/lotro-download-en?locale=en).

In order for Lotro Companion to import characters from the Lotro Client, both the client and Lotro Companion need to be running in the
same *Wine* environment. Rather then change the Wine distribution included in the client installation package and risk breaking a working *Wine* environment,
a new *Wine* environment will be installed. This guide is only designed for MacOS Mojave 10.14.

The process to install and configure a new *Wine* environment is broken down into the following steps:
1. Install Homebrew.
2. Install *Wine*.
3. Run the Lotro Client in the new *Wine* environment.
4. Run Lotro Companion in the new *Wine* environment.

## Step 1: Install Homebrew
In order to install *Wine*, we use a helper tool called `Homebrew`. Open a `Terminal` window and enter the following command:

`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`

After the command completes, verify homebrew installation by running:

`brew doctor`

## Step 2: Install *Wine*
Install the latest stable version of *Wine* by running the following command in `Terminal`:

`brew install wine-stable`

Verify the installation by running:

`brew doctor`

Verify that Homebrew and *Wine* are updated to the latest version by running:

`brew update`

Just to double check everything is good to go, run:

`brew doctor`

## Step 3: Run Lotro Client in new *Wine*

In the Finder, navigate to the following folder:

`~/Library/Application Support/com.standingstonegames.lotro/common/wineprefix/drive_c/Program Files (x86)/StandingStoneGames/The Lord of the Rings Online`

You should find a file called `LotroLauncher.exe`. Drag this file to the Dock but since this is not a native Mac application, you need to drag it to the right side of the Dock (if Dock is horizontal) or the bottom of the Dock (if Dock is vertical). If you click `LotroLauncher.exe` in the Dock, it should now run the launcher in the new *Wine* Stable environment. If it launches a different application, you will need to open it in the Finder and tell it to use Wine Stable to open the application.

## Step 4: Run Lotro Compansion in new *Wine*
LotroCompanion.sh in the `app` folder will run LC using Java Runtime installed on MacOS. To change this to using the Java Runtime for Windows included with Lotro Companion, we need to make some changes to this shell script. However, we will create a new shell script named lcw.sh with the following content:

```
#!/bin/bash
JAVA_EXE=../runtime/bin/java.exe
JAVA_OPTS="-Dcom.sun.management.jmxremote -Duser.language=en -Dlogback.configurationFile=logback.xml"
KS=`pwd`/kickstarter

CLASSPATH=${KS}/delta-kickstarter-1.0.jar
CLASSPATH="${CLASSPATH};${KS}/delta-launcher-1.0.jar"
CLASSPATH="${CLASSPATH};${KS}/delta-updates-manager-1.0.jar"
CLASSPATH="${CLASSPATH};${KS}/delta-downloads-3.1.jar"
CLASSPATH="${CLASSPATH};${KS}/delta-common-1.6.4.jar"
CLASSPATH="${CLASSPATH};${KS}/httpasyncclient-4.1.4.jar"
CLASSPATH="${CLASSPATH};${KS}/httpclient-4.5.5.jar"
CLASSPATH="${CLASSPATH};${KS}/httpcore-4.4.9.jar"
CLASSPATH="${CLASSPATH};${KS}/httpcore-nio-4.4.10.jar"
CLASSPATH="${CLASSPATH};${KS}/commons-codec-1.10.jar"
CLASSPATH="${CLASSPATH};${KS}/commons-logging-1.2.jar"
CLASSPATH="${CLASSPATH};${KS}/log4j-1.2.17.jar"
wine64 $JAVA_EXE ${JAVA_OPTS} -classpath "${CLASSPATH}" delta.kickstarter.Kickstarter
```

Run lcw.sh to verify that Lotro Companion now runs under *Wine* using the Java runtime for Windows. However, importing a character won't work just yet.
The Lotro Client Path setup in [Configuration](../HowTo/ApplicationConfiguration/main.md) will not contain the actual Lotro Client files. However, we can
use a symbolic link to disguise the fact that these files are actually in a different location outside of *Wine*.
```
cd ~/.wine/drive_c/Program\ Files\ \(x86\)`
ln -s ~/Library/Application\ Support/com.standingstonegames.lotro/common/wineprefix/drive_c/Program\ Files\ \(x86\)/StandingStoneGames/ .
```
Re-run lcw.sh and start the Lotro Client. You should now be able to [import characters](../LocalClientImport/main.md).

**NOTE: Be sure to make a backup of lcw.sh outside of the Lotro Application directory as the file might be removed if you re-install Lotro Companion in the same location.**
