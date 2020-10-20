# Open Grant Proposal: `distributed-automotive-development`

**distributed-automotive-development:**

**Proposal Category:** `app-dev`

**Proposer:** `tidley`

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes

# Project Description

_Q_

Please describe exactly what you are planning to build. Make sure to include the following:

- Start with the need or problem you are trying to solve with this project.

_A_

Efficient test data management is crucial for the efficient operation of automotive engineering development facilities where high volumes of high-value test data is generated continuously. Integrating test instrumentation from a variety of manufacturers with a range of data interfaces and data types requires bespoke network solutions. Furthermore, multiple projects with their individual requirements and demands means automotive engineers must often access a variety of data storage media to read, write and modify data.

Being faced with a range of data sources accessed from various locations contributes to limited productivity. Some standard data management solutions with their respective limitations are briefly outlined below:

**1. Relational databases (SQL or Oracle) running on server-grade hardware with configurable client software**

- Artificial restrictions set by the suppliers (number of active connections, feature sets, CPU core availability).
- Physical restrictions created by the infrastructure (network bandwidth, data media read/write speeds).
- Multiple single points of failure on the network and host machine (connection issues, power loss, corrupt media).

**2. Networked machines, both where the data originates and employee devices**

- Data accessed directly from the source can cause excessive wear on storage medium that weren't designed for high numbers of read/write operations.
- Over-use of the local CPU to serve data can cause performance issues if running test software.

**3. Network-share drives with access configured using domain controllers and active directories often running on VM's (Windows Server)**

- Data files can easily be miss-placed and duplicated by employees leading to confusion as to the integrity of data.
- Folder access permissions are granted on a per-user and user-group basis which can become unwieldy with multiple data locations and transitioning employee roles.

**4. Removable media such as USB hard-drives and pen-drives**

- Data are much more likely to be lost when carried on a person.
- Data are more corruptible since removable media storage hardware are designed with fewer read/write cycles than even consumer-grade physical storage media such as SSD's and hard drives.

**5. E-mails**

- Unnecessary use of email servers to store test data.
- Data are only accessible by employees who received the e-mail.
- Unless data are e-mailed it is not necessarily accessible by project engineers.

Increased utilisation of system resources can be achieved by using an IPFS cluster running on system and employee machines with a database such as OrbitDB to provide a uniform front-end for engineers to quickly and reliably access data.

Dependendable long-term storage of data (cold-storage) is required for data audits whereby lack of confirmation of ownership of a particular data set can impose penalties. Leveraging the symbiosis of IPFS and FileCoin can persist the unform front-end experience for employees since data access can be requested using the same key (CID).

Furthermore, long-term data storage of data can be

An automotive engineer is losing efficiency it is a waste of resources for the automotive engineer to be doing anything but analysing test data.

Automotive engineering facilities produce and consume a large amount of data, for example one piece of test equipment may record data at megahertz frequencies and generate several gigabytes of data in under a minute. Data must be stored safely and readily available for analysis.

Data files are often misplaced

Market pressure and regulatory bodies perpetually demand higher performing products at lower cost.
Product development cycles generate test data that are stored on centralised servers.
Bespoke server-side software packages that can provide the required data management tools such as storage, backup, verification, publishing and access control are available for a premium.
Servers operating in isolation unnecessarily restrict access to test data.
Inter-facility data sharing rarely occurs due to network security concerns.
Data retrieval requires licensed and configured client software and access to company networks.
Global manufacturing networks require components to be shipped in order to test.
Shipping takes time, risks damage, and costs money.
Tests could be carried out locally but data cannot be readily shared between facilities.

_Q_

- Describe why your solution is going to adequately solve this problem.

_A_

Profitability can be maintained by reducing development costs in a range of areas.
Cryptographically-secure data sharing opens data sharing potentials.
Open-source software is secure, license-free and typically compatible by design.
Reducing the number of gateways and increasing the quality of security protocols de-restricts rightful data access.
Generic software tools can be used to access data.
Ubiquitous broadband internet enables high volumes of data to be transferred between facilities in real-time.
Bringing testing equipment online facilitates distributed testing.

## Value

Please describe in more detail why this proposal is valuable for the Filecoin ecosystem. Answer the following questions:

- What are the benefits to getting this right?

The automotive industry is becoming increasingly reliant on data and there's pressure to increase the digitisation to recover dropping vehicle sales. As data becomes a backbone of the industry the economic incentive to store data with reliability will increase.

- What are the risks if you don't get it right?

The industry will adapt to the data demands.

- What are the risks that will make executing on this project difficult?

The automotive industry is enormous and there are some major players in the field (AVL etc.)

This section should be 1-3 paragraphs long.

## Deliverables

Please describe in details what your final deliverable for this project will be. Include a specification of the project and what functionality the software will deliver when it is finished.

1. Live test data being stored and visible by authenticated users.

## Development Roadmap

Please break up your development work into a clear set of milestones. This section needs to be very detailed (will vary on the project, but aim for around 2 pages for this section).

For each milestone, please describe:

- The software functionality that we can expect after the completion of each milestone. This should be detailed enough that it can be used to ensure that the software meets the specification you outlined in the Deliverables.
- How many people will be working on each milestone and their roles
- The amount of funding required for each milestone
- How much time this milestone will take to achieve (using real dates)

## Total Budget Requested

Sum up the total requested budget across all milestones, and include that figure here. Also, please include a budget breakdown to specify how you are planning to spend these funds.

## Maintenance and Upgrade Plans

Specify your team's long-term plans to maintain this software and upgrade it over time.

# Team

## Team Members

- Team Member 1
- Team Member 2
- Team Member 3
- ...

## Team Member LinkedIn Profiles

- Team Member 1 LinkedIn profile
- Team Member 2 LinkedIn profile
- Team Member 3 LinkedIn profile
- ...

## Team Website

Please link to your team's website here (make sure it's `https`)

## Relevant Experience

Please describe (in words) your team's relevant experience, and why you think you are the right team to build this project. You can cite your team's prior experience in similar domains, doing similar dev work, individual team members' backgrounds, etc.

## Team code repositories

Please provide links to your team's prior code repos for similar or related projects.

# Additional Information

Please include any additional information that you think would be useful in helping us to evaluate your proposal.
