# What is Version Control System?

Version Control System (VCS) is also known by various other names, including Source Code Management (SCM), Revision Control System (RCS), Source Control System, and Change Management System. It encompasses a range of tools and methodologies designed to manage and track **changes** to files and directories **over time**, providing developers with the ability to **recall** specific versions and facilitate seamless collaboration.

# Version Control System Advantages

1. #### Revert Files and Projects
   
   With a VCS, you can easily revert selected files back to a previous state. If an unintended change or error occurs, you have the flexibility to roll back specific files without affecting the entire project. Additionally, you can revert the entire project back to a previous state, ensuring project stability and eliminating potential issues.

2. #### Compare Changes Over Time
   
   Version control allows you to compare changes made to files over time. By reviewing file differences between versions, you gain insights into modifications, additions, and deletions. This capability helps track the evolution of code and assists in debugging, identifying performance improvements, or understanding the impact of specific changes.

3. #### Track Contributors and Modifications
   
   VCS provides visibility into who last modified a file or piece of code. This information is valuable for identifying potential sources of problems or conflicts, allowing you to reach out to the relevant contributors for clarification or collaboration. By attributing changes to specific individuals, accountability is enhanced, fostering a transparent and collaborative development environment.

4. #### Trace Issues and Introduce Fixes
   
   In cases where issues arise, a VCS helps trace back to when and by whom a particular issue was introduced. This information aids in identifying the root cause and implementing timely fixes. By leveraging the VCS's historical record, you can navigate through the project's timeline, enabling efficient debugging and issue resolution.

5. #### Integration with CI/CD Tools
   
   Version control seamlessly integrates with Continuous Integration/Continuous Deployment (CI/CD) tools. By leveraging VCS within your CI/CD pipeline, you can automate code integration, testing, and deployment processes. This integration streamlines development workflows, enabling efficient collaboration and ensuring the delivery of high-quality software.

6. #### Efficient Source Code and Team Management
   
   A VCS serves as a centralized repository for managing source code. It offers features such as branching and merging, enabling parallel development and facilitating teamwork. With proper branch management, developers can work on features or bug fixes independently, reducing conflicts and enhancing productivity. Additionally, VCS provides access controls and permissions, allowing teams to collaborate securely.

# History of VCS

## Local Version Control System

In the early days, one of the common version-control methods was to <u>manually copy</u> files into another directory. This approach, though simple, had significant drawbacks. People often faced the risk of forgetting the current directory and mistakenly writing to the wrong file or unintentionally overwriting important files.

To address these issues, programmers developed local Version Control Systems (VCSs) that incorporated a basic database to track changes made to files. One notable local VCS tool is [RCS](https://www.gnu.org/software/rcs/) (Revision Control System), which was released in **<u>1982</u>** and is still distributed with many computers today. RCS utilized a special disk format to store patch sets, representing the differences between files. By combining these patches, RCS allowed users to recreate any file's state at a specific point in time.

However, local VCSs were limited to individual use and were not suitable for collaborative teamwork, as they lacked mechanisms for seamless collaboration and sharing changes between multiple developers.

![](./images/local.png)

## Centralized Version Control System

To address the need for collaboration among developers working on different systems, Centralized Version Control Systems (CVCSs) were introduced. These systems, including popular tools like [CVS](https://cvs.nongnu.org/) (Concurrent Versions System), [Subversion](https://subversion.apache.org/) (SVN), and [Perforce](https://www.perforce.com/), utilize a central server that stores all the versioned files. Developers, or clients, check out files from this central repository.

The CVCS setup offers several advantages over local VCSs:

* Enhanced visibility and awareness of project activities among team members.
- Administrators have centralized control over access permissions.
- Easier administration compared to local VCSs.

However, it is important to acknowledge the downsides of the centralized approach:

- Single point of failure with the central server.
- Downtime or issues with the server hinder collaboration.
- Risk of losing all project history if backups are not maintained.
- Similar risk to local VCSs in terms of concentrated project history.

![](./images/centralized.png)

## Distributed Version Control Systems (DVCS)
