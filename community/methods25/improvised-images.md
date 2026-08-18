# Improvised Images: An Introduction to Visual Programming through TouchDesigner
<link rel="stylesheet" href="../../cookbook.css">
<p class="previous-next-lesson"><a href="toc.html">^ Main contents</a></p>

## Contents
- [Writing vs Wiring](#writing-versus-wiring-do-this-then-that-or-follow-the-flow)
- [From Flow to Form](#from-flow-to-form-a-hands-on-introduction-to-touchdesigner)
- [Nine Nodes and Many Lines](#nine-nodes-and-many-lines)
- [Beyond TouchDesigner](#beyond-touchdesigner-where-else-do-we-find-node-based-programming)



A wireframe sphere emerges from a dense constellation of circles, each rotated around a common centre. The resulting form resembles a spirograph, a geodesic globe, or a nineteenth-century scientific model of the cosmos, oscillating between abstract drawing and mathematical visualisation. At once simple and intricate, how might we create such a shape through code?

Two programs generate the same image. The first is built in TouchDesigner, a node-based visual programming environment; the second in Processing, a text-based programming language. While their visual outputs are similar, the two programs embody radically different ways of thinking. One expresses logic through a network of connected operators and data flows, while the other through a sequence of written instructions, in order, line by line. By comparing them side by side, we can begin to see that programming is not merely a technical skill but also a mode of representation, inviting different ways of organising thought, relationships, and processes.

```
int bigRadius = 180;   // radius of large circular structure
int smallRadius = 180;  // radius of small circles
int count = 40;        // number of repetitions

void setup() {
  size(800, 800);
  smooth(8);
}

void draw() {
  background(15);
  translate(width/2, height/2);

  stroke(220);
  noFill();

  for (int i = 0; i < count; i++) {

    float angle = map(i, 0, count, 0, TWO_PI);

    pushMatrix();

    rotate(angle);           // rotate in 2D plane
    translate(bigRadius, 0); // move outward
    ellipse(0, 0, smallRadius*2, smallRadius*2);

    popMatrix();
  }
}
```

## Writing versus Wiring: Do This, Then That? Or Follow the Flow?

In text-based programming, computation is represented through written instructions. Programs are organised as lines of code that are executed according to a particular syntax and order. The programmer describes a sequence of operations: first do this, then do that. Languages such as Python, JavaScript, and C++ belong to this tradition. Because logic can be compressed into functions, classes, and modules, text-based programming is particularly effective for building large and complex software systems. Node-based programming takes a different approach. Instead of writing instructions line by line, programmers construct networks of nodes connected by links. Each node performs a specific operation, while the connections between nodes define how data moves through the system. Rather than focusing on syntax, node-based environments foreground structure and relationships. Computation becomes something that can be seen and arranged *spatially*. Examples of node-based programming environments include TouchDesigner, Grasshopper, Unreal Blueprints, Max/MSP, and Pure Data. The distinction encourage different ways of thinking. While text-based programming excels at abstraction and scalability, node-based programming makes relationships, dependencies, and data flows immediately visible. For artists, designers, and researchers working with images (as well as sounds, data, or other media with an emphasis on interactions), this visibility can make computational processes more intuitive to explore, manipulate, and perform.

Node-based programming belongs to a broader tradition known as *data flow programming*. Writing in 1992, even before the emergence of contemporary platforms such as TouchDesigner, Douglas Hils described dataflow programming as a computational model in which programs are represented as directed graphs with nodes represent functions, while connections represent the movement of data between them.[^1] In this model, the central question is not **What instruction comes next?** but rather **Where does the data go?**

One of the strengths of dataflow systems is their *visibility*. Unlike text-based programs, where intermediate states are often hidden inside variables and functions, node-based environments allow users to observe data as it moves through a network of transformations. Images, audio signals, geometry, and control values can be inspected and manipulated at multiple stages while the program is running. Hils argues that this visibility contributes to what Tanimoto calls *liveness*. In TouchDesigner, changing a parameter instantly updates the output because the program is already running. This quality of liveness helps explain the platform’s popularity in live performances, VJing and improvisational practices.

A related perspective comes from J. Paul Morrison’s theory of *flow-based programming* (2007).[^2] Morrison argues that traditional programming inherited the logic of the von Neumann computer architecture, in which instructions are executed sequentially, one after another. Flow-based programming, in contrast, proposes a different worldview. Rather than asking what sequence of instructions a computer should execute, it asks what is flowing through a system. Programs are assembled from reusable components connected by streams of data. Computation resembles less a written script and more a network of pipes, roads, or electrical circuits through which things continuously move. Morrison argues that *lines of code* is the wrong measure of productivity. A good programmer should write less code, not more. The goal is to build systems from *reusable* components that can be connected, disconnected, and recombined as needed. Flow-based programming therefore privileges **reusability, maintainability, and parallelism** in that existing components can be repurposed, systems can be understood through their diagrams, and multiple processes can operate simultaneously rather than waiting their turn in a sequential queue.

The distinction between text-based and node-based programming is therefore not merely technical but cognitive. Thomas Green and Marian Petre (1996) argue that programming environments shape how programmers think.[^3] Text-based languages encourage symbolic and sequential reasoning since programmers must mentally simulate the execution of instructions step by step. Data flow environments encourage what might be called flow-tracing, following values through a network and asking where they come from and where they go. Visual programming environments are often perceived as *easier* because they possess what Green and Petre call a strong *closeness of mapping* for that the structure of the program resembles the structure of the problem being solved. However, node-based programming is not without limitations. Green and Petre point out that visual environments can introduce their own cognitive challenges when tracing long connections, locating hidden dependencies, and navigating large diagrams. Hils similarly notes that visual programs can occupy a great deal of screen space. While a small network may be immediately understandable, a project containing hundreds of nodes and connections can become difficult to navigate. The question is therefore not whether node-based programming is more convenient than text-based programming, but what kinds of thinking each notation makes possible and what kinds of problems it allows us to approach most effectively.


## From Flow to Form: A Hands-On Introduction to TouchDesigner

### Download and Install TouchDesigner at [TouchDesigner Pages](http://derivative.ca).

### Navigating the workspace:

Left click an operator to select it.

Right click and drag to select multiple operators at once.

Left click and drag on an empty area of the grid to pan around the workspace.

Use the mouse wheel (or trackpad gestures) to zoom in and out.

To create a new operator, double-click on an empty area of the grid. This opens the **OP Create Dialog**, where you can search for and add operators.

TouchDesigner projects are organised as nested networks. Much like folders in Linux or Unix-based operating systems, networks can contain other networks. Learning to move between network layers is essential as projects become more complex.

Press **U** to move up one network level.

Press **I** to move inside a selected network.

TouchDesigner works through the flow of data between operators. To connect operators, drag from an output connector to an input connector. To disconnect them, right-click on the connection and remove it.

Every operator contains adjustable settings. Select an operator and press **P** to open its parameter window. Parameters control how an operator behaves and are where most creative experimentation takes place.

### The Operator Families:

TouchDesigner is built from different families of operators, each designed to work with a particular type of data. At first, the acronyms may seem cryptic, but they quickly become second nature. A useful way to think about them is as specialised tools in a workshop. Each family does something different, but they can all be connected together.

TOPs (Texture Operators):They are the operators for creating, processing, and combining visual material.

CHOPs (Channel Operators): CHOPs work like a nervous system and take care of numerical data changing over time. They are often used for animation, interaction, audio analysis, and control signals.

SOPs (surface operators): They are about shapes and are used to create objects such as spheres, boxes, lines, and point clouds, as well as to deform and transform them.

COMPs (component operators): COMPs build systems inside systems as the containers that organise networks and user interfaces. They can hold other operators and create reusable systems.

### Coding Sample:[^4]

The following coding example offers a step-by-step demonstration of how to build and animate the spirograph-like sphere introduced at the beginning, this time entirely through a node-based network in TouchDesigner.

**Step 1: Circle SOP**

Delete all existing operators in the workspace.
Double-click on an empty area of the network editor to open the **OP Create Dialog**.
Select **SOP**.
Choose **Circle**.
Place the Circle SOP in the workspace.

**Step 2: Add Geometry COMP to Circle SOP**

Locate the output connection point (the small tail) on the right side of the Circle SOP.

Right-click on the connection point.

Navigate to **COMP** (Component Operators) and choose **Geometry**.

**Step 3: Set Viewer**

In the top-right corner of the interface, click the small down arrow.

Select **Split Left/Right**. A second pane will appear on the right side of the screen.

In the new pane, click the down arrow in the top-left corner. Select **Geometry Viewer**.

**Step 4: Give the Circle a Material**

A Circle SOP defines only the geometry of an object (a collection of points and coordinates arranged in space). By itself, it contains no colour, texture, or instructions about how it should appear when rendered. A useful analogy is to think of the SOP as the body and the MAT as the skin. The SOP determines the object’s shape, while the MAT determines how that shape is displayed. When we assign a Line MAT to the Circle SOP, we are telling TouchDesigner to render the circle as a set of visible lines rather than as a solid shaded surface. This gives the geometry the clean wireframe appearance that will become the foundation of our spirograph-like sphere.

Double-click on an empty area of the network and create a **Line** MAT (Material Operator).

Select the Geometry COMP created in the previous step.

Open its parameters (P). Navigate to the Render page. Locate the **Material** parameter (the first field in the page).

Drag the Line MAT onto the Material parameter.

**Step 5: Prepare for Instancing**

Now we will move from drawing a single circle to drawing many copies of it - *instancing*.

Create a second Circle SOP. (It does not have to be a circle—you can experiment with other shapes such as a Rectangle SOP.)

Right-click on the Circle SOP’s output and add a **Null** SOP. The Circle SOP should now be connected to the Null SOP. (The Null SOP does not alter the geometry. Think of it as a labelled checkpoint or clean output location within a network. As projects become more complex, Null operators help keep networks organised and make it easier to reference data elsewhere.)

Select the Geometry COMP.

Open its parameters (P) again and navigate to the **Instance** page.

Turn Instancing **On**.


**Step 6: Instancing**

Instancing is now enabled, but TouchDesigner still does not know where to place the copies. The next step is to provide position data.

Select the Geometry COMP and open the Instance page.

Locate the **Translate OP** parameter.

Drag the Null SOP (connected to the second Circle SOP) onto Translate OP.

Assign:

P(0) to Translate X
P(1) to Translate Y
P(2) to Translate Z

At this point, the Geometry COMP will read point positions from the SOP and use them to position instances in 3D space.

Why three channels?

A position in 3D space is not a single value but a set of coordinates:

Position = (x, y, z)

Each point in the SOP contains these three values. By assigning P(0), P(1), and P(2) to the X, Y, and Z translation parameters, we are telling TouchDesigner how to interpret the point data as spatial coordinates.

You should now see multiple copies of the original circle appearing in the Geometry Viewer.

Experiment: Change the Number of Instances

To better understand what instancing is doing:

In the Instance page, change **Instance Count Mode** from Instance OP(s) Length to **Manual**.

Adjust the Instance Count value.

Increasing the number creates more copies; decreasing it creates fewer.

**Step 7: Transform the Instance Positions**

At the moment, the instances inherit the point positions directly from the second Circle SOP. By inserting a Transform SOP into this network, we can manipulate those positions and reshape the overall structure.

Locate the connection between the second Circle SOP and the Null SOP.

Right-click on the connection line.

Select Insert Operator.

Choose **Transform** SOP.

Select the Transform SOP and open its parameters.

Experiment with the transformation controls:

**Rotate** changes the orientation of the point positions (see examples below of rotate x at 75 and rotate y at 50).

**Scale** expands or contracts the overall arrangement.

**Translate** shifts the positions in space.

As you adjust these parameters, the instances should immediately update in the Geometry Viewer.

What is happening here?

Remember that the second Circle SOP is not the geometry being rendered. It is supplying the position data used by the instancing system. By transforming this SOP, we are not changing the shape of the rendered circle itself; we are changing the coordinates that determine where its copies appear. In other words, we are beginning to sculpt the invisible framework that controls the entire structure. Small adjustments to the Transform SOP can produce dramatic changes in the arrangement of the instances, revealing one of the key strengths of node-based workflows that a single operator can reshape an entire system of relationships.

**Step 8. Animate with Python**

So far, our structure is static. Let's bring it to life by animating the rotation of the Transform SOP.

Select the Transform SOP. Find the Rotate parameters.

Click the small **+** button next to the parameter group.

In the **Rz** (Rotate Z) field, enter: 

`
absTime.seconds
`

As soon as you press Enter, the expression will begin updating automatically. You should now see the structure rotating continuously in the Geometry Viewer. As time increases, the rotation angle increases, producing a smooth counterclockwise motion. Rather than typing a fixed number, we are feeding the parameter a changing value. Every second, the expression returns a slightly larger number, and the Transform SOP updates accordingly.

**Step 9. Add a Noise CHOP**

Until now, the positions of the instances have been determined entirely by the points in the Circle SOP. Next, we will generate a stream of numerical values that can be used to modify the scale of each instance.

Create a **Noise** CHOP in an empty area of the network.

Right-click on its output and connect it to a Null CHOP.

Select the Noise CHOP and open its parameters.

Under the **Channel** page: Rename Channel Names to: scale (This is not strictly necessary, but naming channels clearly makes networks much easier to understand as they become more complex.)

Change Units to **Samples** (see figure below).

Set **End** number to: 39

Why set to 39 here? If you middle-click on the Null SOP connected to the second Circle SOP, you will see that it contains 40 points. 

Each point can correspond to one instance. Since counting begins at zero, 40 points require 40 samples. This gives exactly one sample for each instance position.

What is a Noise CHOP doing here? 

Unlike SOPs, which store geometry, CHOPs store numerical data. The Noise CHOP generates a sequence of values that fluctuate according to a noise algorithm. In the next step, we will connect these values to the instancing system so that each circle receives its own scale value. Instead of forty identical circles, we will begin creating a structure with variation.

**Step 10. Use the Noise CHOP to Scale the Instances**

We now have a stream of 40 noise values. The next step is to use these values to control the size of each instance.

Select the Geometry COMP and open its parameters. Navigate to the Instance page.

Locate the **Scale OP** parameter.

Drag the Null CHOP connected to the Noise CHOP onto **Scale OP**.

Set:

**Scale X** to scale
**Scale Y** to scale
**Scale Z** to scale

The instances should immediately begin changing size according to the values generated by the Noise CHOP. Earlier, we renamed the Noise CHOP’s channel from its default name to **scale**. This makes it easy to identify and reference later. By setting scale into the Scale X, Y, and Z fields, we are telling TouchDesigner to use that channel’s values to drive the scaling of every instance.

**Step 11. Add a Math CHOP**

The Noise CHOP generates raw data, but the Math CHOP allows us to shape and refine that data before it is used elsewhere in the network.

Locate the connection between the Noise CHOP and its Null CHOP. Right-click on the connection line.

Select Insert Operator.

Choose **Math** CHOP.

Select the Math CHOP and explore its parameters.

Experiment with **Range** (to expand or compress the values)

Return to the Noise CHOP and try changing **Seed** (to generate a different pattern)

You should see the instanced circles immediately respond as the scaling values change. At this point, we are no longer simply drawing circles. We are building a small dataflow system in which geometry, numerical data, and transformations interact with one another. Small changes to a few numbers can now reshape the entire spirograph-like sphere.

### Nine Nodes and Many Lines

At the end of this exercise, the TouchDesigner version of the spirograph-like sphere is built from a small network of operators. These nine nodes produce the same kind of animated structure as the Processing sketch below. 

```
int bigRadius = 180;   // radius of large circular structure
int smallRadius = 180; // base radius of small circles
int count = 40; // number of repetitions

void setup() {
  size(800, 800); //1000x1000 pixel window
  smooth(8); //for smoother edges
}

void draw() { //runs every frame in the form of an animation loop
  background(15); //clears the screen each frame with a dark grey to prevent trails
  translate(width/2, height/2); //moves the origin (0,0) from the top-left corner to the centre of the screen so that drawing is centered

  stroke(220); //set line colour to light grey
  noFill(); //circles wire-framed with no colour fill

  float t = frameCount * 0.02; // time variable 
  rotate(t * 0.5); // rotate whole structure slowly

  for (int i = 0; i < count; i++) {
    float angle = map(i, 0, count, 0, TWO_PI);
    pushMatrix();
    rotate(angle);

    float animatedBig = bigRadius + sin(t + i * 0.2) * 40; // make radius gently pulse
    translate(animatedBig, 0);

    float animatedSmall = smallRadius + sin(t * 2 + i * 0.3) * 30; // make circle size ripple

    ellipse(0, 0, animatedSmall * 2, animatedSmall * 2);
    popMatrix();
  }
}
```

In the text-based coding, the logic is written as a sequence of instructions: define the radius, set up the canvas, loop through repetitions, calculate each angle, rotate, translate, animate the radius, and draw each circle. The program unfolds line by line, and understanding it requires mentally simulating its execution. In TouchDesigner, the same logic is distributed across a visible network. The Circle SOP provides the shape, the Geometry COMP instances it, the Transform SOP controls the spatial arrangement, the Noise and Math CHOPs generate changing scale values, and the Line MAT determines how the geometry is rendered. Instead of reading the program from top to bottom, we trace relationships and data flows through the network. More importantly, the program remains *live* while it is being edited, allowing computation to be explored as an ongoing process rather than a completed set of instructions.

## Beyond TouchDesigner: Where Else Do We Find Node-Based Programming?

Although node-based programming is often associated with creative platforms such as TouchDesigner, visual programming has expanded far beyond the worlds of art and design. A review by Kuhail and colleagues (2022) examined visual programming research published between 2010 and 2020 and found that visual programming environments are increasingly used in domains as diverse as the IoT, robotics, education, data science, smart cities, mobile applications, and interactive displays.[^5] Visual programming has become an important way of organising complex technical systems. There are four major forms of visual programming. Some systems are *block-based*, such as Scratch, where puzzle-like blocks help users avoid syntax errors. Others are *form-based*, where applications are built through menus, fields, and configurable actions, or *icon-based*, where icons represent services, commands, or data sources. TouchDesigner belongs to the largest and perhaps the most influential category: *diagram-based visual programming*, representing computation through boxes connected by lines. 

This node-based abstraction makes visual programming accessible to users who may not identify as coder as here the programmer is less a coder than an architect of workflows, but it also imposes constraints as one can only do what the available operators allow. When a workflow exceeds these limits, users often need to extend the system through scripting or custom code (as we have to animate the rotation with Python in the coding example). Aside from the creative platforms such as TouchDesigner, in which visual programming environments are designed for real-time interaction with images, sounds, sensors, and other user inputs, diagram-based programming has also become important in the field of the so-called artificial intelligence. Tools such as DL-IDE allow users to construct deep-learning models visually by dragging and connecting layers on a canvas.[^6] A neural network that might otherwise require hundreds of lines of TensorFlow or PyTorch code can instead be represented as a layered network, suggesting an interesting affinity between machine learning and diagrammatic thinking. In short, node-based visual programming is not simply an alternative or more accessible way of writing code, but a distinct way of conceptualising computation itself—one that foregrounds relationships, data flows, and processes as means of visualising, orchestrating, understanding, and reasoning about complex systems.

[^1]: Daniel D. Hils, ‘Visual Languages and Computing Survey: Data Flow Visual Programming Languages,’ Journal of Visual Languages and Computing 3, no. 1 (1992): 69–101, accessed June 2026, <https://fab.cba.mit.edu/classes/S62.12/docs/Hils_visual.pdf>

[^2]: J. Paul Morrison, ‘Flow-Based Programming,’ (2007) accessed June 2026, <https://www.jpaulmorrison.com/fbp/fbp2.htm?ref=datarabbit.com>

[^3]: Thomas R. G. Green and Marian Petre, ‘Usability Analysis of Visual Programming Environments: A “Cognitive Dimensions” Framework,’ Journal of Visual Languages and Computing 7, no. 2 (1996): 131–174, accessed June 2026, <https://web.engr.oregonstate.edu/~burnett/CS589and584/CS589-papers/CogDimsPaper.pdf>

[^4]: For those wishing to continue beyond this introductory exercise, the TouchDesigner community provides a wealth of freely available online learning resources. One particularly accessible video tutorials can be found at [The Interactive & Immersive HQ](https://www.youtube.com/@TheInteractiveImmersiveHQ)

[^5]: Mohammad Amin Kuhail, Shahbano Farooq, Rawad Hammad, and Mohammed Bahja, ‘Characterising Visual Programming Approaches for End-User Developers: A Systematic Review,’ IEEE Access (2021): 14181–14202, accessed June 2026, <https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=9320477>

[^6]: Srikanth G. Tamilselvam, Naveen Panwar, Shreya Khare, Rahul Aralikatte, Anush Sankaran, and Senthil Mani, ‘A Visual Programming Paradigm for Abstract Deep Learning Model Development,’ in Proceedings of the 10th Indian Conference on Human-Computer Interaction (New York: Association for Computing Machinery, 2019), 1–11.





[Back to table of contents](#contents)

<p class="credits">Written by Wanqi Li, 2026-08-18<br />Licence: <a href="https://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a></p>

<p class="previous-next-lesson"><a href="toc.html">Methods Fellows 2025 lessons</a></p>


