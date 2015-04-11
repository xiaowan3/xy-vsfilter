There are 6 new options currently available from the UI.


## BT709/BT601 switch option ##

![https://sn2files.storage.live.com/y1pqni48Tf6BRR0my23P03gTK79vF3X9od-y1JeqBn4XLQFh2Ppy9fzJa-fPs8myawGVVm9cD_qxfyaX173QDR9aA/bt709_bt601_switcher.png](https://sn2files.storage.live.com/y1pqni48Tf6BRR0my23P03gTK79vF3X9od-y1JeqBn4XLQFh2Ppy9fzJa-fPs8myawGVVm9cD_qxfyaX173QDR9aA/bt709_bt601_switcher.png)

When checked, do internal rgb2yuv convertion following BT709 stardard, other wise using BT601 instead.
## 4 cache options ##

![https://sn2files.storage.live.com/y1pVmfir7xEsgCxmHS4Mvhw-bua5wdrclEnN0MiKyL-6Q37CVnoX9HGdoY-wlmdSfqsF3Z-aE6wsdvbSWvHDky_GA/cache_optons.png](https://sn2files.storage.live.com/y1pVmfir7xEsgCxmHS4Mvhw-bua5wdrclEnN0MiKyL-6Q37CVnoX9HGdoY-wlmdSfqsF3Z-aE6wsdvbSWvHDky_GA/cache_optons.png)

For each option, a large value allow more cache items to be kept in memory so rendering speed get more guarantee but memory load may increased, while a small value allow less cache items to be kept so memory load could get control but rendering speed **may** be slowed down; set to zero would disable the cache. **(WARNING: it is almost impossible do with any ass script if all caches disabled. Don't try to do that unless you want to see how slow your machine can be.)**

(Donot bother to guess the meaning of the names. I'll try to make more comprehensible names and give a more detailed recommentation on how to config them.)

### How it works (NOT FINISHED) ###
Summary, for each draw request, Cache Lv1/Lv2/Lv3/Lv4 are queried one by one, once a qualified item is found, the query process stop and from where it stops, the found item is returned to upper caches for further process.

Detail, first Cache LV1 is searched to see the same request has been previous processed and left a cached item there.
  * If found, the cached item is returned, next it will be drawed to the subpic.
  * If not found, blur/be parameters are discarded and Cache LV2 is queried using the loosed condition.
    * If found, a blur operation is taken to the found Cache LV2 item found and produce a Cache LV1 item. This newly produced Cache LV1 item is put into Cache LV1 and returned for further process.
    * If not found, positioning parameters are discarded and Cache LV3 is queried using this looser condition.
      * If found, the found Cache LV3 item is return, and some operations are taken using previous discarded parameters to the item to generate a correspond Cache LV2 item. This new Cache LV2 item is put into Cache LV2 and returned for further process.
      * If not found, transform parameters are discarded and Cache LV4 is queried.
        * If found, create a new Cache LV3 item using previous discarded parameters and found Cache LV3 item, cache it and return it for further process.
        * If not found, create a new Cache LV4 item using current parameters, cache it and return it for further process.

### About caches info ###

#### FIRST OF ALL, what a cache item represents ? ####
It is decided by the script. A cache item may correspond to
  * a whole line of subtitle, e.g. in the script below:
```
  Dialogue: 1,0:00:35.63,0:00:38.40,Alt,,0000,0000,0000,,Like seriously, I was like “Seriously stop!”
```
> The line may go very long that it exceeds the boudary of the video rect,
```
Dialogue: 0,0:00:00.00,0:00:20.00,Default,,0000,0000,0000,,{\move(1050,286,-550,286)}{\q2} After I'm born I finally realize, I exist just to imitate humans.  A Vocaloid fated to sing forever.  Even if the song already existed, a programmed toy accepts it just fine.  Gnawing on a leek, looking up at the sky, shedding tears, noticing that even all that is fading.  Even songs depend on character.  With no reliable source for foundation, the place I came from already destroyed.  When everyone forgets me, I'll have no heart or anything left.  I can see the end of the world for a Vocaloid.
```
> in such cases cache items corresponding to the line will occupy lot of memory.
  * Or only serveral letters, or even a single letter, e.g. in the script below
```
  Dialogue: 0,0:00:03.13,0:00:06.06,ED - RO,,0000,0000,0000,,{\k25}ki{\k25}ko{\k19}e{\k25}ta{\k24}i {\k28}ko{\k13}e {\k20}ga {\k21}a{\k93}ru
```
the whole word "kikoetai" will be seperated into 5 items ki, ko, e, ta and i, and cache items correponding to them will be created.
  * Or a shape, e.g. in the script below:
```
Dialogue: 0,0:00:00.00,0:00:05.00,Signs,,0000,0000,0000,,{\p1\1c&HB3BB9E&\fscx800\fscy800\pos(1259,594)\clip(m 910 474 l 917 376 1137 440 1120 550)}m 0 0 l -30 0 l -30 28 l 4 28 l 4 0 l 0 0 {\p0}
```
#### Cache info ####
  * store\_num  : how many items currently cached
  * hit\_count  : how many times cached items has been reused
  * query\_count: how many times the cache is queried

For each cache, the greater value hit\_count/query\_count gets (it can never greater than 1), the more acceleration you get from the cache. But a big query\_count value indicates that the script is really complex and maybe you'll have some performance trouble.

For Cache LV1, a big value of query\_count indicates that a lot of alphablending operations have done.

If query\_count of Cache LV2 is much larger then Cache LV3's, it means a lot of \be or \blur operations have done.

For Cache LV3, a big value of query\_count indicates that a lot of transform, e.g. rotation or scaling, and rasterize operations have done.

For Cache LV4, a big value of query\_count means that a lot of GDI calls.

## Subpixel Position Option ##

![https://sn2files.storage.live.com/y1pVmfir7xEsgBCTlkd12jfbaebEC08REwPrKoFfmN9AN8OgjWrhuwE_3LgtvF4GGtr0WoJkJjEK3J7YvOd2xA97A/subpixel_positioning.png](https://sn2files.storage.live.com/y1pVmfir7xEsgBCTlkd12jfbaebEC08REwPrKoFfmN9AN8OgjWrhuwE_3LgtvF4GGtr0WoJkJjEK3J7YvOd2xA97A/subpixel_positioning.png)

Generally, a large value for this option produces more smooth animated effect but reduces cache efficiency in the mean while.
Official VSFilter uses 8\*8 subpixel positioning.

<a href='http://code.google.com/p/xy-vsfilter/issues/detail?id=7&can=1'><a href='https://code.google.com/p/xy-vsfilter/issues/detail?id=7'>Issue 7</a></a> has some nice examples on subpixel positioning.

Further reading: https://freddie.witherden.org/pages/font-rasterisation/#sub-pixel-positioning