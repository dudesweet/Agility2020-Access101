Lab 1: Building a Basic Access Policy
====================================================

Objectives
----------

In this lab, we will use the resources configured in the previous lab
and configure a simple Access Profile using the Visual Policy Editor
(VPE) to perform user authentication.

Lab Requirements
----------------

-  Working HTTP and HTTPS Virtual Servers 

Task 1: Define an Authentication Server
---------------------------------------

Before we can create an access profile, we must create the necessary AAA
server profile for our Active Directory.

1. From the main screen, browse to **Access > Authentication > Active
   Directory**

2. Click **Create…** in the upper right-hand corner

3. Configure the new server profile as follows:

    Name: **Lab\_SSO\_AD\_Server**

    Domain Name: **f5demo.com**

    Server Connection: **Direct**

    Domain Controller: **10.128.20.200**

|image10| |image11|

1. Click **Finished**

Task 2: Create a Simple Access Profile
--------------------------------------

1. Navigate to **Access > Profiles / Policies > Access Profiles
   (Per-Session Policies)
   **\ |image10|

2. From the Access Profiles screen, click **Create...** in the upper
   right-hand corner

3. | In the Name field, enter “\ **MyAccessPolicy**\ ”, and for “Profile
     Type”, select the dropdown and choose **All**
   | |image11|

4. Under “Language Settings”, choose **English** and click the
   “\ **<<**\ “ button to slide over to the “Accepted Languages”
   column\ **.
   **\ |image12|

5. Click **Finished**, which will bring you back to the Access Profiles
   screen.

6. | On the Access Profiles screen, click the **Edit** link under the
     Per-Session Policy column. |image13|
   | The Visual Policy Editor (VPE) will open in a new tab.

7. | On the VPE page, click the ‘\ **+**\ ’ icon on the “fallback” path,
     to the right of the **Start** object.
   | |image14|

8. On the popup menu, choose the **Logon Page** radio button under the
   Logon tab and click **Add Item.
   **\ |image15|\ **
   **\ |image16|

9. Accept the defaults and click **Save**

Now let’s authenticate the client using the credentials to be provided
via the “Logon Page” object.

1. | Between the “Logon Page” and “Deny” objects, click the ‘\ **+**\ ’
     icon, select **AD Auth** found under the **Authentication** tab,
     and click the **Add Item** button
   | |image17|
   | |image18|

2. Accept the default for the **Name** and in the **Server** drop-down
   menu select the AD server created above:
   **/Common/LAB\_SSO\_AD\_Server**, then click **Save
   **\ |image19|

3. | On the “Successful” branch between the **AD Auth** and **Deny**
     objects, click on the word **Deny** to change the ending
   | |image20|

4. Change the “Successful” branch ending to **Allow**, then click **Save
   **\ |image21|\ **
   **\ |image22|

5. | In the upper left-hand corner of the screen, click on the **Apply
     Access Policy** link, then close the window using the **Close**
     button in the upper right-hand. Click **Yes** when asked “Do you
     want to close this tab?”
   | |image23| |image24|

Task 3: Associate Access Policy to Virtual Servers
--------------------------------------------------

Now that we have created an access policy, we must apply it to the
appropriate virtual server to be able to use it.

1. From the **Local Traffic** menu, navigate to the **Virtual Servers
   List** and click the name of the virtual server created previously:
   **https\_vs**.

2. | Scroll down to the “Access Policy” section, then for the “Access
     Profile” dropdown, select **MyAccessPolicy**
   | |image25|

3. Click **Update** at the bottom of the screen

Task 4: Testing
---------------

Now you are ready to test.

1. Open a new browser window and open the URL for the virtual server
   that has the access policy applied:
   `**https://www.f5demo.com** <https://www.f5demo.com>`__\ **
   **\ You will be presented with a login window\ **
   **\ |image26|

2. Enter the following credentials and click **Logon**:

    Username: **user**

    Password: **Agility1**

| You will see a screen similar to the following:
| |image27|

.. |image022| image:: media/image022.png
   :width: 4.5in
   :height: 2.32in
.. |image023| image:: media/image023.png
   :width: 4.5in
   :height: 2.37in
.. |image024| image:: media/image024.png
   :width: 1.75in
   :height: 2.75in
.. |image025| image:: media/image025.png
   :width: 2.5in
   :height: 4.5in
.. |image026| image:: media/image026.png
   :width: 4.5in
   :height: 0.74in
.. |image027| image:: media/image027.png
   :width: 4.5in
   :height: 1.03in
.. |image028| image:: media/image028.png
   :width: 4.5in
   :height: 2.58in
.. |image029| image:: media/image029.png
   :width: 4.5in
   :height: 2.56in
.. |image030| image:: media/image030.png
   :width: 4.5in
   :height: 0.80in
.. |image031| image:: media/image031.png
   :width: 4.5in
   :height: 1.66in
.. |image032| image:: media/image032.png
   :width: 4.5in
   :height: 1.64in
.. |image033| image:: media/image033.png
   :width: 4.5in
   :height: 2.64in
.. |image034| image:: media/image034.png
   :width: 4.5in
   :height: 2.71in
.. |image035| image:: media/image035.png
   :width: 4.0in
   :height: 3.75in
.. |image036| image:: media/image036.png
   :width: 4.5in
   :height: 2.56in
.. |image037| image:: media/image037.png
   :width: 4.5in
   :height: 3.40in
.. |image038| image:: media/image038.png
   :width: 4.5in
   :height: 1.89in
.. |image039| image:: media/image039.png
   :width: 4.5in
   :height: 1.72in
.. |image040| image:: media/image040.png
   :width: 4.5in
   :height: 1.69in
.. |image041| image:: media/image041.png
   :width: 4.5in
   :height: 1.73in
.. |image042| image:: media/image042.png
   :width: 4.5in
   :height: 1.22in
.. |image043| image:: media/image043.png
   :width: 4.5in
   :height: 1.68in
.. |image044| image:: media/image044.png
   :width: 2.5in
   :height: 3.25in
.. |image045| image:: media/image045.png
   :width: 4.5in
   :height: 2.30in
.. |image046| image:: media/image046.png
   :width: 4.5in
   :height: 0.77in
.. |image047| image:: media/image047.png
   :width: 4.5in
   :height: 3.38in
.. |image048| image:: media/image048.png
   :width: 4.5in
   :height: 1.15in
.. |image049| image:: media/image049.png
   :width: 4.5in
   :height: 2.04in
.. |image050| image:: media/image050.png
   :width: 4.5in
   :height: 2.33in
.. |image051| image:: media/image051.png
   :width: 4.5in
   :height: 1.10in
.. |image052| image:: media/image052.png
   :width: 4.5in
   :height: 1.66in
.. |image053| image:: media/image053.png
   :width: 4.5in
   :height: 1.03in
.. |image054| image:: media/image054.png
   :width: 2.0in
   :height: 1.75in
.. |image055| image:: media/image055.png
   :width: 2.0in
   :height: 1.75in
.. |image056| image:: media/image056.png
   :width: 2.0in
   :height: 1.75in
.. |image057| image:: media/image057.png
   :width: 4.5in
   :height: 3.03in
.. |image058| image:: media/image058.png
   :width: 2.5in
   :height: 2.5in
.. |image059| image:: media/image059.png
   :width: 4.5in
   :height: 1.08in

