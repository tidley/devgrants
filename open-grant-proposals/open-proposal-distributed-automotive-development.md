# Open Grant Proposal: `Distributed Automotive Development`

**Distributed Automotive Development:**

**Proposal Category:** `app-dev`

**Proposer:** `tidley`

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes

# Project Description

_Q_

Please describe exactly what you are planning to build. Make sure to include the following:

- Start with the need or problem you are trying to solve with this project.

_A_

Automotive development engineers must access test data from multiple sources before being able to analyse any given suite of tests. Each project, of which there can be dozens running in parallel at a single test facility, consumes terrabytes of data that are saved on various network shares, instrument drives and databases. Aggregating these data into a cohesive project can take time and be fault-prone, leading to data loss and direct drops in operational efficiency.

These data must also be backed up

Streamlined and reliable data management solutions are valuable in automotive engineering where large volumes of high-value data are generated daily at computerised test and development facilities. Each facility will likely operate using test equipment manufactured by different suppliers

Each facility can contain many test laboratories that are used to meausure various attributes from a particular item, such as a turbo, engine, or full vehicle.

where that are used for taking measurements , where anything from a single engine component up to a full vehicle can be tested using an array of digitally-controlled measuring equipment.

labs such as rig-rooms that test individual components to full-vehicle test-cells.

Test systems from multiple suppliers communiate using clearly-defined protocols and commands that are standardised such as AK via serial and HTTP via ethernet. Proprietary file formats may exist for fast-frequency data recorders in the order of MHz, which are often down-sampled for analysis and recorded as something like a '.csv'. tend to be compatible unless of a high-volume (>MHz) data source. can often interact with unencrypted standardised protocols.

Suppliers of the test equipment may use non-standard I/O, requiring bespoke configuration to interface with the facility network. provide test instrumentation, which may operate using fundamentally different control systems such as either non-reprogrammable digitised controllers or fully configurable computer controllers running an operating system such as Microsoft Windows. are manufactured by Integrating test instrumentation from a variety of manufacturers with a range of data interfaces and data types requires bespoke network solutions. Furthermore, a test facility catering for multiple active projects with specific requirements means automotive engineers must often access a variety of data storage media to read, write and modify their project test data.

Efficient management of test data is crucial for the streamlined operation of automotive engineering development facilities where high volumes of measurement data are generated. Multiple suppliers provide test instrumentation, which may operate using fundamentally different control systems such as either non-reprogrammable digitised controllers or fully configurable computer controllers running an operating system such as Microsoft Windows. are manufactured by Integrating test instrumentation from a variety of manufacturers with a range of data interfaces and data types requires bespoke network solutions. Furthermore, a test facility catering for multiple active projects with specific requirements means automotive engineers must often access a variety of data storage media to read, write and modify their project test data.

Being faced with a range of data sources accessed from various locations contributes to limited productivity. Some standard data management solutions with their respective limitations are briefly outlined below:

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

- Data are much more likely to be lost when carried on a person.
- Data are more corruptible since removable media storage hardware are designed with fewer read/write cycles than even consumer-grade physical storage media such as SSD's and hard drives.

**5. E-mails**

- Unnecessary use of email servers to store test data.
- Data are only accessible by employees who received the e-mail.
- Unless data are e-mailed it is not necessarily accessible by project engineers.

Increased utilisation of system resources can be achieved by using an IPFS cluster running on system and employee machines with a database such as OrbitDB to provide a uniform front-end for engineers to quickly and reliably access data.

Dependendable long-term storage of data (cold-storage) is required for data audits whereby lack of confirmation of ownership of a particular data set can impose penalties. Leveraging the symbiosis of IPFS and Filecoin can persist the familiar front-end experience for employees since data access can be requested using the same key (CID). Storing data once it is created will guarantee the validity of data files by comparing CID of files.

_Q_

- Describe why your solution is going to adequately solve this problem.

_A_

- Using an IPFS cluster to store "hot" data will reduce artificial and physical networking bottle-necks.
- Distributed IPFS cluster management allows reconfiguration from any network-connected access point.
- Open-source software is readily validated and customised.
- Hashing algorithms track any changes in data.
- Long-term storage of original

## Value

_Q_

Please describe in more detail why this proposal is valuable for the Filecoin ecosystem. Answer the following questions:

- What are the benefits to getting this right?

_A_

- Data generated by automotive engineering powertrain facilities is high-volume and high-value.
- Concepts such as 'big-data' is driving the industry to push for access to an increasing volume of digital information.
- The automotive engineering industry is highly compatible with the reductions in development costs made possible by data-driven processes such as CAD and DoE.
- Computer-controlled measurement equipment allows improvements in techniques according to Moore's law.

_Q_

- What are the risks if you don't get it right?

_A_

- Loss of confidence in distributed data solutions leading to a lack of potential for future projects.

_Q_

- What are the risks that will make executing on this project difficult?

_A_

- Non-standard operating systems, computer hardware and networks.
- Operational facilities will want to avoid interruptions to producing and processing data whilst migrating to a new system.
- Projects that have already started may find it difficult to transition to a novel network architecture.

This section should be 1-3 paragraphs long.

## Deliverables

_Q_

Please describe in details what your final deliverable for this project will be. Include a specification of the project and what functionality the software will deliver when it is finished.

_A - Specification_

1. Large data files (recorded at MHz frequency generating ~10GB in 1.5 minutes, or ~111MB/s\*) every 2 minutes must be able to be processed by the network. Processing includes:
   - Registered on OrbitDB.
   - Having 3 duplicates locally plus on Filecoin.
2. Registered users having access to new files.
   - Show available files with metadata.
3. User administration and authentication.

_A - Functionality_

1. New data files on specific machines are detected and replicated to the local IPFS cluster as well as Filecoin.
2. OrbitDB updated with new file information.
3. Intuitive, permissioned, data-access portal for users.
   - OrbitDB with information on each file (time, origin, # copies, locations, etc.)
4. Access right management controlled by a private key.
   - Read from an IPNS address.

## Development Roadmap

Please break up your development work into a clear set of milestones. This section needs to be very detailed (will vary on the project, but aim for around 2 pages for this section).

1. Data from several sources are duplicated to a dedicated IPFS cluster to isolate performance when processing high-volumes of data.
   - Determine e.g. if data read values should be limited when there's an active test to reduce system loading.
2.

3. Executable files to setup:

   _Storage nodes_

   1. Install required software to communicate on IPFS.
      - Detects hard drive read/write speed, network speed etc. to generate system score.
   2. Menu for configuring things such as:
      - Database directory
      - % HDD to leave free
      - Bootstrap nodes
   3. Identifies and registers self on network.

   _Admin portal_

   1. Provides relevant admin features to monitor and configure the network

   _Data origins_

   1. Installs required software to communicate on IPFS.
   2. Provides custom instrument configuration menu to define data source including:
      - Interface (ethernet, serial)
      - Internal / external (mirror or read)
      - Timings (baud rate etc.)
      - Data directory (if to monitor folder for new files)
   3. Identifies and registers self on network.

## 2. Executable to run on each oracle which:

- Provides relevant admin features to monitor and configure the network.

## 3. Executable to run on each data generator which:

- Installs required software to communicate on IPFS.
- Provides custom instrument configuration menu to define data source including:
  - Interface (ethernet, serial)
  - Internal / external (mirror or read)
  - Timings (baud rate etc.)
  - Data directory (if to monitor folder for new files)
  -
- Identifies and registers self on network.

For each milestone, please describe:

_Q_

- The software functionality that we can expect after the completion of each milestone. This should be detailed enough that it can be used to ensure that the software meets the specification you outlined in the Deliverables.

_A_

-

_Q_

- How many people will be working on each milestone and their roles

_A_

-

_Q_

- The amount of funding required for each milestone

_A_

-

_Q_

- How much time this milestone will take to achieve (using real dates)

_A_

-

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

_Q_

Please describe (in words) your team's relevant experience, and why you think you are the right team to build this project. You can cite your team's prior experience in similar domains, doing similar dev work, individual team members' backgrounds, etc.

_A_

## Team code repositories

Please provide links to your team's prior code repos for similar or related projects.

# Additional Information

Please include any additional information that you think would be useful in helping us to evaluate your proposal.
