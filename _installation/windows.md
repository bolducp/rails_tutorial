---
url: windows.html
title: Installation on Windows
layout: rails_installation
---
{% sectionheader %}
  {{ page.title }}
{% endsectionheader %}

{% aside %}
## Minimum Requirements

In order to successfully follow these installation instructions, you must have access to an Administrator user with rights to change your computer's properties.
{% enaside %}

{% steps %}
{% list %}
First, we'll start by downloading Node.js. Rails needs a JavaScript runtime to run, and Node.js is a pretty popular one 😉

1.  Go to the [Node.js download page](https://nodejs.org/en/download/) and download the Node.js Windows installer.

1.  Once the download is finished, go to your downloads folder and run the Node.js installer.

    Read the full license agreement, accept the terms, and run through the rest of the wizard leaving all the defaults.

    Click "Yes" when Windows asks you if you want to allow the changes to your computer.
{% endlist %}
{% endsteps %}

{% steps %}
{% list %}
Now, we're going to install Ruby using the [RubyInstaller for Windows](https://rubyinstaller.org/).

1.  To download the Ruby Installer,[click here](http://dl.bintray.com/oneclick/rubyinstaller/rubyinstaller-2.3.1.exe){:target='blank'}

1.  When the download finishes, go to your downloads folder, and run the RubyInstaller to install Ruby 2.3.1 on your computer.

1.  When the installation wizard starts, agree to the license agreement and click "Next".

1.  On the next screen, you can leave the default install destination but you must check the "Add Ruby executables to your PATH" option.

    ![Check this box](screenshot.jpg)

    After you've checked "Add Ruby executables to your PATH", click "Install".

1.  Once the install finishes, click "Finish".
{% endlist %}
{% endsteps %}

{% steps %}
{% list %}
Now, we'll open Command Prompt to verify your Ruby install.

1.  There are a number of ways to open Command Prompt in Windows, but I'm lazy so I just like to search for it.

    From the search bar, type "Command Prompt". It should be the first item in your search results.

    With Command Prompt selected in your search results, press `Enter` to open it.

1.  To verify your Ruby install, type `ruby -v` into the Command Prompt and press `Enter`. It should print "ruby 2.3.1p112" into your Command Prompt.

    If you don't get "ruby 2.3.1p112", try re-running the RubyInstaller and make sure you have the "Add Ruby executables to you PATH" option selected.
{% endlist %}

{% highlight shell %}
C:\Users\awesomesauce>ruby -v
ruby 2.3.1p112 (2016-04-26 revision 54768) [i386-mingw32]
{% endhighlight %}
{% endsteps %}

{% steps %}
{% list %}
To make your development experience just a little bit nicer, we'll now install the [RubyInstaller DevKit](https://rubyinstaller.org/add-ons/devkit/).

1.  To download the RubyInstaller DevKit, [click here](http://dl.bintray.com/oneclick/rubyinstaller/DevKit-mingw64-32-4.7.2-20130224-1151-sfx.exe){:target='blank'}.

1.  Once the download is finished, go to your downloads folder and find the DevKit package. It will be named something like `DevKit-mingw64-32-4.7.2-20130224-1151-sfx.exe`.

    Run the package and extract it to `C:\RubyDevKit`.

1.  Now, open the Command Prompt and run the following commands:

    ```shell
    ruby C:\RubyDevKit\dk.rb init
    ruby C:\RubyDevKit\dk.rb install
    ```
{% endlist %}

{% highlight shell %}
C:\Users\awesomesauce>ruby C:\RubyDevKit\dk.rb init
[INFO] found RubyInstaller v2.3.1 at C:\Ruby23

Initialization complete! Please review and modify the auto-generated 'config.yml' file to ensure it contains the root directories to all of hte installed Rubies you want enhanced by the DevKit.

C:\Users\awesomesauce>ruby C:\RubyDevKit\dk.rb install
[INFO] Updating convenience notice gem override for 'C:\Ruby23'
[INFO] Installing 'C:/Ruby23/lib/ruby/site_ruby/devkit.rb'
{% endhighlight %}
{% endsteps %}

{% steps %}
Before you can install Rails, you'll need to apply an update for [RubyGems](http://guides.rubygems.org/ssl-certificate-update/).

{% list %}
1.  [Click here](https://rubygems.org/downloads/rubygems-update-2.6.7.gem){:target='blank'} to download the update.

    Take a note of where the update file gets downloaded. Most likely, it will get downloaded to your download directory.

    For example if your username was "awesomesauce", the path to your download directory would be `C:\Users\awesomesauce\downloads`.

1.  After the download finishes, open Command Prompt.

1.  Now, install the update file by running the following command. However, you will have to replace "awesomesauce" with your username.

    ```shell
    gem install --local C:\Users\awesomesauce\downloads\rubygems-update-2.6.7.gem --no-document
    ```

1.  Then, run the update:

    ```shell
    update_rubygems --no-document
    ```

1.  Run the following command to verify that the update was installed:

    ```shell
    gem --version
    ```

    It should return 2.6.7.

1.  Now that you've run the update, you can uninstall update file. Run:

    ```shell
    gem uninstall rubygems-update -x
    ```
{% endlist %}

{% highlight shell %}
C:\Users\awesomesauce>gem install --local C:\Users\awesomesauce\downloads\rubygems-update-2.6.7.gem --no-document
Successfully installed rubygems-update-2.6.7
1 gem installed

C:\Users\awesomesauce>update_rubygems --no-document
RubyGEms 2.6.7 installed

=== 2.6.7 / 2016-09-26

Bug fixes:
...

---------------------------------------------------
RubyGems installed the following executables:
        C:/Ruby23/bin/gem

C:\Users\awesomesauce>gem --version
2.6.7

C:\Users\awesomesauce>gem uninstall rubygems-update -x
Removing update_rubygems
Successfully uinstalled rubygems-update-2.6.7
{% endhighlight %}
{% endsteps %}

{% steps %}
{% list %}
Now, we're ready to install Rails! 🎉

1.  Open the Command Prompt and run the following command to install Rails:

    ```shell
    gem install rails --version 5.0.1 --no-document
    ```

    Windows Firewall may ask you to give Ruby access to public networks. If it does, click "Allow access".

1.  To verify the install, run

    ```shell
    rails -v
    ```

    It should return Rails 5.0.1.
{% endlist %}

{% highlight shell %}
C:\Users\awesomesauce>gem install rails --version 5.0.1 --no-document
Fetching: i18n-0.8.0.gem (100%)
Successfully installed i18n-0.8.0
Fetching: thread_safe-0.3.5.gem (100%)
...
Fetching: rails-5.0.1.gem (100%)
Successfully installed rails-5.0.1
36 gems installed

C:\Users\awesomesauce>rails -v
Rails 5.0.1
{% endhighlight %}
{% endsteps %}

{% steps %}
{% list %}
Finally, we'll check if everything is working by creating a new Rails app.

1.  Open Command Prompt and run the following command to create a new Rails app called "installfest".

    ```shell
    rails new installfest
    ```

    This will add a new directory name "installfest" with the contens of a new Rails application.

1.  From Command Prompt, go into the new "installfest" directory by running:

    ```shell
    cd installfest
    ```

1.  Now, start the Rails application by running

    ```shell
    rails server
    ```

1.  Go to [http://localhost:3000](http://localhost:3000) to see the running application!

    ![Browser showing Yay! You're on Rails](screenshot.jpg)

1.  Now that you've verified everything is working, you can stop the application by running `Ctrl-c` in the Command Prompt.

    You can also remove the "installfest" directory.
{% endlist %}

{% highlight shell %}
C:\Users\awesomesauce>rails new installfest
      create
      create  README.md
      create  Rakefile
      create  config.ru
      create  .gitignore
      create  Gemfile
      ...
         run  bundle install
      ...
      Bundle complete! 12 Gemfile dependencies, 56 gems now installed.
      Use 'bundle show [gemname]' to see where a bundled gem is installed.

C:\Users\awesomesauce>cd installfest

C:\Users\awesomesauce>rails server
=> Booting Puma
=> Rails 5.0.1 application starting in development on http://localhost:3000
...
Use Ctrl-C to stop
Started GET "/" for 127.0.0.1 at 2017-02-11 12:47:30 -0800
Processing by Rails::WelcomeController#index as HTML
  Parameters: {"internal"=>true}
  Rendering C:/Ruby23/lib/ruby/gems/2.3.0/gems/railties-5.0.1/lib/rails/templates/rails/welcome/index.html.erb
  Rendering C:/Ruby23/lib/ruby/gems/2.3.0/gems/railties-5.0.1/lib/rails/templates/rails/welcome/index.html.erb (15.6ms)
Completed 200 OK in 78ms (Views: 42.6ms | ActiveRecord: 0.0ms)



Exiting
Terminate batch job (Y/N)? y
{% endhighlight %}
{% endsteps %}
