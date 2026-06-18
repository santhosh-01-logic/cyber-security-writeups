# Bandit Level 3 → Level 4

## Goal

Find the password for Bandit Level 4.

## Solution

First, I connected to the server using SSH.

```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
```

After entering the password for Bandit Level 3, I logged in.

## Step 1: Check files

I listed the files in the home directory:

```bash
ls
```

There was a directory named:

```text
inhere
```

## Step 2: Enter the directory

To move into the directory, I used:

```bash
cd inhere
```

`cd` is used to change the current directory.

## Step 3: Check hidden files

After entering, I again used:

```bash
ls
```

But nothing was shown clearly, so I checked all files including hidden ones:

```bash
ls -la
```

### Explanation

- `-l` shows detailed list (permissions, size, etc.)
- `-a` shows hidden files (files starting with `.`)

This showed a hidden file inside the directory.

## Step 4: Read the file

To read the hidden file, I used:

```bash
cat ./...HidingFileName...
```

(Replace with the actual hidden file name shown in output)

This displayed the password for Bandit Level 4.

## Screenshot

[Insert Screenshot Here]

## Commands Used

```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
ls
cd inhere
ls -la
cat ./<hidden-file>
```

## Result

Successfully found the password for Bandit Level 4.