# How to Write Your README

Your `README.md` must have these sections, in this order:

1. **Title** : which challenge you're answering
2. **My Approach** : why you chose a certain method, whenever relevant
3. **Step-by-Step Solution** : numbered steps, each with the command you ran, the output you got, and a screenshot
4. **Output / Results** : final outputs in proper code blocks (`bash`, `json`, `yaml`, whatever fits)

All screenshots go inside a `screenshots/` folder in your repo. Embed them in the README using relative paths. If it doesn't render on GitHub, it doesn't count.

Every command and every output must be inside a fenced code block with the right language tag. Raw unformatted pastes will not be accepted.

Below is a complete example. This was done on **macOS using `brew services` and `launchctl`** just to show you the format. Your challenge requires **Linux**, so you can't copy this. Follow the structure, not the commands.


## Example : Managing the `unbound` DNS Service on macOS

> This is a format demo only. Your submission must be on Linux. 

### My Approach

I'm on macOS (Sequoia 26.5, Apple Silicon) so I used `brew services` which is the Homebrew wrapper around `launchctl`. I picked `unbound` because it's a DNS resolver I installed via Homebrew and it's safe to start/stop without breaking anything on my machine. On macOS there's no `systemd`, so the equivalent is `launchd` and you interact with it through `launchctl` or the friendlier `brew services` CLI.

### Step-by-Step Solution

#### Step 1 : Check system info and pick a service

First I checked what OS I'm running and what services are available.

```bash
sw_vers
```

**Output:**

```text
ProductName:    macOS
ProductVersion: 26.5
BuildVersion:   25F71
```

```bash
brew services list
```

**Output:**

```text
Name      Status User File
dbus      none
openvpn   none
tailscale none
unbound   none
```

I picked `unbound` since it's installed but not running.

**Screenshot:**

![Step 1 : system info and service list](./screenshots/example/step1-system-info.png)

#### Step 2 : Start the service and find its PID

```bash
brew services start unbound
```

**Output:**

```text
==> Successfully started `unbound` (label: homebrew.mxcl.unbound)
```

Now find the PID:

```bash
pgrep -l unbound
```

**Output:**

```text
28410 unbound
```

Also confirmed through `launchctl`:

```bash
launchctl list | grep unbound
```

**Output:**

```text
28410   0   homebrew.mxcl.unbound
```

**Screenshot:**

![Step 2 : unbound started with PID](./screenshots/example/step2-service-started.png)

#### Step 3 : Stop the service

```bash
brew services stop unbound
```

**Output:**

```text
Stopping `unbound`... (might take a while)
==> Successfully stopped `unbound` (label: homebrew.mxcl.unbound)
```

Verified the PID is gone:

```bash
pgrep -l unbound
```

**Output:** _(no output, process is gone)_

**Screenshot:**

![Step 3 : unbound stopped](./screenshots/example/step3-service-stopped.png)

#### Step 4 : Start it again and kill it manually

Started it back up:

```bash
brew services start unbound
```

Got the new PID:

```bash
pgrep -l unbound
```

**Output:**

```text
28523 unbound
```

Now killed it directly instead of using `brew services stop`:

```bash
kill 28523
```

Checked what happened:

```bash
brew services list | grep unbound
```

**Output:**

```text
unbound   error  1        swar ~/Library/LaunchAgents/homebrew.mxcl.unbound.plist
```

Notice it says `error` instead of `none`. That's because `launchd` expected the process to keep running but it died unexpectedly. Same concept as `systemd` marking a service as `failed` when you `kill` it instead of doing a proper stop.

**Screenshot:**

![Step 4 : service in error state after kill](./screenshots/example/step4-killed-error.png)

#### Step 5 : Clean up

```bash
brew services stop unbound
```

**Output:**

```text
Stopping `unbound`... (might take a while)
==> Successfully stopped `unbound` (label: homebrew.mxcl.unbound)
```

Back to clean state.

### What I Learned

- On macOS, `brew services` wraps `launchctl` the same way `systemctl` wraps `systemd` on Linux. Different tools, same idea.
- Killing a managed process directly (`kill <PID>`) puts the service in an error/failed state on both macOS and Linux because the service manager didn't initiate the shutdown.
- `pgrep` works the same way on both macOS and Linux for finding PIDs.
