# AltspaceUtil
Provides helper functions, behaviors and A-Frame components for common functionality compatible with [AltspaceSDK](https://github.com/AltspaceVR/AltspaceSDK/).

# Usage
Include the utility library in your project:
```html
<script src="https://cdn.jsdelivr.net/npm/altspacevr-behaviors@1.1.5/js/altspaceutil.min.js"></script>
```

# API Reference

## Functions
* [altspaceutil.getFullspaceApp](#getFullspaceApp)
* [altspaceutil.getFullspaceEnclosure](#getFullspaceEnclosure)
* [altspaceutil.getAbsoluteURL](#getAbsoluteURL)
* [altspaceutil.getBasePath](#getBasePath)
* [altspaceutil.isMobileApp](#isMobileApp)
* [altspaceutil.expandSerializationBuffer](#expandSerializationBuffer)
* [altspaceutil.profileSerializationBuffer](#profileSerializationBuffer)
* [altspaceutil.setCursorCollider](#setCursorCollider)
* [altspaceutil.isCursorCollider](#isCursorCollider)
* [altspaceutil.loadTexture](#loadTexture)
* [altspaceutil.loadScript](#loadScript)
* [altspaceutil.loadScripts](#loadScripts)
* [altspaceutil.loadAsset](#loadAsset)
* [altspaceutil.loadAssets](#loadAssets)
* [altspaceutil.addAssetLoader](#addAssetLoader)
* [altspaceutil.removeAssetLoader](#removeAssetLoader)
* [altspaceutil.overrideTextureLoader](#overrideTextureLoader)

## Behaviors
* [altspaceutil.behaviors.NativeComponent](#NativeComponent)
* [altspaceutil.behaviors.NativeComponentSync](#NativeComponentSync)
* [altspaceutil.behaviors.TransformControls](#TransformControls)
* [altspaceutil.behaviors.OrbitControls](#OrbitControls)
* [altspaceutil.behaviors.UserEvents](#UserEvents)
* [altspaceutil.behaviors.PreloadNativeSounds](#PreloadNativeSounds)
* [altspaceutil.behaviors.HoverMaterialOpacity](#HoverMaterialOpacity)
* [altspaceutil.behaviors.HoverMaterialColor](#HoverMaterialColor)
* [altspaceutil.behaviors.NativeTextMaterial](#NativeTextMaterial)
* [altspaceutil.behaviors.TWEEN](#TWEEN)
* [altspaceutil.behaviors.Billboard](#Billboard)
* [altspaceutil.behaviors.Text](#Text)
* [altspaceutil.behaviors.GLTF](#GLTF)
* [altspaceutil.behaviors.Sound](#Sound)

## Events
* [transform-controls-dragmove](#transform-controls-dragmove)
* [transform-controls-dragbegin](#transform-controls-dragbegin)
* [transform-controls-dragend](#transform-controls-dragend)
* [avatarchange](#avatarchange)
* [userchange](#userchange)
* [avatarstatus](#avatarstatus)
* [n-sound-preloaded](#n-sound-preloaded)
* [gltf-loaded](#gltf-loaded)
* [sound-loaded](#sound-loaded)
* [sound-played](#sound-played)
* [sound-paused](#sound-paused)
* [sound-stopped](#sound-stopped)

## Classes
* [FullspaceApp](#FullspaceApp)

## A-Frame Components
* [altspace-transform-controls](#altspace-transform-controls)
* [n-text-material](#n-text-material)

# Functions

## <a name="getFullspaceApp">altspaceutil.getFullspaceApp</a>
Gets an initialized fullspace app instance.  The app will be initialized on the first call to this function, which sets up the render loop, fullspace enclosure and anchors.

### Parameters
| Name                             | Type   | Default | Description |
| -------------------------------- | ------ | ------- | ----------- |
| `config`                         | Object |         | Optional parameters. |
| `config.serializationBufferSize` | Number | 500000  | Initial size of the serialization buffer. See [altspaceutil.expandSerializationBuffer](#expandSerializationBuffer) for more information. |

### Returns
| Type    | Description |
| ------- | ----------- |
| Promise | A promise that resolves to a [FullspaceApp](#FullspaceApp). |

## <a name="getFullspaceEnclosure">altspaceutil.getFullspaceEnclosure</a>
Gets the fullspace enclosure for the app.

### Returns
| Type    | Description |
| ------- | ----------- |
| Promise | A promise that resolves to a fullspace [Enclosure](https://altspacevr.github.io/AltspaceSDK/doc/js/module-altspace-Enclosure.html). |

## <a name="getAbsoluteURL">altspaceutil.getAbsoluteURL</a>
Create an absolute URL from the specified relative URL, using the current host as the URL base.

### Parameters
| Name  | Type   | Description |
| ----- | ------ | ----------- |
| `url` | String | A relative URL.  Providing an absolute URL will return itself unchanged. |

### Returns
| Type   | Description |
| ------ | ----------- |
| String | An absolute URL of the given relative URL. |

## <a name="getBasePath">altspaceutil.getBasePath</a>
Create a base path from the specified file URL.

### Parameters
| Name  | Type   | Description |
| ----- | ------ | ----------- |
| `url` | String | A URL to a file. |

### Returns
| Type   | Description |
| ------ | ----------- |
| String | A URL to the file's base path. |

## <a name="isMobileApp">altspaceutil.isMobileApp</a>
Indicates whether the app is being loaded on a mobile version of the Altspace client.  This is typically determined by the user agent exposed to the app.

### Returns
| Type    | Description |
| ------- | ----------- |
| Boolean | Whether the app is running on a mobile client.  Returns `true` for mobile clients, `false` otherwise. |

## <a name="expandSerializationBuffer">altspaceutil.expandSerializationBuffer</a>
Expands the Altspace client's serialization buffer to improve loading performance.

### Parameters
| Name   | Type   | Description |
| ------ | ------ | ----------- |
| `size` | Number | The size to expand the serialization buffer by, in bytes. |

## <a name="profileSerializationBuffer">altspaceutil.profileSerializationBuffer</a>
Enables or disables the profiler for the Altspace client's serialization buffer to determine whether the buffer needs to be expanded.  Profiler messages will be displayed in the console when enabled.

### Parameters
| Name      | Type    | Description |
| --------- | ------- | ----------- |
| `enabled` | Boolean | Specifies whether the serialization buffer is to be enabled. |

## <a name="setCursorCollider">altspaceutil.setCursorCollider</a>
Sets the Altspace cursor collider property for the specified object.

### Parameters
| Name                | Type                                                          | Default | Description |
| ------------------- | ------------------------------------------------------------- | ------- | ----------- |
| `object3d`          | [THREE.Object3D](https://threejs.org/docs/#api/core/Object3D) |         | An object to set the cursor collider property for. |
| `isCursorCollider`  | Boolean                                                       |         | Specifies if the object is a cursor collider. |
| `recursive`         | Boolean                                                       | false   | Specifies if the property change should also be applied recursively to all children of the object. |

## <a name="isCursorCollider">altspaceutil.isCursorCollider</a>
Gets the Altspace cursor collider property for the specified object.

### Parameters
| Name       | Type                                                          | Description |
| ---------- | ------------------------------------------------------------- | ----------- |
| `object3d` | [THREE.Object3D](https://threejs.org/docs/#api/core/Object3D) | An object to retrieve the cursor collider property from. |

### Returns
| Type    | Description |
| ------- | ----------- |
| Boolean | Whether the object is a cursor collider. |

## <a name="loadTexture">altspaceutil.loadTexture</a>
Loads a three.js texture from the specified texture file URL, optimizing for faster loading times in the Altspace client where appropriate.

### Parameters
| Name     | Type   | Description |
| -------- | ------ | ----------- |
| `url`    | String | A URL to a texture file. |
| `config` | Object | Optional parameters to be passed to the texture loader (e.g. crossOrigin, withCredentials, path). |

### Returns
| Type                                                            | Description |
| --------------------------------------------------------------- | ----------- |
| [THREE.Texture](https://threejs.org/docs/#api/textures/Texture) | The loaded texture. |

## <a name="loadScript">altspaceutil.loadScript</a>
Loads and executes a script from the specified JavaScript file URL.

### Parameters
| Name                | Type     | Default | Description |
| ------------------- | -------- | ------- | ----------- |
| `url`               | String   |         | A URL to a JavaScript file. |
| `config`            | Object   |         | Optional parameters for specialized cases. |
| `config.scriptTest` | Function | null    | A predicate function that tests whether the script contents has loaded.  A return value of true indicates that the loaded script content exists, false otherwise. |
| `config.loadOnce`   | Boolean  | true    | Indicates whether the script should be loaded if it was previously loaded.  If true, the script will not be loaded again on subsequent calls if it was previously loaded. |

### Returns
| Type    | Description |
| ------- | ----------- |
| Promise | A promise that resolves when the javascript file has been loaded. |

## <a name="loadScripts">altspaceutil.loadScripts</a>
Loads and executes one or more scripts from the specified JavaScript file URL.

### Parameters (1)
| Name         | Type     | Description |
| ------------ | -------- | ----------- |
| `scripts`    | String[] | An array of JavaScript file URLs to be loaded. |

### Parameters (2)
| Name         | Type     | Description |
| ------------ | -------- | ----------- |
| `scripts`    | Script[] | An array of objects containing a URL and optional config parameters for the scripts to be loaded. See below for object parameters. |

Script parameters.

| Name         | Type     | Default | Description |
| ------------ | -------- | ------- | ----------- |
| `url`        | String   |         | A URL to a JavaScript file. |
| `scriptTest` | Function | null    | A predicate function that tests whether the script contents has loaded.  A return value of true indicates that the loaded script content exists, false otherwise. |
| `loadOnce`   | Boolean  | true    | Indicates whether the script should be loaded if it was previously loaded.  If true, the script will not be loaded again on subsequent calls if it was previously loaded. |

### Returns
| Type    | Description |
| ------- | ----------- |
| Promise | A promise that resolves when the javascript files have been loaded. |

## <a name="loadAsset">altspaceutil.loadAsset</a> ([Example](https://github.com/NGenesis/altspacevr-behaviors/blob/master/examples/loadassets.html))
Loads an asset from the specified URL.

Default formats supported:

- [Wavefront OBJ (.obj)](https://en.wikipedia.org/wiki/Wavefront_.obj_file)
  - Material is applied automatically based on MTL file linked to OBJ.
- [COLLADA (.dae)](https://en.wikipedia.org/wiki/COLLADA)
- [glTF (.gltf/.glb)](https://en.wikipedia.org/wiki/GlTF)
  - Altspace client loads glTF assets using n-gltf by default, which can be overridden with the `native` config parameter.
- [STL (.stl)](<https://en.wikipedia.org/wiki/STL_(file_format)>)
- [AutoDesk FBX (.fbx)](https://en.wikipedia.org/wiki/FBX)
- [Open Asset Import Library (.assimp)](https://en.wikipedia.org/wiki/Open_Asset_Import_Library)
- [Binary Object/Material (.bom)](https://github.com/NGenesis/bom-obj2bom#features)

Additional formats can be loaded by registering a custom file handler using [addAssetLoader](#addAssetLoader).

### Parameters
| Name                    | Type                                                              | Default                    | Description |
| ----------------------- | ----------------------------------------------------------------- | -------------------------- | ----------- |
| `url`                   | String                                                            |                            | A URL to the asset to be loaded. |
| `config`                | Object                                                            |                            | Optional parameters. |
| `config.applyTransform` | Boolean                                                           | true                       | When true, the `position`/`rotation`/`quaternion`/`scale` properties will be applied to the loaded asset. |
| `config.cursorCollider` | Boolean                                                           | false                      | Specified whether cursor collision is enabled on the loaded asset. |
| `config.native`         | Boolean                                                           | true                       | When true, assets loaded in the Altspace client will be loaded as native objects where appropriate (e.g. n-gltf for glTF assets), otherwise standard browser behavior will be followed. |
| `config.position`       | [THREE.Vector3](https://threejs.org/docs/#api/math/Vector3)       | { x: 0, y: 0, z: 0 }       | Position to be applied to the loaded asset. |
| `config.rotation`       | [THREE.Euler](https://threejs.org/docs/#api/math/Euler)           | { x: 0, y: 0, z: 0 }       | Rotation to be applied to the loaded asset, in radians. |
| `config.quaternion`     | [THREE.Quaternion](https://threejs.org/docs/#api/math/Quaternion) | { x: 0, y: 0, z: 0, w: 1 } | Quaternion to be applied to the loaded asset.  Specifying quaternion will override the rotation property. |
| `config.scale`          | [THREE.Vector3](https://threejs.org/docs/#api/math/Vector3)       | { x: 1, y: 1, z: 1 }       | Scale to be applied to the loaded asset.  Alternatively, uniform scaling is applied when a number is specified. |
| `config.onLoaded`       | Function                                                          | null                       | A callback function to execute when the asset has been loaded.  A reference to the loaded asset will be passed into this function. |
| `config.crossOrigin`    | String                                                            | anonymous                  | Specifies the cross-origin state for loading textures. |

### Returns
| Type    | Description |
| ------- | ----------- |
| Promise | A promise that resolves to the loaded asset. |

## <a name="loadAssets">altspaceutil.loadAssets</a> ([Example](https://github.com/NGenesis/altspacevr-behaviors/blob/master/examples/loadassets.html))
Loads one or more assets from the specified URLs.

### Parameters (1)
| Name         | Type     | Description |
| ------------ | -------- | ----------- |
| `assets`     | Asset[]  | An array of assets to be loaded. |

### Parameters (2)
| Name         | Type     | Description |
| ------------ | -------- | ----------- |
| `assets`     | Object   | An object of unordered, named assets to be loaded. |

Asset parameters.

| Name             | Type                                                              | Default                    | Description |
| ---------------- | ----------------------------------------------------------------- | -------------------------- | ----------- |
| `url`            | String                                                            |                            | A URL to a JavaScript file. |
| `applyTransform` | Boolean                                                           | true                       | When true, the `position`/`rotation`/`quaternion`/`scale` properties will be applied to the loaded asset. |
| `cursorCollider` | Boolean                                                           | false                      | Specified whether cursor collision is enabled on the loaded asset. |
| `native`         | Boolean                                                           | true                       | When true, assets loaded in the Altspace client will be loaded as native objects where appropriate (e.g. n-gltf for glTF assets), otherwise standard browser behavior will be followed. |
| `position`       | [THREE.Vector3](https://threejs.org/docs/#api/math/Vector3)       | { x: 0, y: 0, z: 0 }       | Position to be applied to the loaded asset. |
| `rotation`       | [THREE.Euler](https://threejs.org/docs/#api/math/Euler)           | { x: 0, y: 0, z: 0 }       | Rotation to be applied to the loaded asset, in radians. |
| `quaternion`     | [THREE.Quaternion](https://threejs.org/docs/#api/math/Quaternion) | { x: 0, y: 0, z: 0, w: 1 } | Quaternion to be applied to the loaded asset.  Specifying quaternion will override the rotation property. |
| `scale`          | [THREE.Vector3](https://threejs.org/docs/#api/math/Vector3)       | { x: 1, y: 1, z: 1 }       | Scale to be applied to the loaded asset.  Alternatively, uniform scaling is applied when a number is specified. |
| `onLoaded`       | Function                                                          | null                       | A callback function to execute when the asset has been loaded.  A reference to the loaded asset will be passed into this function. |
| `crossOrigin`    | String                                                            | anonymous                  | Specifies the cross-origin state for loading textures. |

### Returns
| Type    | Description |
| ------- | ----------- |
| Promise | A promise that resolves to the loaded assets, either as an array or object of named assets depending on the supplied parameters. |

## <a name="addAssetLoader">altspaceutil.addAssetLoader</a> ([Example](https://github.com/NGenesis/altspacevr-behaviors/blob/master/examples/loadassets.html))
Registers a handler that will load and construct the specified asset type when [loadAsset](#loadAsset) or [loadAssets](#loadAssets) is called.

### Parameters
| Name      | Type                                                                                              | Description |
| --------- | ------------------------------------------------------------------------------------------------- | ----------- |
| `regex`   | [RegExp](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp) | The regular expression that will be used to identify an asset from its URL (e.g. `/\.dae$/i` to match the file extension for Collada assets.) |
| `handler` | AssetLoaderHandler                                                                                | A handler function that accepts a URL and configuration parameters that will load and construct the asset.  The function must return a promise that resolves that resolves to the loaded asset, or a rejected promise on failure. |

`AssetLoaderHandler` parameters.

| Name     | Type   | Description |
| -------- | ------ | ----------- |
| `url`    | String | A URL to the asset to be loaded. |
| `config` | Object | Optional parameters. |

## <a name="removeAssetLoader">altspaceutil.removeAssetLoader</a>
Unregisters a handler for the specified asset type that is used when [loadAsset](#loadAsset) or [loadAssets](#loadAssets) is called.

### Parameters
| Name      | Type                                                                                              | Default | Description |
| --------- | ------------------------------------------------------------------------------------------------- | ------- | ----------- |
| `regex`   | [RegExp](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp) |         | The regular expression associated with an asset handler. |
| `handler` | AssetLoaderHandler                                                                                | null    | An asset handler function that is associated with the specified regular expression.  If omitted, all handlers for the specified regular expression will be removed. |

## <a name="overrideTextureLoader">altspaceutil.overrideTextureLoader</a>
Enables or disables texture loading optimizations in the Altspace client.  Enabling texture loader optimizations can drastically improve texture loading times, reduce resource usage and correct compability issues with embedded textures in the Altspace client.

Please note that these optimizations are enabled by default, and can be disabled when compatibility issues with other libraries arise.

### Parameters
| Name       | Type    | Description |
| ---------- | ------- | ----------- |
| `override` | Boolean | Specifies whether texture loader optimizations are enabled. |

# Behaviors

## <a name="NativeComponent">altspaceutil.behaviors.NativeComponent</a> ([Example](https://github.com/NGenesis/altspacevr-behaviors/blob/master/examples/NativeComponent.html))
Provides support for AltspaceVR native components to be attached to objects, providing sane configuration defaults where appropriate.

### Parameters
`type` - Native component type.

`data` - Native component properties.  See [here](#native-component-properties) for available properties and defaults.

`config` - Optional parameters for specialized use cases.  Many of these properties are provided only to override the internal behavior of a component in specialized use cases.

| Name                | Type                                                          | Default | Description |
| ------------------- | ------------------------------------------------------------- | ------- | ----------- |
| `targetEntity`      | [THREE.Object3D](https://threejs.org/docs/#api/core/Object3D) | null    | An object in the scene that a user will teleport to when entering a native portal. |
| `useCollider`       | Boolean                                                       | false   | Specifies whether cursor collision should be disabled on the native component. |
| `sharedComponent`   | Boolean                                                       | true    | Specifies whether the native component should share the same [THREE.Mesh](https://threejs.org/docs/#api/objects/Mesh) instance with other native components. |
| `recursiveMesh`     | Boolean                                                       | false   | Specifies whether the native component is applied recursively to all [THREE.Mesh](https://threejs.org/docs/#api/objects/Mesh) children. |
| `recursive`         | Boolean                                                       | false   | Specifies whether the native component is applied recursively to all children. |
| `sendUpdates`       | Boolean                                                       | true    | Specifies whether the native component should send updates to the native Altspace client. |
| `updateOnStaleData` | Boolean                                                       | true    | Specifies whether the native component should send updates to the native Altspace client when a property has changed. |
| `inheritParentData` | Boolean                                                       | false   | Specifies whether the native component should inherit its property state from a parent component. |
| `meshComponent`     | Boolean                                                       | false   | Specifies whether the native component is treated as a mesh-specific component.  This is used as a performance optimization to defer initialization of mesh-specific components (e.g. native parents and colliders) attached to placeholder objects, until another component is added that gives them functionality (e.g. text, spawner). |

### Methods

#### <a name="callComponentAction">callComponentAction</a>
Invokes an action associated with the native component, and does not provide a return value.

| Name           | Type   | Description |
| -------------- | ------ | ----------- |
| `actionName`   | String | The action name to invoke on the native component. |
| `actionArgs`   | Object | Arguments that will be passed along with the action when invoked. |

#### <a name="callComponentFunc">callComponentFunc</a>
Calls a function associated with the native component, and returns a promise of the value that will be returned by the native component function.

| Name           | Type   | Description |
| -------------- | ------ | ----------- |
| `functionName` | String | The function name to invoke on the native component. |
| `functionArgs` | Object | Arguments that will be passed to the function when called. |

#### <a name="callComponent">callComponent</a>
*This function has been **Deprecated**. See [callComponentAction](#callComponentAction).*

#### <a name="getAttribute">getAttribute</a>
Retrieves an attribute associated with a native component.  See [here](#native-component-attributes) for available attributes.

| Name            | Type   | Description |
| --------------- | ------ | ----------- |
| `attributeName` | String | An attribute name associated with the native component. |

### <a name="native-component-attributes">Native Component Attributes</a>
Attributes associated with a native component can be retrieved using the [getAttribute](#getAttribute) method.

#### n-sound
| Name           | Type    | Description |
| -------------- | ------- | ----------- |
| `loaded`       | Boolean | Indicates that the component has been loaded by the AltspaceVR client. |

#### n-gltf
| Name           | Type    | Description |
| -------------- | ------- | ----------- |
| `loaded`       | Boolean | Indicates that the component has been loaded by the AltspaceVR client. |

#### n-container
| Name           | Type    | Description |
| -------------- | ------- | ----------- |
| `count`        | Number  | The number of objects in the n-container. |

### <a name="native-component-properties">Native Component Properties</a>
#### n-object

```javascript
data: {
	res: 'architecture/wall-4w-4h'
}
```

#### n-spawner

```javascript
data: {
	res: 'interactables/basketball'
}
```

#### n-text

```javascript
data: {
	text: '',
	fontSize: 10,
	width: 10,
	height: 1,
	horizontalAlign: 'middle',
	verticalAlign: 'middle'
}
```

#### n-sphere-collider

```javascript
data: {
	isTrigger: false,
	center: { 'x': 0, 'y': 0, 'z': 0 },
	radius: 0,
	type: 'environment'
}
```

#### n-box-collider

```javascript
data: {
	isTrigger: false,
	center: { 'x': 0, 'y': 0, 'z': 0 },
	size: { 'x': 0, 'y': 0, 'z': 0 },
	type: 'environment'
}
```

#### n-capsule-collider

```javascript
data: {
	isTrigger: false,
	center: { 'x': 0, 'y': 0, 'z': 0 },
	radius: 0,
	height: 0,
	direction: 'y',
	type: 'environment'
}
```

#### n-mesh-collider

```javascript
data: {
	isTrigger: false,
	convex: true,
	type: 'environment'
}
```

#### n-container

```javascript
data: {
	capacity: 4
}
```

#### n-sound

```javascript
data: {
	on: '',
	res: '',
	src: '',
	loop: false,
	volume: 1,
	autoplay: false,
	oneshot: false,
	spatialBlend: 1,
	pitch: 1,
	minDistance: 1,
	maxDistance: 12,
	rolloff: 'logarithmic'
}
```

#### n-skeleton-parent

```javascript
data: {
	part: 'head',
	side: 'center',
	index: 0,
	userId: null // defaults to current user when omitted
}
```

#### n-cockpit-parent
No properties to be configured.

#### n-billboard
No properties to be configured.

#### n-layout-browser

```javascript
data: {
	url: 'about:blank',
	isEnclosure: false
}
```

#### n-portal

```javascript
data: {
	targetSpace: null, // defaults to current space when omited
	targetEvent: null, // defaults to current space when omited
	targetPosition: { x: 0, y: 0, z: 0 },
	targetQuaternion: { x: 0, y: 0, z: 0, w: 1 }
}
```

#### n-gltf

```javascript
data: {
        sceneIndex: 0,
        url: ''
}
```

#### n-rigidbody
*Experimental! This native component is not yet officially supported by the AltspaceSDK.*

```javascript
data: {
	mass: 1,
	drag: 0,
	angularDrag: 0.05,
	useGravity: true,
	isKinematic: false,
	positionConstraints: [false, false, false],
	rotationConstraints: [false, false, false],
}
```

## <a name="NativeComponentSync">altspaceutil.behaviors.NativeComponentSync</a> ([Example](https://github.com/NGenesis/altspacevr-behaviors/blob/master/examples/NativeComponentSync.html))
Provides support for AltspaceVR native component data to be synchronized over Firebase.  The behavior must be used in conjunction with [SceneSync](https://altspacevr.github.io/AltspaceSDK/doc/js/module-altspace_utilities_behaviors.SceneSync.html), [Object3DSync](https://altspacevr.github.io/AltspaceSDK/doc/js/module-altspace_utilities_behaviors.Object3DSync.html) and a [NativeComponent](#NativeComponent) of the same type specified for NativeComponentSync.

### Parameters
`type` - Type of native component to be synchronized.  To retrieve the behavior using the `getBehaviorByType` method, prepend `sync-` to the name of the native component type (e.g. `sync-n-text` for an `n-text` native component).

`config` - Optional parameters.

| Name      | Type                                                                                                                                               | Default | Description |
| --------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | ----------- |
| `syncRef` | [altspace.utilities.behaviors.Object3DSync](https://altspacevr.github.io/AltspaceSDK/doc/js/module-altspace_utilities_behaviors.Object3DSync.html) | null    | A reference to the object syncing component.  Defaults to using the syncing component of the object the behavior is attached to. |

## <a name="TransformControls">altspaceutil.behaviors.TransformControls</a> ([Example](https://github.com/NGenesis/altspacevr-behaviors/blob/master/examples/TransformControls.html))
Enables an object's position, rotation and scale to be manipulated in AltspaceVR using a draggable transform gizmo.

### Parameters
`config` - Optional parameters.

| Name                    | Type                                                          | Default | Description |
| ----------------------- | ------------------------------------------------------------- | ------- | ----------- |
| `controlType`           | String                                                        | none    | The default control type to be selected.  Supported control types are `none`, `position`, `rotate` or `scale`. |
| `showButtons`           | Boolean                                                       | false   | Specifies whether buttons should be displayed to toggle between control types. |
| `followTarget`          | Boolean                                                       | true    | Specified whether the transform gizmo should follow the object that is being manipulated. |
| `target`                | [THREE.Object3D](https://threejs.org/docs/#api/core/Object3D) | null    | The target that the transform gizmo should manipulate when interacted with.  If omitted, the object that the behavior is associated with will be used as the target. |
| `scale`                 | Number                                                        | 1       | Adjusts the scale of the transform gizmo. |
| `allowNegativeScale`    | Boolean                                                       | false   | Specifies whether the scale transform gizmo will allow the target's scale to be negative. |
| `positionAxisLock`      | Object                                                        |         | Specifies which axes of the position gizmo can be displayed and manipulated. |
| `positionAxisLock.x`    | Boolean                                                       | true    | X axis of the position gizmo. |
| `positionAxisLock.y`    | Boolean                                                       | true    | Y axis of the position gizmo. |
| `positionAxisLock.z`    | Boolean                                                       | true    | Z axis of the position gizmo. |
| `rotateAxisLock`        | Object                                                        |         | Specifies which axes of the rotate gizmo can be displayed and manipulated. |
| `rotateAxisLock.x`      | Boolean                                                       | true    | X axis of the rotate gizmo. |
| `rotateAxisLock.y`      | Boolean                                                       | true    | Y axis of the rotate gizmo. |
| `rotateAxisLock.z`      | Boolean                                                       | true    | Z axis of the rotate gizmo. |
| `scaleAxisLock`         | Object                                                        |         | Specifies which axes of the scale gizmo can be displayed and manipulated. |
| `scaleAxisLock.x`       | Boolean                                                       | true    | X axis of the scale gizmo. |
| `scaleAxisLock.y`       | Boolean                                                       | true    | Y axis of the scale gizmo. |
| `scaleAxisLock.z`       | Boolean                                                       | true    | Z axis of the scale gizmo. |
| `disableColliders`      | Boolean                                                       | true    | Specifies whether colliders on the target object should be disabled. |
| `disableChildColliders` | Boolean                                                       | true    | Specifies whether colliders on the target's children should be disabled. |

### Events

#### <a name="transform-controls-dragmove">transform-controls-dragmove</a>
Fires an event when the transform gizmo is being dragged.

| Name              | Type                                                          | Description |
| ----------------- | ------------------------------------------------------------- | ----------- |
| `behavior`        | [TransformControls](#TransformControls)                       | The behavior that controls the transform gizmo. |
| `parent`          | [THREE.Object3D](https://threejs.org/docs/#api/core/Object3D) | The object that the transform gizmo is parented to. |
| `transformTarget` | [THREE.Object3D](https://threejs.org/docs/#api/core/Object3D) | The object that the transform gizmo will manipulate. |
| `transformType`   | String                                                        | The type of transform being performed.  Possible values are `position`, `rotate` and `scale`. |
| `transformAxis`   | String                                                        | The axis that the transform is being performed on.  Possible values are `x`, `y`, `z` (for single axes) and `xyz` (for all axes). |
| `transformDelta`  | [THREE.Vector3](https://threejs.org/docs/#api/math/Vector3)   | The transform delta that was applied to the target object. |

#### <a name="transform-controls-dragbegin">transform-controls-dragbegin</a>
Fires an event when the transform gizmo starts being dragged.

| Name              | Type                                                          | Description |
| ----------------- | ------------------------------------------------------------- | ----------- |
| `behavior`        | [TransformControls](#TransformControls)                       | The behavior that controls the transform gizmo. |
| `parent`          | [THREE.Object3D](https://threejs.org/docs/#api/core/Object3D) | The object that the transform gizmo is parented to. |
| `transformTarget` | [THREE.Object3D](https://threejs.org/docs/#api/core/Object3D) | The object that the transform gizmo will manipulate. |
| `transformType`   | String                                                        | The type of transform being performed.  Possible values are `position`, `rotate` and `scale`. |
| `transformAxis`   | String                                                        | The axis that the transform is being performed on.  Possible values are `x`, `y`, `z` (for single axes) and `xyz` (for all axes). |

#### <a name="transform-controls-dragend">transform-controls-dragend</a>
Fires an event when the transform gizmo is no longer being dragged.

| Name              | Type                                                          | Description |
| ----------------- | ------------------------------------------------------------- | ----------- |
| `behavior`        | [TransformControls](#TransformControls)                       | The behavior that controls the transform gizmo. |
| `parent`          | [THREE.Object3D](https://threejs.org/docs/#api/core/Object3D) | The object that the transform gizmo is parented to. |
| `transformTarget` | [THREE.Object3D](https://threejs.org/docs/#api/core/Object3D) | The object that the transform gizmo will manipulate. |
| `transformType`   | String                                                        | The type of transform being performed.  Possible values are `position`, `rotate` and `scale`. |
| `transformAxis`   | String                                                        | The axis that the transform is being performed on.  Possible values are `x`, `y`, `z` (for single axes) and `xyz` (for all axes). |

## <a name="OrbitControls">altspaceutil.behaviors.OrbitControls</a> ([Example](https://github.com/NGenesis/altspacevr-behaviors/blob/master/examples/OrbitControls.html))
Provides a convenience wrapper for [THREE.OrbitControls](https://threejs.org/docs/#examples/controls/OrbitControls) when working with [altspace.utilities.Simulation](https://altspacevr.github.io/AltspaceSDK/doc/js/module-altspace_utilities.Simulation.html).

## <a name="UserEvents">altspaceutil.behaviors.UserEvents</a> ([Example](https://github.com/NGenesis/altspacevr-behaviors/blob/master/examples/UserEvents.html))
Subscribes to avatar and user preference update events for a given list of users, and dispatches events which have been triggered by a given user changing their avatar and/or account preferences.

### Parameters
`config` - Optional parameters.

| Name            | Type                            | Default | Description |
| --------------- | ------------------------------- | ------- | ----------- |
| `userIds`       | String[]                        | null    | An array of (legacy) User IDs for each user to dispatch events for.  When omitted, only avatar change events for the user currently logged in will be handled. |
| `onRequestData` | [onRequestData](#onRequestData) | null    | A precondition callback returning a boolean that determines if a user should have their data requested.  User data is requested if the callback returns true, otherwise no action is taken. |
| `refreshTime`   | Number                          | 5000    | Duration to wait between user updates, in milliseconds. |
| `trace`         | Boolean                         | false   | Specifies whether debugging information should be displayed. |

### Callbacks

#### <a name="onRequestData">onRequestData</a>
A precondition callback returning a boolean that determines if a user should have their data requested.  User data is requested if the callback returns true, otherwise no action is taken.

| Name     | Type                                                          | Description |
| -------- | ------------------------------------------------------------- | ----------- |
| `userId` | String                                                        | User ID of a user who will have their data requested. |
| `object` | [THREE.Object3D](https://threejs.org/docs/#api/core/Object3D) | The object that will emit the request. |

### Methods

#### <a name="subscribeUser">subscribeUser</a>
Subscribe to receiving events for a given User ID.

| Name     | Type   | Description |
| -------- | ------ | ----------- |
| `userId` | String | User ID to receive events for. |

#### <a name="unsubscribeUser">unsubscribeUser</a>
Unsubscribe from receiving events for a given User ID.

| Name     | Type   | Description |
| -------- | ------ | ----------- |
| `userId` | String | User ID to stop receiving events for. |

### Events

#### <a name="avatarchange">avatarchange</a>
Fires an event when the user changes avatar preferences.

| Name          | Type                                                          | Description |
| ------------- | ------------------------------------------------------------- | ----------- |
| `userId`      | String                                                        | User ID of the user. |
| `avatarId`    | String                                                        | Avatar type identifier that was selected by the user. |
| `avatarClass` | String                                                        | Avatar type classification. Typically one of `Pod`, `Robothead` or `Rubenoid`, or empty when unclassified. |
| `colors`      | Object                                                        | [THREE.Color](https://threejs.org/docs/#api/math/Color) preferences of the avatar.  This typically provides `primary` and `highlight` properties for Pod avatars, and `highlight` for Robothead avatars. |
| `rawColors`   | Object                                                        | Raw color preferences of the avatar.  This typically provides `primary` and `highlight` properties for Pod avatars, and `highlight` for Robothead avatars. |
| `textures`    | Object                                                        | Texture identifier preferences for the avatar.  This typically provides `hair`, `skin` and `clothing` properties for Rubenoid avatars. |
| `target`      | [THREE.Object3D](https://threejs.org/docs/#api/core/Object3D) | The object which emitted the event. |

#### <a name="userchange">userchange</a>
Fires an event when the user changes account preferences.

| Name          | Type                                                          | Description |
| ------------- | ------------------------------------------------------------- | ----------- |
| `userId`      | String                                                        | User ID of the user. |
| `username`    | String                                                        | Username of the user. |
| `displayName` | String                                                        | Display name of the user. |
| `target`      | [THREE.Object3D](https://threejs.org/docs/#api/core/Object3D) | The object which emitted the event. |

#### <a name="avatarstatus">avatarstatus</a>
Fires an event when the user's connection status changes.

| Name          | Type                                                          | Description |
| ------------- | ------------------------------------------------------------- | ----------- |
| `userId`      | String                                                        | User ID of the user. |
| `displayName` | String                                                        | Display name of the user. |
| `online`      | Boolean                                                       | Specifies whether user is currently logged in. |
| `target`      | [THREE.Object3D](https://threejs.org/docs/#api/core/Object3D) | The object which emitted the event. |

## <a name="PreloadNativeSounds">altspaceutil.behaviors.PreloadNativeSounds</a> ([Example](https://github.com/NGenesis/altspacevr-behaviors/blob/master/examples/PreloadNativeSounds.html))
Preloads the specified sound files used by n-sound to ensure the resources are cached for subsequent uses. The behavior will remove itself automatically once the sound files have been preloaded or the specified timeout threshold has been reached.

### Parameters
`sounds` - Native sound resources to be preloaded.  Can either be an array of sound file paths or an array of [NativeComponent](#NativeComponent) n-sound data objects (e.g. `{ src: 'file.wav', volume: 1.5 }`).

`config` - Optional parameters.

| Name      | Type    | Default | Description |
| --------- | ------- | ------- | ----------- |
| `dispose` | Boolean | true    | Specifies whether the preloaded native sound objects will be destroyed after the preload has completed.  By default, preloaded sound objects will be destroyed after being cached. |
| `timeout` | Number  | 10000   | Time in milliseconds to wait before ending the preload.  A [n-sound-preloaded](#n-sound-preloaded) event will be fired with a timeout property set to true when the timeout threshold has been reached. Specifying a zero or negative value will disable the timeout. |

### Events

#### <a name="n-sound-preloaded">n-sound-preloaded</a>
Fires an event once all sounds have been preloaded, or the specified timeout threshold has been reached.

| Name          | Type                                                            | Description |
| ------------- | --------------------------------------------------------------- | ----------- |
| `behavior`    | [PreloadNativeSounds](#PreloadNativeSounds)                     | The behavior that preloaded the sounds. |
| `sounds`      | [THREE.Object3D](https://threejs.org/docs/#api/core/Object3D)[] | The sound objects that were preloaded. Sound objects are children of the object the behavior is associated with. |
| `timeout`     | Boolean                                                         | Indicates whether the timeout threshold has been reached before all sounds were preloaded. |

## <a name="HoverMaterialOpacity">altspaceutil.behaviors.HoverMaterialOpacity</a> ([Example](https://github.com/NGenesis/altspacevr-behaviors/blob/master/examples/HoverMaterialOpacity.html))
Changes the opacity of an object's material when the cursor hovers over it, and restores the original opacity when the cursor is no longer hovering over the object.

### Parameters
`config` - Optional parameters.

| Name              | Type                                                                        | Default  | Description |
| ----------------- | --------------------------------------------------------------------------- | -------- | ----------- |
| `material`        | [THREE.Material](https://threejs.org/docs/#api/materials/MeshBasicMaterial) | null     | A reference to the material whose opacity will be updated.  Defaults to material of the object the behavior is attached to. |
| `opacity`         | Number                                                                      | 1        | The value that will be applied to the object's current material opacity when the cursor hovers over it. |
| `beginDuration`   | Number                                                                      | 75       | Duration the hovered opacity adjustment effect is intended to take to complete, in milliseconds. |
| `endDuration`     | Number                                                                      | 75       | Duration the unhovered opacity adjustment effect is intended to take to complete, in milliseconds. |
| `revertOnDispose` | Boolean                                                                     | true     | Specifies whether the object's original material opacity should be restored when the behavior has been destroyed. |
| `eventListener`   | [THREE.Object3D](https://threejs.org/docs/#api/core/Object3D)               | null     | Specifies an optional object that will listen for cursor events.  By default the object that the behavior is attached to will be used as the event listener. |
| `hoverChildren`   | Boolean                                                                     | true     | Specifies whether hovering over children of the event listener object should invoke the hover effect. |

## <a name="HoverMaterialColor">altspaceutil.behaviors.HoverMaterialColor</a> ([Example](https://github.com/NGenesis/altspacevr-behaviors/blob/master/examples/HoverMaterialColor.html))
Changes the color of an object's material when the cursor hovers over it, and restores the original color when the cursor is no longer hovering over the object.

### Parameters
`config` - Optional parameters.

| Name              | Type                                                                        | Default                   | Description |
| ----------------- | --------------------------------------------------------------------------- | ------------------------- | ----------- |
| `material`        | [THREE.Material](https://threejs.org/docs/#api/materials/MeshBasicMaterial) | null                      | A reference to the material whose color will be updated.  Defaults to material of the object the behavior is attached to. |
| `color`           | [THREE.Color](https://threejs.org/docs/#api/math/Color)                     | new THREE.Color('yellow') | The value that will be applied to the object's material color when the cursor hovers over it. |
| `beginDuration`   | Number                                                                      | 75                        | Duration the hovered color adjustment effect is intended to take to complete, in milliseconds. |
| `endDuration`     | Number                                                                      | 75                        | Duration the unhovered color adjustment effect is intended to take to complete, in milliseconds. |
| `revertOnDispose` | Boolean                                                                     | true                      | Specifies whether the object's original material color should be restored when the behavior has been destroyed. |
| `eventListener`   | [THREE.Object3D](https://threejs.org/docs/#api/core/Object3D)               | null                      | Specifies an optional object that will listen for cursor events.  By default the object that the behavior is attached to will be used as the event listener. |
| `hoverChildren`   | Boolean                                                                     | true                      | Specifies whether hovering over children of the event listener object should invoke the hover effect. |

## <a name="NativeTextMaterial">altspaceutil.behaviors.NativeTextMaterial</a> ([Example](https://github.com/NGenesis/altspacevr-behaviors/blob/master/examples/NativeTextMaterial.html))
Updates the color and opacity of a [n-text](https://altspacevr.github.io/AltspaceSDK/doc/aframe/module-altspace_components.n-text.html) native component using a material source.

### Parameters
`config` - Optional parameters.

| Name       | Type                                                                        | Default  | Description |
| ---------- | --------------------------------------------------------------------------- | -------- | ----------- |
| `material` | [THREE.Material](https://threejs.org/docs/#api/materials/MeshBasicMaterial) | null     | A reference to the material whose properties will be applied to the n-text native component.  Defaults to material of the object the behavior is attached to. |
| `color`    | Boolean                                                                     | true     | Specifies whether the n-text native component should use the color of the source material. |
| `opacity`  | Boolean                                                                     | true     | Specifies whether the n-text native component should use the opacity of the source material. |

## <a name="TWEEN">altspaceutil.behaviors.TWEEN</a> ([Example](https://github.com/NGenesis/altspacevr-behaviors/blob/master/examples/TWEEN.html))
Provides a convenience wrapper for [tween.js](https://github.com/tweenjs/tween.js/) to manage and update `TWEEN` and `TWEEN.Group` objects.  Refer to the [tween.js user guide](https://github.com/tweenjs/tween.js/blob/master/docs/user_guide.md) for further information.

### Parameters
| Name         | Type        | Default  | Description |
| ------------ | ----------- | -------- | ----------- |
| `tweengroup` | TWEEN.Group | TWEEN    | A tween group to be managed by the behavior.  When ommitted, the global `TWEEN` object will be managed by the behavior. |

## <a name="Billboard">altspaceutil.behaviors.Billboard</a> ([Example](https://github.com/NGenesis/altspacevr-behaviors/blob/master/examples/Billboard.html))
The Billboard behavior updates the orientation of an object to face the camera.

### Parameters
| Name            | Type                                                          | Default  | Description |
| --------------- | ------------------------------------------------------------- | -------- | ----------- |
| `config`        | Object                                                        |          | Optional parameters. |
| `config.target` | [THREE.Object3D](https://threejs.org/docs/#api/core/Object3D) | null     | A target that the object should face.  If omitted, the scene camera will be used. |
| `config.x`      | Boolean                                                       | true     | Specifies whether the X-axis of the object should be reoriented to face the camera. |
| `config.y`      | Boolean                                                       | true     | Specifies whether the Y-axis of the object should be reoriented to face the camera. |
| `config.z`      | Boolean                                                       | true     | Specifies whether the Z-axis of the object should be reoriented to face the camera. |
| `config.native` | Boolean                                                       | true     | Specifies whether a native billboard (n-billboard) component will be used when running the app in the Altspace client. |

## <a name="Text">altspaceutil.behaviors.Text</a> ([Example](https://github.com/NGenesis/altspacevr-behaviors/blob/master/examples/Text.html))
The Text behavior displays a text string using an SDF font, supporting line breaks, text alignment and inline formatting tags.

e.g. `<color=#FFFFFF>The</color> <color="red">quick <#FFFF00>brown <alpha=#33>fox <color=#FFFFFFFF> jumps over the <noparse><alpha=#DD>lazy</noparse> dog.`

### Supported Tags
* `<color=...>Text</color>`
* `<color="name">` - Changes the color of the text using the specified color name. Supported color names are `black`, `blue`, `green`, `orange`, `purple`, `red`, `yellow` or `white`.
* `<color=#RRGGBB>` `<color=#RGB>` `<color=#RRGGBBAA>` `<color=#RGBA>` `<#RRGGBB>` `<#RGB>` `<#RRGGBBAA>` `<#RGBA>` - Changes the color and opacity of text using the specified hexidecimal code.
* `<alpha=#AA>` - Changes the opacity of any text that follows.
* `<b>Text</b>` - Applies a bold effect to the text.
* `<i>Text</i>` - Applies an italic effect to the text.
* `<noparse>Text</noparse>` - Prevents formatting tags from being parsed.

### Parameters
| Name                     | Type    | Default  | Description |
| ------------------------ | ------- | -------- | ----------- |
| `config`                 | Object  |          | Optional parameters. |
| `config.text`            | String  |          | The text to be displayed. |
| `config.fontSize`        | Number  | 10       | The size of the text. |
| `config.width`           | Number  | 10       | The width of the text block to display before text wrapping occurs. |
| `config.height`          | Number  | 1        | The height offset of the text block. |
| `config.horizontalAlign` | String  | middle   | The horizontal alignment of the text block. |
| `config.verticalAlign`   | String  | middle   | The vertical alignment of the text block. |
| `config.native`          | Boolean | true     | Specifies whether a native text (n-text) component will be used when running the app in the Altspace client. |

## <a name="GLTF">altspaceutil.behaviors.GLTF</a> ([Example](https://github.com/NGenesis/altspacevr-behaviors/blob/master/examples/GLTF.html))
The GLTF behavior loads and displays a glTF model asset.

### Parameters
| Name                | Type    | Default | Description |
| ------------------- | ------- | ------- | ----------- |
| `config`            | Object  |         | Optional parameters. |
| `config.url`        | String  |         | A URL to the GLTF model file to be loaded. |
| `config.sceneIndex` | Number  | 0       | Specifies the scene to load when the GLTF model contains multiple scenes. |
| `config.native`     | Boolean | true    | Specifies whether a native glTF (n-gltf) component will be used when running the app in the Altspace client. |

### Members
| Name        | Type    | Description |
| ----------- | ------- | ----------- |
| `loaded`    | Boolean | Indicates whether the sound has been loaded. |

### Methods
### <a name="getBoundingBox">getBoundingBox</a>
Retreives the axis aligned bounding box of the loaded glTF model.

#### Returns
| Type    | Description |
| --------| ----------- |
| Promise | Resolves to a [THREE.Box3](https://threejs.org/docs/#api/math/Box3) representing an axis aligned bounding box of the loaded glTF model. |

### Events
#### <a name="gltf-loaded">gltf-loaded</a>
Fires an event once the glTF model has been loaded.

## <a name="Sound">altspaceutil.behaviors.Sound</a> ([Example](https://github.com/NGenesis/altspacevr-behaviors/blob/master/examples/Sound.html))
The Sound behavior loads and plays a sound asset supporting positional audio.

### Parameters
| Name                  | Type                                                          | Default     | Description |
| --------------------- | ------------------------------------------------------------- | ----------- | ----------- |
| `config`              | Object                                                        |             | Optional parameters. |
| `config.target`       | [THREE.Object3D](https://threejs.org/docs/#api/core/Object3D) |             | A target that will listen for the sound being played.  If omitted, the scene camera will be used. |
| `config.src`          | String                                                        |             | A URL to the sound file to be loaded. |
| `config.res`          | String                                                        |             | A sound resource identifier to be loaded. |
| `config.on`           | String                                                        |             | Name of the event that will trigger the sound to be played. |
| `config.loop`         | Boolean                                                       | false       | Specifies whether the sound should loop back to the beginning once playback has finished. |
| `config.autoplay`     | Boolean                                                       | false       | Specifies whether the sound will play automatically when the parent object is loaded into the scene. |
| `config.oneshot`      | Boolean                                                       | false       | Specifies whether multiple instances of the sound can be played simultaneously.  Note that one-shot sounds cannot be paused, stopped or seeked into, and instances will clean themselves up automatically when playback has finished. |
| `config.volume`       | Number                                                        | 1           | Volume that the sound should play at. |
| `config.spatialBlend` | Number                                                        | 1           | Specifies how the sound will be perceived spactially, ranging from 0 (2D stereo without panning between left and right sound channels) up to 1 (localized 3D with panning between left and right sound channels). |
| `config.pitch`        | Number                                                        | 1           | The speed and octave adjustment that the sound will play at.  0.5 for half speed at a lower octave, 2 for double speed at a higher octave. |
| `config.minDistance`  | Number                                                        | 1           | The minimum distance that the sound will play at full volume. |
| `config.maxDistance`  | Number                                                        | 12          | The maximum distance that the sound will play before volume reaches silent when a linear/cosine rolloff algorithm is specified, otherwise the volume will stop lowering after the specified distance when a logarithmic rolloff algorithm is specified. |
| `config.rolloff`      | String                                                        | logarithmic | Volume can reach a silent level when a linear/cosine rolloff algorithm is specified, otherwise the volume will stop lowering after the specified distance when a logarithmic rolloff algorithm is specified. |
| `config.native`       | Boolean                                                       | true        | Specifies whether a native sound (n-sound) component will be used when running the app in the Altspace client. |

### Members
| Name        | Type    | Description |
| ----------- | ------- | ----------- |
| `loaded`    | Boolean | Indicates whether the sound has been loaded. |

### Methods
### <a name="play">play</a>
Begins playback of the sound, and emits a [sound-played](#sound-played) event.

### <a name="pause">pause</a>
Pauses playback of the sound at the current position, and emits a [sound-paused](#sound-paused) event.

### <a name="stop">stop</a>
Stops playback of the sound, and emits a [sound-stopped](#sound-stopped) event.

### <a name="seek">seek</a>
Skips playback to a specific time point in the sound.

#### Parameters
| Name  | Type   | Description |
| ----- | -------| ----------- |
| time  | Number | Number of milliseconds from the beginning of the sound to skip playback to. |

### Events
#### <a name="sound-loaded">sound-loaded</a>
Fires an event once the sound has been loaded.

#### <a name="sound-played">sound-played</a>
Fires an event when playback of the sound begins.

#### <a name="sound-paused">sound-paused</a>
Fires an event when playback of the sound is paused.

#### <a name="sound-stopped">sound-stopped</a>
Fires an event when playback of the sound is stopped.

# Classes

## <a name="FullspaceApp">FullspaceApp</a>
Manages the render and update loop and creation of anchor points for a three.js app. This class is not intended to be created directly, but should be retrieved using [altspaceutil.getFullspaceApp](#getFullspaceApp).

### Anchor Points
#### Overview
Anchor points (also referred to as Anchors) are nodes in a scene which can be positioned, rotated and scaled externally by end users using URL parameters passed in when the app is loaded into an enclosure, allowing an app to be customized for any environment layout.

By default, all apps using [altspaceutil.getFullspaceApp](#getFullspaceApp) are provided with a root anchor point which encompasses all objects in the scene.  Additional user-defined anchor points which are transformed relative to the root anchor may also be used to split a scene into seperately customizable parts.
Scene objects should be attached to either the root `anchor` point, or a user-defined anchor point obtained from `anchors` to ensure that apps can be customized by end users as appropriate.

#### Example Usage
Imagine a concert environment app containing a skybox, a stage for performers and a seating area for an audience, where each part of the scene can be arranged independently of each other.

`https://example.com/concertapp/index.html`
```javascript
altspaceutil.getFullspaceApp(app => {
	app.anchor.add(skyboxModel);
	app.anchors('performerstage').add(concertStageModel);
	app.anchors('audiencestand').add(audienceStandModel);
});
```

`https://path/to/manifest.json`
```javascript
{
	"enclosure": {
		"position": { "x": 0, "y": 0, "z": 0 }, "rotation": { "x": 0, "y": 0, "z": 0 }, "scale": { "x": 1, "y": 1, "z": 1 }
	},
	"anchors": [
		{ "name": "performerstage", "position": { "x": 5, "y": 0, "z": -3 }, "rotation": { "x": 0, "y": 0, "z": 0 }, "scale": { "x": 2, "y": 0.5, "z": 3 } },
		{ "name": "audiencestand", "position": { "x": 1, "y": 0, "z": 0 }, "rotation": { "x": 0, "y": 0, "z": 0 }, "scale": { "x": 1, "y": 1, "z": 1 } }
	]
}
```

Manifest file example: `https://example.com/concertapp/index.html?altvr.manifest=https://path/to/manifest.json`

Anchors can be customized without a manifest file with URL parameters: `https://example.com/concertapp/index.html?altvr.enclosure.position=0,0,0&altvr.enclosure.rotation=0,0,0&altvr.anchors.performerstage.position=5,0,-3&altvr.anchors.performerstage.scale=2,0.5,3&altvr.anchors.audiencestand.position=1,0,0`

URL parameters can also be used to override a manifest file: `https://example.com/concertapp/index.html?altvr.manifest=https://path/to/manifest.json&altvr.enclosure.scale=0.1&altvr.anchors.performerstage.position=4,0,-2&altvr.anchors.performerstage.scale=1,0.6,4&altvr.anchors.audiencestand.position=2,0,0`

### Members
| Name        | Type                                                                                            | Description |
| ----------- | ----------------------------------------------------------------------------------------------- | ----------- |
| `scene`     | [THREE.Scene](https://threejs.org/docs/#api/scenes/Scene)                                       | The scene associated with the app. |
| `renderer`  | [AltRenderer](https://altspacevr.github.io/AltspaceSDK/doc/js/module-altspace-AltRenderer.html) | The renderer associated with the app. |
| `camera`    | [THREE.Camera](https://threejs.org/docs/#api/cameras/Camera)                                    | The camera associated with the app. |
| `anchor`    | [THREE.Group](https://threejs.org/docs/#api/objects/Group)                                      | The root anchor associated with the app.  The root anchor can have its transform specified using the `altvr.enclosure.position`, `altvr.enclosure.rotation` and `altvr.enclosure.scale` URL parameters, or a manifest file referenced using the `altvr.manifest` URL parameter. |
| `enclosure` | [Enclosure](https://altspacevr.github.io/AltspaceSDK/doc/js/module-altspace-Enclosure.html)     | The enclosure associated with the app. |
| `space`     | [Space](https://altspacevr.github.io/AltspaceSDK/doc/js/module-altspace.html#~Space)            | The space associated with the app. |

### Methods
### <a name="FullspaceApp.anchors">anchors</a>
Retrieves an anchor point with the specified name.  If the anchor point does not exist, it will be created automatically. The anchor can have its transform specified using the `altvr.anchors.[name].position`, `altvr.anchors.[name].rotation` and `altvr.anchors.[name].scale` URL parameters, or a manifest file referenced using the `altvr.manifest` URL parameter.

#### Parameters
| Name   | Type   | Description |
| ------ | ------ | ----------- |
| `name` | String | Name of the anchor. |

#### Returns
| Type                                                       | Description |
| ---------------------------------------------------------- | ----------- |
| [THREE.Group](https://threejs.org/docs/#api/objects/Group) | An anchor with the specified name. |

# A-Frame Components
## <a name="altspace-transform-controls">altspace-transform-controls</a> ([Example](https://github.com/NGenesis/altspacevr-behaviors/blob/master/examples/aframe/altspace-transform-controls.html))
Enables an object's position, rotation and scale to be manipulated in AltspaceVR using a draggable transform gizmo.

### Properties

| Name                      | Type     | Default | Description |
| ------------------------- | -------- | ------- | ----------- |
| `control-type`            | String   | none    | The default control type to be selected.  Supported control types are `none`, `position`, `rotate` or `scale`. |
| `show-buttons`            | Boolean  | false   | Specifies whether buttons should be displayed to toggle between control types. |
| `follow-target`           | Boolean  | true    | Specified whether the transform gizmo should follow the object that is being manipulated. |
| `target`                  | Selector | null    | The target that the transform gizmo should manipulate when interacted with.  If omitted, the object that the behavior is associated with will be used as the target. |
| `scale`                   | Number   | 1       | Adjusts the scale of the transform gizmo. |
| `allow-negative-scale`    | Boolean  | false   | Specifies whether the scale transform gizmo will allow the target's scale to be negative. |
| `sync-events`             | Boolean  | true    | Specifies whether the sync ownership is gained when drag events are fired.  Requires `sync` and `sync-transform` components be present on the target object. |
| `position-axis-lock`      | String   | xyz     | Specifies which axes of the position gizmo can be displayed and manipulated. |
| `rotate-axis-lock`        | String   | xyz     | Specifies which axes of the rotate gizmo can be displayed and manipulated. |
| `scale-axis-lock`         | String   | xyz     | Specifies which axes of the scale gizmo can be displayed and manipulated. |
| `disable-colliders`       | Boolean  | true    | Specifies whether colliders on the target object should be disabled. |
| `disable-child-colliders` | Boolean  | true    | Specifies whether colliders on the target's children should be disabled. |

## <a name="n-text-material">n-text-material</a> ([Example](https://github.com/NGenesis/altspacevr-behaviors/blob/master/examples/aframe/n-text-material.html))
Updates the color and opacity of a [n-text](https://altspacevr.github.io/AltspaceSDK/doc/aframe/module-altspace_components.n-text.html) native component using a material source.

### Properties

| Name       | Type     | Default | Description |
| ---------- | -------- | ------- | ----------- |
| `material` | Selector |         | A reference to the object whose material properties will be applied to the n-text native component.  Defaults to material of the object the component is attached to. |
| `color`    | Boolean  | true    | Specifies whether the n-text native component should use the color of the source material. |
| `opacity`  | Boolean  | true    | Specifies whether the n-text native component should use the opacity of the source material. |

# Resources
* [Three.js API for AltspaceVR](https://altspacevr.github.io/AltspaceSDK/doc/js/)
* [A-Frame API for AltspaceVR](https://altspacevr.github.io/AltspaceSDK/doc/aframe/)
* [AltspaceVR Native Resources](https://altspacevr.github.io/AltspaceSDK/doc/aframe/module-altspace_resources.html)
* [TextMesh Pro Documentation](http://digitalnativestudios.com/textmeshpro/docs/rich-text/)
