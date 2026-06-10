# My site

Based on GitHub Pages and Jekyll.

## Run locally

From the repository root:

```bash
gem install --user-install bundler:2.4.22 ffi:1.15.5 public_suffix:5.1.1 jekyll:4.2.2 jekyll-theme-minimal
/Users/pavel/.gem/ruby/2.6.0/bin/jekyll serve -s docs --host 127.0.0.1 --port 4000
```

Open the site at:

```text
http://127.0.0.1:4000
```

If your Ruby version is newer and `jekyll` is already available in `PATH`, this is enough:

```bash
jekyll serve -s docs
```
