# Cowboystyle

We're trying to do Heroku with the same repository now. This should reduce
duplication.

This is a proposed source and toolkit for the CSS and sidebar used in
r/UCSantabarbara. This is only to be used within your own test subreddits by
creating your own little configuration files and passing it as the second
argument to `deploy.py`. For production deployment on an interval,
[cowboybeepbot](https://github.com/crazysim/cowboybeepbot) is used.

## Git

This project is under `git`. It uses `git-flow` to manage releases and such. As
such, development generally happens in the `develop` branch.

Pull requests are appreciated, even if you can't use the `git-flow`.

## CSS

Compilation of this will require a modern ruby and python development setup.
Use `bundler` to install the requirements. Ensure that whatever ruby version
manager you use, use something that is 1.9.3. For Python, it is recommended
that a virtualenv setup be used. The version you should select while creating
the virtualenv for this project should be Python 3.x. Install the package
requirements with `pip -r`. 

CSS is is generally generated by Compass. Files in the `sass` folder are
compiled and the resulting CSS files are put into the `styleheets` folder.

You can upload the css files into the test subreddits by editing their
stylesheets manually and pasting in the content from the generated files. This
is stupid and error prone to do constantly so don't do that too often.

Instead, do this because having near instant feedback on whatever you are doing
is extremely valuable:

1. Create two test subreddits and ensure that you have moderator privledges.
   Ensure that the images have been uploaded to both reddits.  See the images
   section for more details on what images must have been uploaded. If the
   images aren't present, the upload will fail.

2. Run `compass compile` to compile the SCSS to CSS.

2. Create a `day.config` and `night.config` file with a template similar to
   this:

    [user]
    username=aredditusername
    password=lol_password
    subreddit=crazysimreddittest
    file=stylesheets/day.css
    mkdn=markdown/sidebar.mkdn

3. Within the project directory, run `python deploy day.config` and `python
   deploy night.config`. Pay attention to the output for any errors.

4. Make sure that the CSS is uploaded. If it isn't you'll see a hacky diff of
   the current CSS and the uploaded CSS. To obtain the actual error message,
   you must upload manually as the current Python API does not respond with
   errors.  Sometimes, it errors out anyway so if your change was very minor or
   there's no way your change can cause that, upload again to make sure.

5. At this point, you have verified that uploading manually works. To compile
   and upload automatically, run `guard`.

## Images

Images must be manually uploaded until the python API allows image uploading.
Only finalized versions are to be put in the images folder. Development of
these images happen in a [Dropbox
folder](https://www.dropbox.com/sh/i3qo9cgdgen1bcf/oNpFhT8gF0).

Images that must be uploaded to the reddit before uploading CSS include:

* Storke Tower
    * Top Night
        * This special image is an APNG with the top light blinking at 40 times
          per minute. Reddit does not allow gifs. It's a minor detail.
    * Top Day
    * Middle Night
    * Middle Day
* Header Background
    * The Alien without the text but the same dimensions as the logo in
      half DPI. This will have seperate night and day versions in the future.
      The framework has been laid out for such already.

_If these images are not uploaded, CSS uploading will fail!_

One more image that doesn't need to be uploaded but is nevertheless important:
    * A 144dpi image of the subreddit text at 280x80. This image will be
      resquashed to the proper dimensions. The reason for the high DPI is to
      ensure that it looks good on Retina-class displays such as the ones on
      newer Macs, iPads, and Android Tablets.

## Sidebar

`sidebar.markdown` is the source for the sidebar. Since the styling may rely on
the ordering of certain elements in the sidebar, the sidebar is placed under
version control as well.

## Random Notes

Modded Official logo from http://satedproductions.com/tmp/reddit/alien/
UCSB alien logo and variants from u/snifty.

