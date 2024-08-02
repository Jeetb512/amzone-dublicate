
A WordPress plugin which provides shortcodes for Amazon Associates tags.

## Usage

In posting blog article pages (or any other shortcode-enabled context),
type like this:

````
Blah blah blah [asin asin="4063827216"] blah blah blah.
````

or

````
Blah blah blah [asin]4063827216[/asin] blah blah blah.
````

shows you:

>Blah blah blah  
>  *:*  
>  *Amazon Affiliate banner for ASIN:4063827216*  
>  *:*   
>blah blah blah.

`4063827216` is a typical example of Amazon's product unique code,
i.e. ASIN.

Or you can use Amazon's full URL for products instead of pure ASIN.
Amazoness captures ASIN from the URL like this:



But this capturing feature does not work properly always.
You'd better use pure ASINs.

The difference between
`[asin asin="ASIN"]`
and
`[asin]ASIN[/asin]`
is that
latter one's ASIN code is displayed in HTML source
so crawlers (e.g. Googlebot) catch some noises.
Former one is better, I think.

## Unique Point

* Merits
    * No need for obtaining Amazon API key, nor knowing about it!
    * Amazoness shows affiliate banners with specifying only ASIN code
    * The product name, information, and an image are automatically crawled and displayed
    * Users can fully customize how it can be seen by CSS and HTML
    * Uses cache for fetching product data, so speedy  
* Demerits
    * The product's price and other informations are not supported
    * Crawls Amazon pages without any permissions ;-( I expect they were tender people...
    * Not suitable for people who don't know what ASIN is

ASIN code is a universal product code in Amazon
which has 9-13 digits.
It seems to be same with EAN/JAN/ISBN.
Visit the Amazon's product page and check if ASIN is there.
Or you can see it in browser's URL bar also.


## Environment

Amazoness works properly in environments like below:

* PHP 5.6 and greater versions   
  Using Closures, Classes, Name Spaces, const arrays
* PHP dom, xml, xmlreader extensions   
  Using DOMDocument, DOMXPath

Tested under:

* CentOS 6.x, Alpine Linux 3.3.x

## Settings

Visit WordPress dashboard, select [Amazoness] in [Settings] menu (at the leftside if you are using PC).
You can configure these entries:

<a name="setting_associate_id">&nbsp;</a>
### Amazon Associate ID 

**!MANDATORY!**  
Set your own Amazon Associate ID.
Visit Amazon Associate page to purchase the ID:
it looks like "netspin-22".
By default, Amazoness uses the plugin developer's ID (mine :)

<a name="setting_image_size">&nbsp;</a>
### Image Size Descriptor 

The descriptor which determines product's image size.
But it has none-sense almost always because image sizes
determined by CSS.
By default, largest(`LZZZZZZZ`). Available options are:

* `THUMBZZZ` :   thumbnail
* `TZZZZZZZ` :   tiny
* `MZZZZZZZ` :   middle
* `LZZZZZZZ` :   large

<a name="setting_css_definition">&nbsp;</a>
### CSS Definition

CSS for Amazoness' output.

Consult <a href="#setting_html_template">Template HTML</a>
to know what kind of id/classes used.

<a name="setting_html_template">&nbsp;</a>
### Template HTML

Template HTML for displaying product's information.
Miss-configuration in this entry may cause 
some security hall so pay much attention.

Some variables and filters are available inside double `%%`:

* Variables:
    * `PRODUCT_URL`  
      URL for Amazon's product page. Contains Amazon Associate ID
    * `PRODUCT_IMAGE_URL`  
      URL for product's image size. Contains an image size descriptor
    * `PRODUCT_TITLE`  
      Product's name
    * `PRODUCT_DESCRIPTION`  
      Product's description
    * `IS_CACHED`
      Show which this HTML fragment uses cache or not
* Filters:
    * `html`  
      Escape danger characters with HTML
    * `url`
      Escape danger characters with URL encoding

Use variables like this:

````
...blah blah blah %%PRODUCT_URL%% blah blah...
````

Filters work like this:

````
...blah blah blah %%PRODUCT_URL|url%% blah blah...
````

## Q&A

* Is ASIN Voodoo magic? What is it?
    * I'm sorry but you should use other WordPress plugins or Web services...
      They are convinience more than Amazoness for your purpose.
      Or consider is as 'URLs for Amazon products pages'
* Amazoness got insane after I made changes in configuration page
    * Click `Reset Configuration` button to reset your configuration

## Author, Donation & Copyright

I know little about PHP and WordPress, so codes might be very strange.

You can use / re-distribute this plugin without any permissions.
But I am very poor. Thank you for kindness if would give me any donation.

I will keep this plugin under the dual license of GPL and MIT.
Settle it after leared much about WordPress's license rule.



## History
