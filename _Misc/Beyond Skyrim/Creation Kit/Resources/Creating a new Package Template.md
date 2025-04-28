Here is a small tutorial for taking a somewhat complicated template and changing one aspect of its behavior, even if you don't know how the whole setup works. We're going to take use the AcquireItem Package Template to make something very similar, but different. Right now, someone running a package templated off of the AcquireItem template would first travel to a starting location, then wander around looking for the designated item to acquire. If the actor sees the right item, he will stop wandering and pick the item up. What if we wanted the actor to patrol instead of wander while looking for the item to pick up?

-   1\. Create a new package
-   2\. Template using AcquireItem  
    

[![AcquirePatrol01.jpg](https://ck.uesp.net/w/images/thumb/c/cd/AcquirePatrol01.jpg/300px-AcquirePatrol01.jpg)](https://ck.uesp.net/wiki/File:AcquirePatrol01.jpg)

-   3\. Set template to "None" and note that you now have much more control over the package's inner-workings.  
    

[![AcquirePatrol02.jpg](https://ck.uesp.net/w/images/thumb/d/d3/AcquirePatrol02.jpg/300px-AcquirePatrol02.jpg)](https://ck.uesp.net/wiki/File:AcquirePatrol02.jpg)

-   4\. Find the wander procedure and change it to a patrol procedure by clicking on Wander and then changing it in the drop-down menu.
-   5\. Note that some new Package Data was created. This is because the Patrol procedure requires more inputs than a Wander procedure.
-   6\. Set all of the package data up for your specific instance, just as if you were using a template.  
    

NOTE: Depending on the current state of the editor, switching or adding procedures might grab the first valid package data that it can and try to use that as a procedure parameter. In this example, I had to create a new SingleRef(SingleRef will be changed to Ref in the future) object by right-clicking in the Public Package Data area and making a new piece of data. I named it "Patrol Start" and then clicked on the Patrol procedure. I then had to click on the PathStart parameter and then use the Input Data dropdown to pick the "Patrol Start" Package Data. Now the patrol procedure knows to start at the reference defined in "Patrol Start".  
[![AcquirePatrol03.jpg](https://ck.uesp.net/w/images/thumb/5/5f/AcquirePatrol03.jpg/300px-AcquirePatrol03.jpg)](https://ck.uesp.net/wiki/File:AcquirePatrol03.jpg)

  
NOTE2: If you use something generic for the package data and make it public, such as using Linked Ref for the Patrol Start, you could turn this into a template for future use.