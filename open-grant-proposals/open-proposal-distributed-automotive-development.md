# Open Grant Proposal: `Decentralised Automotive Development Test Data`

**Distributed Automotive Development:**

**Proposal Category:** `app-dev`

**Proposer:** `tidley`

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes

# Project Description

Please describe exactly what you are planning to build. Make sure to include the following:

> Start with the need or problem you are trying to solve with this project.

###### Read https://www.dataversity.net/brief-history-analytics/

Data storage is an issue at automotive engineering facilities where large volumes of test data are generated and must be made available for analysis. The issue can be broken up into:

1. Storage - The physical storage requirements grow exponentially as tests become increasingly sophisticated to match legislative requirements.
1. Indexing - One test can generate data files from multiple test instruments, each covering varying time spans and sample rates, all needing to be linked to the same test.
1. Retrieval - Accessing large datasets can put a strain on IT network infrastructure.
1. Processing - Data integrity must be assured for effective analysis.

Traditional client-server architecture is relied upon for the majority of data handling although other methods can be used to access data. Common pitfalls for these are outlined:

**1. Relational databases (SQL, Oracle) running on server-grade hardware with configurable client software**

- Artificial restrictions set by the suppliers (number of active connections, feature sets, CPU cores).
- Physical restrictions created by the infrastructure (network bandwidth, data media read/write speeds).
- Multiple single points of failure on the network and host machine (connection issues, power loss, corrupt media).

**2. Networked machines, both where the data originates and employee devices**

- Data accessed directly from the source can cause excessive wear on storage medium that weren't designed for high numbers of read/write operations.
- Over-use of the local CPU to serve data can cause performance issues if running test software.
- Dispersed, un-checked copies of data increases data storage waste and reduces data integrity.

**3. Network-share drives with access configured using domain controllers and active directories often running on VM's (Windows Server)**

- Data files can easily be miss-placed and duplicated by employees leading to confusion as to the integrity of data.
- Folder access permissions are granted on a per-user and user-group basis which can become unwieldy with multiple data locations and transitioning employee roles.

**4. Removable media such as USB hard-drives and pen-drives**

- Data can be misplaced when carried on a person.
- Data are more likely to be corrupted due to the less robust storage media on portable devices.

**5. Emails**

- Unnecessary use of email servers to store test data.
- Data are only accessible by employees who received the e-mail.

These issues can be remedied using a decentralised approach built around IPFS clusters, in brief:

1. An IPFS cluster configured to operate on machines running on the local network.
1. Data files are replicated to the IPFS cluster and Filecoin immediately upon creation. IPFS provides the fast access required by engineers whilst Filecoin provides archiving.
1. The file CID is stored along with metadata on OrbitDB for retrieval from the cluster.
1. Data origins can be tracked using the network port that each device is connected to. A secondary use of this is that instrument locations would be known at all times using the network address mapped to physical location.

> Describe why your solution is going to adequately solve this problem.

1. Data storage is not restricted to specialised hardware and so can be distributed amongst all compatible machines to maximise the use of available storage and reduce overhead costs associated with purchasing and maintaining servers.
1. IPFS and OrbitDB are fully integrated for comprehensive and automated indexing of data.
1. Distributing the storage and processing will reduce data transfer and processing bottlenecks.
1. Data provenance can be verified using the CID of each file.

---

## Value

Please describe in more detail why this proposal is valuable for the Filecoin ecosystem. Answer the following questions:

> What are the benefits to getting this right?

Reliable storage is required in the automotive industry for auditing and long-term analysis. Providing an easy to integrate storage solution at less cost that doesn't need infrastructure changes when storage requirements grow is a very attractive proposition. Additional benefits such as globally accessible sharing increase the value of data for the client.

The data management requirements of automotive facilities are similar so once an implementation is shown to be effective it can be readily reproduced at other sites.

The solution would be a unified and more cost-effective approach compared to the data management solutions available that require expensive licenses and infrastructure.

> What are the risks if you don't get it right?

| Risk                                                                                               | Mitigation                                                                                                                  |
| -------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Data that are misplaced or corrupted would be costly to replace.                                   | Gradually migrate with existing data management systems continuing to operate.                                              |
| Poorly implemented client software on critical equipment could cause damage to facility equipment. | Use a parallel network of computers that are non-critical to allow performance monitoring before using in-service machines. |

> What are the risks that will make executing on this project difficult?

| Risk                                                                                               | Mitigation                                                                                                |
| -------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| Training and gaining trust of employees on new systems.                                            | Understand the workflow and develop the client software to integrate with minimal effort to the end user. |
| Integrating with data acquisition systems.                                                         | Develop low-level interfaces to communicate with instruments.                                             |
| Ensure no long-term performance degradation caused by over-use of hard drives or processing power. | Allow some overheads by monitoring system performance.                                                    |
| Processing files from some instruments that can generate a 10 GB data file within a minute.        | Avoid excessive data handling.                                                                            |
| Interfacing with various computer operating systems.                                               | Develop software to be compatible on a wide range of system architectures.                                |
| Operational facilities will want to avoid interruptions.                                           | Develop system in parallel to allow seamless switching.                                                   |

---

## Deliverables

> Please describe in details what your final deliverable for this project will be. Include a specification of the project and what functionality the software will deliver when it is finished.

### Specification

1. Continuous monitoring of multiple locations for new test files (>6 per test cell). New files rapidly duplicated to IPFS cluster and Filecoin.
   1. Data production volume from each test cell can peak at 10 GB per minute.
   1. A facility may contain anywhere between 5 to 100 test cells.
1. Three copies of live files on IPFS cluster at any time.
1. Entry for new files containing any required information on OrbitDB.
1. Modifications to entry in OrbitDB when file status changes.
1. Authenticated content delivery via intuitive front-end with OrbitDB as back-end.

### Functionality

There will be two core sides to the solution that will have their functionalities outlined seperately:

1. Server-side software for the bulk of files management.
1. Client-side software for administration and content delivery.

**Server**

1. New data files on monitored machines are replicated to the local IPFS cluster as well as Filecoin.
1. OrbitDB updated with new file including metadata such as time of creation, origin, project, test name, current location, # duplicates, is-archived, last accessed, expiry date, failed operations, etc.

**Client**

1. Front-end to OrbitDB allowing data retrieval for authenticated users.
1. Access right management configuration.

---

## Development Roadmap

> Please break up your development work into a clear set of milestones. This section needs to be very detailed (will vary on the project, but aim for around 2 pages for this section).

### **Milestone X: Process analysis**

1. Review standard operating procedures at current facility.

### Software functionality

### People assigned

### Funding

### Duration

### **Milestone X: Shadow system**

1. Data from several sources are duplicated to a dedicated IPFS cluster to isolate performance when processing high-volumes of data.
   1. Determine e.g. if data read values should be limited when there's an active test to reduce system loading.

### Software functionality

### People assigned

### Funding

### Duration

### **Milestone X: Program development**

### Software functionality

3. Executable files to setup:

   _Servers_

   1. Install required software to communicate on IPFS.
      - Detects hard drive read/write speed, network speed etc. to generate system score.
   2. Menu for configuring things such as:
      - Database directory
      - % HDD to leave free
      - Bootstrap nodes
   3. Identifies and registers self on network.

   _Clients_

   1. Installs required software to communicate on IPFS.
   1. Provides relevant admin features to authenticated user to monitor and configure the network.
   1. Provides custom instrument configuration menu to define data source including:
      - Interface (ethernet, serial)
      - Internal / external (mirror or read)
      - Timings (baud rate etc.)
      - Data directory (if to monitor folder for new files)
   1. Identifies and registers instruments on network.

### People assigned

### Funding

### Duration

### **Milestone X: System handover**

### Software functionality

### People assigned

### Funding

### Duration

For each milestone, please describe:

> The software functionality that we can expect after the completion of each milestone. This should be detailed enough that it can be used to ensure that the software meets the specification you outlined in the Deliverables.

> How many people will be working on each milestone and their roles

> The amount of funding required for each milestone

> How much time this milestone will take to achieve (using real dates)

## Total Budget Requested

Sum up the total requested budget across all milestones, and include that figure here. Also, please include a budget breakdown to specify how you are planning to spend these funds.

## Maintenance and Upgrade Plans

Specify your team's long-term plans to maintain this software and upgrade it over time.

1. Hardware boxes to plug-and-play devices into network allowing non-computer controlled instruments to interface with the network. This would include features to convert analogue data to digital data where necessary. Such a box would have to consider:
   - Interface (analogue, ethernet, serial)
   - If analogue:
     - Baud rate
     - Triggers
   - If digital:
     - Data format

---

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

> Please describe (in words) your team's relevant experience, and why you think you are the right team to build this project. You can cite your team's prior experience in similar domains, doing similar dev work, individual team members' backgrounds, etc.

| Team member   | Relevant experience                                                                                                                                                                                                                                                                                                                                                                                                                |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Dr. Tom Dwyer | A BEng in Motorsport Engineering and a Ph.D in Automotive Engineering studying the effects of test conditions on data quality. Academia was proven by industrial experience working at MG (2 years), Caterpillar-Perkins (9 months) and Mahle Powertrain (3 years). More recently working in the blockchain industry for a year developing decentralised apps using decentralised technologies such as IPFS, Bitcoin and Ethereum. |

## Team code repositories

Please provide links to your team's prior code repos for similar or related projects.

# Additional Information

Please include any additional information that you think would be useful in helping us to evaluate your proposal.
