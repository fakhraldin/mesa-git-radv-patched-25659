# mesa-git-radv-patched-25659
mesa-git radv with applied patch 25659 fixing mesh shaders with array derefs of vectors

--------------------------------------------------------------------------------------------

This is a compiled version of mesa-git radv with an applied patch from merge request 25659.
This is to resolve mesh shader issues in certain affected applications. 

Currently that fix request has not been merged yet. After inital tests though that MR seems
to resolve the issue for a couple of users at the cost of possible performance loss.

Linux users who want to test the patched driver nevertheless, but don't want to mess with 
their linux distribution's default mesa driver, can follow this tutorial.

Before you continue though, a disclaimer: I compiled and packaged the driver, but i do not 
take any responsibility for any damage to your GPU, PC & OS! MR 25659 is pre aplpha status! 
Apart from that nothing else has been changed or applied to this mesa-git package.
By using the patched driver in this project you hereby agree to use it at your own risk.

----

Agreed? Then read on for the Tutorial!

Prolog about the method:

Don't worry about your system's default mesa driver. We are not going to touch it at all!
We are going to use the vulkan-icd-loader library as a connection between an application
and multiple vulkan drivers. That way we can keep the distro's mesa default driver in
charge, while instructing an application to use a specific vulkan driver on demand, 
that we saved before in our home directory outside of our system. This is to keep the 
test environment at a lower risk level, to avoid any complicated circumstances, 
which might be hard to debug especially for linux newbies. 

We are going to use a winemanger as an easier means to organize our wine prefixes.
I choose Lutris here but you can also use heroic game launcher and others. The place
of the settings to enter the needed environment varables may differ a bit.

1. First download the latest driver release from this git repository.
2. Decompress the zip file to your home directory: /home/(YOUR-USER-PROFILE-NAME)/
3. Now you should see the following directory: /home/(YOUR-USER-PROFILE-NAME)/mesa
4. Open Lutris and right click on your game's icon. Choose "Config".
5. Go to the tab "system settings".
6. Scroll down to "environment variables" and click the "add" button right next to it.
7. In the key field enter: VK_ICD_FILENAMES then right next to it,
8. In the value field enter: /home/user/mesa/share/vulkan/icd.d/radeon_icd.x86_64.json
9. Press the save button in the top right corner of the current config window.

That's it! We now instructed the application to use our separate mesa radv driver,
that we saved in our home directory. 

This is a quick setup and help, that i arranged and wrote after midnight :) so... 
to be continued ... maybe!

Until then good luck and salam to you friends of the penguin :)
