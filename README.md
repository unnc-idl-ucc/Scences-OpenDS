# Scenes-OpenDS

Scenes, which were used to conduct user studies, were released.

## Motivation

OpenDS is a useful open drive framework that allows user to create driving task themselves to support their research. However, driving task creation requires the support of the scene model. This project is used to create a corresponding model scene file for the establishment of driving task by JMonkeyEngineer.

## Introduction

This project aims to create 3D scene for OpenDS framework by using JMonkeyEngine SDK3. We upload the needed models and textures, the code to build scene and the corresponding generated scene file.

## Goal

In this project, by using JMonkeyEngine SDK3, We can just use existing models or create the required models and combine to generate the scene which use be used in OpenDS. We can also set the physical effects of objects in the scene such as illumination and collision. Our goal is to use JMonkeyEngine SDK3 to build a scene that meets user requirements for this project.

## Design_Choices

We design to built several scenes to study people's behavior in different scene. To simulate more realistic scenes, all objects in the scene are set proportional to the proportion in reality. For the first scene, the road we designed is two-way four-lane. We also design another scene with two-way eight-lane road. With different number of lanes, the driver may have different behaviors when encountering the same event such as being overtaken. We also add fence, tree and some road signs to make the scene more like the same world.

## Contributors

[Zilin Song](https://github.com/ZilinSONG), mentored by [Xiangjun Peng](https://github.com/Shiangjun)
