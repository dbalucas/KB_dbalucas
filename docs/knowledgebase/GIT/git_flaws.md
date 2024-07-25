---
title: Git flaws
date: 2024-07-25
authors: [dbalucas]
description: >
  anyone can access deleted and private repos on github
categories:
  - git
tags:
  - git
---

## Summary:

Today I read an article about some git flaws. Moste people are not aware of it. Private and Public repositories are not always secure by default. This article is a referrence to the circumstances:

https://trufflesecurity.com/blog/anyone-can-access-deleted-and-private-repo-data-github

> 
> We have a few takeaways from this:
> 
> 1. As long as one fork exists, any commit to that repository network (ie: commits on the “upstream” repo or “downstream” forks) will exist forever
>   1. This further cements our view that the only way to securely remediate a leaked key on a public GitHub repository is through key rotation. > We’ve spent a lot of time documenting how to rotate keys for the most popularly leaked secret types - check our work out here: howtorotate.com.
> 2. GitHub’s repository architecture necessitates these design flaws and unfortunately, the vast majority of GitHub users will never understand how a repository network actually works and will be less secure because of it.
> 3. As secret scanning evolves, and we can hopefully scan all commits in a repository network, we’ll be alerting on secrets that might not be our > own (ie: they might belong to someone who forked a repository). This will require more diligent triaging.
> 4.  While these three scenarios are shocking, that doesn’t even cover all of the ways GitHub could be storing deleted data from your repositories. Check out our recent post (and related TruffleHog update) about how you also need to scan for secrets in deleted branches. 
> 
> Finally, while our research focused on GitHub, it’s important to note that some of these issues exist on other version control system products.