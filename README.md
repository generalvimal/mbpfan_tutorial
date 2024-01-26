Below is the backup of the guide from 19 April 2021 (https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html):

<main class="page-content" aria-label="Content">
        <div class="w">
            <p id="logo"><a href="https://web.archive.org/web/20210419093324/https://ineed.coffee/"><img src="/web/20210419093324im_/https://ineed.coffee/assets/images/logo-icon.png" class="logo" alt="ineed.coffee" title="go to ineed.coffee homepage" aria-label="go to ineed.coffee homepage" loading="lazy"></a></p>
<h1 id="title">a beginner's tutorial for mbpfan under ubuntu</h1>

<p id="2016-01-30"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#2016-01-30" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>2016-01-30</p>

<p id="update-as-of-2019-10-14-this-project-is-being-maintained-by-the"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#update-as-of-2019-10-14-this-project-is-being-maintained-by-the" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a><strong>Update</strong>: As of 2019-10-14, <a href="/web/20210419093324/https://ineed.coffee/5620/mbpfan-moved-to-linux-on-mac-organization/">this project is being maintained by the community linux-on-mac</a>. Please head to <a href="https://web.archive.org/web/20210419093324/https://github.com/linux-on-mac/mbpfan">https://github.com/linux-on-mac/mbpfan</a> to download the latest release of mbpfan and to report bugs. The project has also changed since the publication of this tutorial. Thanks!</p>

<hr>

<p id="although-mbpfan-is-not-a-program-for-everyone-heck-i-do-not-even"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#although-mbpfan-is-not-a-program-for-everyone-heck-i-do-not-even" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>Although <a href="/web/20210419093324/https://ineed.coffee/projects/mbpfan/">mbpfan</a> is not a program for everyone (heck, I do not even provide compiled packages for distros), I received several requests for an easy, step-by-step tutorial for installing mbpfan for Ubuntu. Here is my attempt. The present tutorial was written using Ubuntu 15.10, after a fresh install.</p>

<p id="first-thing-to-do-is-to-take-note-of-the-configuration-parameter"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#first-thing-to-do-is-to-take-note-of-the-configuration-parameter" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>First thing to do is to take note of the configuration parameters for mbpfan settings. Let’s start with the fan speed’s min and max values that the system was able to detect. Open a terminal, and type the following commands, one at a time.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>cd /sys/devices/platform/applesmc.768/
cat fan*_min
cat fan*_max
</code></pre></div></div>

<p id="note-down-the-lowest-among-the-numbers-for-fan__min-_for-example"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#note-down-the-lowest-among-the-numbers-for-fan__min-_for-example" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>Note down the <strong>lowest</strong> among the numbers for <em>fan__min. _For example, I got 1299.
Note down the <strong>highest</strong> among the numbers for _fan__max. _For example, I got 6199.
These two values are your _min_fan_speed</em> and <em>max_fan_speed</em> values for mbpfan configuration.</p>

<p id="now-see-what-are-the-max-values-that-the-system-was-able-to-dete"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#now-see-what-are-the-max-values-that-the-system-was-able-to-dete" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>Now, see what are the max values that the system was able to detect for the temperature.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>cat /sys/devices/platform/coretemp.*/hwmon/hwmon*/temp*_max
</code></pre></div></div>

<p id="note-down-the-highest-among-the-numbers-you-might-obtain-divide"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#note-down-the-highest-among-the-numbers-you-might-obtain-divide" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>Note down the <strong>highest</strong> among the numbers you might obtain.
Divide the number by 1000.
The value you will obtain is _max_temp _value for mbpfan configuration.
For example, I got 105000. Therefore, my max_temp is 105.</p>

<p id="second-thing-to-do-is-to-obtain-and-install-mbpfan-download-the"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#second-thing-to-do-is-to-obtain-and-install-mbpfan-download-the" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>Second thing to do is to obtain and install mbpfan. Download the latest <em>.tar.gz</em> version of the source code from <a href="https://web.archive.org/web/20210419093324/https://github.com/dgraziotin/mbpfan/tags">mbpfan tag/release page</a>.</p>

<p id="assuming-that-the-download-will-land-to-the-downloads-folder-and"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#assuming-that-the-download-will-land-to-the-downloads-folder-and" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>Assuming that the download will land to the Downloads folder, and that the file you download is mbpfan-1.9.1.tar.gz (the -1.9.1 part will change in the future). Open the terminal, go to the downloads folder, extract mbpfan, and enter the source code directory.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>cd ~/Downloads/
tar xfvz mbpfan-1.9.1.tar.gz
cd mbpfan-1.9.1
</code></pre></div></div>

<p id="install-the-build-essential-package-which-contains-what-is-requi"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#install-the-build-essential-package-which-contains-what-is-requi" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>Install the build-essential package, which contains what is required for compiling basic source code like the one of mbpfan.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>sudo apt-get update &amp;&amp; sudo apt-get install build-essential
</code></pre></div></div>

<p id="the-command-sudo-lets-you-execute-commands-as-the-root-user-the"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#the-command-sudo-lets-you-execute-commands-as-the-root-user-the" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>The command sudo lets you execute commands as the root user. The first time you use sudo, you need to supply your user password. It is completely normal that you won’t see any star (***) appearing here. Just type the password and press enter.</p>

<p id="you-might-receive-the-message-that-“build-essential-is-already-t"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#you-might-receive-the-message-that-%E2%80%9Cbuild-essential-is-already-t" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>You might receive the message that “build-essential is already the newest version”. All good if you have got it already.</p>

<p id="compile-install-and-test-mbpfan"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#compile-install-and-test-mbpfan" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>Compile, install, and test mbpfan.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>make
sudo make install
sudo make tests
</code></pre></div></div>

<p id="you-should-receive-some-text-which-has-to-tell-you-that-“all-tes"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#you-should-receive-some-text-which-has-to-tell-you-that-%E2%80%9Call-tes" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>You should receive some text, which has to tell you that “ALL TESTS PASSED”. If not, please contact me.</p>

<p id="third-thing-to-do-is-to-configure-mbpfan-open-the-configuration"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#third-thing-to-do-is-to-configure-mbpfan-open-the-configuration" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>Third thing to do is to configure mbpfan. Open the configuration file using a text editor (like Gedit) with root access.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>sudo gedit /etc/mbpfan.conf
</code></pre></div></div>

<p id="the-content-of-the-file-will-be-the-following"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#the-content-of-the-file-will-be-the-following" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>The content of the file will be the following:</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>[general]

min_fan_speed = 2000    # default is 2000
max_fan_speed = 6200    # default is 6200
low_temp = 63            # try ranges 55-63, default is 63
high_temp = 66            # try ranges 58-66, default is 66
max_temp = 86            # do not set it &gt; 90, default is 86
polling_interval = 7    # default is 7
</code></pre></div></div>

<p id="change-the-values-of-min_fan_speed-max_fan_speed-and-max_temp-to"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#change-the-values-of-min_fan_speed-max_fan_speed-and-max_temp-to" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>Change the values of <em>min_fan_speed</em>, <em>max_fan_speed</em>, and <em>max_temp</em> to the values that your marked down at the beginning of this tutorial.</p>

<p id="as-example-this-is-my-resulting-file"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#as-example-this-is-my-resulting-file" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>As example, this is my resulting file.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>[general]
min_fan_speed = 1299    # default is 2000
max_fan_speed = 6199    # default is 6200
low_temp = 63            # try ranges 55-63, default is 63
high_temp = 66            # try ranges 58-66, default is 66
max_temp = 105            # do not set it &gt; 90, default is 86
polling_interval = 7    # default is 7
</code></pre></div></div>

<p id="you-might-note-that-for-max_temp-i-suggest-to-never-setting-the"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#you-might-note-that-for-max_temp-i-suggest-to-never-setting-the" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>You might note that for <em>max_temp</em>, I suggest to never setting the value above 90. Yet, I got 105. You <em>can</em> set it to any value smaller (never bigger) than the one you obtained before. This is for having a more conservative system. The <em>max_temp</em> value is what mbpfan considers a critical temperature, where the fans have to be set <em>immediately</em> at the maximum possible speed.</p>

<p id="the-low_temp-_option-can-be-as-low-as-50-55-degrees-according-to"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#the-low_temp-_option-can-be-as-low-as-50-55-degrees-according-to" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>The <em>low_temp _option can be as low as 50-55 degrees (according to your CPU model). Feel free to try different settings for this value and for _high_temp</em>. Mbpfan attempts to keep a low fan speed if the temperature is between <em>low_temp</em> to <em>high_temp</em>.</p>

<p id="finally-turn-mbpfan-into-a-system-service-be-sure-to-be-back-int"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#finally-turn-mbpfan-into-a-system-service-be-sure-to-be-back-int" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>Finally, turn mbpfan into a system service. Be sure to be back into mbpfan source directory, in the Downloads folder. Then, run the following two commands:</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>sudo cp mbpfan.service /etc/systemd/system/
sudo systemctl enable mbpfan.service
</code></pre></div></div>

<p id="reboot-your-system-in-order-to-check-that-mbpfan-is-up-and-runni"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#reboot-your-system-in-order-to-check-that-mbpfan-is-up-and-runni" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>Reboot your system. In order to check that mbpfan is up and running, open a terminal again, and give the following command.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>ps aux | grep mbpfan
</code></pre></div></div>

<p id="if-there-is-a-line-ending-with-usr-sbin-mbpfan-you-are-good-to-g"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#if-there-is-a-line-ending-with-usr-sbin-mbpfan-you-are-good-to-g" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>If there is a line ending with /usr/sbin/mbpfan, you are good to go.</p>

<p id="you-can-delete-the-files-in-the-downloads-folder-they-are-not-ne"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#you-can-delete-the-files-in-the-downloads-folder-they-are-not-ne" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>You can delete the files in the Downloads folder, they are not needed anymore.</p>

<p id="once-an-update-of-mbpfan-is-released-you-just-have-to-extract-th"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#once-an-update-of-mbpfan-is-released-you-just-have-to-extract-th" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>Once an update of mbpfan is released, you just have to extract the new source files, enter the directory, and give the commands make, sudo make install, and sudo make tests. The configuration file does not get overwritten when updating mbpfan.</p>

<p id="i-wish-you-a-happy-fresh-macbook-did-you-find-a-bug-please-descr"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#i-wish-you-a-happy-fresh-macbook-did-you-find-a-bug-please-descr" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>I wish you a happy, fresh Macbook. Did you find a bug? Please describe your issue at <a href="https://web.archive.org/web/20210419093324/https://github.com/dgraziotin/mbpfan/issues">mbpfan’s Github issue tracker</a>.</p>


<hr>

<p id="i-do-not-use-a-commenting-system-anymore-but-i-would-be-glad-to"><a class="anchorjs-link anchor-left" aria-label="Anchor" data-anchorjs-icon="¶" href="https://web.archive.org/web/20210419093324/https://ineed.coffee/post/a-beginners-tutorial-for-mbpfan-under-ubuntu.html#i-do-not-use-a-commenting-system-anymore-but-i-would-be-glad-to" style="position: absolute; margin-left: -1em; padding-right: 0.5em;"></a>
  I do not use a commenting system anymore, but I would be glad to read your feedback. Feel free to <a href="/web/20210419093324/https://ineed.coffee/contact.html">contact me</a>.
</p>
        </div>
    </main>
