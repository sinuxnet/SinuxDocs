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

<img src="./images/local.png" title="" alt="" data-align="center">

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

<img src="./images/centralized.png" title="" alt="" data-align="center">

## Distributed Version Control Systems (DVCS)

In a Distributed Version Control System (DVCS), clients fully mirror the repository, including its complete history. Some common DVCS tools are [Git](https://git-scm.com/), Mercurial, Bazaar, and Darcs.

<img src="./images/distributed.png" title="" alt="" data-align="center">

Links:

1. [Comparison of version-control software - Wikipedia](https://en.wikipedia.org/wiki/Comparison_of_version-control_software)

# A Short History of Git

- **1991-2002:** Changes to the Linux kernel were managed through patches and archived files.

- **2002:** The Linux kernel project adopted a proprietary Distributed Version Control System (DVCS) called BitKeeper.

- **2005:** Dispute arose between the Linux development community and the company behind BitKeeper, leading to the revocation of the tool's free-of-charge status.

- **2005:** In response, Linus Torvalds and the Linux development community created their own DVCS called Git.

The objectives for Git were clear from the outset:

- Speed
- Simple design
- Robust support for non-linear development with thousands of parallel branches
- Full distributed capabilities
- Efficient handling of large-scale projects like the Linux kernel in terms of speed and data size.

# The Major difference between Git and Other VCSs

The major difference between Git and any other VCS (Subversion and friends included) is the way Git thinks about its data. 

* **Other systems** think of the information they store as a set of files and the changes made to each file over time (this is commonly described as ***delta-based*** version control).

<img src="./images/deltas.png" title="" alt="" data-align="center">

* **Git** thinks of its data more like a series of snapshots which stores all your data.

* To be efficient, if files have not changed, Git doesn’t store the file again, just a link to the previous identical file it has already stored.

* Git thinks about its data more like a **stream of snapshots**.

<img src="./images/snapshots.png" title="" alt="" data-align="center">

* Most operations in Git need only local files and resources to operate.
  
  In Perforce, for example, you can’t do much when you aren’t connected to the server; in Subversion and CVS, you can edit files, but you can’t commit changes to your database (because your database is offline).

* Everything in Git is checksummed before it is stored and is then referred to by that checksum.
  
  This means it’s impossible to change the contents of any file or directory without Git knowing about it.
  
  The mechanism that Git uses for this checksumming is called a [SHA-1](https://en.wikipedia.org/wiki/SHA-1)) hash. This is a 40-character string composed of hexadecimal characters (0–9 and a–f) and calculated based on the contents of a file or directory structure in Git. A SHA-1 hash looks something like this:
  
  ```
  a239da6552752987aa793b52f8696cr6d3b00567
  ```

# The Three States

Git has three main states that your files can reside in: *modified*, *staged*, and *committed*:

1. **Modified:** 
   
   * means that you have changed the file but have not committed it to your database yet.
   
   * Modifications can include adding, deleting, or modifying content within a file.

2. **Staged:**
   
   - Files in the staged state have been marked to be included in the next commit snapshot.
   - By staging files, you specify that you want to include their current version in the upcoming commit.

3. **Committed:**
   
   - Files in the committed state have their data safely stored in the local Git database.
   - A commit represents a specific version of a file or a set of files, capturing the changes made since the last commit.

<img src="./images/areas.png" title="" alt="" data-align="center">

These three states correspond to three essential components in a Git project:

1. **Working Tree:**
   
   - The working tree refers to the current state of your project directory.
   - It contains all the files and directories, including both modified and unmodified files.

2. **Staging Area:** (also known as the index)
   
   - The staging area is where you prepare your changes before committing them.
   - By staging files, you indicate that you want to include their changes in the next commit.

3. **Git Directory:** (also known as the Repository)
   
   - The Git directory is where Git stores all the metadata and object database for your project.
   - It contains the complete history and snapshots of your project, preserving committed changes.

The basic Git workflow goes something like this:

1. You **modify** files in your working tree.

2. You **selectively stage** just those changes you want to be part of your next commit, which adds ***only*** those changes to the staging area.

3. You do a **commit**, which takes the files as they are in the staging area and stores that snapshot permanently to your Git directory.

# First-Time Git Setup

When setting up Git for the first time, there are a few configuration steps you need to follow. Git provides different levels of configuration: system, global, and local. Here's a breakdown of the setup process:

1. **System Configuration** (`git config --system`):
   
   - This configuration applies to the entire system and is stored in `/etc/gitconfig`.
   - It requires administrative privileges to modify.
   - Generally, system configuration is set by the Git administrator and applies to all users on the machine.

2. **Global Configuration** (`git config --global`):
   
   - This configuration applies to a specific user and is stored in `~/.gitconfig` or `~/.config/git/config`.
   - It can be accessed and modified by the user.

3. **Local Configuration** (`git config --local`):
   
   - This configuration applies to a specific Git repository and is stored in `.git/config` within the repository.
   - It is specific to that repository and overrides any global or system configurations.

To set up your user information globally, use the following commands:

```bash
git config --global user.name "Sergio Marquina"
git config --global user.email "sergimarqi@gmail.com"
git config --global core.editor vim
git config --global init.defaultBranch main
```

These commands set your name and email address, which are used to identify your commits.

To verify the configuration settings, you can use the following command:

```shellsession
$ git config --list
user.name=Sergio Marquina
user.email=sergimarqi@example.com
color.status=auto
color.branch=auto
color.interactive=auto
color.diff=auto
...
```

This command lists all the Git configuration settings, including the ones you have set.

You can view all of your settings and where they are coming from using:

```shellsession
git config --list --show-origin
```

# git init VS git init --bare

When initializing a Git repository, you have the option to use either `git init` or `git init --bare`. Let's explore the differences between these two commands:

### `git init`

The `git init` command is used to initialize a new Git repository with a working directory. When you run `git init` in a directory, Git creates a new repository, sets up the necessary files and directories, and prepares it for version control.

The `git init` command creates the following structure:

- The `.git` directory: This directory contains the repository's metadata, including the object database, commit history, branches, tags, and configuration.

- Working directory: This is the directory where you can create, modify, and organize your project files.

With `git init`, you can start tracking changes in your project, commit modifications, and collaborate with others using the repository.

### `git init --bare`

On the other hand, `git init --bare` initializes a bare Git repository. A bare repository does not have a working directory. It only contains the Git repository's essential elements, such as the object database, commit history, branches, tags, and configuration.

The `git init --bare` command creates the following structure:

- The repository folder: This is the root folder of the bare repository, typically ending with a `.git` extension. It contains the repository's metadata and does not include a working directory.

# Bare Repository VS Working Tree

### Bare Repositories:

1. **No Working Directory**:
   
   - Bare repositories do not have a working directory where you can directly modify files.
   - They contain only the necessary Git repository files, such as the object database, commit history, branches, tags, and configuration.

2. **Remote Collaboration**:
   
   - Bare repositories are often used as remote repositories or central repositories that multiple developers can push changes to or pull changes from.
   - They serve as a reference point for sharing code and collaborating with others.

3. **No Direct Editing**:
   
   - Since bare repositories lack a working directory, you cannot directly edit or modify files within the repository.
   - They are designed to facilitate collaboration, not as a workspace for making changes.

### Working Trees:

1. **Includes Working Directory**:
   
   - Working trees, also known as non-bare repositories, have a working directory associated with them.
   - The working directory is where you can create, modify, and organize your project files.

2. **Local Development**:
   
   - Working trees are primarily used for local development and version control.
   - You can make changes to files, stage them, and commit them to track the project's history.

3. **Workspace for Modifications**:
   
   - Working trees provide a workspace where you can edit files, test changes, and perform various development tasks.
   - They allow you to switch between branches, create new branches, and work on different features concurrently.

# 
