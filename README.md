![Greenbone Logo](https://www.greenbone.net/wp-content/uploads/gb_new-logo_horizontal_rgb_small.png)

# osbom - Reducing your risks
**Software Bills of Material and Vulnerability Scanning combined in one easy to use tool!**
> People who don't take risks generally make about two big mistakes a year. People who do take risks generally make about two big mistakes a year. There is the risk you cannot afford to take, and there is the risk you cannot afford not to take. (Peter Drucker)
![Image of Peter Drucker by Jeff McNeill, CC BY-SA 2.0 <https://creativecommons.org/licenses/by-sa/2.0>, via Wikimedia Commons](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ea/Drucker5789.jpg/180px-Drucker5789.jpg)

Modern open source software integrate a variety of modules and components from different sources. These include libraries, frameworks and runtime environments. The security of this supply chain is essential for both users and developers. An SBOM is an important part of a process that should end up with the best possible security. It helps to represent dependencies in a human- and machine-readable format. However, its full benefit only becomes apparent when the security status of each component involved can be assessed. This concerns the entire life cycle of the software, since new vulnerabilities of the included components may appear even after the release of the software package, sometimes years later.

Our project aims to strengthen the security of open source programs by combining their SBOMs with vulnerability data.

Due to the large number of dependencies usually given in software products, it is only possible to keep track of the vulnerabilities of the different components by supporting automation. Both the creation of SBOMs and thus the identification of dependencies of a software, is already well solved by various open source projects.

However, the challenge remains to automatically map the extensive dependencies to known vulnerabilities. This is complicated by the lack of standardization in naming components and their versions in practice. Exactly these challenges we solve with our project.

### Goals and vision
As open source developers, we are aware of the ever-growing security challenges within the FOSS infrastructure. With the recent increase in security breaches, it is more important than ever to provide solutions to strengthen this essential infrastructure. At the core of our effort is the development of a comprehensive, quality-assured, and trusted open source SBOM scanner solution.

With the vision of making the use of open source software more secure, we are working to create a platform for checking the security of dependencies in software projects. It contributes to security throughout the development lifecycle. At the same time, linking SBOM and vulnerability data also opens up the possibility for end users to check open source products for vulnerabilities and thus increase trust in FOSS.

## Addressing the challenges
To address the identified challenge, we are pursuing a plan to develop a platform that enables the processing and analysis of various SBOM formats. These include SPDX and CycloneDX, and we intend to gradually incorporate different packet identification mechanisms such as packet names, packet URLs (purls), SWID, or CPE. In terms of feasibility, we need to focus on a packet identification mechanism first. In our assessment, vulnerability checking based on package names currently offers the greatest added value. However, the solution architecture should be designed from the outset in such a way that it will be possible to integrate other package identification mechanisms later on.

We are aware of the complexity involved in integrating and processing different public data sources. These include vulnerability data from the National Vulnerability Database (NVD), advisory messages from CERT teams, vendor notices, and security advisories from Linux distributions. Our goal is to present this disparate and often unstructured information in a consistent, easily accessible form. Again, in the spirit of feasibility, we intend to focus in the first increment on the compilation and preparation of vulnerability data from the following data sources:
1. advisories from Linux distributions (debian, euleros, mageia, slackware, suse, ubuntu, almalinux, amazon linux, oracle linux, rocky linux).
2. github advisories about vulnerabilities in libraries of different programming languages (Java, Javascript, Python, Go, PHP, Rust, Ruby)

The functionality of our platform can be extended in later increments by integrating additional data sources: 
- Vendor Advisories integration allows scans on SBOMs from Windows systems 
- Vulnerability data from NVD in combination with CPE data preparation can enable scans on CPE-based SBOMs
- Conversion of SWID tags to CPE enables scanning of SBOMs in SWID format
- Integration of advisories from CERT teams. These would be costly to integrate due to lack of standardization in terms of product specification, but can provide even more up-to-date and comprehensive vulnerability data

To ensure the functionality and quality of our platform, we will write automated tests and benchmark the vulnerabilities found against the results of a proprietary solution. 

## Accessibility: public database and user-friendly tools 

A key component of our project is the creation of a public database that will provide all of the merged vulnerability information. This database will be accessible via a REST API. In addition, a CLI tool will be provided that reads SBOMs, queries the vulnerability data from the database, and returns the found vulnerabilities in a report. Furthermore, a user-friendly interface will be made available on our website through which SBOMs can be uploaded and which subsequently returns vulnerabilities contained therein. To ensure that our data is up to date, we plan to implement a pipeline that automatically compiles and prepares data from the various sources on a daily basis.


