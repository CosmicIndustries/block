# Block Lists

This folder contains several block lists used to restrict access to specific services or content platforms. Each file within this folder represents a list of domains, IPs, or other identifiers that are **blocked**, grouped by service or platform. These block lists are the inverse of the corresponding allow lists, meaning they restrict everything except for the domains and services mentioned in their allow list counterparts.

## Files

### 1. [`blockList.txt`](https://github.com/CosmicIndustries/lists/blob/main/blockList.txt)
This is the general block list that contains domains and services that are not allowed. It inversely mirrors the domains in the `allowList.txt`, blocking everything that isn't explicitly approved.

### 2. [`disney_block.txt`](https://github.com/CosmicIndustries/lists/blob/main/disney_block.txt)
This block list specifically targets services **not related to Disney**. Only Disney-approved domains (from `disney.txt`) are allowed, while everything else is blocked.

### 3. [`list2mrg_block.txt`](https://github.com/CosmicIndustries/lists/blob/main/list2mrg_block.txt)
This block list is intended to be merged with other block lists. It contains additional domains to be blocked, expanding the restrictive policies of the main block list.

### 4. [`netflix_block.txt`](https://github.com/CosmicIndustries/lists/blob/main/netflix_block.txt)
This block list is dedicated to services **not related to Netflix**. It inversely mirrors `netflix.txt`, blocking any domains that are not Netflix-related.

### 5. [`roku_block.txt`](https://github.com/CosmicIndustries/lists/blob/main/roku_block.txt)
This block list restricts access to all domains and services **not related to Roku**. It mirrors `roku.txt`, ensuring only Roku-specific domains are allowed and everything else is blocked.

## Usage
These block lists can be imported into firewall configurations, content filters, or any other system that requires domain-based restrictions. Each file can be used individually to block services that aren't relevant to the respective platform, or they can be merged to create a comprehensive block list.

### Merging Block Lists
To combine multiple block lists into one (e.g., `list2mrg_block.txt`), simply use the following command (Linux/MacOS):

```bash
cat blockList.txt disney_block.txt netflix_block.txt roku_block.txt > mergedBlockList.txt
```

On Windows, you can use:

```bash
type blockList.txt disney_block.txt netflix_block.txt roku_block.txt > mergedBlockList.txt
```

This will create a new file `mergedBlockList.txt` containing the entries from all specified block lists.
