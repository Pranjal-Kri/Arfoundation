
# AR Apps

Playing Around with Augmented Reality with Unity 3D and AR Foundation.


## SimpleAR

This is a good starting sample that enables point cloud visualization and plane detection. There are buttons on screen that let you pause, resume, reset, and reload the ARSession.

When a plane is detected, you can tap on the detected plane to place a cube on it. This uses the `ARRaycastManager` to perform a raycast against the plane.

| Action | Meaning |
| ------ | ------- |
| Pause  | Pauses the ARSession, meaning device tracking and trackable detection (e.g., plane detection) is temporarily paused. While paused, the ARSession does not consume CPU resources. |
| Resume | Resumes a paused ARSession. The device will attempt to relocalize and previously detected objects may shift around as tracking is reestablished. |
| Reset | Clears all detected trackables and effectively begins a new ARSession. |
| Reload | Completely destroys the ARSession GameObject and re-instantiates it. This simulates the behavior you might experience during scene switching. |


## LightEstimation

### BasicLightEstimation
Demonstrates basic light estimation information from the camera frame. You should see values for "Ambient Intensity" and "Ambient Color" on screen. The relevant script is [`BasicLightEstimation.cs`](https://github.com/Unity-Technologies/arfoundation-samples/blob/master/Assets/Scripts/BasicLightEstimation.cs) script.

### HDRLightEstimation
This sample attempts to read HDR lighting information. You should see values for "Ambient Intensity", "Ambient Color", "Main Light Direction", "Main Light Intensity Lumens", "Main Light Color", and "Spherical Harmonics". Most devices only support a subset of these 6, so some will be listed as "Unavailable." The relevant script is [`HDRLightEstimation.cs`](https://github.com/Unity-Technologies/arfoundation-samples/blob/master/Assets/Scripts/HDRLightEstimation.cs) script.

On iOS, this is only available when face tracking is enabled and requires a device that supports face tracking (such as an iPhone X, XS or 11). When available, a virtual arrow appears in front of the camera which indicates the estimated main light direction. The virtual light direction is also updated, so that virtual content appears to be lit from the direction of the real light source.

When using `HDRLightEstimation`, the sample will automatically pick the supported camera facing direction for you, for example `World` on Android and `User` on iOS, so it does not matter which you facing direction select in the `ARCameraManager.cs` component.


## TogglePlaneDetection

This sample shows how to toggle plane detection on and off. When off, it will also hide all previously detected planes by disabling their GameObjects. See [`PlaneDetectionController.cs`](https://github.com/Unity-Technologies/arfoundation-samples/blob/master/Assets/Scripts/PlaneDetectionController.cs).

## PlaneClassification

This sample shows how to query for a plane's classification. Some devices attempt to classify planes into categories such as "door", "seat", "window", and "floor". This scene enables plane detection using the `ARPlaneManager`, and uses a prefab which includes a component which displays the plane's classification, or "none" if it cannot be classified.

## FeatheredPlanes

This sample demonstrates basic plane detection, but uses a better looking prefab for the `ARPlane`. Rather than being drawn as exactly defined, the plane fades out towards the edges.

## PlaneOcclusion

This sample demonstrates basic plane detection, but uses an occlusion shader for the plane's material. This makes the plane appear invisible, but virtual objects behind the plane are culled. This provides an additional level of realism when, for example, placing objects on a table.

Move the device around until a plane is detected (its edges are still drawn) and then tap on the plane to place/move content.

## UX

A sample demonstrating UI that may be useful when guiding new users through an AR application is available in the [ARFoundation Demos](https://github.com/Unity-Technologies/arfoundation-demos#ux--also-available-on-the-asset-store-here) repository.

## EnvironmentProbes

This sample demonstrates environment probes, a feature which attempts to generate a 3D texture from the real environment and applies it to reflection probes in the scene. The scene includes several spheres which start out completely black, but will change to shiny spheres which reflect the real environment when possible.

## ARWorldMap

An `ARWorldMap` is an ARKit-specific feature which lets you save a scanned area. ARKit can optionally relocalize to a saved world map at a later time. This can be used to synchronize multiple devices to a common space, or for curated experiences specific to a location, such as a museum exhibition or other special installation. Read more about world maps [here](https://developer.apple.com/documentation/arkit/arworldmap). A world map will store most types of trackables, such as reference points and planes.

The [`ARWorldMapController.cs`](https://github.com/Unity-Technologies/arfoundation-samples/blob/master/Assets/Scripts/ARWorldMapController.cs) performs most of the logic in this sample.

## ImageTracking

There are two samples demonstrating image tracking. The image tracking samples are supported on ARCore, ARKit, and Magic Leap. To enable image tracking, you must first create an `XRReferenceImageLibrary`. This is the set of images to look for in the environment. [Click here](https://docs.unity3d.com/Packages/com.unity.xr.arsubsystems@4.2/manual/image-tracking.html) for instructions on creating one.

You can also add images to the reference image library at runtime. This sample includes a button that adds the images `one.png` and `two.png` to the reference image library. See the script `DynamicLibrary.cs` for example code.

Run the sample on an ARCore or ARKit-capable device and point your device at one of the images in [`Assets/Scenes/ImageTracking/Images`](https://github.com/Unity-Technologies/arfoundation-samples/tree/master/Assets/Scenes/ImageTracking/Images). They can be displayed on a computer monitor; they do not need to be printed out.

### BasicImageTracking

At runtime, ARFoundation will generate an `ARTrackedImage` for each detected reference image. This sample uses the [`TrackedImageInfoManager.cs`](https://github.com/Unity-Technologies/arfoundation-samples/blob/master/Assets/Scenes/ImageTracking/BasicImageTracking/TrackedImageInfoManager.cs) script to overlay the original image on top of the detected image, along with some meta data.

### ImageTrackingWithMultiplePrefabs

With [`PrefabImagePairManager.cs`](https://github.com/Unity-Technologies/arfoundation-samples/blob/master/Assets/Scenes/ImageTracking/ImageTrackingWithMultiplePrefabs/PrefabImagePairManager.cs) script, you can assign different prefabs for each image in the reference image library.

You can also change prefabs at runtime. This sample includes a button that switch between the original and alternative prefab for the first image in the reference image library. See the script [`DynamicPrefab.cs`](https://github.com/Unity-Technologies/arfoundation-samples/blob/master/Assets/Scenes/ImageTracking/ImageTrackingWithMultiplePrefabs/DynamicPrefab.cs) for example code.

## Face Tracking

There are several samples showing different face tracking features. Some are ARCore specific and some are ARKit specific.

### FacePose

This is the simplest face tracking sample and simply draws an axis at the detected face's pose.

This sample uses the front-facing (i.e., selfie) camera.

### FaceMesh

This sample instantiates and updates a mesh representing the detected face. Information about the device support (e.g., number of faces that can be simultaneously tracked) is displayed on the screen.

This sample uses the front-facing (i.e., selfie) camera.

## HumanBodyTracking2D

This sample demonstrates 2D screen space body tracking. A 2D skeleton is generated when a person is detected. See the [`ScreenSpaceJointVisualizer.cs`](https://github.com/Unity-Technologies/arfoundation-samples/blob/master/Assets/Scripts/ScreenSpaceJointVisualizer.cs) script.

This sample requires a device with an A12 bionic chip running iOS 13.

## HumanBodyTracking3D

This sample demonstrates 3D world space body tracking. A 3D skeleton is generated when a person is detected. See the [`HumanBodyTracker.cs`](https://github.com/Unity-Technologies/arfoundation-samples/blob/master/Assets/Scripts/HumanBodyTracker.cs) script.

This sample requires a device with an A12 bionic chip running iOS 13.














  
