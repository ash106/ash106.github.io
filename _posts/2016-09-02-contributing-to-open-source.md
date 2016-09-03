---
layout: post
title: Contributing to Open Source
---

So you just finished your coding bootcamp or reading Michael Hartl's wonderful [Rails Tutorial](https://www.railstutorial.org/) (or read one of the countless articles about why contributing to open source is so important), and you're ready to start pumping out some awesome open source code. As a newly christened Rails developer, the most natural place to start would be the Rails [repo](https://github.com/rails/rails). You open up the issues tab and are greeted by a bunch of this nonsense:

![Rails issues](/assets/rails_issues.png)

Hmm... I know some of those words. Ok, maybe we'll come back to Rails later. What else do I use a lot? Let's try the Bootstrap [repo](https://github.com/twbs/bootstrap). Again, you head to the issues tab and find a bunch of text seemingly written in a different language.

![Bootstrap issues](/assets/bootstrap_issues.png)

In my experience, this is where the doubt starts to creep in. *Maybe I'm not good enough to help with open source. Maybe I'll **never** be good enough to help with open source.* Ok, stop right there. You absolutely can contribute to open source at your current skill level. Are you going to submit an amazing patch to Rails as your first pull request? Incredibly unlikely. Popular projects like Rails have a huge number of moving parts and a lot of very smart, experienced people working on them. Your three months of Rails experience are not going to get you very far into fixing Rails bugs. However, if you move down to some slightly less popular gems and projects, you can start to find and fix bugs pretty easily. Here are a few examples of how I did just that.

### thoughtbot script

When I got my last laptop, I decided to use thoughtbot's laptop [script](https://github.com/thoughtbot/laptop) to setup my development environment. It's a shell script that installs a bunch of awesome tools like Zsh, Heroku Toolbelt, ImageMagick, Rbenv, etc. I tried running the script a few times and I kept getting an error on this line:

{% highlight bash %}
node_version = "0.10.28"
{% endhighlight %}

I had never written a shell script before, so I googled "shell script variable declaration" and the first result was, unsuprisingly, a Stack Overflow [link](http://stackoverflow.com/questions/2268104/bash-script-variable-declaration-command-not-found). Oh ok, you can't have spaces in your variable declaration. I changed the line to this:

{% highlight bash %}
node_version="0.10.28"
{% endhighlight %}

I ran the script again and it worked. Great, I fixed the bug! Now how do I get this fix added to the main repo?

Creating a pull request on a real project seems intimidating until you do it a couple times and realize how shockingly easy it is. For a small fix like this, you don't even have to manually fork the repo. Just click on the file you want to change in the repo and then click the pencil icon in the upper right corner of the file.

![GitHub buttons](/assets/github_buttons.png)

Make your edits to the file and add a title and description of what you are changing in the pull request. That's it! Submit your pull request and wait for a maintainer of the project to accept it. 

![thoughtbot pull request](/assets/thoughtbot_pull_request.png)

Do you see how easy that was? I didn't even write any code. All I did was **delete two spaces**. You have to think about the context of what deleting those two spaces means though. This script has over 5,000 stars on GitHub. The commit that broke the script was made three months before I submitted the fix. That means possibly hundreds of users had tried to use this script and had it fail on them. It turns out deleting those two spaces was actually pretty helpful. Never underestimate the power of fixing small bugs.

### Rails Composer

I used [Rails Composer](https://github.com/RailsApps/rails-composer) for a ton of projects during and after the bootcamp I attended. It's great for quickly getting a project going and trying out a bunch of different options for things like front end frameworks and authentication gems. I love Rails Composer, but there was always one small problem that drove me nuts.

![Bootstrap alert with and without alert-dismissible class](/assets/bootstrap_alerts.png)

On the left is the Rails Composer Bootstrap alert. On the right is a standard Bootstrap alert. See the difference? It's the wrong color and not vertically centered. It drove me *insane*.

I just lived with it for a while, but one day I was poking around in the Bootstrap docs and realized what was missing from the Rails Composer alerts!

{% highlight css %}
.alert-dismissable,
.alert-dismissible {
  padding-right: 35px;
}
.alert-dismissable .close,
.alert-dismissible .close {
  position: relative;
  top: -2px;
  right: -21px;
  color: inherit;
}
{% endhighlight %}

There is a class called `alert-dismissible` that takes care of the position and color of the close icon. Adding that class to the alert div immediately fixed the problem. 

So I just add that class to the Rails Composer repo and call it fixed, right? Well here's another tip for contributing to open source: **Make sure you read the [Contributing section](https://github.com/RailsApps/rails-composer#contributing)**. I didn't take this advice, and my original [pull request](https://github.com/RailsApps/rails-composer/pull/229) is still open to this day.

A few months later I realized my mistake, and after some poking around I found out that I was supposed to add my changes to the RailsLayout [gem](https://github.com/RailsApps/rails_layout).

![RailsLayout pull request](/assets/rails_layout_pull_request.png)

Again, we aren't talking about huge changes here. I just **added a single CSS class**. However, I know that a ton of beginners use Rails Composer to make their applications. I probably just made hundreds, if not thousands, of blogs and Twitter clones look just a tiny bit better.

### CodeTriage

This last example is an even simpler way to contribute to open source: **submitting issues**. Open source projects really appreciate well-written bug reports, and as a developer you are in a great position to provide those bug reports.

I was recently using a site called [CodeTriage](https://www.codetriage.com/) to find open source projects to contribute to. I noticed that the number of issues on the homepage didn't match the number of issues for the actual repo on GitHub, so I wrote up an issue.

![CodeTriage issue](/assets/code_triage_issue.png)

I provided as much detail as I could about the bug (which was pretty simple in this case), and the project maintainer was able to find and fix the bug within a couple days.

I hope by now the point of this post is starting to sink in. **If you want to start contributing to open source, start fixing small things right now.** 

- Adding one line of code
- Deleting some extra whitespace characters
- Adding `.rb` extension to a file
- Changing single quotes to double quotes
- Submitting issues

These are all real examples of contributions I've made. None of them are very hard to do, but add enough of them together and you start being pretty helpful. Go check out some of your most used repos, or get on [CodeTriage](https://www.codetriage.com/) and find a project that looks interesting. I promise there is something you can start doing right now!
