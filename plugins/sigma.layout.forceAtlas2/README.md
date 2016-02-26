sigma.layout.forceAtlas2
========================

Algorithm by [Mathieu Jacomy](https://github.com/jacomyma).

Plugin by [Guillaume Plique](https://github.com/Yomguithereal).

---

This plugin implements [ForceAtlas2](http://www.plosone.org/article/info%3Adoi%2F10.1371%2Fjournal.pone.0098679), a force-directed layout algorithm.

For optimization purposes, the algorithm's computations are delegated to a web worker.

## Methods

**sigma.forceAtlas2.start**

Starts or unpauses the layout. It is possible to pass a configuration if this is the first time you start the layout.

```js
sigmaInstance.forceAtlas2.start(config);
```

**sigma.forceAtlas2.stop**

Pauses the layout.

```js
sigmaInstance.forceAtlas2.stop();
```

**sigma.forceAtlas2.cooldown**

Gently stops the layout in 30 iterations by default or in a number provided to the function.

```js
// 30 iterations of cooldown
sigmaInstance.forceAtlas2.cooldown();

// 20 iterations of cooldown
sigmaInstance.forceAtlas2.cooldown(20);

// Passing a callback
sigmaInstance.forceAtlas2.cooldown(20, callback);

// Passing only a callback to keep the default 30
sigmaInstance.forceAtlas2.cooldown(callback);
```

**sigma.forceAtlas2.config**

Changes the layout's configuration.

```js
sigmaInstance.forceAtlas2.config(config);
```

**sigma.forceAtlas2.kill**

Completely stops the layout and terminates the assiociated worker. You can still restart it later, but a new worker will have to initialize.

```js
sigmaInstance.forceAtlas2.kill();
```

**sigma.forceAtlas2.running**

Returns whether ForceAtlas2 is running.

```js
sigmaInstance.forceAtlas2.running();
```

**sigma.forceAtlas2.cooling**

Returns whether ForceAtlas2 is in a cooling state.

```js
sigmaInstance.forceAtlas2.cooling();
```

## Configuration

*Algorithm configuration*

* **linLogMode**: *boolean* `false`
* **outboundAttractionDistribution** *boolean* `false`
* **adjustSizes** *boolean* `false`
* **edgeWeightInfluence** *number* `0`
* **scalingRatio** *number* `1`
* **strongGravityMode** *boolean* `false`
* **gravity** *number* `1`
* **barnesHutOptimize** *boolean* `true`: should we use the algorithm's Barnes-Hut to improve repulsion's scalability (`O(n²)` to `O(nlog(n))`)? This is useful for large graph but harmful to small ones.
* **barnesHutTheta** *number* `0.5`
* **slowDown** *number* `1`
* **startingIterations** *integer* `1`: number of iterations to be run before the first render.
* **iterationsPerRender** *integer* `1`: number of iterations to be run before each render.

*Supervisor configuration*

* **worker** *boolean* `true`: should the layout use a web worker?
* **workerUrl** *string* : path to the worker file if needed because your browser does not support blob workers.

## Notes
1. The layout won't stop by itself, so if you want it to stop, you will have to trigger it explicitly.
