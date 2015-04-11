### Want ToDo ###
  * Use sub-sampled UV plan. xy-Vsfilter supports YUV internally. The raterizer can produce a plannar ayuv output. Since chroma subsampling is really widely used technic，full sample UV plan may be not necessary. By using sub-sampled UV plan, 3/8 of the calculations can be saved.

  * NV12 support.

  * Bitmap cache.

  * Subpixel positioning using Lanczos interpolation.

  * DXVA. Still need investigation but it seems really difficult.

  * Uniscribe.

  * Rewrite SSE2 code for YV12 alphablending.
### Once Want ToDo ###
  * Support new tags added in VsfilterMod?.
  * Huge refactor to improve efficiency while animating. In most animated scene, two adjacent subpics differ only in a small area. Currently no matter how little that difference is, renderer has to recreate the whole subpic. Though with the help of cache, a lot redundent caculation is saved. But if the renderer renders the new subpic via updating that small changing area on previous subpic, it would be much faster.
  * Agg (Anti-Grain Geometry). Its [demo](http://www.antigrain.com/demo/index.html) is really cool. But some of its code give me a feeling that it must be really slow and not suitable for realtime rasterization.