# mesa-git-radv-patched-25659
mesa-git radv with applied patch 25659 fixing mesh shaders with array derefs of vectors

--------------------------------------------------------------------------------------------

Salam friends of the penguin!

This is a compiled version of mesa-git radv with an applied patch from merge request 25659.
This is to resolve mesh shader issues in certain affected applications. 

Currently that fix request has not been merged yet. After initial tests though that MR seems
to resolve the issue for a couple of users at the cost of possible performance loss. On the
other hand one user reported this to be running just fine without fps drops.

Linux users who want to test the patched driver nevertheless, but don't want to mess with 
their linux distribution's default mesa driver, can follow this tutorial.

Before you continue though, a disclaimer: I compiled and packaged the driver, but i do not 
take any responsibility for any damage to your GPU, PC & OS! MR 25659 is pre aplpha status! 
Apart from that nothing else has been changed or applied to this mesa-git package.
By using the patched driver in this project you hereby agree to use it at your own risk.

----

Agreed? Then read on for the Tutorial!

1.) Prologue about the used method:

Don't worry about your system's default mesa driver. We are not going to touch it at all!
We are going to use the vulkan-icd-loader library as a connection between an application
and multiple vulkan drivers. That way we can keep the distro's mesa default driver in
charge, while instructing an application to use a specific vulkan driver on demand. 
We save the latter in our home directory isolated from our system. This is to keep the 
test environment at a low risk level, to avoid any complicated circumstances, 
which might be hard to debug especially for linux newbies. 

We are going to use a winemanger as an easier means to organize our wine prefixes.
I choose Lutris here but you can also use heroic game launcher and others. The place
of the settings to enter the needed environment variables may differ a bit.

2.) Procedure:

1. Download the latest driver package from the release section.
2. Decompress the zip file to your home directory: /home/(YOUR-USER-PROFILE-NAME)/
3. Now you should see the following directory: /home/(YOUR-USER-PROFILE-NAME)/mesa
4. Open Lutris and right click on your game's icon. Choose "Config".
5. Go to the tab "system settings".
6. Scroll down to "environment variables" and click the "add" button right next to it.
7. In the field "key" enter: `VK_ICD_FILENAMES`
8. In the field "value" right next to it enter:
   `/home/(YOUR-USER-PROFILE-NAME)/mesa/share/vulkan/icd.d/radeon_icd.x86_64.json`
   Don't forget to replace (YOUR-USER-PROFILE-NAME) with your actual user name.
9. Press the save button in the top right corner of the current config window.


3.) Result:
That's it! We now instructed the application to specifically use our separate mesa 
radv driver, that we saved in our home directory, every time we launch it.

This is just a quick help and setup, that i arranged and wrote after midnight. 
So sorry for any inconveniences. To be continued ... maybe!

Salam
