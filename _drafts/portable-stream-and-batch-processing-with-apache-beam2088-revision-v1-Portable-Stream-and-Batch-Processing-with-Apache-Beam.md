---
id: 2095
title: Portable Stream and Batch Processing with Apache Beam
date: 2017-12-08T20:13:12-05:00
author: Alan Verdugo
layout: revision
guid: http://www.kippel.net/blog/?p=2095
permalink: /?p=2095
---
<p style="text-align: justify;">
      I had the opportunity to attend another one of the <a href="https://academy.wizeline.com/apache-beam/" target="_blank" rel="noopener">Wizeline&#8217;s academy</a> sessions. This time, it was about <a href="https://beam.apache.org/" target="_blank" rel="noopener">Apache Beam</a>, a <strong>B</strong>atch and Str<strong>eam</strong> processing open source project. Wizeline brought three instructors from Google itself to explain what Beam is, how to use it, and its main advantages over their competitors. All three instructors had impressive backgrounds and were very nice and open to comments and questions from a group of students that only had basic knowledge on the subject.
</p>

<p style="text-align: justify;">
      <a href="http://davorbonaci.com/" target="_blank" rel="noopener">Davor Bonaci&#8217;s</a> explanations were particularly useful and interesting. He has a lot of experience talking in conferences about these topics and it shows. He was able to clearly explain such a complex technology in a way that could be understood by anyone while still ensuring that the we also understood the huge potential in Beam.
</p>

&nbsp;

<p style="text-align: justify;">
      There were three concepts that I found extremely interesting:<strong>   </strong>
</p>

<p style="text-align: justify;">
  <strong>    Windowing:</strong> In streaming, we will eventually receive data that is out of time in the context of when it was generated and when we received other data. The concept is useful to define how lenient we will be with this &#8220;late&#8221; data. We will have an easy way to specify categories of this data and group them according to our business rules.
</p>

<p style="text-align: justify;">
      An example of this would getting records at 12:30 that were created at 12:10. At that point in time, we should be only processing records that were created in the last few minutes (or even seconds, according to your needs). However, that late record could be crucial for our processing and we need to find a way to discern if we keep it or if we ignore it completely. With windowing, we can achieve this.
</p>

<p style="text-align: justify;">
  <strong>    Autoscaling:</strong> This is probably the holy grail of IT infrastructure management. The ideal scenario would be to have a &#8220;lean infrastructure&#8221;. One that, in any given moment, only has the exact amount of processing power that is needed, no more and no less. However, thanks to the global nature of the Internet and the variations in usage according to time zones and seasons, it is practically impossible to achieve this. Resources are either over or under-allocated, the first option means wasting at least some of the infrastructure (and hence money). The second means to not be able to handle usage spikes when they occur (and they <em>will</em> occur eventually if you are doing things right).
</p>

<p style="text-align: justify;">
      As the name implies, Autoscaling attempts to let the infrastructure grow organically when and how it needs to, and to reduce it once it is not needed anymore. This obviously has huge benefits, like having the peace of mind of knowing that the infrastructure can take care of itself but also knowing that servers will not be over-provisioned carelessly. The cloud only needs to be properly orchestrated according to the data processing needs, and we can finally deliver this. I can only imagine what would be possible once this is combined with the power of containers or even Unikernels and their transient microservices.
</p>

<p style="text-align: justify;">
      You can read more about Autoscaling here: <a href="https://cloud.google.com/blog/big-data/2016/03/comparing-cloud-dataflow-autoscaling-to-spark-and-hadoop" target="_blank" rel="noopener">https://cloud.google.com/blog/big-data/2016/03/comparing-cloud-dataflow-autoscaling-to-spark-and-hadoop</a>
</p>

<p style="text-align: justify;">
  <strong>    Dynamic workload rebalancing:</strong> When a processing job is created, it is (hopefully) distributed equally across all the nodes of a cluster, however, due to subtle differences in bandwidth, latency and other factors, some nodes always end up finishing their assignment later, and at the end of the day, we cannot say that the job is finished until the last of these stragglers is done. In the meantime, there will be many nodes that are idle, waiting for the stragglers to finish. Dynamic workload rebalancing means that these idle nodes will try to help the stragglers as much as possible, and in theory, this will reduce the overall completion time of the job. This, coupled with Autoscaling, could mean that the waste of resources is minimum.
</p>

<p style="text-align: justify;">
      You can read more about dynamic workload rebalancing here: <a href="https://cloud.google.com/blog/big-data/2016/05/no-shard-left-behind-dynamic-work-rebalancing-in-google-cloud-dataflow" target="_blank" rel="noopener">https://cloud.google.com/blog/big-data/2016/05/no-shard-left-behind-dynamic-work-rebalancing-in-google-cloud-dataflow</a>
</p>

&nbsp;

<p style="text-align: justify;">
      One student asked if it would be worth it to study Beam and forget about Spark or the other platforms. It may sound like a simple question but it is something we all were thinking. Davor&#8217;s response was great. He said that whatever we studied, our main focus should be in writing code and building infrastructure that is able to scale regardless of the platform that we wish to use. Beam is not a Spark killer, they have different approaches, different methodologies, and the people working in these projects have different ambitions, goals, and beliefs. Besides, the community keeps evolving, the projects will continue to change, some will be forgotten and new ones will be created. There is a huge interest in data-processing tools due to the increased speed and volume of our data needs, which will only keep increasing. Because of that, this part of IT is experiencing violent and abrupt growing pains. I just don&#8217;t think that right now we can settle and learn just one technology since it may disappear (or change dramatically) in the very near future.
</p>

<p style="text-align: justify;">
      There are some things that can still be improved in Beam. One example is the interaction with Python and Spark, another would be making it more user-friendly, but there is a group of smart people that is quickly tackling these issues and adding new and great features, so it would be a good idea to keep learning about Beam and to consider it for our batch and stream processing needs.
</p>

<p style="text-align: justify;">
      Overall, I really enjoyed the workshop. As I mentioned before, all three instructors were very capable and had a deep understanding of the technology, its use cases and its potential. Besides it was really enjoyable to talk with them about the current state and the future of data processing. I will certainly keep paying attention to the Beam project.
</p>

<p style="text-align: justify;">
      I would like to thank Davor, Pablo and Gris from Google, and all the team behind the Wizeline academy initiative.
</p>