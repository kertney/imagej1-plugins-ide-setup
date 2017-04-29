# imagej1-plugin-eclipse
This repo contains a minimal setup for writing ImageJ (1) plugins with the Eclipse IDE. 

The Eclipse project is set up with ``plugins/`` as the default output folder (for generated ``.class`` files).

## Setup
Clone this repository, start **Eclipse** and open this project with ``Open Projects from File System...`` (at the top-level directory).

## Starting ImageJ
The ImageJ runtime can be launched in various ways:
- **Windows**: Execute ``ImageJ.exe`` (by double-clicking in the file).
When ImageJ starts up, it may ask for the ``javaw.exe`` execetutable, typically located in ``C:\Program Files\java\jre1.8xxx\bin\``. In case of problems, simply delete the ``ImageJ.cfg`` file and start anew.
- **MacOS**: Launch ``ij.jar``.
- **Java**: Run the ``ij.ImageJ.main()`` method within Eclipse.

The entire ImageJ functionality is contained in the single archive ``ij.jar``. To **update** to the most recent version, simply select ``Help`` -> ``Update ImageJ...`` from the ImageJ main menu.

## Adding/editing your plugin code
Code for ImageJ plugins is contained in the ``src-plugins`` directory. Plugins may be contained in Java packages (such as ``my_plugins`` in this example). **Note** that packages with plugins may only be **one level deep**, otherwise ImageJ will not find them! It is recommended to use at least one underscore (``_``) in a plugin name to make ImageJ automatically install the plugin into the ``Plugins`` menu at startup.

## Executing plugins
At startup, ImageJ automaticall installs existing plugin classes (under the above conditions) into the ``Plugins`` menu. To execute, simple select the listed plugin from the menu.

If the plugin's source code is **edited**, the associated ``.class`` file in ``plugins/`` is updated (by Eclipse), but **not** automatically reloaded by the ImageJ runtime. To **exectute an edited plugin**, use ``Plugins`` -> ``Compile and Run...`` and select the associated ``.class`` file (no compiler is needed).

## Adding other libraries
This project does not use any dependency management (such as *Maven*) to keep things simple. If any external libraries are required, just do the following:
- Copy the associated JAR file ``xxx.jar`` into ``jars/``.
- In eclipse, add the JAR file to Java build path.
- Restart ImageJ.
