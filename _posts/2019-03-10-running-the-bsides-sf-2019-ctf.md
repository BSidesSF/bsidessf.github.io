---
layout: post
title: "Running the BSides SF 2019 CTF"
category: CTF
date: 2019-03-10
tags:
  - CTF
  - BSidesSF
---

By [@Matir](https://twitter.com/matir), 2019 CTF Team Lead.

## The Event ##

This year, I had the privilege to lead the team for the BSides San Francisco
CTF.  We had 1112 active players on 676 teams over the 32 hour CTF.
Collectively, 2740 flags were submitted to 41 of our 43 challenges.  So far, the
[CTFTime ratings](https://ctftime.org/event/753/weight/) have been excellent,
and I hope we'll be able to do that again.

Before I go any further, I want to give kudos to my entire team:

- [iagox86](https://twitter.com/iagox86)
- [c0rg1](https://twitter.com/itsC0rg1)
- [symmetric](https://twitter.com/bmenrigh)
- [bryane](https://twitter.com/cornflakesavage)
- [exploitexercise](https://twitter.com/exploitexercise)

This would not have been possible without all their efforts.  I also want to
give a special shoutout to Puneet, who handled all the physical logistics for us
so we could focus on building the CTF.  I also want to thank the BSidesSF staff
and volunteers for giving us the space and opportunity to do this.  Also thanks
to the bar staff for keeping us "hydrated!"

## The Infrastructure ##

(Full disclosure: I'm a member of the Google Information Security Team.)

We were running [the scoreboard](https://github.com/google/ctfscoreboard) I
originally wrote for the Google CTF (though it's no longer used for that
purpose), hosted on [Google AppEngine](https://cloud.google.com/appengine/).  I
love hosting apps on a runtime like that -- the scaling and replication is just
magic, so we didn't have the typical latency spike a lot of CTFs do at the very
beginning.  95th percentile latency remained under 500ms, which is a result I'm
very happy with.

![Traffic](/images/ctf_2019/sb_traffic.png)

All of the online challenges were run on Kubernetes on [Google Cloud
Platform](https://cloud.google.com/) (for the 3rd year straight).
We continue to love this option, because we run Docker locally for building &
testing challenges, then transform these images straight to Kubernetes.
Additionally, Kubernetes provides capabilities like load balancing that allow us
to scale challenges up when some people feel the need to try to brute force.

This year, for the first time, we attempted to use Network Policies to prevent
access to the GCP metadata API, which worked, until I inadvertantly deleted the
policies while debugging an issue with another challenge.  Fortunately, I don't
believe this was exploited during the CTF, but I did notice some exploitation
attempts after the game.

Another first for this year was the use of an `Ingress` for all of our HTTP
services.  We used a wildcard certificate from Let's Encrypt and then performed
distribution to backends based on the hostname provided by the client.  This
allowed us to use a single external IP, easily provide HTTPS for the challenges,
and also provided load balancing for the challenges.

All of this infrastructure comes with some difficulties compared to just
spinning up a bunch of VMs.  First off, there's layers of complexity, like the
load balancers and the pods that contain containers.  There's multiple backends,
so if only one is acting up, it's harder to debug.  Additionally, for anything
with load balancing, it either needs to be stateless, or you need a way to sync
the state.  (IP load balancing might work, except we had a large portion of our
players coming from the one IP on site.)

[Google Cloud](https://cloud.google.com/) was nice enough to give us credits to
run all of our infrastructure, so big thanks to them for making this possible
for over 1100 players.  Questions about how we ran this?  Reach out to me on
[Twitter](https://twitter.com/matir) or see my follow-up
[blog posts](https://systemoverlord.com).

## Challenges ##

Rather than trying to describe the challenges, I'd rather just point to our
public [release of our source
code](https://github.com/bsidessf/ctf-2019-release).  Check out the challenges
and keep in mind that (as of writing) we're still running the services and the
[scoreboard](https://ctf.bsidessf.net).  Give them a shot and now you can see
how the source and actual service interact.

## Winners ##

Congratulations to our 3 winners:

1. dcua (2nd year running)
2. perfect blue
3. OpenToAll

I also want to congratulate every team that played.  If you learned something or
had a good time (preferrably both), then we did our jobs correctly.

## Writeups ##

There have been a number of challenge writeups appearing, including author
writeups:

- [My Author Writeups](https://systemoverlord.com/)
- [CTFTime Writeups](https://ctftime.org/event/753/tasks/)
- [dcua Writeups](https://aadityapurani.com/2019/03/07/bsidessf-ctf-2019-mobile-track/)
- [xor19x91 Writeup](https://x0r19x91.github.io/2019/bsides-opendoor)

## Conclusion ##

It's been a fun year, and most of the staff will be back for next year.  If
you're interested in joining us to write some challenges, please reach out to
`ctf@` this domain.  We'd love to have new talent, feedback, or suggestions.
