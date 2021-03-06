# Panorama全景

## 实现

### DeviceMotionAndOribitControls.js
利用 [DeviceMotionEvent](https://developer.mozilla.org/en-US/docs/Web/API/DeviceMotionEvent) 的 [DeviceMotionEvent.rotationRate](https://developer.mozilla.org/en-US/docs/Web/API/DeviceMotionEvent/rotationRate) ，加上 Touch交互。


### DeviceOrientAndOribitControls.js
基于 [OrbitControls](https://threejs.org/docs/index.html#examples/controls/OrbitControls) ，加上 [DeviceOrientation](https://developer.mozilla.org/zh-CN/docs/Web/Events/deviceorientation) ，但是目前存在问题万向节死锁（待解决）。

### DeviceOrientationControls.js  + [Photo Sphere Viewer](https://github.com/mistic100/Photo-Sphere-Viewer)

利用 `DeviceOrientationControls.js` 完成陀螺仪转动 `Photo Sphere Viewer` 完成touch交互(但是无法上下交互) [demo](https://csgo.wanmei.com/csgoanniversay/) 


## 方法

- div + Css3 实现
  - 图片是围成了一个圆筒  参考 http://show.im20.com.cn/zwj/   http://shrek.imdevsh.com/demo/kfc/
  - 图片是分为了6张组成一个球 参考 https://threejs.org/examples/?q=pano#css3d_panorama_deviceorientation 
- Canvas Webgl 参考 https://threejs.org/examples/?q=pano#canvas_geometry_panorama

## 技术要点
> 重力传感器和方向传感器都是派生传感器。重力传感器基于加速度传感器；方向传感器主要基于陀螺仪和磁力计，但主要还是基于陀螺仪。
>

- [Three.js: rotate camera with both touch and device orientation](https://stackoverflow.com/questions/35283320/three-js-rotate-camera-with-both-touch-and-device-orientation) 
- [OrbitControls and DeviceOrientationControls](https://github.com/mrdoob/three.js/issues/9047)
- [欧拉角](https://www.zhihu.com/question/47736315)
- [Coordinate Systems in Two and Three Dimensions](https://math.oregonstate.edu/home/programs/undergrad/CalculusQuestStudyGuides/vcalc/coord/coord.html)
- [设备屏幕方向与运动](https://developers.google.com/web/fundamentals/native-hardware/device-orientation/#rotation-data)
- [制作全景图教程](http://vr.sina.com.cn/news/js/2017-08-18/doc-ifykcppx9208605.shtml)

  - Ps 3D图层

  - Ps 2D图层，利用Ps插件 [Flexify2](http://www.flamingpear.com/flexify-2.html) 转为全景图


## JS插件：

- Threejs 全景参考 中 https://threejs.org/examples/?q=panorama

  - [css3d-engine](https://github.com/shrekshrek/css3d-engine) Threejs的3D核心类库
  - [DeviceOrientationControls解析](https://juejin.im/entry/5933ce66a22b9d0058e381b0) Threejs的DeviceOrientationControls

- [Pannellum](https://pannellum.org/)


## 工具

- 3D建模软件 [blender](https://www.blender.org/thanks/) Maya

- 在线建模 [three.js / editor](https://threejs.org/editor/) [ThreeFab](http://blackjk3.github.io/threefab/)


## 实测

[**Canvas渲染**](https://threejs.org/docs/#examples/renderers/CanvasRenderer)，即`new THREE.CanvasRenderer();` ，利用 Canvas 2D Api。**手机端**效果极其不好，iphone6s fps不到10。

[**WebGL渲染**](https://threejs.org/docs/#api/renderers/WebGLRenderer)，即`new THREE.WebGLRenderer();`，利用 GPU渲染的着色器。**手机端**性能不错，iphone6s fps30-60，无明显卡顿。

[**CSS3 3D渲染**](https://threejs.org/docs/#examples/renderers/CSS3DRenderer)，即`new THREE.CSS3DRenderer();`，利用 CSS3 3d transform，同样利用GPU加速。**手机端**效果不错，iphone6s fps60，流畅。



## 参考

[高冷的WebGL](https://juejin.im/entry/591d0b4d128fe1005cf6d90b)

[threeVR](https://github.com/richtr/threeVR)

[3D图形:矩阵、欧拉角、四元数与方位的故事](https://www.jianshu.com/p/7a114062866e)

[Web方向传感器的正确使用姿势](http://dtysky.moe/article/Skill-2018_06_25_a)