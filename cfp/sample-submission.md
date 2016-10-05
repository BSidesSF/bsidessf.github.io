---
layout: page
title: "Sample Submission"
permalink: /cfp/sample-submission.html
---

**Note to the reader**: This is a completely made up talk (*courtesy of [ShmooCon](http://shmoocon.org/)*). However it should give you an idea of what types of information to include, the lowest level of detail to use, and the overall flow of a good submission.

**1. Title of Presentation**

Template Management using Osiris

**2. Presenter(s) Name**

Bruce Potter

**3. Bio**

Bruce Potter is jack of many trades and master of none… well, maybe public speaking, but that's about it. Bruce has been doing security related things for nearly 20 years, which makes him feel old. Bruce is the founder of The Shmoo Group, helps out with ShmooCon, and has more Shmoo-branded shwag in his basement that he'll publicly admit.

**4. Abstract**

Osiris is an open source integrity monitoring software system written by the Shmoo Group many years ago. It is used in many organizations as a scalable means to monitor for changes created by change management violations and penetration by external actors. One of the challenges with Osiris (and any integrity monitoring tool) is minimizing the amount of noise created by inconsequential changes. Osiris addresses this problem through the use of templates that limit the scope of monitoring based on the host OS and user customizations. Unfortunately as OS's evolve, the set of files that SHOULD be monitored can often change and osiris templates don't account for these changes.

We have developed a lightweight tool to monitor running systems to instrument changes over time and ultimately recommend changes to the currently deployed templates. Rather than performing full blown scans and checksumming to look for changes, this tool will only examine MAC times thereby dramatically reducing a "normal" instrumentation scan. Administrators are able to look at the statistical data under the tool and determine what changes to accept to the running template. We have also developed a public database of templates based on results from the tool so that organizations can provide updated templates back to the community.

**5. Detailed Outline**

* Who we are (3 mins) – We're The Shmoo Group. We developed osiris originally and for many years it was maintained by member Brian Wotring. We have many years experience in integrity monitoring research, engineering including leveraging hardware modules to provide better assurance of integrity measurements.
* Quick Osiris Background (5 mins) – Osiris is a multi platform integrity monitoring tool that has been widely deployed. However, many in the audience may be unfamiliar with how it works. We'll provide an architectural overview of Osiris and discuss a few use cases
* The Problem with Template "Drift" (15 mins) – Over the last year, we've examined several operating systems and examined how and when core, critical files were moved to new locations/names/etc. These changes were usually occurred during the application of patches rather than administrative activities. We will present data on how large the problem is and how the movement (or "drift") of these files caused some of them to fall out of bounds for the existing Osiris templates
* A lightweight solution (15 mins) – The whole purpose of Osiris templates is prevent scanning all files on the filesystem. A scanner that attempts to identify drift through checksumming would be counterproductive to the performance goals of Osiris. Our solution was to examine the MAC times of all files on the filesystem as a low priority thread. We then examine the MAC times and look for files that fall in to the following 3 buckets
    - M/C time did not change and file is in Osiris template (good)
    - M/C time changed a small number of times (1-2), nearby files did the same. Files not in Osiris template (candidates for inclusion)
    - M/C times changed constantly. Files outside Osiris template (probably user specific files that aren't system security relevant. Not a good candidate for inclusion)
* Demo (10 mins) – We'll show the interface we created for template management and demonstrate the process an administrator goes through to update system templates. We'll also demonstrate our database and service that can help jumpstart an administrators modifications.
* Questions (2 minutes)

**6. List of other conferences**

We presented our data on system file drift at BSides Antarctica in July. However that research as been updated and the tools and database are completely new.

**7. Why is this a good fit for BSides SF**

We feel that integrity management is an important capability for any modern enterprise, especially with the ease of which adversaries can modify attacks and malware to avoid detection by AV and IPS. We feel that our template update system provides a key component that is otherwise missing in integrity management systems.

**8. Previous experience**

We have presented at BSides SF before. We have also delivered presentations at DefCon, Blackhat, The Gathering of The Shmoo, and InfoSec Anonymous
