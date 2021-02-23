# scleeza.github.io
:triangular_ruler: Jekyll theme for building a personal site, blog, project documentation, or portfolio.

https://scleeza.github.io

# How to run this site locally
> Be alert when installing ruby, there have been several issues reported

1.Install jekyll on your computer [link](https://jekyllrb.com/docs/installation/macos/)
 * when installing ruby, pls use rbenv to install version _2.7.2_ , 
 version later than 2.7.2 is not support by jekyll, it will save you a lot of time.
 * remember to install jekyll and bundle in local repo that contains site codes
 * if you already installed ruby > 2.7.2, try use bundle to add this plugin
    ```console
    bundle add webrick
    ```
 * issues here\
    [ruby 3.0.0](https://github.com/github/pages-gem/issues/752) \
    [rbeny install 2.7.2](https://github.com/rbenv/ruby-build/issues/1483) 
 
 * Run website locally
    ```console
    bundle exec jekyll serve
    ```
2.Modify gem file [link](https://docs.github.com/en/github/working-with-github-pages/testing-your-github-pages-site-locally-with-jekyll)
 * I use remote theme
 
## Error  Debug (Load Error)
bundle install error: <load error> 
```commandline
 cannot load such file -- /usr/local/lib/ruby/gems/3.0.0/gems/bundler-2.2.7/exe/bundle (LoadError)
```

1. rerun gem install bundler
```commandline
gem install bundler
```

2. Check bundler installation version 
```commandline
Successfully installed bundler-2.2.11
```

3. Find Gemfile.lock in project folder, change version into new version
```commandline
BUNDLED WITH
   2.2.11
```