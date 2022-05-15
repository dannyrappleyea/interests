# What is it? 

A second brain is an attempt to graft digital storage into our thought processes. This isn't an easy thing. We're having to build the tools to do it, and experiment a lot.

One realization that few have grasped yet is that it will not be one digital brain, but many. The simplest example is having work and personal lives, and there is a limit to the knowledge that can be shared between the two.

So there are two problems to solve:
1) How to create a self-contained pool of knowledge
2) How to share and link pools of knowledge together

# Vaults of Knowledge
Knowledge needs to be split into pools that can be combined together in various ways.

I've mostly been experimenting with [[git-notes]], basically folders of markdown files stored in a git repository. It works great for single files, but linking files together is pretty clumbsy.  [[obsidian]] vaults are far better in that regard, and integrates well with a git storage tier. So I'm using vault to describe a single pool of knowledge

## Knowledge Vault Criteria
I see three main questions to ask to determine what knowledge vaults to create, and how to divide knowledge into them.

### Persona
What part of your life does it belong to? Personal and work are two obvious ones. But it could include organizations, even family. There should be a strong reason why data should be split, like having to live on different computers.

### Sharing
Who is this going to be shared with? Is it private, public, shared within a company or with a few friends?

### Topic
Is it a topic large enough to be split out into it's own vault?

## Creating a Knowledge Vault
For each knowledge vault, create a vault or folder to house the data.


# Linking Knowledge Vaults
## By Persona
Each persona should have a private knowledge vault, used as the starting point to link in all other knowledge vaults. Inside should be folders roughly corresponding to combinations of persona and sharing level, like:
- private
- public
- shared-me
- shared-friends

Looking at it from each persona, I might have a personal-private vault on my home machine, a work-private vault on my work machine, then the shared-me folder has the vaults shared between the two. How the shared vaults are synced is entirely up to you and your work IT department.

## Linking Vaults
I'm trying symbolic links to link a vault into the right folder inside the private vault. I'm sure it will tricky to manage, but my first attempt having many vaults open at once just wasn't working. And I like having the single unified view into everything.

# Notes
- instead of personas, thinking about it more in terms of communities. You inherently know how much you reveal or hide with each group of people you interact with, so use that skill.

