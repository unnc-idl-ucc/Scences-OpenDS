# Scenes-OpenDS

Scenes, which were used to conduct user studies, were released.

Directory
=========
</br>


<!--ts-->
   * [Introduction](#Introduction)
   * [Design Choices](#Design_Choices)
   * [Prerequisites](#Prerequisites)
   * [Demonstration to Set Up](#Demonstration_to_Set_Up)
      * [Geometry](#Geometry)
      * [Textures](#Textures)
      * [Models](#Models)
      * [Light](#Light)
      * [Export](#Export)
   * [References](#References)
   
<!--te-->
   
Introduction
============

This project is used to create scene for OpenDS framework and created in JMonkeyEngine3. We upload the needed models and textures, the code to build scene and the corresponding generated scene file.

Design_Choices
============

We design to built three scenes to study people's behavior in different scene. To simulate more realistic scenes, all objects in the scene are set proportional to the proportion in reality. For the first scene, the road we designed is two-way four-lane. We also design another scene with two-way eight-lane road. With different number of lanes, the driver may have different behaviors when encountering the same event such as being overtaken. The last scene is auto driving scene and used to study people's feelings under different driving styles.

Prerequisites
============

1. Before import this project, make sure you download the JMonkeyEngine SDK3, you can download form https://github.com/jMonkeyEngine/sdk/releases.
2. Download the whole project flie
3. Open JMonkeyEngine SDK3, click File, then click open project and select the project file you download.
4. Run the project and you can see the established scene.

Demonstration_to_Set_Up
========

To set up the scene, you need to change the corresponding code. The code file is loacated at "\Scences-OpenDS\src\net\jmecn\physics3d" with name "The_First_Scene.java".

Geometry
-----
<br>
The Geometry is the basic element in the scene. Every object is a geometry or the combination of geometries in the scene. We can set the mesh shape,  size, material, position and rotation angle of the geometry in the code.
<br>

Geometry set up demonstration:

```bash
        Mesh Grand = new Box (3000f,0.1f,3000f);
        Material Grand_brick = new Material(
        assetManager, "Common/MatDefs/Misc/Unshaded.j3md");	
        Geometry grand = new Geometry("floor", Grand); 
        grand.setMaterial(Grand_brick);
        grand.rotate(0.0f,0.0f,0.0f);
        grand.setLocalTranslation(400, -0.11f, 398);
```

* The first line define the mesh shape and the size of mesh.  
* The second line set material.  
* The third and forth lines define a geometry with the setted mesh and material.  
* The fifth line is used to chanage the rotation angle.  
* The last line is used to attach the geometry to the scene.

mesh shape|	Box
:- | :-
size in 3 dimensions|	(3000f,0.1f,3000f);
Rotation in 3 dimensions	|(0.0f,0.0f,0.0f);
Position in 3 dimensions	|(400, -0.11f, 398);

Textures
-----
<br>
The Textures are some 2D image and we paste the texture onto the geometry to show different objects. We can set pasted mode(Clamp/Repeat)
<br>

Textures set up demonstration:

```bash
        Texture grasst = assetManager.loadTexture("Scenes/Task/two/grass.png");
        grasst.setWrap(WrapMode.Repeat);
        Grand.scaleTextureCoordinates(new Vector2f(3000, 3000));
        Grand_brick.setTexture("ColorMap", grasst);
```
* The frist line is used to read the texture from the customer path.  
* The second line set the wrap mode of the texture.  
* The thrid line define the number of repeat for this texture in a geometry(2D).  
* The last line means paste the material onto the geometry.  

Wrap Mode|	Repeat
:- | :-
repeat number in 2 dimensions|	(3000,3000);


Models
-----
<br>
Some models can be imported to the scene by code. The supported model files are *.j3o, *.mesh.xml, *.scene, *.obj+*.mtl, *.blender.
We can reset up models' size, rotation and position.
<br>

Models Imported demonstration:

```bash
        String model_path = "Scenes/Task/speedLimit50/speedLimit50.scene";
        assetManager.registerLocator("assets", FileLocator.class);
        Spatial speed_limit = (Spatial) assetManager.loadModel(model_path);
        speed_limit.scale(2f, 2f, 2f);
        speed_limit.rotate(0f, 3.1415f, 0)
        speed_limit.setLocalTranslation(-5f, -1.1f, -200f);
        rootNode.attachChild(speed_limit);
```
* The first three line is read the model file.  
* The forth line is set the size of the model.  
* The fifth line is set the rotation of the model.  
* The sixth line define the position of the moedel in the scene.  

Model type|	.scene
:- | :-
size scale in 3 dimensions|	(2f, 2f, 2f);
Rotation in 3 dimensions	|(0f, 3.1415f, 0);
Position in 3 dimensions	|(-5f, -1.1f, -200f);



Light
-----
<br>
We can add lighting in different directions to make the photosensitive material show the original color.
<br>

Light set up demonstration:

```bash
        DirectionalLight light = new DirectionalLight();                        
        sun1.setDirection(new Vector3f(0.1f, 0.7f, 1.0f).normalizeLocal());
        rootNode.addLight(sun1);
```
Light|	Light
:- | :-
Light attitude |(0.1f, 0.7f, 1.0f);


Export
-----
<br>
In order to use in OpenDS, we need to export the scene file as .j3o file. The export function is used to save the sceneto a custom path as .j3o file.
<br>

Export set up demonstration:

```bash
    String path = "Result/scene1.j3o";
    BinaryExporter exporter = BinaryExporter.getInstance();
    assetManager.registerLocator("assets", FileLocator.class);
    File file = new File("assets/" + path.replace("Scene", "j3o"));
    try {
      exporter.save(rootNode, file);
    } catch (IOException ex) {
      ex.printStackTrace();
    }
```
* The first line define the path to save the file.  
* The second line define a binary exporter.  
* The sixth line used to save the scene as .j3o file.  

save type|	.j3o
:- | :-
save path|	./assets/Result/
file name	| scene1.j3o


References
========

Kusterer R. jMonkeyEngine 3.0 Beginner's Guide[M]. Packt Publishing Ltd, 2013.

Math R, Mahr A, Moniri M M, et al. OpenDS: A new open-source driving simulator for research[C]//Proceedings of the International Conference on Automotive User Interfaces and Interactive Vehicular Applications, Adjunct Proceedings. 2012: 7-8.



