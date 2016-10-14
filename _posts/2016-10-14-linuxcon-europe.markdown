---
layout: post
title: LinuxCon Europe 2016 ( aka Presenting for the first time at a conference)
modified: 2016-10-14
categories:
description:
tags: []
image:
  feature: main-background.jpg
  credit: 7themes
  creditlink: http://7-themes.com/7025787-brown-wallpaper-background-dekstop.html
comments:
share:
date: 2016-10-14T22:30:06+02:00
---

Berlin was the host of LinuxCon Europe this year, 4-6 october 2016.
I had the opportunity to attend this conference as part of the Outreachy
internship with the Linux Kernel and took the chance to be part of the
Outreachy Kernel Report Panel session and present the work that I did,
what I've learnt and how did this internship helped me.

Unlike Linaro Connect, the conference that I attended sometime in March,
I had a bunch of people with me at the LinuxCon Europe. First of all, I
met Julia, our project coordinator, and all the other participants from
various rounds on the Outreachy Kernel internship. Also, some of my
classmates where there as a reward for winning an Operating Systems
contest that is help in my university.

The Outreachy Kernel Report session was held in the first day of the
conference. We did not expect many people to attend it and so it was but
those that were there are the people that are actually interested in how
the kernel community welcomes the newbies. Because, let's face it.. even
though some of us now have full-time jobs we are still newbies. Julia
presented the program as a whole, all the interns presented their work
in about 5 minutes each and then the questions began. One of my favorite
one is about the ramp-up process that a newbie goes through on order to
get the hand of creating a patch, sending it as an text email on some
mailing list, review it, etc. I, personally, have no particular problem
with the mailing list way of work of the kernel, it seems to me that
it's as clean as possible and easy to use. But if you want to hear Greg
KH's opinion on this check out this
[video](https://www.youtube.com/watch?v=L8OOzaqS37s)

You can find the slides
[here](http://events.linuxfoundation.org/events/linuxcon-europe/program/slides).
My part won't be there (at least when I published this).. because I am
that kind of person that waits to get things done in the last minute.

When the hard part was done - we all presented ouw progress - the fun
part began. I attended as many sessions. In the next part I will present
some of the most interesting ones.

* Geo-Replication and Disaster Recovery for Cloud Object Storage with
  Ceph Rados Gateway - Orit Wasserman

  During the time that I worked on Ceph - the distributed filesystem run
  by RedHat and Sage Weil - I only investigated and tried to
  improved cluster-wide performance without knowing or going into the
  concept of Geo-Replication. Learn a lot of new things and the
  direction Ceph is going at.


 * Ceph and Flash - Allen Samuels

  Efficiency doesn't only come from smart algorithms, sometimes you also
  need to choose your hardware appropriatly. Allen thaught us how to
  improve our Ceph clusters by working at the storage hardware.
  
 * lguest: A Journey of Learning the Linux Kernel Internals - Daniel
  Baluta

  Daniel is a teaching assistent in my university, an Intel employee and
  also a mentor in the Outreachy Kernel. He was the one that held a
  kernel entry-level workshop in our faculty to introduce on the linux
  field from early on. This session was another attept to give newbies
  a welcoming entry in the kernel. lguest is basic hypervisor that
  introduces people into many important topics such as - interrupts,
  memorry assembly, stack trace etc. Great to watch.

 * Cgroups and namespaces, The Building blocks of linux containers -
   Rami Rosen

  Used Docker in order to create and run multiple containers that would
  create the Ceph cluster. Eventually you have to learn also how these
  containers are created and managed by the kernel. If you also have
  the same opinion, check Rami's talk.

  * Build your own ChromeOS distro and Image Server - Ronald G. Minnich

  Being able to run your own software from firmware to OS is really an
  incredible thing. Intersting to see how some companies give the
  end-user the possibility to change everything in their systems. Unlike
  the majority, Google is doing that.

  * CephFS and LXC: Container High Availability and Scalability,
    Redefined - Florian Haas

  Learnt about ansible playbooks in corelation with containers and LXC.
  Will have a look at that in the near future.


  * Locking down your Systemd services - Lennart Poettering

  Last but not least, systemd - the controversial init system that
  lately becomes much more than that. In this talk, Lennard presented
  new options for service sandboxing. I think that going before people
  and owning your opinions and decisions no matter what takes a great
  man.


Fun fact:

  25 years of Linux. I remember that during one of the keynotes, the
  presenter ask to raise the hand the people that were no older than 25.
  Well, not so many as I would expect but some. Oh, and he reminded nnot
  be too eager.. we will also get old.


Fun fact #2:

  Linus did not attend LinuxCon.., instead it went to Linaro Connect LAs
  Vegas where he presented its opinion of the ARM ecosystem. Google it.

 
All in all, the LinuxCon experience was one of a kind. I hope to attend
it also next year and to be a better part of the community as I grow as
a person and a engineer.


