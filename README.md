# GPU Mandelbulb Raymarching Benchmark

This project is a WebGL-based GPU benchmark utilizing raymarching of a Mandelbulb fractal. It is optimized for high-performance rendering to stress-test GPU capabilities, independent of display refresh rates.

Based on the original implementation by **cznull@bilibili**.

## Optimizations Implemented

Compared to the original code, the following key optimizations were made to achieve higher performance for benchmarking:

1.  **Unlimited Frame Rate Rendering:** Switched the rendering loop from `window.requestAnimationFrame` to a `MessageChannel`-based microtask scheduling mechanism. This bypasses the browser's typical Vertical Sync (VSync) synchronization, allowing the GPU to render frames as fast as it can complete them. This provides a more accurate measure of raw GPU rendering throughput.

2.  **Simplified Raymarching Surface Detection:** The complex surface intersection solving algorithm in the fragment shader was replaced with a more standard distance estimation threshold check. This significantly reduces the per-pixel computation cost, leading to much higher frame rates.

3.  **Increased Mandelbulb Iterations:** Increased the number of iterations (`ITER`) in the Mandelbulb distance estimation function. This increases the computational load on the GPU and reveals finer details of the fractal, making the benchmark more demanding.

## How to Run

Simply open the `index.html` file in a modern web browser that supports WebGL2.

## Acknowledgements

Original code base by **cznull@bilibili**.

Optimizations contributed by **迷湖浅浅@bilibili**. 
