# WSU Embeds

[![Build Status](https://travis-ci.org/washingtonstateuniversity/WSUWP-Plugin-Embeds.svg?branch=master)](https://travis-ci.org/washingtonstateuniversity/WSUWP-Plugin-Embeds)

Extends the WSUWP Platform to include support for various embeds.

## Supported Shortcodes

* `[qualtrics]` to embed Qualtrics surveys.
	* `url` - **Required.** The full URL to your Qualtrics survey.
	* `width` - Defaults to `100%`. Accepts the same values as the CSS property `width`.
	* `height` - Defaults to `100%`. Accepts the same values as the CSS propety `height`.
	* `min_height` - Defaults to `400px`. Accepts the same values as the CSS property `min-height`.
* `[qualtrics_multi]` to redirect a user randomly to one of multiple surveys.
	* `url1`, `url2`, `url3`, `url4`, `url5` can all be used to specify a different URL for the survey.
	* This shortcode can only be used on individual pages. We recommend using the default page template rather than the builder.
* `[wsu_uchat]` to embed UChat scripts.
	* `id` - **Required.** The ID for your UChat script.
* `[tvw_video]` to embed videos from tvw.org.
    * `event_id` - **Required.** The ID of the video to play.
    * `client_id` - Defaults to 9375922947, which may change depending on the video.
    * `start` - The number of seconds into the video at which it should start playing.
    * `stop` - The number of seconds into the video at which it should stop playing.
* `[wsuwp_iframe]` to embed iframes.
    * `src` - The full URL of the page to embed. Currently allows pages from `emailwsu.sharepoint.com` only. Required.
    * `title` - The value to use for the iframe `title` attribute. Required.
    * `width`- Defaults to 800.
    * `height` - Defaults to 600.
    * `responsive` - Set to any value to make the iframe responsive. Blank by default.
* `[formtool]` - to embed formtool forms
    * `url` - The URL for the form.
* `[fatv]` - to embed fatv videos & playlists
    * `id` - Id (iid) for the account. script type="text/javascript" src="embed.financialaidtv.com/cms/embed/script/381?iid=**86317**&amp;hd=1&amp;dim=responsive&amp;language=en"
    * `key` - Video or playlist key. script type="text/javascript" src="embed.financialaidtv.com/cms/embed/script/**381**?iid=86317&amp;hd=1&amp;dim=responsive&amp;language=en"
    * `type` - Single video or playlist. Supports "**playlist** (/script-playlist-ng/)" or "**video** (/srcipt/)".
    * Example: **[fatv id="86317" key="381" type="video"]**
* `[wsuwp_powerbi]` to embed iframes.
    * `[path]` - Required | The relative path of the page to embed. Everything that follows https://app.powerbi.com/
        * Example: app.powerbi.com/**view?r=eyJrIjoiYTRjMDU2MTc..etc....**
    * `width`- Optional | Defaults to 100%.
    * `height` - Optional | Defaults to 800px.
* `[wsuwp_photo_carousel]` to embed a swiper.js powered photo carousels.
    * `ids` - Required. Default null. IDs for the images to be displayed in the carousel.
    * `name` - Default null; Returns the name of the current instance from the shortcode params or the current page id. Allows for site-wide customization or carousel specific styles. Example `#swiper.swiper_page-id-2 { background: crimson }` to change all sliders on the page.
    * `image_size` - Default medium. Image size identifier.
    * `random_order` - Default false. Shuffles the order in which the ids are included into the shortcode.
    * `slides_per_view` - Default 3. Number of slides per view (slides visible at the same time on slider's container).
    * `slides_per_column` - Default 2. Number of slides per column, for multirow layout.
    * `space_between` - Default 20. Distance between slides in px.
    * `preload_images` - Default false. When enabled Swiper will force to load all images.
    * `lazy` - Default true. Enables images lazy loading. If you use slidesPerView, then you should also enable watchSlidesVisibility and Swiper will load images in currently visible slides.
    * `watch_slides_visibility` - Default true. Enable this option and slides that are in viewport will have additional visible class.
    * `download_image_on_click` - Default false. Returns true or false, if the user whats the images to download on click.
    * `download_image_size` - Default full. Image size identifier.
    * `pagination_type` - Default bullets. The type of pagination to display. Can be "bullets", "fraction", or "progressbar".
    * `autoplay` - Default true. Controls whether the slider should autoplay.
    * `autoplay_delay` - Default 3000. Controls the duration at which the carousel progresses to the next slide.


## Twitter Timeline

Twitter [embedded timelines](https://dev.twitter.com/web/embedded-timelines) can be added to content in two ways.

First, a shortcode can be generated directly from a Twitter timeline embed code just by pasting it into your content.

```
<a class="twitter-timeline" href="https://twitter.com/WSUPullman" data-widget-id="583397974576734209">Tweets by @WSUPullman</a>
<script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0],p=/^http:/.test(d.location)?'http':'https';if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src=p+"://platform.twitter.com/widgets.js";fjs.parentNode.insertBefore(js,fjs);}}(document,"script","twitter-wjs");</script>
```

The above code, copied directly from the WSUPullman profile on Twitter, will translate to `[wsu_twitter_timeline href="https://twitter.com/WSUPullman" id="583397974576734209" name="Tweets by @WSUPullman"]` when a draft is saved or published.

This resulting `[wsu_twitter_timeline]` shortcode can also be used directly as long as these attributes are available:

* `href` - The URL the embed should return to.
* `data_widget_id` - The ID of the widget, generated by Twitter.
* `name` - The text wrapped in the anchor before Javascript renders the widget.
