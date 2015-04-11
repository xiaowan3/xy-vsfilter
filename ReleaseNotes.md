# XySubFilter 3.1.0.705 Beta2 #

Released: 2014-12-07

## Features & Changes ##

  * Support Yasm 1.3.0

  * Query the EVR Presenter for ISubRenderConsumer (Pull Request #10)

  * Update Boost & UnRAR Libraries (Pull Request #12)

## Bug Fix ##

  * Fix override tag argument splitting (Pull Request #11)

  * Add ISubRenderFrame to NonDelegatingQueryInterface

  * Certain PGS subtitles display an opaque background instead of transparent.

  * Avoid loading .sub as MicroDVD text when VOBSUB .idx present

  * Revert Insane Border Support (temporary crash fix)

<br>
Commit: caded623f9a801dbbf76eee3cf30bac6b8544fd0<br>
<hr />
<br>

<h1>xy-VSFilter 3.0.0.306 Stable</h1>

Released: 2014-12-06<br>
<br>
<h2>Features & Changes</h2>

<ul><li>Update Cache defaults (LV1 256->2048, LV4 512->768)</li></ul>

<ul><li>Parser optimizations</li></ul>

<ul><li>Support Yasm 1.3.0</li></ul>

<ul><li>Update Boost & UnRAR Libraries (Pull Request #12)</li></ul>

<ul><li>Support for building with Visual Studio 2012/2013</li></ul>

<ul><li>Static UnRAR support</li></ul>

<ul><li>Interlaced video: Pass-through dwTypeSpecificFlags and dwInterlaceFlags</li></ul>

<ul><li>Pass-through dwControlFlags and actually use colorimetry information</li></ul>

<ul><li>Update CSRI name (vsfilter_textsub -> xy-vsfilter_textsub)</li></ul>

<ul><li>Update Blacklist</li></ul>

<h2>Bug Fix</h2>

<ul><li>Fix override tag argument splitting (Pull Request #11)</li></ul>

<ul><li>PGS palette was incorrectly parsed</li></ul>

<ul><li>Certain PGS subtitles display an opaque background instead of transparent.</li></ul>

<ul><li>Unable to load subtitle files with uppercase file extension</li></ul>

<ul><li>Correct a parser check which broke loading of script embedded UUE fonts</li></ul>

<ul><li>Support U+10000-U+10FFFF UTF-8 encoded character</li></ul>

<ul><li>Improve handling of UTF-8 subtitles with BOM</li></ul>

<ul><li>'YCbCr Matrix = None' used incorrect matrix</li></ul>

<ul><li>WrapStyle 3</li></ul>

<ul><li>Various pin and colorspace connection logic issues</li></ul>

<ul><li>Corruption with extremely large border sizes</li></ul>

<ul><li>VOBSUB with overlapping timestamps</li></ul>

<ul><li>VOBSUB custom palette in MKV</li></ul>

<ul><li>CSRI & SSF color type was incorrect</li></ul>

<br>
Commit: 9a214501a4ffc959abed93fa71130a735cece189d<br>
<hr />
<br>

<h1>XySubFilter 3.1.0.697 Beta2</h1>

Released: 2014-04-29<br>
<br>
<h2>Features & Changes</h2>

<ul><li>Update Cache defaults (LV1 256->2048, LV4 512->768)</li></ul>

<ul><li>Disable /arch:SSE2 in VS2012/VS2013 builds</li></ul>

<h2>Bug Fix</h2>

<ul><li>Unable to load subtitle files with uppercase file extension</li></ul>

<ul><li>Correct a parser check which broke loading of script embedded UUE fonts</li></ul>

<ul><li>Revert Insane Border Support (temporary crash fix)</li></ul>

<br>
Commit: 29f47e612b6df07418523c928bd8c5d025e0724d<br>
<hr />
<br>

<h1>XySubFilter 3.1.0.682 Beta2</h1>

Released: 2014-03-04<br>
<br>
<h2>Features & Changes</h2>

<ul><li>Static Unrar support</li></ul>

<ul><li>Maximum cache size limiter<br>
<ul><li>Defaults to 512MB on 32bit, 1/4 Physical RAM on 64bit</li></ul></li></ul>

<ul><li>Autoload Helper for external subtitles</li></ul>

<ul><li>Style Editor: Support floating point Border & Shadow values</li></ul>

<ul><li>Initial implementation for rendering subtitles outside the video frame<br>
<ul><li>Requires Consumer support</li></ul></li></ul>

<ul><li>SourceFilter/Splitter whitelist moved to registry key</li></ul>

<ul><li>Removed legacy PAR compensation function<br>
<ul><li>Superseded by 'Use AR Adjusted Video Size'</li></ul></li></ul>

<ul><li>Removed connected YCbCr Matrix from filter name</li></ul>

<ul><li>Removed legacy function for changing playback speed</li></ul>

<ul><li>Support for building with Visual Studio 2013</li></ul>

<h2>Bug Fix</h2>

<ul><li>Subpixel gaps visible between the main glyph and the border<br>
<ul><li>Certain limitations</li></ul></li></ul>

<ul><li>Crash when resizing to certain window sizes</li></ul>

<ul><li>Unexpected slowdown 30 seconds after intense subtitles</li></ul>

<ul><li>Improve handling of empty VobSub frames</li></ul>

<ul><li>Double-clicking Tray doesn't open Properties Page on the same monitor it is called from</li></ul>

<ul><li>Subtitle were rendered at FPS value reported by Consumer, even when incorrect</li></ul>

<ul><li>Corruption with extremely large border sizes</li></ul>

<ul><li>CPU loop after external subtitle modification</li></ul>

<ul><li>Improve style override logic</li></ul>

<ul><li>Allow connection to Consumer even if values provided are invalid</li></ul>

<ul><li>Various stability fixes</li></ul>

<br>
Commit: 662950690c4ca30d92a021b230f2b5aef94febca<br>
<hr />
<br>

<h1>XySubFilter 3.1.0.546 Beta</h1>

Released: 2013-07-18<br>
<br>
<h2>Performance</h2>

<ul><li>New SSE code for ARGB packed format</li></ul>

<h2>Features & Changes</h2>

<ul><li>Version number bumped from 3.0.0 to 3.1.0</li></ul>

<ul><li>Implement Subtitle Provider for SubRenderIntf.h subtitle interface version 1.0.6<br>
<ul><li>XySubFilter requires a Subtitle Consumer to function<br>
</li><li>At release time, madVR 0.86.9+ is the only compatible Subtitle Consumer available</li></ul></li></ul>

<ul><li>Scale and render text subtitles to the native resolution of the Subtitle Consumer's output window<br>
<ul><li>allows high resolution subtitles, desktop resolution rendering, etc.</li></ul></li></ul>

<ul><li>Modified icon for XySubFilter</li></ul>

<ul><li>Override Placement is now enabled for VOBSUB only</li></ul>

<ul><li>New Style Override Dialog<br>
<ul><li>Allows individual modifications to each style in a script</li></ul></li></ul>

<ul><li>Force Default Style<br>
<ul><li>Replace all base styles in a script with a single Global Default Style<br>
</li><li>Inline style override tags are left intact</li></ul></li></ul>

<ul><li>More readable registry settings</li></ul>

<ul><li>Render to Original Video Size (non-default option)<br>
<ul><li>Disables scale function allowing madVR to blend subtitles prior to video scaling<br>
</li><li>Output resolution identical to VSFilter.dll</li></ul></li></ul>

<ul><li>AR Adjusted Layout (non-default option)<br>
<ul><li>Enable for anamorphic video scripts which were not compensated for VSFilter.dll behavior</li></ul></li></ul>

<ul><li>Support TV range RGB output for text and bitmap subtitles<br>
<ul><li>When requested by Subtitle Consumer</li></ul></li></ul>

<ul><li>Internal RGB color correction for TV.601 YCbCr Matrix script -> TV.709 video<br>
<ul><li>Other color correction combinations are handled by madVR</li></ul></li></ul>

<ul><li>External support for PGS/HDMV subtitles</li></ul>

<ul><li>Increased verbosity for logging builds</li></ul>

<ul><li>Make the ms part of SRT timecodes optional.</li></ul>

<ul><li>Support MicroDVD tags with MPL2</li></ul>

<ul><li>XySubFilter presently only supports building with Visual Studio 2010<br>
<ul><li>Official support for other compliers will come at a later date</li></ul></li></ul>

<h2>Bug Fix</h2>

<ul><li>"YCbCr Matrix = None" used incorrect matrix</li></ul>

<ul><li>Support U+10000-U+10FFFF UTF-8 encoded character</li></ul>

<ul><li>Improve handling of UTF-8 subtitles with BOM</li></ul>

<ul><li>Allow display of overlapping VOBSUB lines</li></ul>

<ul><li>Fix a potential crash when reopening a file as text</li></ul>

<ul><li>Fixed some potential memory leaks</li></ul>

<ul><li>Fixed handling of WrapStyle 3</li></ul>

<ul><li>PGS palette was incorrectly parsed</li></ul>

<ul><li>Fix a crash with some DVB subtitles streams</li></ul>

<ul><li>Simplify DVB palette parsing</li></ul>

<ul><li>Fix DVB subtitles timing when buffering is enabled</li></ul>

<ul><li>Improve DVB parsing: some subtitles could have been missing</li></ul>

<br>
Commit: 1a1e77b212b8d67fc4c5b92196bcb25a04ac9657<br>
<hr />
<br>

<h1>xy-VSFilter 3.0.0.211 Stable</h1>

Released: 2012-11-20<br>
<br>
<h2>Performance</h2>

<ul><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#95'>Issue #95</a> : Introduce new algorithm to improve the performance and quality of Border rendering.</li></ul>

<ul><li>Replaced fixed-point integer Gaussian Blur with a faster floating-point implementation.<br>
<ul><li>Significant quality and performance improvement with large \blur values.</li></ul></li></ul>

<ul><li>Transform code re-written for better performance</li></ul>

<ul><li>Bitmap cache for SSA/ASS subtitles</li></ul>

<ul><li>Increased the default size of the ASS Tag cache</li></ul>

<ul><li>Increased the subtitle parsing buffer to 90 seconds</li></ul>

<h2>Features & Changes</h2>

<ul><li>AYUV 4:4:4 input/output support<br>
<ul><li>Disable AYUV in your decoder if using EVR</li></ul></li></ul>

<ul><li>Merged UTF-8 detection for .txt subtitles from MPC-HC project</li></ul>

<ul><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#124'>Issue #124</a> : Improved external subtitle ordering<br>
<ul><li>Priority is now given to identical filenames</li></ul></li></ul>

<ul><li>LOAD_EXT_LIST added to registry to control allowed external subtitle types for auto-loading</li></ul>

<ul><li>PGS_COLOR_TYPE added to registry to control PGS YCbCr->RGB matrix and levels conversion<br>
<ul><li>Defaults to TV YCbCr -> PC RGB levels & YCbCr matrix guessed based on resolution</li></ul></li></ul>

<ul><li>Minor script parsing adjustments to transform and alpha tags</li></ul>

<ul><li>Removed screensaver prevention feature<br>
<ul><li>This is a job for players not for filters</li></ul></li></ul>

<ul><li>Function for scaling layout resolution (Renderer Layout Option)<br>
<ul><li>Use Original Video = VSFilter Default Behavior (for accurate typesetting on original videos)<br>
</li><li>Customize = Layout Debug Mode (read <a href='http://code.google.com/p/xy-vsfilter/issues/detail?id=97#c10'>Issue #97</a> for details)</li></ul></li></ul>

<ul><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#72'>Issue #72</a> : x64 build support</li></ul>

<ul><li>Visual Studio 2012 build support</li></ul>

<ul><li>Bundle unrar.dll/unrar64.dll with installer</li></ul>


<h2>Bug Fix</h2>

<ul><li>Caching error when \p<code>&lt;scale&gt;</code> drawing commands use different <code>&lt;scale&gt;</code> factors on a single layer</li></ul>

<ul><li>Shadow not rendered with small border strength (<0.0625)</li></ul>

<ul><li>Potential bug with \kt</li></ul>

<ul><li>Swapped UV color palette with PGS & DVB subtitles</li></ul>

<ul><li>Incorrect level range with PGS & DVB subtitles</li></ul>

<ul><li>Incorrect YCbCr matrix with PGS subtitles</li></ul>

<ul><li>Heap corruption due to unbounded dirty rectangle with PGS & DVB</li></ul>

<ul><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#112'>Issue #112</a> : Merged latest PGS & DVB subtitle code from MPC-HC project<br>
<ul><li>Support for multi-line PGS subtitles<br>
</li><li>Fixed broken DVB subtitles<br>
</li><li>Various other improvements</li></ul></li></ul>

<ul><li>Merged "VSFilter might not load when using the overlay mixer." commit from MPC-HC project</li></ul>

<h3>Bug Fixes (for issues which only affected test builds 3.0.0.111 through 3.0.0.144)</h3>

<ul><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#116'>Issue #116</a> : Fix corruption bug with 8x8 bilinear sub-pixel positioning option</li></ul>

<ul><li>Unable to hide VOB/PGS/DVB subtitles</li></ul>

<ul><li>Semi-transparent box was occasionally visible around subtitles<br>
<br>
Commit: 48eeccaf9243329451235826d5cc06a0712d1596<br>
<hr />
<br>
<h1>xy-VSFilter 3.0.0.144 Test</h1></li></ul>

Released: 2012-08-19<br>
<br>
<h2>Performance</h2>

<ul><li>Replaced fixed-point integer Gaussian Blur with a faster floating-point implementation. Significant improvment with larger \blur values.</li></ul>

<ul><li>Improved caching efficiency. Resolves a performance regression compared to the Stable branch.</li></ul>

<ul><li>Transform code re-written for better performance</li></ul>

<h2>Features & Changes</h2>

<ul><li>Added C code path to the Beta branch for CPUs which don't support SSE2.</li></ul>

<ul><li>CPU Runtime Detection for Beta branch. SSE2 code path is enabled at runtime only when supported.</li></ul>

<h2>Bug Fix</h2>

<ul><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#113'>Issue #113</a>: Scroll Effect Crash</li></ul>

<ul><li>Fixed crash when \clip runs out of video frame</li></ul>

<h2>Known Issues</h2>

<ul><li>This build is a work-in-progress, for beta testing purposes only. Please report any bugs and performance regressions to our issue tracker: <a href='http://code.google.com/p/xy-vsfilter/issues/entry'>http://code.google.com/p/xy-vsfilter/issues/entry</a>
<br>
Commit: bac768e02081317ae17cf19e496ca3a3a1e5f7af<br>
<hr />
<br>
<h1>xy-VSFilter 3.0.0.65 Bug Fix</h1></li></ul>

Released: 2012-08-19<br>
<br>
<h2>Bug Fix</h2>

<ul><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#113'>Issue #113</a>: Scroll Effect Crash</li></ul>

<ul><li>Fixed crash when \clip runs out of video frame</li></ul>

<br>
Commit: 6a29b75ba86bbe57ddaaca57f6d464c3d8d64636<br>
<hr />
<br>
<h1>xy-VSFilter 3.0.0.63 Stable</h1>

Released: 2012-07-26<br>
<br>
<h2>Features & Changes</h2>

<ul><li>New C code path for CPUs which don't support SSE2. Minimum requirements have been reduced to CPUs with MMX support.</li></ul>

<ul><li>CPU Runtime Detection. SSE2 code path is enabled at runtime only when supported.</li></ul>

<h2>Bug Fix</h2>

<ul><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#106'>Issue #106</a>: Broken YUY2 Output<br>
<br>
Commit: 01713751b7a2d614e8a46d158717d7d40f0696eb<br>
<hr />
<br>
<h1>xy-VSFilter 3.0.0.112 Test</h1></li></ul>

Released: 2012-07-26<br>
<br>
<h2>Bug Fix</h2>

<ul><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#106'>Issue #106</a>: Broken YUY2 Output</li></ul>

<ul><li>Checking or Unchecking a format on the Colors tab and clicking OK/Apply, changes YCbCr Matrix from Auto -> BT.601 on next launch.</li></ul>


<h2>Known Issues</h2>

<ul><li>Requires a CPU with SSE2 support.</li></ul>

<ul><li>This build is a work-in-progress, for beta testing purposes only. Please report any bugs and performance regressions to our issue tracker: <a href='http://code.google.com/p/xy-vsfilter/issues/entry'>http://code.google.com/p/xy-vsfilter/issues/entry</a>
<br>
Commit: 875f9db146e68415e7bede1853c832e56fe7029e<br>
<hr />
<br>
<h1>xy-VSFilter 3.0.0.111 Test</h1></li></ul>

Released: 2012-07-17<br>
<br>
<h2>Performance</h2>

<ul><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#95'>Issue #95</a>: Introduce new algorithm to improve the performance and quality of Border rendering. Up to 12x higher minimum & average fps when rendering large border sizes compared to VSFilter 2.39/2.41.</li></ul>

<h2>Features & Changes</h2>

<ul><li>Introduce an experimental Bitmap cache for SSA/ASS subtitles<br>
</li><li>Initial commits to prepare for implementation of xy-VSFilter's new subtitle interface, <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#91'>Issue #91</a></li></ul>


<h2>Bug Fix</h2>

<ul><li>Crash in 3.0.0.111 (git 3aafdc9) when \xbord0 is used with \ybord value >0</li></ul>


<h2>Known Issues</h2>

<ul><li><a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#106'>Issue #106</a>: Broken YUY2 Output</li></ul>

<ul><li>Checking or Unchecking a format on the Colors tab and clicking OK/Apply, changes YCbCr Matrix from Auto -> BT.601 on next launch.</li></ul>

<ul><li>This build is a work-in-progress, for beta testing purposes only. Please report any bugs and performance regressions to our issue tracker: <a href='http://code.google.com/p/xy-vsfilter/issues/entry'>http://code.google.com/p/xy-vsfilter/issues/entry</a>
<br>
Commit: 742a9b175afb4412dd0688e023cfdb4d84cc4e32<br>
<hr />
<br>
<h1>xy-VSFilter 3.0.0.53 Stable</h1></li></ul>

Released: 2012-07-15<br>
<br>
<h2>Performance</h2>

<ul><li>Increased the size of Clipper cache from 8 to 48 to improve cache hits</li></ul>


<h2>Features & Changes</h2>

<ul><li>xy-VSFilter now uses <i>'correct'</i> MPEG-2/H.264 left chroma placement, unlike VSFilter 2.39/2.41 which uses <i>'incorrect'</i> MPEG-1 center chroma placement. This should eliminate the problem of chroma bleeding and misaligned chroma which plagued VSFilter for years. As side-effects, perceived sharpness and quality after upscaling should also be improved slightly.</li></ul>

<ul><li>Support non-integer values of \fscx \fscy. Fixes yet another longstanding VSFilter limitation. We highly recommend typesetters make use this increased precision for future scripts, and migrate away from the Libass breaking workaround of scaling tiny font sizes with insane values of \fscx \fscy when \fax \fay are also being used.</li></ul>

<h2>Bug Fix</h2>

<ul><li>Sub-pixel positioning for the CSRI API was inadvertently set to NONE when it should have been 8x8.</li></ul>

<h2>Known Issues</h2>

<ul><li><a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#106'>Issue #106</a>: Broken YUY2 Output<br>
<br>
Commit: 9db6bc07b89148dd1c406cacc688fb626895c20e<br>
<hr />
<br>
<h1>xy-VSFilter 3.0.0.42 Bug Fix</h1></li></ul>

Released: 2012-06-23<br>
<br>
<h2>Bug Fix</h2>

<ul><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#102'>Issue #102</a>: Corruption resulting from draw border routine running when not needed<br>
<br>
Commit: efecf9a9bd5d8e706f66082ce3719b04069fe6b8<br>
<hr />
<br>
<h1>xy-VSFilter 3.0.0.41 Stable</h1></li></ul>

Released: 2012-06-20<br>
<br>
<h2>Performance</h2>

<ul><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#94'>Issue #94</a>: High memory consumption with \clip gradients<br>
</li><li>Refactored Cache stack and introduced three new Caches</li></ul>

<h2>Features & Changes</h2>

<ul><li>Support sub-pixel drawing of vector shapes. <font size='1'><i><b>WARNING:</b> Unsafe to use outside of hardsubbing. VSFilter 2.39 will crash. VSFilter 2.40 & 2.41 silently fails.</i></font></li></ul>

<ul><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#92'>Issue #92</a>: Added option to hide tray icon</li></ul>

<ul><li>Auto-versioning support. <font size='1'><i>Requires using build_vsfilter.sh when compiling xy-VSFilter. Read 'Usage' for advanced build options.</i></font></li></ul>

<ul><li>Include minor version number and GIT commit hash (short SHA1) on xy-VSFilter About tab.</li></ul>

<ul><li>Record version info into registry, to enable better handling of default setting changes.</li></ul>

<ul><li>Support PC level range (0-255) YCbCr subtitle output</li></ul>

<ul><li>Rename 'Auto-Guess' (guess matrix by resolution) to 'Guess'.</li></ul>

<ul><li>Support <code>[Script Info]</code> 'YCbCr Matrix' in ASS scripts. <font size='1'><i>Aegisub 3.0 will add support for tagging 'YCbCr Matrix' based on video bitstream info.</i></font></li></ul>

<ul><li>Add a new default setting 'Auto' for honoring 'YCbCr Matrix' script tagging, with automatic fallback to TV BT.601 for legacy scripts.</li></ul>

<u><i>Supported 'YCbCr Matrix' Values:</i></u>

<code>[Script Info]</code><br>
<code>YCbCr Matrix: TV.601</code><br>
<code>YCbCr Matrix: TV.709</code><br>
<code>YCbCr Matrix: PC.601</code><br>
<code>YCbCr Matrix: PC.709</code><br>
<code>YCbCr Matrix: None</code><br>

'YCbCr Matrix' as well as override settings in the GUI, only have an effect on YCbCr subtitle output. The video is always untouched.<br>
<br>
TV.601 = Output BT.601 with 16-235 YCbCr level range<br>
TV.709 = Output BT.709 with 16-235 YCbCr level range<br>
PC.601 = Output BT.601 with 0-255 YCbCr level range<br>
PC.709 = Output BT.709 with 0-255 YCbCr level range<br>
None = Output BT.601 or BT.709 with 16-235 YCbCr level range based on video resolution<br>
<br>
If 'YCbCr Matrix' is missing from a script, xy-VSFilter will use TV.601 for legacy script compatibility. It is highly recommended to leave the GUI settings at their defaults of Auto | Auto for 'YCbCr level range' | 'YCbCr matrix'. The Auto settings obey the 'YCbCr Matrix' tag (if present), else fallback to TV.601 as decribed above.<br>
<br>
<h2>Bug Fix</h2>

<ul><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#96'>Issue #96</a>: Secondary Color animation effect corruption</li></ul>

<ul><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#98'>Issue #98</a>: Multi-byte to Wide character translation with certain codepages</li></ul>

<ul><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#100'>Issue #100</a>: Crash when drawing sub-pixel value vector shapes (VSFilter 2.39 Bug)</li></ul>

<ul><li>8x8 (bilinear) sub-pixel positioning triggered crashes in xy-VSFilter 3.0.0.40</li></ul>

<h2>Known Issues</h2>

<ul><li><a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#102'>Issue #102</a>: Corruption resulting from draw border routine running when not needed<br>
<br>
Commit: 5936ade2f0a187b9d57ab32660dfd240550c1892<br>
<hr />
<br>
<h1>xy-VSFilter 3.0.0.8 Stable</h1></li></ul>

Released: 2012-04-29<br>
<br>
<h2>Bug Fix</h2>

<ul><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#75'>Issue #75</a>: \iclip animation<br>
</li><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#78'>Issue #78</a>: Multiple instances of simple fade<br>
</li><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#81'>Issue #81</a>: Vector drawing inside text<br>
</li><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#84'>Issue #84</a>: \h tag displays incorrectly with GB2312<br>
</li><li>Purple fringing on some VOBSUBs<br>
<br>
Commit: 734a3d11174ad688a4ef4aabba6c82f58e8f9e2f<br>
<hr />
<br>
<h1>xy-VSFilter 3.0.0.2 Bug Fix</h1></li></ul>

Released: 2012-01-23<br>
<br>
<h2>Features & Changes</h2>

<ul><li>Merge the MPC-HC fixes to reduce Visual Studio 2010 MFC Bloat. Size of VSFilter.dll is now 1.19MB instead of 2.42MB.</li></ul>

<h2>Bug Fix</h2>

<ul><li>Fixed <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#73'>Issue #73</a> & <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#74'>Issue #74</a>: Crash in the parser with unclosed parentheses and invalid use of \t</li></ul>

<br>
Commit: 7a242a92180b32fd22a475fd83befe2f222b1f98<br>
<hr />
<br>
<h1>xy-VSFilter 3.0.0.1 Stable</h1>

Released: 2012-01-08<br>
<br>
<h2>Performance</h2>

<ul><li>Add support for animation detection internally. Significant performance improvement for static typesetting using the \pos tag.</li></ul>

<h2>Features & Changes</h2>

<ul><li>Add xy-VSFilter branding to the resource files</li></ul>

<ul><li>Version number bumped from 2.39.5 to 3.0.0</li></ul>

<ul><li>Begin using incremental version numbers for future builds</li></ul>

<h2>Known Issues</h2>

<ul><li><a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#73'>Issue #73</a> & <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#74'>Issue #74</a>: Crash in the parser with unclosed parentheses and invalid use of \t<br>
<br>
Commit: 139b6d9ae7b0ab49bb66281864116251c57d70cc<br>
<hr />
<br>