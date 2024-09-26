# Block Lists

This folder contains several block lists used to **explicitly block** access to specific services or content platforms. Each file within this folder represents a list of domains or IP addresses that are denied access based on the service or platform.

## Files

### 1. [`blockList.txt`](https://github.com/CosmicIndustries/block/blob/main/blockList.txt)
This is the general block list containing domains and services that are explicitly blocked. Use this file to prevent access to general domains that should not be accessed on your network.

### 2. [`disney_block.txt`](https://github.com/CosmicIndustries/block/blob/main/disney_block.txt)
This block list specifically targets **Disney** domains and services (e.g., Disney+, ESPN+). Use this file to block traffic to all Disney-related services on your network.

### 3. [`list2mrg_block.txt`](https://github.com/CosmicIndustries/block/blob/main/list2mrg_block.txt)
This is a block list intended to be merged with other lists. It contains additional domains that you may want to block alongside the general or specific service block lists.

### 4. [`netflix_block.txt`](https://github.com/CosmicIndustries/block/blob/main/netflix_block.txt)
This block list explicitly targets **Netflix** domains and services. Use this file to block all traffic to Netflix on your network.

### 5. [`roku_block.txt`](https://github.com/CosmicIndustries/block/blob/main/roku_block.txt)
This block list targets **Roku** domains and services, blocking any traffic to Roku-related platforms.

## Usage
These block lists can be used within firewall or content filtering systems to prevent access to the specific services or platforms mentioned in the lists. Each file can be used individually to block certain services or combined to create a more comprehensive block list.

### Merging Block Lists
To combine multiple block lists into one, simply use the following command (Linux/MacOS):

```bash
cat blockList.txt disney_block.txt netflix_block.txt roku_block.txt > mergedBlockList.txt
```

On Windows, you can use:

```bash
type blockList.txt disney_block.txt netflix_block.txt roku_block.txt > mergedBlockList.txt
```

This will create a new file `mergedBlockList.txt` containing the entries from all specified block lists.

---

## Optional: Blocking Everything Except Certain Domains (allowList)

If you want to block **everything** and allow only specific domains (like those in the original allow lists), this would require setting up a **whitelist policy** in your firewall or filtering system. Here's a general approach:

### Steps to Implement an Allow-Only List

1. **Block All Traffic By Default**:
   Configure your firewall or filtering system to block all outbound and inbound traffic by default.

2. **Allow Specific Domains**:
   Then, specify an allow list of domains that should be accessible. You can use the following rules in many firewall or content filtering systems:

   - For **Linux iptables**:
     ```bash
     # Block all outgoing traffic
     iptables -P OUTPUT DROP

     # Allow specific domains by IP (e.g., Netflix IP range)
     iptables -A OUTPUT -p tcp -d <IP_ADDRESS> -j ACCEPT
     ```

   - For **pfSense** or similar firewall systems:
     - Set the default rule to block all traffic.
     - Create exceptions for specific domains in the firewall rules section.
     - Use domain-based rules or translate domains into IPs if the system doesn’t support domain-based allow lists.

3. **Manage DNS Resolution**:
   If your system supports domain-based blocking, configure DNS filtering or domain-based firewall rules. Otherwise, you'll need to manually resolve the domains to their IPs and allow only those IP ranges.

* Forward all peer traffic - Ensure all traffic from the peer is tunneled through the router's wireguard interface by adding an Allowed IP of 0.0.0.0/0

By following this method, you will effectively block everything except the domains or services explicitly allowed in your configuration, such as Netflix, Disney, or Roku.
```
👋
Let me know if you'd like help setting up one of these methods!
```
