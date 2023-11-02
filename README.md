# mesa-git-radv-with-applied-patches-25530,25659 and partially 25890
mesa-git radv with applied patch 25659 fixing mesh shaders with array derefs of vectors
plus other patches with focus on mesh shaders!

 1. [MR 25530](https://gitlab.freedesktop.org/mesa/mesa/-/merge_requests/25530) "ac/nir: fix partial mesh shader output writes on GFX11"
    
 3. [MR 25659](https://gitlab.freedesktop.org/mesa/mesa/-/merge_requests/25659) "radv: mesh shader fixes with array derefs of vectors"

    UPDATE!: MR 25659 has been merged into mesa-git today! So no need anymore to include it in your build!
    
 5. [MR 25890](https://gitlab.freedesktop.org/mesa/mesa/-/merge_requests/25890) "radv: add mesh shader support with DGC"
    
    (MR 25890 excluded in mesa-git-edfbf74 pkg: compilation failed, too much out of sync)

----

Primary Target Platform: Fedora 38+ and RDNA2 GPUs. 

The pkg might also work on other distros & RDNA3 but without any warranty because untested.

----

1.) Introduction:

Salam friends of the penguin!

This is a compiled version of mesa-git radv with an applied patch from merge request 25659.
This and other patches are to resolve mesh shader issues in certain affected applications. 

Currently those code requests have not been merged yet. After initial tests though the MRs 
seem to resolve the issue for a couple of users at the cost of possible performance loss. 
On the other hand some users reported this to be running just fine without fps drops.

Linux users who want to test the patched driver nevertheless, but don't want to mess with 
their linux distribution's default mesa driver, can follow this tutorial.

Before you continue though a disclaimer: I patched, compiled & packaged the driver, but i
do not take any responsibility for any damage to your GPU, PC & OS! MRs are aplpha status! 
Apart from that nothing else has been changed or applied to this mesa-git v24 dev package.
By using the patched driver in this project you hereby agree to use it at your own risk.

Agreed? Then read on for the Tutorial!

----

2.) Prologue about the used method:

Don't worry about your system's default mesa driver. We are not going to touch it at all!
We are going to use the vulkan-icd-loader library as a connection between an application
and multiple vulkan drivers. This way we can keep the distro's mesa default driver in
charge, while instructing an application to use a specific vulkan driver on demand. 
We save the latter in our home directory isolated from our system. This is to keep 
the risk for breakage as low as possible. Primarily we want to avoid any complicated 
circumstances, which might be hard to debug especially for linux newbies. 

We are going to use a wine-manager as an easier means to organize our wine prefixes.
I choose Lutris here but you can also use heroic games launcher and others. The place
of the settings may differ a bit, but the entered environment variables are the same.

----

3.) Procedure:

1. Download the latest driver package from the release section of this project.
2. Decompress the zip file to your home directory: /home/(YOUR-USER-PROFILE-NAME)/

   (Don't forget to replace (YOUR-USER-PROFILE-NAME) with your actual user name!)
   
4. Now you should see the following directory: /home/(YOUR-USER-PROFILE-NAME)/mesa
5. Open Lutris and right click on your game's icon. Choose "Config".
6. Go to the tab "system settings".
7. Scroll down to "environment variables" and click the "add" button right next to it.
8. In the field "key" enter: `VK_ICD_FILENAMES`
9. In the field "value" right next to it enter:
   
   `/home/(YOUR-USER-PROFILE-NAME)/mesa/share/vulkan/icd.d/radeon_icd.x86_64.json`
   
10. Press the save button in the top right corner of the current config window.

----

4.) Result:

That's it! We now instructed the application to specifically use our separate mesa 
radv driver, that we saved in our home directory, every time we launch it.

This is meant as a quick help and setup, that i arranged and wrote after midnight
on fedora 39.
If you can wait, then be patient until the patch gets merged hopefully soon.

to be continued ... maybe! 

Salam
