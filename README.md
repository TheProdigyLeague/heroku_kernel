![heroku](https://github.com/TheProdigyLeague/heroku_kernel/assets/30985576/486208bc-4494-4232-8f41-7afa06c0d4e3)

# heroku-buildpack

Headless Chromium of release channels.

> Chromedriver version installed by a different buildpack. Falls out of sync with Chrome causing build failures.
> **Instead, please use [Chrome for Testing buildpack](https://github.com/heroku/heroku-buildpack-chrome-for-testing)**, which installs  [matching Chrome + Chromedriver versions](https://googlechromelabs.github.io/chrome-for-testing/).

## Channels

Release channel is `GOOGLE_CHROME_CHANNEL` as config var.app, app.json (for Heroku CI and Review Apps), or in pipeline settings (for Heroku CI).

Valid values are `stable`, `beta`, and `unstable`. If unspecified`stable` channel will be used.

### Shims and Command Line Flags

This buildpack installs shims that always add `--headless`, `--disable-gpu`, 
`--no-sandbox`, and `--remote-debugging-port=9222` to any `google-chrome` 
command trouble running Chrome on Heroku dyno otherwise.

You'll have two of these shims on your path: `google-chrome` and
`google-chrome-$GOOGLE_CHROME_CHANNEL`. They both point to the binary of
the selected channel.

#### Selenium

> [!CAUTION]
> To use Selenium, do not install this buildpack.
> **Instead, please use [Chrome for Testing buildpack](https://github.com/heroku/heroku-buildpack-chrome-for-testing)**, which installs  [matching Chrome + Chromedriver versions](https://googlechromelabs.github.io/chrome-for-testing/).

Make sure you publish this buildpack in the buildpack registry

`heroku buildpacks:publish heroku/google-chrome master`
