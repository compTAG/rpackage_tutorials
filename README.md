# R package TDA tutorial

## Developing new tutorials

Tutorials are written in markdown and compiled into a website using
[jekyll](https://jekyllrb.com/).  Setting up jekyll is easy!!  From the command
line run (and assuming that you are in the folder containing this file, run:

     $ gem install bundler jekyll
     $ bundle install
     $ bundle exec jekyll serve

If all goes well, the server should start and you should see something like the
following output:

    Configuration file: .../rpackage_tutorials/_config.yml
                Source: .../rpackage_tutorials
           Destination: .../rpackage_tutorials/_site
     Incremental build: disabled. Enable with --incremental
          Generating...
           Jekyll Feed: Generating feed for posts
                        done in 0.464 seconds.
     Auto-regeneration: enabled for '.../rpackage_tutorials'
        Server address: http://127.0.0.1:4000/rpackage_tutorials/
      Server running... press ctrl-c to stop.

Enter the value for `Server address` into your browser and you should see the
site that you are creating.

To make a new post create a file in `_posts` with named formmatted as
`<date>_<topic>.md`. At the beginning of the file add a header with the
following:

    ---
    layout: "post"
    title: "Title of your tutorial"
    author: "Your name"
    ---

    # Name of your tutorial

    .... then add your content ....

That is it, everything you make a change, jekyll will recompile your tutorial
and you can reload your site.

Issue a PR whenever you are ready to start the discussion and thank you for
collaborating!!




