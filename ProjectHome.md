# xy-VSFilter - VSFilter Fork for Smooth Playback #
# XySubFilter - High Quality Subtitle Rendering #


---

<p>Based on VSFilter 2.39 Guliverkli2 with various important changes from VSFilter 2.41 MPC-HC</p>
<p><b>Supports and ONLY supports</b> subtitle scripts supported by <b>Official VSFilter 2.39</b> builds, but in a more efficient way.</p>
<p>xy-VSFilter (VSFilter.dll) is the traditional subtitle filter, which connects to a video decoder and renderers at video resolution.</p>
<p>XySubFilter (XySubFilter.dll) is the new high quality subtitle filter which requires a compatible Subtitle Consumer supporting the new subtitle interface. We recommend madVR 0.87.5+ or MPC-HC 1.7.2+ (EVR-CP).</p>


## What Is Different in xy-VSFilter & XySubFilter ##
  * <font size='3'>Significantly faster overall compared to Libass</font>.<br>Up to multiple orders of magnitude faster than VSFilter 2.41<b><br>
<ul><li>High resolution subtitle rendering (XySubFilter only)<br>
</li><li>External support for PGS/HDMV subtitles (XySubFilter only)<br>
</li><li>New Style Override Dialog (XySubFilter only)<br>
</li><li>Force Default Style (XySubFilter only)<br>
</li><li>Support U+10000-U+10FFFF UTF-8 encoded character (XySubFilter only)<br>
</li><li>Subpics are now drawn directly in YUV/RGB as needed to improve performance<br>
<ul><li>Official VSFilter always rendered subtitles in RGB and did a RGB -> YUV conversion when outputting YUV formats<br>
</li></ul></li><li>Floating-point Gaussian Blur implementation (higher quality + significantly faster with large blur values)<br>
</li><li>More efficient Border code (higher quality + up to 12x faster with large border sizes)<br>
</li><li>More efficient Clip code (significantly faster + up to 1.8GB reduction in RAM usage when rendering gradients)<br>
</li><li>More efficient Color Conversion, Chroma Placement, Alpha Blending, and Rasterization code (SSE2 optimized)<br>
</li><li>Alpha blending on dirty areas of the frame only<br>
</li><li>Alpha-blending with sub-sampled/interlaced chroma where applicable<br>
</li><li>Addition of numerous caches to speed up animated effects<br>
</li><li>Proper implementation of animation detection to speed up static typesetting<br>
</li><li>New script parser to speed up loading of very large subtitle scripts<br>
</li><li>75% reduction in CPU load overhead when idle</li></ul></li></ul></b>

<ul><li><b>Input/Output support for 10-bit P010 & 16-bit P016 4:2:0 YUV formats</b>
<ul><li>Requires: P010 or P016 support in both the video renderer <a href='http://forum.doom9.org/showpost.php?p=1271414&postcount=1'>(e.g. madVR)</a> <i>and</i> video decoder to use this optional feature.</li></ul></li></ul>

<ul><li><b>Input/Output support for NV12 & NV21 4:2:0 YUV formats</b>
<ul><li>Important for users of ATI GPUs and EVR-CP</li></ul></li></ul>

<ul><li><b>Input/Output support for AYUV 4:4:4 YUV format</b></li></ul>

<ul><li><b>Sub-pixel Positioning configuration option</b> [None, 2x2, 4x4, 8x8, 8x8(bilinear)]<br>
<ul><li>Official VSFilter defaults to 8x8. New method 8x8(bilinear) offers 8x8 positioning using bilinear scaling instead of rasterization.</li></ul></li></ul>

<ul><li><b>BT.709/BT.601 matrix configuration option for subtitle rendering</b>
<ul><li>Support for 'YCbCr Matrix' tagging in SSA/ASS scripts.<br>
</li><li>Defaults to BT.601 when 'YCbCr Matrix' is not present in the script.</li></ul></li></ul>

<ul><li><b>TV/PC YCbCr level range configuration option for subtitle rendering</b>
<ul><li>Support for 'YCbCr Matrix' tagging in SSA/ASS scripts.<br>
</li><li>Defaults to TV range when 'YCbCr Matrix' is not present in the script.</li></ul></li></ul>

<ul><li><b>Support for sub-pixel drawing of vector shapes.</b>
<ul><li>Warning: Unsafe outside of hardsubbing. VSFilter 2.39 will crash. VSFilter 2.41 won't display anything.</li></ul></li></ul>

<ul><li><b>Support for non-integer values of \fscx \fscy</b></li></ul>

<ul><li><b>Support for <i>'correct'</i> MPEG-2/H.264 left chroma placement for YCbCr output</b>
<ul><li>VSFilter 2.39/2.41 uses <i>'incorrect'</i> MPEG-1 centered chroma placement</li></ul></li></ul>

<ul><li><b>ASS/SSA layout scaling function</b></li></ul>

<ul><li><b>HDMV(PGS) & DVB Subtitle support from VSFilter 2.41</b></li></ul>

<ul><li><b>Correct level range & matrix used with PGS & DVB subtitles</b></li></ul>

<ul><li><b>Option to hide VSFilter tray icon</b></li></ul>

<ul><li>Removed pre-buffer subpics option (may be re-added in the future)<b></li></ul></b>

<h2>Install ##
<p>
<b>Current builds can be found on the <a href='Downloads.md'>Downloads</a> page.</b>


XySubFilter.dll requires a compatible Subtitle Consumer. We recommend madVR 0.86.9 or newer.<br>
<br>
xy-VSFilter 32-bit builds can only be used with 32-bit DirectShow filters and programs (Recommended for most users).<br>
<br>
xy-VSFilter 64-bit builds can only be used with 64-bit DirectShow filters and programs.<br>
<br>
If you have another version of VSFilter currently installed, merely replacing the VSFilter.dll file will <b>NOT</b> work correctly.<br>
<br>
If you didn't use our installer, you <b>MUST</b> run <b><i>regsvr32 VSFilter.dll</i></b> from an Administrative Command Prompt in the directory you extracted VSFilter.dll to reinstall it.<br>
<hr />
For example, if you <i>extracted VSFilter.dll to "C:\Program Files (x86)\xy-VSFilter"</i> (replace this path with the directory of your choice in the command lines below):<br>
<br>
<b>Open an Administrative Command Prompt</b>

<b>cd "C:\Program Files (x86)\xy-VSFilter"</b>

<b>regsvr32 VSFilter.dll</b>


<i>OR</i>


<b>Open an Administrative Command Prompt</b>

<b>regsvr32 "C:\Program Files (x86)\xy-VSFilter\VSFilter.dll"</b>

It is <b>NOT</b> recommended to store VSFilter.dll in your System32 or SystemWOW64 directory. If you have a copy of VSFilter.dll in either of these locations, run <b>regsvr32 /u VSFilter.dll</b> to unregister/uninstall, and then follow the steps above to move and register/install it in a new location.<br>
<hr />

The recommend download(s) will always be <i>Featured</i> on the left column of this page.<br>
<br>
Any builds tagged as <i>test</i> or <i>experimental</i> are for beta-testing only.<br>
<br>
<p>
<b>Media Player Classic Home Cinema (MPC-HC) Users:</b> Update to MPC-HC 1.6.5.6197 or <a href='http://xhmikosr.1f0.de/mpc-hc/'>newer</a>. Confirm <i>Auto-load subtitles</i> is unchecked/disabled under Options->Playback to disable MPC-HC's ISR (internal subtitle renderer).<br>
</p>
<p>
For MPC-HC revisions prior to 1.6.5.6197, both of the following steps are required for xy-VSFilter to be used. Confirm <i>Auto-load subtitles</i> is unchecked/disabled under Options->Playback. Confirm that <i>DirectVobSub (auto-loading version)</i> is set to Prefer in MPC-HC External Filters.<br>
</p>
<p>
<b>madVR Video Renderer Users:</b> Confirm madVR's internal decoders are unchecked/disabled under <i>Edit Settings</i> -> <i>Processing</i> -> <i>Decoding</i>. This is required for xy-VSFilter to be used.<br>
</p>
<p>
<b>Zoom Player Users:</b> An automated xy-VSFilter (VSFilter 3.0) installer is now included as an optional download from the Zoom Player Install Center, starting with the release of Zoom Player 8.1 on January 5th, 2012.<br>
</p>
<p>
<b>CCCP Codec Pack Users:</b> Download and Extract the Featured xy-VSFilter archive (.7z) release, and replace the VSFilter.dll found in the CCCP Filters directory. Open the CCCP Settings application and enable 'Re-register Filters' on the second page and click Apply. This will cause CCCP to silently reinstall VSFilter with regsvr32. If you ever run into problems running xy-VSFilter with CCCP, we recommend you run 'Reset All Settings' from the CCCP Settings application as your first troubleshooting step before reporting a bug.<br>
</p>
<p>
<b>Windows Media Player 12 Users:</b> We recommend installing some basic 32-bit DirectShow Codecs (e.g. LAV Video + LAV Audio + Haali Media Splitter + xy-VSFilter), and setting all 'Preferred Decoders' to 'Use Merit' with Win7DSFilterTweaker.<br>
</p>
<p>
<b>XBMC Users:</b> xy-VSFilter cannot be used with a default XBMC installation. Requires <a href='http://wiki.xbmc.org/index.php?title=DSPlayer'>DSPlayer add-on for XBMC</a>, libsubs.dll deleted from C:\..\XBMC\system\players\dsplayer\ , 'Use System Filters' enabled in DSPlayer Settings, setting all 'Preferred Decoders' to 'Use Merit' with Win7DSFilterTweaker, and having some basic 32-bit DirectShow Codecs installed (e.g. LAV Video + LAV Audio + Haali Media Splitter + xy-VSFilter).<br>
</p>

<h2>Source Code is located at</h2>
<a href='http://repo.or.cz/w/xy_vsfilter.git'>http://repo.or.cz/w/xy_vsfilter.git</a>
<p>
Our developer's ISP in China has blocked him from creating a repository here at code.google.com, so we're using repo.or.cz instead. If repo.or.cz is ever experiencing downtime, you can access a mirror of our repository on <a href='https://github.com/Cyberbeing/xy-VSFilter'>GitHub</a>.<br>
</p>
<h2>Bug Report</h2>
<p>If you ever encounter any issue using this mod, you can open a <a href='http://code.google.com/p/xy-vsfilter/issues/list'>issue</a> here</p>
<p>OR contact me via email yuzhuohuang@qq.com</p>
<p> I'll try to fix it.</p>
<h2>Troubleshooting Q&A</h2>
<hr />
<b>Q:</b> Why do I get a crash whenever I open xy-VSFilter's property page?<br>
<br>
<b>A:</b> You've forgotten to register VSFilter.dll. Please re-read the Install instructions above.<br>
<hr />
<b>Q:</b> Which operating systems are supported by xy-VSFilter?<br>
<br>
<b>Q:</b> Which CPU instruction sets are required by xy-VSFilter?<br>
<br>
<b>A:</b> Supports 32-bit (x86) & 64-bit (x64) versions of Windows XP SP2/SP3, Windows Vista, Windows 7, Windows 8, and Windows Server variants. Minimum requirement is a CPU with MMX support. Recommended requirement is a CPU with SSE2 support.<br>
<hr />
<b>Q:</b> I use MPC-HC, why are subtitles not displayed or flicker?<br>
<br>
<b>A:</b> xy-VSFilter is not being used. Please check the following common issues:<br>
<br>
Make sure you've run regsvr32 on VSFilter.dll as described in the <b>Install</b> section above.<br>
<br>
If using MPC-HC, go into Options->Playback and confirm <i>Auto-load subtitles</i> is unchecked/disabled. If you're running an MPC-HC revision prior to 1.6.5.6197 on Windows Vista, Windows 7, or Windows 8, you'll also need to confirm that <i>DirectVobSub (auto-loading version)</i> is set to Prefer in MPC-HC External Filters. It is not recommended to add normal <i>DirectVobSub</i> to external filters, as that will force xy-VSFilter to always be loaded, even when no subtitles exist, and can conflict with the MPC-HC ISR.<br>
<br>
For first-time users of madVR, you'll need disable the built-in madVR decoders, which are enabled by default, in order to use VSFilter. When a video is playing in MPC-HC, right-click the video window, Filters -> madVR Renderer -> Edit Settings -> Processing -> Decoding. Uncheck all three boxes in this section and click OK.<br>
<br>
<b>A:</b> The subtitle script contains invalid SSA/ASS alpha tag syntax, see <a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=#80'>Issue #80</a> (fix your script)<br>
<br>
At this point in time, we consider this behavior an undocumented feature of VSFilter 2.39 and prior, and not a bug.<br>
<br>
<hr />
<b>Q:</b> I installed xy-VSFilter on my Windows Vista, Windows 7, or Windows 8 computer, but why is my performance still poor?<br>
<br>
<b>Q:</b> Why was my performance with xy-VSFilter significantly degraded after doing a clean install/re-install/upgrade of Windows?<br>
<br>
<b>A:</b> Navigate to Control Panel -> Power Options, set your power plan to "High Performance". If performance improves drastically, you have an incompatibility between your motherboard and Windows which is causing your CPU clock speed to be throttled improperly. If performance doesn't improve, your computer is either too weak, or you have some other kind of hardware/software issue.<br>
<br>
<hr />
<b>Q:</b> I use the EVR or VMR9 video renderer, why is my picture 'messed up' after upgrading VSFilter to xy-VSFilter?<br>
<br>
<b>A:</b> This is not a xy-VSFilter issue. First thing first, I'd recommend making sure your <a href='http://www.microsoft.com/en-us/download/details.aspx?id=35'>DirectX Runtimes</a> and GPU driver are up-to-date. Though most likely what you are seeing is the result of your GPU's driver based video post-processing, which is now active since xy-VSFilter supports NV12. Go into your GPU's control panel and make sure everything classified under Video is disabled, set to 0%, or video player settings (application controlled). Make sure you don't miss any advanced video settings either. ATI and Intel in particular are both notorious for having extremely destructive video settings enabled by default. As a last resort, you can just uncheck NV12 under xy-VSFilter's colors tab.<br>
<hr />
<b>Q:</b> I use FFDShow, why do I get a crash whenever opening a video?<br>
<br>
<b>A:</b> This is not a xy-VSFilter issue. FFDShow does not support Vertical Padding set to anything other than Original Height (xy-VSFilter default & recommended setting) when a non-default colorspace is used. Either install and use <a href='http://code.google.com/p/lavfilters/'>LAV Video</a> which does support the Vertical Padding setting, or open regedit and delete any VSFilter keys located at HKEY_CURRENT_USER\Software\Gabest\ to reset xy-VSFilter settings to defaults.<br>
<hr />
<b>Q:</b> I use CoreAVC 3.0, why do I get a green bar on the right side of some 10-bit videos?<br>
<br>
<b>A:</b> This is not a xy-VSFilter issue. CoreAVC 3.0.1 has a P010 bug with non-mod16 (display width/height not divisible by 16) videos. Either disable P010 output in CoreAVC, or use <a href='http://code.google.com/p/lavfilters/'>LAV Video</a> instead.<br>
<hr />
<b>Q:</b> Why are certain fonts not loading with MKV files muxed with mkvtoolnix >=5.1.0 ?<br>
<br>
<b>Q:</b> Why does typesetting sometimes render too big, too small, or get cut off with MKV files muxed with mkvtoolnix >=5.1.0 ?<br>
<br>
<b>A:</b> This is not a xy-VSFilter issue. Loading fonts is the splitter's job. mkvtoolnix >=5.1.0 changed the auto-detected MIME types for fonts, while splitters like Haali Media Splitter only support application/x-truetype-font. You can fix this by first demuxing the fonts with mkvextract, and then re-adding them into mkvmerge GUI with application/x-truetype-font manually specified as MIME type.<br>
<hr />
<b>Q:</b> Why aren't Blu-ray PGS subtitles showing on my cropped/resized video?<br>
<br>
<b>A:</b> Blu-ray PGS subtitles often have a fixed resolution of 1920x1080. Unless the encoded video frame matches the PGS subtitle resolution, no subtitles will be displayed. This is a limitation of the VSFilter 2.41 PGS code we are using. In the case of cropped 1920x1080 video, you can workaround this problem by padding the video back to 1920x1080. FFDShow users can use it's Resize filter to pad the video. LAV Video users can set temporarily set xy-VSFilter Vertical Padding to Extend to 16:9 (requires xy-VSFilter to be restarted).<br>
<br>
If a video has been resized from 1920x1080 to 1280x720, the PGS subtitles as well need to be resized to 1280x720 with a tool like <a href='https://github.com/mjuhasz/BDSup2Sub/downloads'>BDSup2Sub</a> before they will be displayed in xy-VSFilter. If the 1280x720 resized video has also been cropped before encoding, in addition to resizing the subtitles with BDSup2Sub to 1280x720, you'll also need to pad the video to 1280x720 (16:9) as described above.<br>
<br>
As an alternative to padding during playback, we've created a <a href='http://code.google.com/p/xy-vsfilter/downloads/detail?name=BDSup2Sub-5.1.1-Custom.zip'>custom version of BDSup2Sub</a> which adds support for resizing and exporting PGS SUP(BD) subtitles directly to common cropping aspect ratios. By matching the PGS resolution to that of the cropped/resized video, this should allow xy-VSFilter to display the PGS subtitles normally.<br>
<br>
<hr />
<b>Q:</b> Why do Blu-ray PGS subtitles appear late with TRUEHD audio streams?<br>
<br>
<b>A:</b> This is a limitation of the VSFilter 2.41 PGS code we are using, which is potentially caused by the splitter not giving VSFilter enough time to process subtitles with the tiny TRUEHD packet intervals. You can workaround this problem by re-encoding the TRUEHD audio to FLAC using <a href='http://forum.doom9.org/showthread.php?t=125966'>eac3to</a>.<br>
<hr />
<b>Q:</b> Performance of 10-bit video playback with madVR + xy-VSFilter is too slow. Anything I can do to make it faster?<br>
<br>
<b>A:</b> Unfortunately, P010 10-bit and P016 16-bit formats have a performance overhead of a few percent for both the video decoder and xy-VSFilter. <a href='http://code.google.com/p/lavfilters/'>LAV Video</a> should offer the best P010 performance, but if still too slow, disabling P010 and P016 in your decoder and using YV12 output will be fastest. It may seem unintuitive, but having the decoder dither 10-bit 4:2:0 video to 8-bit YV12, is actually faster than outputting 10-bit 4:2:0 as 10-bit P010 or 16-bit P016.<br>
<hr />
<b>Q:</b> Why won't xy-VSFilter let me override the DEFAULT style of ASS/SSA subtitles like VSFilter 2.39/2.41 does?<br>
<br>
<b>Q:</b> Why do certain xy-VSFIlter settings not apply until I re-open the video?<br>
<br>
<b>A:</b> We found the instant apply/override behavior extremely annoying with styled subtitles, so it's been disabled until we get around to revamping the functionality into something more flexible.<br>
<hr />
<b>Q:</b> I use Windows XP, why do I see boxes instead instead of Japanese hiragana/kanji?<br>
<br>
<b>A:</b> Windows XP has limited Unicode support, and years after the release of Vista and Win7 which added proper Unicode support, some people have forgotten the requirements to properly support Japanese subtitles on English WinXP. 1) The exact Japanese font(s) specified in the script must either be embedded in the video or installed on the system. 2) The primary English font name for the Japanese font must be used, not the secondary Japanese font name. 3) NOT RECOMMENDED... If neither of the previous requirements are met, as a last resort the end-user can set 'Language for non-Unicode programs' to 'Japanese' which will allow fallback behavior similar to Vista/Win7 and reading secondary Japanese font names from scripts. This will have the unintended side-effect of causing other multilingual programs to show up in Japanese instead of English, which is why I don't recommend this as a general purpose setting unless you can read Japanese.<br>
<hr />
<b>Q:</b> I use Windows Vista, Windows 7, or Windows 8. Why do I see boxes instead instead of Japanese hiragana/kanji?<br>
<br>
<b>A:</b> While Windows Vista and newer unicode support is miles better than Windows XP, it will still fail to fallback on some special characters and punctuation when the glyph isn't found in the specified font. In cases such as this, it's best to fix the script by manually specifying the desired font \fn and encoding \fe for rendering the glyph.<br>
<hr />

<h2>Related Links</h2>
VSFilter 2.39<br>
<ul><li><a href='http://sourceforge.net/projects/guliverkli2/'>Guliverkli2</a>
VSFilter 2.41<br>
</li><li><a href='http://sourceforge.net/projects/mpc-hc/'>MPC-HC project</a>
Another VSFilter fork<br>
</li><li><a href='http://code.google.com/p/threaded-vsfilter/'>threaded-vsfilter (discontinued)</a>
Other ASS/SSA subtitle renderer<br>
</li><li><a href='http://code.google.com/p/libass/'>libass</a></li></ul>
