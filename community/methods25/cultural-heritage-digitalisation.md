# Cultural Heritage Digitalisation: 3D Surveying and Modelling
<link rel="stylesheet" href="../../cookbook.css">
<p class="previous-next-lesson"><a href="toc.html">^ Methods Fellow 2025</a></p>


## Contents
- [Introduction](#introduction)
- [Part I: Theory](#part-i-theory)
- [Part II: Tutorial](#part-ii-tutorial-for-practice)

## Introduction

This lesson introduces the principal digital methods used to document and analyse cultural heritage sites and objects. It combines a short theoretical overview with a practical introduction to photogrammetry using **Agisoft Metashape**.

In the first part, we explore the main technologies currently used in heritage documentation, including:

- Structure from Motion (SfM)
- Laser scanning
- Simultaneous Localisation and Mapping (SLAM)
- Structured-light scanning
- Mobile applications such as Polycam and RealityScan

In the second part, we focus on the workflow of Agisoft Metashape, a widely used photogrammetry software. You will learn how to generate a 3D model from photographs taken with a camera or smartphone, including the processes of image capture, photo alignment, point cloud generation, mesh creation, texturing, and tiled model creation. 

No prior technical experience is required. The lesson is designed as a step-by-step introduction for beginners interested in applying digital methods to cultural heritage research and practice.

## Part I. Theory

## Why Use Digital Tools in Cultural Heritage?

Before beginning, considering the following questions: 
- Why are you interested in digital tools for cultural heritage studies?
- What challenges in heritage research, conservation, or interpretation might digital methods help address?

Digital technologies are commonly used in cultural heritage for two broad purposes:

### 1. Research, Documentation, and Conservation

Digital recording methods provide accurate and detailed documentation of heritage sites, monuments, and artefacts. Such records support conservation planning, condition assessment, and long-term preservation.

Digital documentation is particularly valuable when heritage is threatened by natural disasters, climate change, conflict, or urban development. Following the fire at the Notre-Dame Cathedral, for example, previous laser-scanning surveys played an important role in informing restoration efforts.

### 2. Public Interpretation and Engagement

Digital heritage data can also be used to improve public access and understanding through:
- Museum and gallery exhibitions
- Virtual and augmented reality experiences
- Interactive visualisations of archaeological sites
- Online collections and digital archives

**Case Study**: [UNESCO’s discussion of protecting heritage sites in Lebanon demonstrates how digital technologies can assist in documenting and safeguarding cultural heritage during periods of conflict] (https://www.youtube.com/watch?v=jqAAi5QFyQQ). 
This lesson focuses primarily on the first area—digital tools for research, documentation, and conservation—while briefly introducing applications for public engagement.

## Principal Digital Tools for Heritage Documentation

Several technologies are commonly used to capture and record heritage assets:
- **Structure from Motion(SfM)** photogrammetry (e.g. Agisoft Metashape)
- **Laser scanning**
- **SLAM (Simultaneous Localization and Mapping)** systems (e.g. ZEB Horizon, Leica BLK2Go)
- **Structured-light scanning** (e.g. Faro Freestyle)
- **Mobile scanning applications** (e.g. Polycam, RealityScan) 
- **HBIM (Heritage Building Information Modelling)** 

Before we go into details, it is useful to think of heritage digitisation as a sequence of interconnected stages rather than a single technical process.

It begins with **data collection**, where digital tools such as photogrammetry, laser scanning, or archival digitisation are used to capture physical, visual, or spatial information from heritage sites and objects. This is followed by **data processing**, which involves cleaning, aligning, scaling, and transforming raw data into usable forms such as point clouds, models, or maps. However, data do not become meaningful on their own. Through **data interpretation and communication**, digital outputs are analysed, contextualised, and translated into drawings, narratives, visualisations, or arguments that support research, conservation decisions, and public understanding. Finally, **data sharing** ensures that digital heritage data can circulate beyond a single project, through archives, repositories, publications, or open platforms, raising important questions about accessibility, standards, ethics, and long-term preservation.

*Digital heritage workflows are rarely linear, which often require researchers to revisit earlier stages and refine their data collection or processing methods*. 

## Structure from Motion (SfM)

**What it is Structure form Motion?**

Structure from Motion (SfM) is a computer vision technique that reconstructs three-dimensional geometry from a series of overlapping two-dimensional photographs. In simple terms, it turns a collection of images into a 3D model.

SfM works by identifying matching features across multiple photographs and using these correspondences to estimate both the position of the camera and the three-dimensional structure of the scene. The resulting output is typically a **point cloud**, which can then be developed into a textured 3D model.

Although SfM is often grouped under the broader category of **photogrammetry**, there is a subtle distinction between the two. Traditional photogrammetry usually relies on known camera positions, pre-calibrated cameras, and carefully planned image acquisition. SfM, by contrast, automatically calculates camera positions and orientations from the photographs themselves. In contemporary practice, however, the terms *SfM* and *photogrammetry* are often used interchangeably.

[Structure from Motion concept (http:// www. theia-sfm. org/ sfm. html)](https://www.researchgate.net/profile/Araz-Gharehaghajlou/publication/364157192/figure/fig2/AS:11431281160802175@1684855658935/Structure-from-Motion-concept-http-www-theia-sfm-org-sfm-html.png)

### How Does SfM Work?

**1. Feature Detection and Matching**
Distinct visual features are automatically identified and matched across multiple photographs.

**2. Camera Calibration and Pose Estimation**
The software estimates camera positions, orientations, and internal camera parameters.

**3. 3D Reconstruction**
Matched features are used to generate a sparse point cloud, which can be further processed into dense point clouds, meshes, and textured models.

One of the most influential algorithms used for feature matching is **SIFT (Scale-Invariant Feature Transform)**, developed by David Lowe in 1999. SIFT enables reliable feature detection across changes in scale, viewpoint, and lighting, making it particularly effective for photogrammetric reconstruction.

For readers interested in the theoretical foundations of SfM, see:
Ullman, Shimon, ‘The Interpretation of Structure from Motion’, *Proceedings of the Royal Society of London. Series B. Biological Sciences*, 203.1153 (1979), 405–26 <https://doi.org/10.1098/rspb.1979.0006⁠>

Lowe, David G., ‘Object Recognition from Local Scale-Invariant Features’, in *Proceedings of the Seventh IEEE International Conference on Computer Vision*, 2 vols (Los Alamitos, CA: IEEE Computer Society Press, 1999), II, 1150–57 <https://doi.org/10.1109/ICCV.1999.790410⁠>

**Early applications of the SIFT algorithm:** 

A landmark application of SfM was the Photo Tourism project developed by Noah Snavely, Steven Seitz, and Richard Szeliski in 2006. The project demonstrated how large collections of publicly available photographs could be used to reconstruct famous landmarks in three dimensions, laying the foundation for many contemporary photogrammetry workflows.

Photo Tourism, see Snavely, Noah, Steven M. Seitz, and Richard Szeliski, ‘Photo Tourism: Exploring Photo Collections in 3D’, *ACM Transactions on Graphics (Proceedings of SIGGRAPH 2006)*, 25.3 (2006), 835–46 <https://doi.org/10.1145/1141911.1141964⁠>

### Common SfM Software

Several software packages implement SfM and multi-view stereo (MVS) workflows:

- **Agisoft Metashape**
- **RealityCapture**
- **Meshroom** (open source)
- **COLMAP** (research-oriented, open source)

[Examples of software implementing SfM-MVS, based on Mike James https://www.lancaster.ac.uk/staff/jamesm/research/sfm.htm](https://www.lancaster.ac.uk/staff/jamesm/research/SfM_MVS_software.pdf).

### Why Use SfM?

SfM has become one of the most widely adopted methods in cultural heritage documentation because it offers several advantages:

- **Low cost and accessible**: requires only a digital camera or smartphone.
- **High-quality visual outputs**: produces detailed textured models and orthophotos.
- **Rapid and non-invasive data capture**: ideal for fieldwork and heritage recording.
- **Scalable across different contexts**: suitable for objects, buildings, archaeological sites, and landscapes.
- **Flexible and portable**: can be applied in environments where other surveying equipment may be difficult to deploy. 

## Laser Scanning

### What is Laser Scanning?

Laser scanning is a surveying technique that uses laser light to measure the position of points on an object’s surface and record them as three-dimensional coordinates. Unlike photogrammetry, which reconstructs geometry from photographs, laser scanning directly measures distance and spatial position.

Because millions of measurements can be captured in a short period of time, laser scanners are capable of producing highly accurate and detailed records of buildings, monuments, archaeological sites, and landscapes.

### Measuring using Light

Laser scanners emit pulses of light and measure how the light returns after striking a surface. The scanner then calculates the position of each point in three-dimensional space.

Depending on the instrument, laser systems may use:
- Ultraviolet light (200–400 nm)
- Visible light (400–700 nm)
- Infrared light (above 700 nm)

### Two Main Types of Laser Scanner

Laser scanning systems generally fall into two categories:

**1. Range-Based Scanners (Time-of-Flight or Phase Shift)**
These scanners calculate distance by measuring how long it takes a laser pulse to travel to an object and return to the sensor. They are commonly used for surveying buildings, archaeological sites, and large landscapes.

**2. Triangulation Scanners**
These scanners determine position through geometric triangulation between the laser source, the sensor, and the target object. They typically achieve higher precision but are designed for smaller objects and shorter scanning distances.
[Different ranges of static laser scanning](https://drive.google.com/file/d/1xcrS5I9QOnB-KOhCrtkgykxltiX2LXws/view?usp=sharing)

### Processing Laser Scan Data

After fieldwork, scan data must be processed and combined into a complete model.

Common tasks include:

- Registering multiple scans into a single coordinate system
- Removing noise and unwanted points
- Cleaning and segmenting point clouds
- Colourising scans using photographic data
- Exporting data for visualisation or analysis

Common software packages include:
- **Leica Cyclone**: scan registration, noise filtering, colourisation, export
- **CloudCompare**: point cloud cleaning, comparison, distance and deformation analysis
- **Autodesk ReCap**: management of large datasets and integration with CAD software

### Photogrammetry versus Laser Scanning

Both photogrammetry and laser scanning produce three-dimensional data, but they collect information in different ways.

<table>
<tr>
<th>Photogrammetry (SfM)</th>
<th>Laser Scanning (TLS)</th>
</tr>
<tr>
<td>Passive technique</td>
<td>Active technique</td>
</tr>
<tr>
<td>Uses photographs</td>
<td>Uses laser measurements</td>
</tr>
<tr>
<td>Reconstructs geometry from image matching</td>
<td>Directly measures distance</td>
</tr>
<tr>
<td>Low-cost and accessible</td>
<td>Requires specialised equipment</td>
</tr>
<tr>
<td>Produces high-quality textures and colour information</td>
<td>Produces highly accurate geometry</td>
</tr>
<tr>
<td>Processing is largely automated</td>
<td>Registration and processing often require additional user input</td>
</tr>
<tr>
<td>Suitable for objects, buildings, and landscapes</td>
<td>Particularly effective for complex architecture and large sites</td>
</tr>
</table>
In practice, many heritage projects combine both methods. Laser scanning provides highly accurate geometry, while photogrammetry contributes detailed colour and texture information.

### Understanding Point Clouds

A **point cloud** is the primary output of both photogrammetry and laser scanning. It consists of a collection of points in a three-dimensional coordinate system, defined by X, Y, and Z coordinates. Together, these points describe the surface geometry of an object or site.

Although both techniques generate point clouds, the nature of the data differs:

<table>
<tr>
<th>Photogrammetry</th>
<th>Laser Scanning</th>
</tr>
<tr>
<td>Point cloud generated after image processing</td>
<td>Point cloud generated directly during scanning</td>
</tr>
<tr>
<td>Usually unstructured</td>
<td>Usually structured and systematically acquired</td>
</tr>
<tr>
<td>Requires scaling and georeferencing</td>
<td>Recorded at true scale (1:1)</td>
</tr>
<tr>
<td>Often contains colour information derived from photographs</td>
<td>May contain colour, reflectance values, surface normals, etc.</td>
</tr>
</table>

## Simultaneous Localization and Mapping (SLAM)

### What is SLAM?

**Simultaneous Localisation and Mapping (SLAM)** is a technology that allows a device to determine its own position while simultaneously creating a map of its surroundings.

In heritage documentation, SLAM is commonly combined with **LiDAR** sensors to create mobile mapping systems that capture three-dimensional data as the operator walks through a site. Unlike traditional laser scanning, which requires the scanner to be placed at multiple fixed positions, SLAM systems continuously collect data while moving.

This makes SLAM particularly useful for:
- Large buildings and architectural complexes
- Archaeological sites
- Historic interiors with many rooms
- Rapid documentation and emergency recording

### How Does SLAM Work?

A SLAM system continuously combines information from multiple sensors, including:
- **LiDAR** for measuring distances
- **IMUs (Inertial Measurement Units)** for tracking movement
- **Cameras** for visual information and positioning

As the operator moves through the environment, the system identifies overlapping features and continuously updates both its location and the emerging 3D map.

### Examples of SLAM Systems

**GeoSLAM ZEB Horizon**
- Use LiDAR + SLAM to continuously map as the operator moves.
- Produce large area point clouds suitable for indoor loops and outdoor corridors.
- Interval mapping (like a continuous path) rather than isolated handheld scan frames.  

**Leica BLK 2GO** 
- Uses Leica’s GrandSLAM technology, combining LiDAR, cameras, and inertial sensors.
- Real-time point cloud building and imaging as you walk.
- Integrated photo-georeferenced colour point clouds (good for visualization and documentation).
- Designed for both indoor and outdoor scanning of buildings and interiors.  

## Structured-Light Scanning

### What is Structured-Light Scanning?

Structured-light scanning is a high-accuracy, non-contact method for capturing three-dimensional geometry. Instead of measuring distance with laser pulses, the scanner projects a known pattern of light—typically stripes or grids—onto an object and records how the pattern deforms across the surface.

By analysing these distortions, the system reconstructs a highly detailed 3D model.

Structured-light scanners are commonly used for:

- Artefacts and museum objects
- Sculptures and decorative details
- Architectural fragments
- Conservation and condition assessment

### How Does It Work?

The process involves three steps:
1. A projector casts a pattern of light onto the object.
2. One or more cameras record the deformation of the pattern.
3. Software calculates the position of surface points and generates a dense 3D model.

Because the projected pattern is precisely controlled, structured-light scanning can achieve very high levels of accuracy and detail.

**Example: FARO Freestyle 2**

The FARO Freestyle 2 is a handheld structured-light scanner designed for capturing complex surfaces and confined spaces.

Key features include:
- Handheld operation with real-time visual feedback
- High point density and detailed colour information
- Immediate visualisation during acquisition
- Effective for interiors, construction environments, and detailed architectural features
 
## Mobile Applications

Recent advances in mobile technology have made 3D documentation more accessible than ever. Several smartphone applications can generate three-dimensional models using photogrammetry or LiDAR sensors (available on some devices).

While mobile applications cannot generally match the accuracy and reliability of professional photogrammetry or laser-scanning workflows, they provide a quick and accessible way to create preliminary records of buildings, objects, and archaeological features.

Mobile scanning applications are particularly useful for:

- Rapid site documentation
- Preliminary surveys
- Teaching and training
- Public engagement and outreach
- Experimenting with 3D modelling before using professional software

### RealityScan

RealityScan is a mobile photogrammetry application developed by Epic Games. Users capture a series of overlapping photographs, which are automatically processed into a textured 3D model.

Key features include:

- Simple image-based workflow
- Automated cloud processing
- Quick generation of textured models
- Easy export and sharing options

### Polycam

Polycam allows users to create 3D models using either photogrammetry or LiDAR (on supported devices).

Key features include:

- Photogrammetry and LiDAR capture modes
- Real-time visualisation during acquisition
- Export to common 3D formats
- Suitable for documenting rooms, buildings, and small objects

## 3D Printing

### From Digital Twin to Physical Replica

One of the most exciting applications of heritage digitisation is the ability to transform a digital model into a physical object through **3D printing**.

Once a heritage asset has been documented using photogrammetry, laser scanning, or other surveying methods, the resulting digital model can be used to create accurate physical replicas at full scale or reduced scale. This process connects the digital and physical worlds, allowing heritage objects to be studied, conserved, and exhibited in new ways.

### Applications of 3D Printing in Cultural Heritage

**Research and Education**
Three-dimensional replicas allow researchers, students, and visitors to handle and examine objects that may otherwise be inaccessible due to their fragility, rarity, or location.

**Conservation and Restoration**
Digital models can be used to recreate missing or damaged elements of heritage objects and buildings. Replicas may be employed for testing conservation interventions or, in some cases, for the reconstruction of lost components.

**Museums and Exhibitions**
3D-printed replicas enable museums to display accurate copies of important artefacts while reducing risks to the originals. Replicas can also improve accessibility by allowing visitors to touch and interact with objects that would normally be protected behind glass.

### Case Study: The Boxer at Rest

A notable example is the Hellenistic bronze sculpture Boxer at Rest, housed in National Roman Museum. For an exhibition in Beijing in 2022, a high-quality replica was produced using digital surveying and advanced fabrication techniques, allowing the work to be displayed internationally while preserving the original sculpture.

The project demonstrates how digital heritage workflows can extend beyond documentation to support cultural exchange, conservation, and public engagement.

[Reproducing Art is ‘Art’: The Boxer and Its Replica (video)](https://www.youtube.com/watch?v=paxiCyRKA1A).

## VR/AR/MR for Cultural Heritage

Virtual, Augmented, and Mixed Reality (VR/AR/MR) technologies are increasingly used in cultural heritage to create immersive and interactive experiences of sites, objects, and historical environments.

These technologies allow users to move beyond static documentation and engage with heritage in embodied and spatial ways.

### Key Applications

- **Accessibility**: enabling remote access to heritage sites and collections that may be geographically distant or physically inaccessible
- **Education and engagement**: supporting interactive learning experiences in museums, classrooms, and public exhibitions
- **Embodied experience**: allowing users to explore reconstructed spaces and understand scale, spatial relationships, and context

Consider the following questions: 

How faithfully do digital reconstructions represent historical reality?
What is the status of a virtual reconstruction in relation to the original heritage object or site?
How are historical uncertainties visualised or simplified in immersive environments?

## Key Reflections
Digital heritage work is most effective when guided by clear research and communication goals. The choice of tools should always follow from the question being asked, rather than the other way around.

A successful workflow typically depends on:

- **Purpose**: What are you trying to achieve: documentation, analysis, conservation, or communication?
- **Accuracy**: What level of precision is required for your project?
- **Understanding**: How will the data be interpreted and used by others?
- **Integration**: How do different methods and tools work together in a coherent pipeline?

*‘If you fail to plan, you are planning to fail.’*

In digital heritage practice, planning is not only technical but also conceptual. It involves selecting appropriate methods, understanding their limitations, and combining them into an integrated approach that aligns with the research question.

## Part II. Tutorial for Practice

**Software used**: Agisoft Metashape 

Download from the official website: <https://www.agisoft.com/downloads/installer/>

Choose the **Professional Edition**. A 30-day free trial is available. After the trial period, the software can still be used in Demo mode, or unlocked with a paid license.

### Workflow Overview

The basic photogrammetry workflow in Metashape is as follows:
- **Add Photos**
- **Align Photos**
- **Build Point Cloud**
- **Build Mesh**
- **Build Texture**
- **Build Tiled Model**
- **Build Orthomosaic**
- **Export Results**


[Metashape workflow diagram](https://drive.google.com/file/d/1zN9YdP9C7KlDCwRwbQIoq_xVICVvZEwo/view)

In the following sections, we will go through this process step by step to create a 3D model from your own images.

## Capture Photos

Choose an object or a space you would like to reconstruct in 3D. 

Not all subjects are suitable for photogrammetry. Avoid objects that are:
- Transparent, reflective, glossy, or metallic
- Highly symmetrical or monochromatic
- Extremely small or extremely large (without appropriate equipment)
- Flat objects that cannot be photographed from multiple angles

Photographs for Agisoft Metashape can be taken with any digital camera (including smartphones), as long as consistent capture guidelines are followed. Image quality and overlap are essential for successful reconstruction.

### General Photography Guidelines

Whatever camera you use, follow these principles:

- **Focus:** Keep the subject consistently sharp in every image
- **Stability:** The object should not move during capture; ideally, nothing in the scene should move
- **Camera settings:** Keep settings consistent (no changes in zoom, focal length, ISO, shutter speed, or image orientation)
- **Image quantity:** More images generally produce better results, but will increase processing time
- **Lighting:** Use soft, diffuse lighting to minimise shadows and reflections
- **Background:** Use a neutral or uniform background for small objects
- **Scale:** Include a known measurement or reference object for scale
- **Coverage:** Move around the object in a full circle, capturing multiple heights and angles
- **Detail shots:** Take additional close-up images of important features or textures

[Correct way to move while capturing different types of subjects and examples of image taking positions](https://drive.google.com/file/d/1RNljgiwC2FnmWqOj1wy9uhkO3RJwSfpN/view?usp=share_link)

### Image Overlap and Coverage

For successful reconstruction, ensure:

- At least **60–80% overlap** between consecutive images
- Each surface point is visible in at least **three different images**
- ‘Blind zones’ (areas not visible from multiple viewpoints) are minimised

[Overlap and camera coverage diagram](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/31037515990/original/ZrCNWoU5dF1yyt6aIzG1CArsFPJRL99FsA.png?1643789850)

If the object has repetitive patterns or lacks distinct visual features, fiducial markers can be added during photography to improve feature matching and alignment.

## Creating a 3D Model from Image Files

This section walks through the full photogrammetry workflow in Agisoft Metashape, from image import to final export.

### 1. Add Photos

First, import your images into Metashape.

You can do this in several ways:
- Go to **Workflow → Add Photos**
- Use the **Add Photos** button in the Workspace panel
- Drag and drop images directly into the Workspace

Select all images and click **Open**. A new *chunk* will be created containing your dataset.

### 2. Align Photos/ Build Sparse Cloud

Go to **Workflow → Align Photos**
In most cases, you can keep the default settings (e.g. medium accuracy and generic preselection).
After processing, Metashape generates a **sparse point cloud** and estimates camera positions.
In the Workspace panel, you can check how many images were successfully aligned. Ideally, all photos should be included.
You can navigate the scene using your mouse or trackpad (orbit, zoom, and pan). Camera positions can be displayed by enabling: **Model → Show/Hide Items → Show Cameras**

### 3. Build Dense Point Cloud

Before generating the dense cloud, define the working area to reduce unnecessary computation.

Go to: **Region → Resize Region**. 

Adjust the bounding box to include only the object of interest. Ensure all important parts remain inside the region from multiple viewing angles.

Then run: **Workflow → Build Dense Cloud** (quality: medium, depth filtering: aggressive)

Once complete, the dense cloud should contain millions of points and clearly represent the object’s surface geometry.

### 4. Clean Up

The dense cloud may include unwanted points (background noise or reconstruction errors).

Use selection tools to:
- Select unwanted points
- Press **Delete (X)** to remove them

This step improves mesh quality in later stages.

*Remember to save your project regularly.*

### 5. Build Mesh

Go to **Workflow → Build Mesh**
Choose settings depending on your subject: 

**For object:** 
- Source data: Dense Cloud
- Surface type: Arbitrary (3D)
- Face count: Medium
- Interpolation: Extrapolated

**For space/terrain:** 
- Source data: Dense Cloud
- Surface type: Height field (2.5D)
- Face count: Medium
- Interpolation: Extrapolated

The mesh converts the point cloud into a continuous surface.

### 6. Build Texture

Once the mesh is generated, you can apply image-based texture.

Go to **Workflow → Build Texture**

This step projects the original photographs onto the mesh, producing a photorealistic surface representation. Texture is one of the main advantages of photogrammetry compared to other 3D capture methods.

### 7. Build Tiled Model (Optional)

Tiled models are designed for large-scale visualisation (e.g. buildings, cities, landscapes).

Go to  **Workflow → Build Tiled Model**

This format supports efficient streaming and rendering of high-resolution models by dividing them into hierarchical tiles.

Tiled models are typically generated from mesh, point cloud, or depth maps and are automatically textured from source images.

### 8. Export Model

When satisfied with the result, export your model via:

**File → Export → Export Model**

You can export different outputs depending on your needs:
- Point cloud only (for analysis workflows)
- Mesh + texture (for visualisation and sharing)

After export, you will typically obtain three files:
- **.obj** — geometry (3D mesh)
- **.jpg / .png** — texture image
- **.mtl** — material file linking geometry and texture

These files must remain in the same folder for correct display. Some software will display the image texture automatically when you open the OBJ and in other software you might need to re-assign the image texture to the material.

## Viewing and Sharing Your Model

You can view exported models using:
- **MeshLab** (https://www.meshlab.net)
- **CloudCompare** (https://www.cloudcompare.org)
- **Adobe Photoshop (3D viewer)**

To share models online:
- **Sketchfab** (https://sketchfab.com)
- Web embedding via **Google Model Viewer** (https://modelviewer.dev)

For guidance on publishing to Sketchfab, see:

<http://cycollection.com/visualthinking/links.html>

[Back to table of contents](#contents)

<p class="credits">Written by Jiayao Jiang, <a href="mailto:jj596@cam.ac.uk">jj596@cam.ac.uk</a>, 2026-08-18
<br />Licence: <a href="https://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a></p>

<p class="previous-next-lesson"><a href="toc.html">Methods Fellows 2025 lessons</a></p>


