---
marp: true
---

<!-- _class: invert -->

## Amazon Linux 2

* Amazon Linux 2 is a server operating system from Amazon Web Services (AWS).

* AL2 long-term support includes security updates and bug fixes for 5 years.

* AL2 is provided without charge as an Amazon Machine Image (AMI) for EC2.

* AL2 is available as container/virtual images downloads for free as well.

* These images can be used for on-premises development and testing.

---

## AL2 - Software

* Extras in AL2 provide bleeding edge software on a stable base of AL2.

* AL2 packages and configurations provide tight integration with AWS services.

* AL2 comes among others with many AWS tools (e.g. AWS CLI) and cloud-init.

* AL2 includes the widely adopted systemd init system - (was upstart before).

* AL2 includes a LTS Kernel tuned for enhanced performance on Amazon EC2.

---

## AL2 - Security

* AL2 limits remote access by using SSH key pairs and by disabling remote root login.

* AL2 reduces the number of non-critical packages which are installed on an instance.

* So, it limits exposure to potential security vulnerabilities and attack vectors.

* Security updates rated critical/important are automatically applied on initial boot.

* AL2 allows for kernel live patching (kernel patches without reboot or downtime).

---

## AL2 - Roots and History

* AL2 started off as a RHEL/CentOS modification.
  
* It has changed enough that you can probably call it a separate distro now.
  
* AL2 hasn't been compatible with RHEL/CentOS anything in quite a while.
  
* Blogs and forums show hundreds of issues wrt packages on RHEL/CentOS vs AL2 .

* Using *uname -a* returns

  * kernel "amzn1" - centos6
  
  * kernel "amzn2" - centos7
  
---

## CentOS Stream Announcement

* IBM/RedHat announced that the future of the CentOS Project is CentOS Stream on Tuesday, 8th December 2020.

* Over 2021 IBM/RedHat will be shifting focus away from CentOS Linux, the rebuild of RedHat Enterprise Linux (RHEL).

* On Tuesday, 16th November 2021, CentOS Linux 8, as a rebuild of RHEL 8, announced GA of its latest version.

* CentOS Linux 8 will EOL on 31 December 2021 and will handle it as directed by the CentOS Project Board of Directors.
  
* CentOS Stream continues after that date, serving as the upstream (development) branch of RedHat Enterprise Linux.

---

## CentOS Alternatives

* Current alternatives are:

  * AlmaLinux
  * CentOS Stream
  * Oracle Linux
  * Red Hat Enterprise Linux (RHEL) mit einem Developer Account kostenlos nutzen
  * Rocky Linux

* RHEL offers a free Developer Account meanwhile.

---

## AlmaLinux

* AlmaLinux is built and maintained by the developers at CloudLinux.

* CloudLinux traditionally provides server hosting and Linux software.

* CloudLinux builds and maintaines their in-house distro called CloudLinux OS.
  
* AlmaLinux offers AMD64/ARM64 builds and a special image for Raspberry Pi.

---

## RockyLinux

* Rocky Linux is headed up by Gregory Kurtzer, the original founder of CentOS.
  
* The Rocky Enterprise Software Foundation (RESF) is a Public Benefit
  Corporation (PBC) formed in Delaware (file number 4429978). The RESF was
  founded and is owned by Gregory Kurtzer and is backed by an advisory board of
  trusted individuals and team leads from the Rocky Linux community.

* Rocky Linux claims to be 100% bug-for-bug compatible with America's top distro.

* RockyLinux functions as a downstream build as CentOS had done previously.

* RockyLinux builds releases after - not before - they have been added upstream.

---

## Amazon Linux Extras

* Extras enables the consumption of new versions of application and supporting software.

* Examples include Ansible, memcached, nginx, Postgresql, MariaDB, Go, Redis, Rust.

* Extras provide topics containing all the dependencies to select software bundles.

* The packages associated with each topic are consumed with **yum** as usual.

* Available packages in extras can be listed with **amazon-linux-extras** accordingly.

* Packages from extras can be installed with **sudo amazon-linux-extras install**.

---

<!-- _class: invert -->

## Amazon Corretto

* Amazon Corretto is a no-cost, multiplatform, production-ready distribution of (OpenJDK).

* Corretto comes with long-term support including performance enhancements and security fixes.

* With Corretto, customers can develop and run Java applications on Linux, Windows, and macOS.

* Amazon runs Corretto internally on thousands of production services.

* Amazon Corretto is certified as compatible with the Java SE standard.

---

## Amazon Corretto 8 on AL2

* Enable corretto8 as Amazon Linux 2 Extra.

```
sudo amazon-linux-extras enable corretto8
```

* Install Amazon Corretto 8 as JRE.

```
sudo yum install java-1.8.0-amazon-corretto
```

* Install Amazon Corretto 8 as JDK.

```
sudo yum install java-1.8.0-amazon-corretto-devel
```

* The installation location is /usr/lib/jvm/java-1.8.0-amazon-corretto.<cpu_arch>.

---

## Amazon Corretto 11 on AL2

*  Amazon Corretto 11 has a 'headless' variant available. This variant omits runtime dependencies that are typically associated with GUI applications such as X11 and ALSA and is worth considering for server-oriented workloads.

* Install headless Amazon Corretto 11:

```
sudo yum install java-11-amazon-corretto-headless
```

* Install the full Amazon Corretto 11:

```
sudo yum install java-11-amazon-corretto
```

* The installation location is /usr/lib/jvm/java-11-amazon-corretto.<cpu_arch>.

---

## Amazon Corretto 15 on AL2

* Import the Corretto public key and then add the repository to the system list.

```
 sudo rpm --import https://yum.corretto.aws/corretto.key 
 sudo curl -L -o /etc/yum.repos.d/corretto.repo https://yum.corretto.aws/corretto.repo
```

* After the repository is added, Corretto 15 can be installed by running:

```
sudo yum install -y java-15-amazon-corretto-devel
```

---

## Amazon Corretto 16 on AL2

* Import the Corretto public key and then add the repository to the system list.

```
 sudo rpm --import https://yum.corretto.aws/corretto.key 
 sudo curl -L -o /etc/yum.repos.d/corretto.repo https://yum.corretto.aws/corretto.repo
```

* After the repository is added, Corretto 15 can be installed by running:

```
sudo yum install -y java-16-amazon-corretto-devel
```

---

## Amazon Corretto 17 on AL2

* Amazon Corretto 17 has a 'headless' variant available. This variant omits runtime dependencies that are typically associated with GUI applications such as X11 and ALSA and is worth considering for server-oriented workloads.

* The Amazon Corretto 17 'headful' variant adds support for X11 and ALSA.

* There is also a Amazon Corretto 17 'devel' package which contains the JDK development tools.

* There is also a Amazon Corretto 17 'jmods' package containing the JMods to create custom runtime images.

---

## Amazon Corretto 17 on AL2 (II)

* Install the headless Amazon Corretto:

```
sudo yum install java-17-amazon-corretto-headless
```

* Install the headful Amazon Corretto:

```
sudo yum install java-17-amazon-corretto
```

* Install the JDK for Amazon Corretto:

```
sudo yum install java-17-amazon-corretto-devel
```

* Install the JMods for Amazon Corretto:

```
sudo yum install java-17-amazon-corretto-jmods
```

* The installation location is /usr/lib/jvm/java-17-amazon-corretto.<cpu_arch>.

---

<!-- _class: invert -->

## Amazon Linux 2 on and for AWS ECS/EKS/Lambda

* Amazon Linux 2 is not only available in EC2 but embedded in other services as well.

  * IaaS with EC2 ...
  * CaaS with ECS ...
  * KaaS with EKS ...
  * FaaS with Lambda

* IaaS requires you to manage software at machine level.

* CaaS (Containers-as-a-Service) lets you abstract away the complexity of single
  machine configurations by sharing them among multiple services. You’re still
  required to keep your base container images up-to-date.

---

## Amazon Linux 2 on and for AWS ECS/EKS/Lambda (II)

* KaaS (Kubernetes-as-aService) lets you abstract away the complexity of single
  container configuration by giving you abstractions for entire microservice
  architectures. The Cloud Native Landscape gives you an overview on
  technologies involved. Kubernetes can happen to be a crystallization germ for
  the emergence of an ecosystem of evolutions around culture, people,
  organisation and technology.

* FaaS (Functions-as-a-Service) lets you abstract away the complexity of single
  container lifecycles by giving you abstractions for chaining events and
  invocations. The Cloud Native Computing Foundation gives you an overview on
  the evolving ecosystem of FaaS and/or Serverless as others might call it.

---

<!-- _class: invert -->

## Amazon Linux 2 on Amazon Graviton

* AWS **Graviton** processors are designed by AWS to deliver the best price
  performance for your cloud workloads.

* Many AWS services support **Graviton2** instances for a fully managed
  experience with significant price performance benefits. Thousands of customers
  are running production workloads on Graviton2-based instances.

* AWS **Graviton3** processors are the latest in the AWS Graviton processor
  family (launched in November 2021) with considerable performance improvements.

* **WRT Climate Change and Global Warming: AWS Graviton processors help
  customers reduce their carbon footprint as they are more energy efficient.
  Graviton3-based EC2 instances use up to 60% less energy for the same
  performance than comparable EC2 instances.**
