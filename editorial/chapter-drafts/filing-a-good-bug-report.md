---
description: 
author: 
updated: 
---

# Filing a Good Bug Report

Any software you work on should indicate where to submit a bug report and what rules to follow. The information may be on the project's web page or in its repository, probably in a README or CONTRIBUTING file.

The basic rules are simple: do what the project tells you to do, and include any information that might be useful to someone trying to narrow down the problem. This includes:

* Information about the software you're using, particularly the version number.
* A precise description of what you did to trigger the problem, including a piece of your relevant source code if you're describing a bug found while programming.
* Information about your environment, such as types and version numbers of your hardware, operating system, and browser (if you're reporting a bug that appears in software that runs in your browser).

Those are the basics. Other useful advice can be found on a [Mozilla site](https://developer.mozilla.org/en-US/docs/Mozilla/QA/Bug_writing_guidelines). A [posting on Sifter](https://sifterapp.com/academy/essays/great-bug-reports/) and a [posting on Testlio](https://testlio.com/blog/the-ideal-bug-report/) list some useful considerations and mostly agree with each other. The rest of this article offers more considerations that can save you from wasting your time, and the time of the developers who handle bug reports. These steps are:

* Make sure you really have found a bug, and that no one has already reported it.
* Make sure your software is up-to-date, if you can.
* Report the sequence of events that caused the bug in a manner that is as narrow and simple as possible.

## Make sure you really have found a bug

A large number of bug reports are dismissed as user errors—that is, the person reporting the bug did not understand the proper use of the software, or simply introduced an error in their own code. Another large set of bug reports turn out to be duplicates; that is, someone else has already reported the error.

To distinguish a bug from a user error (that is, whether you are using the software in a way it wasn't designed for), read the project's documentation carefully, if documentation is available. If you're running Software as a Service (SaaS), which runs in your browser, check their web page to find out whether your browser is supported---lack of such support is a common reason that a site doesn't work. If you find that the error is your own, but that it results from a confusing design decision, you can request a change.

It's often hard to determine which piece of software has caused a bug. For instance, if you are trying to log in from web site A to web site B and you're being rejected, you really don't know which web site is the source of the problem. If you're writing a program that reads in several libraries and doesn't work right, it's hard to know which library has to be corrected. So if you're not sure whom to report a bug to, try to cut down the libraries or tools you use (a process described later in the section \"Report a narrow sequence of events\") or try alternatives. For instance, see whether you can log in from web site A to web site C. If you succeed, web site B is probably the source of your problem.

It's more efficient for everybody if you can avoid opening an issue on a known problem. To find out whether the bug has been reported before, think of words that describe your problem and search for them in the project's bug database (in GitHub or GitLab, an issue board). Try to use search terms that are commonly used by the project. For instance, if they often talk about a \"key\", it's best to search for that term than to search for \"password\", even if \"password\" is a reasonable way to describe the key.

If you find that your problem has already been reported, you may be able to see in the database a fix, work-around, or date when a fix is promised. If you yourself have found useful information that's not already reported---a fix, workaround, or just extra information to help locate the problem---please add it as a comment in the database. It may be worth adding a comment to an existing report just to say that you're experiencing the problem too. In some systems, including GitHub and GitLab, you can "upvote" a bug report, which may persuade developers to assign a higher priority.

Even if your problem was caused by your own mistake, certain problems should never happen in software: for instance, the software should never crash, never hang for indefinite periods of time, and never expose internal data or internal error messages meant for the developer. These problems are always worth reporting.

## Update your software

Even if a bug isn't reported, a newer version of software may fix it. Therefore, you should make sure that everything that could affect a problem---the software you're using, your operating system, etc.\--is up to date while trying to solve your problem. Certainly, a project should fix any version that is still officially supported. And SaaS should run in every popular browser and should support very old browser versions. Robust projects should support a reasonable set of older software versions. You might not have to upgrade to the newest version, but you might need to fix your problem by installing an intermediate bug-fixing release. If so, you will probably learn of that solution by searching the issues.

## Report a narrow sequence of events

Developers on a project need to reproduce your bug in order to investigate it. You should report a minimal set of tasks, or a minimal set of code and data, that shows the bug in action. Be generous in the amount of information you report on your environment (such as the system you're on and all version numbers of the relevant software involved in the bug). Be precise but parsimonious in describing the steps needed to reproduce the bug. If your build process includes extra steps such as code preprocessors, just take the output from those steps and submit a simpler workflow.

Programmers should include a code sample that causes the bug to occur. They also may need to show data. This presents a problem with confidentiality, because both code and data may show internal information that you don't want your competitors or the general public to see. The data may even be protected by regulation. Remember that bug reports on open source projects are public documents.

To submit a bug report with code that will not reveal corporate secrets, put the offending segments into a small mock program that can run on its own, and change variable names or other strings that may suggest what you're doing with the code.

There are many ways to anonymize or fuzz data. The best way is to create mock or synthetic data that has the same effect on the bug as your real data. Some companies compile fake data sets in advance—but make sure it triggers the problem you're trying to report before using the data in the report. If anonymization is difficult, try some combination of the following techniques for your existing data:

* Omit sensitive fields, such as credit card numbers.
* Switch fields from row to another. If your data contains a Henry Molton and a Greta Blustein, submit a bug report listing a Greta Molton and a Henry Blustein. The same trick can be used to mix up birthdates, parts of the address, etc.
* Add or subtract an arbitrary amount from numerical fields.

Of course, you have to make sure you can still invoke the bug with all these changes.
