=========
Debugging
=========

The game has a debug panel which you can add messages to.

Using the panel
===============
To open the panel press **F7** in game.
You can resize the panel and drag it around.
The panel also has a clear button, this will clear all the messages.

Reference the DLL
=================
To be able to use this method of logging you will have to add a reference to the **Assembly-CSharp DLL**.
If you're not sure how to do this see this guide for :doc:`Visual Studio </modding/Getting-Started/Setting-Up-Visual-Studio>` or for :doc:`MonoDevelop </modding/Getting-Started/Setting-Up-MonoDevelop>`.
And you'll also have to add this line at the top of your class to be able to use it.

.. code-block:: c#

    using ColossalFramework.Plugins;

Logging
=======
To send a message to the debug panel you use this code.

.. code-block:: c#
    :linenos:

    DebugOutputPanel.AddMessage(PluginManager.MessageType.Message, "Message");

you can easily create some static methods for logging.
It's also recommended to prefix you log message so that users know were the message came from.
For example: *"[TreeBrush] Some debug message.."*

Logging an objects properties
=============================
If you want to print out all the properties of an object, you can use the method below.

.. code-block:: c#

    using System;
    using System.ComponentModel;

    public void dumpObject(object myObject)
    {
        string myObjectDetails = "";
        foreach (PropertyDescriptor descriptor in TypeDescriptor.GetProperties(myObject))
        {
            string name = descriptor.Name;
            object value = descriptor.GetValue(myObject);
            myObjectDetails+= name + ": " + value + "\n";
        }
        DebugOutputPanel.AddMessage(PluginManager.MessageType.Message, myObjectDetails);
    }

Other logging methods
=====================
There are a few other logging methods that other people made.
Here is a list to some of them.

* `ChirpLogger <https://github.com/Enagan/ChirpLogger>`__
* `Debugging Deluxe <http://www.skylinesmodding.com/t/debugging-deluxe/136>`__
* *More will be added soon...*
