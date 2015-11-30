---
layout: page
title: "Sample Submission"
permalink: /cfp/sample-submission.html
--- 

<p><strong>Note to the reader: This is a completely made up talk (courtesy of <a href="http://shmoocon.org/">ShmooCon</a>). However it should give you an idea of what types of information to include, the lowest level of detail to use, and the overall flow of a good submission.</strong></p>
<p><strong>1. Title of Presentation</strong><br />
Template Management using Osiris</p>
<p><strong>2.  Presenter(s) Name </strong><br />
Bruce Potter</p>
<p><strong>3. Abstract </strong><br />
Osiris is an open source integrity monitoring software system written by the Shmoo Group many years ago. It is used in many organizations as a scalable means to monitor for changes created by change management violations and penetration by external actors. One of the challenges with Osiris (and any integrity monitoring tool) is minimizing the amount of noise created by inconsequential changes. Osiris addresses this problem through the use of templates that limit the scope of monitoring based on the host OS and user customizations. Unfortunately as OS&#8217;s evolve, the set of files that SHOULD be monitored can often change and osiris templates don&#8217;t account for these changes.</p>
<p>We have developed a lightweight tool to monitor running systems to instrument changes over time and ultimately recommend changes to the currently deployed templates. Rather than performing full blown scans and checksumming to look for changes, this tool will only examine MAC times thereby dramatically reducing a &#8220;normal&#8221; instrumentation scan. Administrators are able to look at the statistical data under the tool and determine what changes to accept to the running template. We have also developed a public database of templates based on results from the tool so that organizations can provide updated templates back to the community.</p>
<p><strong>4. Bio </strong><br />
Bruce Potter is jack of many trades and master of none… well, maybe public speaking, but that&#8217;s about it. Bruce has been doing security related things for nearly 20 years, which makes him feel old. Bruce is the founder of The Shmoo Group, helps out with ShmooCon, and has more Shmoo-branded shwag in his basement that he&#8217;ll publicly admit.</p>
<p><strong>5. Detailed Outline </strong></p>
<p>&#8211; Who we are (3 mins) &#8211; We&#8217;re The Shmoo Group. We developed osiris originally and for many years it was maintained by member Brian Wotring. We have many years experience in integrity monitoring research, engineering including leveraging hardware modules to provide better assurance of integrity measurements.</p>
<p>&#8211; Quick Osiris Background (5 mins) &#8211; Osiris is a multi platform integrity monitoring tool that has been widely deployed. However, many in the audience may be unfamiliar with how it works. We&#8217;ll provide an architectural overview of Osiris and discuss a few use cases</p>
<p>&#8211; The Problem with Template &#8220;Drift&#8221; (15 mins) &#8211; Over the last year, we&#8217;ve examined several operating systems and examined how and when core, critical files were moved to new locations/names/etc. These changes were usually occurred during the application of patches rather than administrative activities. We will present data on how large the problem is and how the movement (or &#8220;drift&#8221;) of these files caused some of them to fall out of bounds for the existing Osiris templates</p>
<p>&#8211; A lightweight solution (15 mins) &#8211; The whole purpose of Osiris templates is prevent scanning all files on the filesystem. A scanner that attempts to identify drift through checksumming would be counterproductive to the performance goals of Osiris. Our solution was to examine the MAC times of all files on the filesystem as a low priority thread. We then examine the MAC times and look for files that fall in to the following 3 buckets<br />
&#8211; M/C time did not change and file is in Osiris template (good)<br />
&#8211; M/C time changed a small number of times (1-2), nearby files did the same. Files not in Osiris template (candidates for inclusion)<br />
&#8211; M/C times changed constantly. Files outside Osiris template (probably user specific files that aren&#8217;t system security relevant. Not a good candidate for inclusion)</p>
<p>&#8211; Demo (10 mins) &#8211; We&#8217;ll show the interface we created for template management and demonstrate the process an administrator goes through to update system templates. We&#8217;ll also demonstrate our database and service that can help jumpstart an administrators modifications.</p>
<p>&#8211; Questions (2 minutes)</p>
<p><strong>6.  List of other conferences</strong><br />
We presented our data on system file drift at BSides Antarctica in July. However that research as been updated and the tools and database are completely new.</p>
<p><strong>7. Why is this a good fit for BSides SF</strong><br />
We feel that integrity management is an important capability for any modern enterprise, especially with the ease of which adversaries can modify attacks and malware to avoid detection by AV and IPS. We feel that our template update system provides a key component that is otherwise missing in integrity management systems.</p>
<p><strong>8. Previous experience</strong><br />
We have presented at BSides SF before. We have also delivered presentations at DefCon, Blackhat, The Gathering of The Shmoo, and InfoSec Anonymous</p>
<p><strong>9. Proceedings</strong><br />
Sure.</p>
<p><strong>10.  List of facilities requested </strong><br />
We need to be able to project 2 different systems at one time for our demonstration. Please let us know if that&#8217;s a problem as we&#8217;ll retool our demo to accommodate one screen.</p>
