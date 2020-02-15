
Overview of Technical Architecture
=========================================

1 Overall Overview
------------------------

HiCoin is positioned as a **Wallet Technology Platform** 。

**Wallet** means finance, so our entire system is built according to international financial system standards (ISO27000, SOC, CC EAL4 +, FIPS 140-2 level3, etc.).

**Technology Platform** means that we, as an underlying service provider of the Blockchain, need to be technically proficient with strong scalability. HiCoin technologically adopts the strategy of **Five Horizontal & One Vertical Modules** ，and enables low coupling dynamic expansion among modules through micro services. Meanwhile, we provide a full range of WaaS interface documents and open platform documents, which really makes the wallet become a platform for business activities, so that the wallet not only **Goes Out** （as a basic service (of being integrated into other applications, and providing payment or chain services for other applications, like what Alipay does), but also **Connects In** (other applications like applets are integrated into the wallet to open accounts and transfer assets).

Summary of Programming Languages Used at Each End:

:Back End: Java （SpringCloud, RabbitMQ, Mysql, Redis, ）

:Front End: Vue technology stack (multi-site framework built by vue-cli3.0 and webpack), React

:IOS Client: Swift is a main programming language, which adopts MMVC mode and also supports Object-C mixed programming .

:Android Client: Kotlin is the main programming language, which adopts MVP mode and also supports Java mixed programming.

:Underlying Wallet: t depends on the programming language used for different main chains, such as go, python, C / C + +.

Overall Framework Diagram:：

.. image:: images/tech_framework.png
   :width: 700px
   :height: 394px
   :scale: 100%
   :align: center


2 Overall Technical Framework
------------------------------------

The overall framework of HiCoin is expanded by adopting five horizontal and one vertical modules to enable low coupling, high concurrency and strong robust among modules.

**Five Horizontal Modules** means that the system is divided into five layers - data layer, base layer, business layer, access layer and display layer from bottom to top according to different business attributes. High concurrency strategy is customized based on different module features, and low coupling is enabled among different layers and modules.

**One Vertical Module** means to make the Five Horizontal Modules more stable and robust by monitoring, routing, disaster tolerance, load balancing and other governance services.

It is shown in the figure below:

.. image:: images/tech_framework_full.png
   :width: 700px
   :height: 501px
   :scale: 100%
   :align: center

3 Server Network Framework
------------------------------------

The whole HiCoin network framework is divided into three areas: **Computer Room Network Area** 、**Load Balancing Area** 、**Computing Resource Area** .The overall architecture is featured by local active-active computer rooms to ensure high availability of services and no failure of single points, and automatically expand capacity within one minute when the access pressure exceeds the target without manual intervention. In addition, multiple subnets are set up through VPC, and security interworking policies are set up among subnets.


.. image:: images/tech_framework_network.png
   :width: 700px
   :height: 350px
   :scale: 100%
   :align: center


4 Guarantee of More Than 30 Security Technologies
----------------------------------------------------------
HiCoin has in-depth cooperation with the world’s top blockchain security companies: Certik, Johnwick.io, SlowMist, Beosin, Chainsguard and adopts more than 30 security technologies by maining focusing on user, business and system to guarantee a more secure system.

.. image:: images/tech_framework_securty.png
   :width: 700px
   :height: 394px
   :scale: 100%
   :align: center


This article was proofread by Ryan.
