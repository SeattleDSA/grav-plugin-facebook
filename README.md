# Grav Facebook Plugin

`Facebook` is a simple [Grav][grav] Plugin that includes your Facebook page content to your Grav website.

# Installation

Installing the Facebook plugin can be done in one of two ways. Using GPM (Grav Package Manager) installation method enables you to quickly and easily install the plugin with a simple terminal command, while the manual method enables you to do so via a zip file.

## GPM Installation (Preferred)

The simplest way to install this plugin is via the [Grav Package Manager (GPM)](http://learn.getgrav.org/advanced/grav-gpm) through your system's Terminal (also called the command line).  From the root of your Grav install type:

    bin/gpm install facebook

This will install the Instagram plugin into your `/user/plugins` directory within Grav. Its files can be found under `/your/site/grav/user/plugins/facebook`.

## Manual Installation

To install this plugin, just download the zip version of this repository and unzip it under `/your/site/grav/user/plugins`. Then, rename the folder to `facebook`. You can find these files either on [GitHub](https://github.com/mikahanninen/grav-plugin-facebook) or via [GetGrav.org](http://getgrav.org/downloads/plugins#extras).

You should now have all the plugin files under

    /your/site/grav/user/plugins/facebook

# Configuration

You need to provide few configurations in order for the feed show up. In your Grav Administration panel, go to Plugins > Facebook to view the plugin configuration page.

Enter the Facebook *page_id* which feed you want to show, and your Facebook API *application_id* and *application_secret*.


For more information how to get application set up, see the [Facebook Developers documentation](https://developers.facebook.com/).

# Customization

To customize how the your feed looks like, you might want to customize the generated markup. To do that, copy the template file [facebook.html.twig](templates/partials/facebook.html.twig) to your `templates/partials` folder of your theme. For example:

```
/your/site/grav/user/themes/custom-theme/templates/partials/facebook.html.twig
```

It will now override the default markup of the feed. You can tweak it however you like.

# Config Defaults

If you need to override some plugin default values, the best practise is to copy the [facebook.yaml](facebook.yaml) file into your `users/config/plugins/` folder (create it if it doesn't exist), and then modify there. This will override the default settings.

# Usage

To use this plugin you simply need to include a function your template file such as:

```
{{ facebook_posts() }}
```

This will be converted into your Facebook posts as follows:

```
<div id='facebook-posts'>
{{ sectionTitle }}
  <div class='facebook-post'>
    <a href='{{ post.link }}' title='Facebook post'>
    <i class="fa fa-envelope" aria-hidden='true' style='display: inline-block; font-size: 22px; line-height: 22px; padding-right: 10px;'></i><h4 class='media-heading' style='display: inline-block;'>{{ post.time }}</h4>
    <p>{{ post.message }}</p>
    {{ post.image }}
    </a>
  </div>
  ...
</div>
```