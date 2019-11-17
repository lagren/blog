---
author: Eirik Tenold
title: Web harvesting and GUI testing with WebDriver
tags:
- Java
- Selenium
- Firefox
- WebDriver
---

For a spare time project I've been working on lately, I had to web harvest (also known as screen scraping) a 
couple of web pages to get the information I needed. A coworker recommended WebDriver, a part of 
[Selenium](http://seleniumhq.org/) testing framework.

In a nutshell, WebDriver is a library that controls your browser from code. This can be useful when doing 
GUI testing or when you want to simulate a web browser to fetch something from the web.

You can control different browsers (Firefox, Chrome, etc). In my experiment I used Firefox. WebDriver 
currently only support version 3 of Firefox, so I had to download it and point WebDriver to where it was located.

WebDriver worked very well for my project and even though I'm not a big fan of web harvesting the overall result was 
good enough.

How I pointed WebDriver to Firefox 3 and turned on autodownload for Excel spreadsheets:

    System.setProperty("webdriver.firefox.bin", "/opt/firefox-3.6/firefox/firefox");
    FirefoxProfile fp = new FirefoxProfile();
    fp.setPreference("browser.download.dir", "/tmp/firefox-webdriver");
    fp.setPreference("browser.download.folderList", 2);
    fp.setPreference("browser.helperApps.neverAsk.saveToDisk", "application/mx-msdownload");
    WebDriver driver = new FirefoxDriver(fp);

The Maven dependency looks like this:

{{< highlight xml >}}
    <dependency>
        <groupId>org.seleniumhq.webdriver<groupId>
        <artifactId>webdriver-firefox</artifactId>
        <version>0.9.7376</version>
    </dependency>
{{< /highlight >}}