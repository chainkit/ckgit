# ckgit - Git Scripts for Chainkit

These are Chainkit's *Git Plugins* for Git Hardening. 

# Usage

This is our [blog post](https://chainkit.com/blog/how-we-hacker-proof-our-git-repos-using-chainkit) explaining
how the hardening mechanism works. In short, it allows you to check if a Git Commit was registered to
a blockchain, and you can verify it later.

# Pre-Requisites

This project requires you to have the [Chainkit CLI](https://github.com/chainkit/ckcli.git) to be installed
and configured in the `PATH`.

It requires you to set the `CKTOKEN` or `CKUSER CKPASS` variables correctly.

Then you finally clone this repo, and add it to your `PATH`, so that `git` can 
find these plugins.

# Basic Workflow

## Step 1: Fetch Notes

```bash
git nfetch
```

## Step 2: Register New Commit

```bash
git register
```

## Step 3: View and Verify Registered Commit

```bash
git log

commit 1234567689012345678901234567890123456789
Author: Blah Blah <blah@blah.com>
Date:   Mon Mar 1 12:34:56 2021 -0500

    Your Commit

Notes:
    Asset Id: 1234567890123456789, Storage: pencil
```

```bash
git verify
```

## Step 4: Synchronize Notes

```bash
git nsync
```

# Advanced Workflow

## Backfilling All Commits

1. First, fetch existing notes.

```bash
git nfetch
```

2. Then parallelize register.

```bash
git list | tac | xargs -L1 -P32 git register
```

3. Then parallelize verify.


```bash
git list | tac | xargs -L1 -P32 git verify
```

4. Then synchronize.

```bash
git nsync
```

# Feedback

Send any feedback to us. We'd love to hear from you.

