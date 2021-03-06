=== Gif2html5 ===
Contributors: fusionengineering
Donate link: http://example.com/
Tags: comments, spam
Requires at least: 3.0.1
Tested up to: 3.4
Stable tag: 4.3
License: GPLv2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html

Gif2Html5 translates animated GIF attachments to MP4, and displays the MP4 in place of the original GIF.

== Description ==

When a user adds a new GIF to the Media library, or updates an existing GIF, Gif2Html will start the image translation process.

This plugin does not handle the actual file translation routine. The translation is handled by a standalone web application. Gif2Html sends the URL of the GIF to the web application, and the web application responds asynchronously with a POST handled via `admin_post`.

When the gif2html5 plugin receives the POST from the web application, it receives an MP4 URL and a poster image URL, and saves those as post meta fields of the GIF attachment.

The gif2html5 plugin filters post content, and replaces `img` elements with `video` elements where MP4 replacements are available.

== Installation ==

The standalone web application is a requirement. In order to set up the web application, you should clone it from the GitHub repository, and follow the setup instructions [here](https://github.com/fusioneng/gif2html5-app).

Once you have your web application running. You will need to set the `gif2html5_api_url` option to the `/convert` endpoint of your web application.

If you have your web application running on Heroku, setting the `gif2html_api_url` option might look like this:

```PHP
set_option( 'gif2html5_api_url', 'https://my-web-app.herokuapp.com/convert' );
```

If you've chosen to secure your web application with an API key (the GIF2HTML5_API_KEY setting described [here](https://github.com/fusioneng/gif2html5-app#configuration)), then you will also need to set the `gif2html5_api_key` option.

```PHP
set_option( 'gif2html_api_key', 'secret-api-key' );
```

Now you should be ready to use the plugin.
