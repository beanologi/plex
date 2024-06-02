# _plex_

Portalab Executive


## Status

In early development phase.


## Description

`plex` is an essential component of Portalab and is used to manage the lab resources.

<details>
<summary>
<b>Wait... what is "Portalab" anyways?</b>
</summary>
Portalab is a distribution of tools designed for provisioning reproducible, virtualized, homelab environments. It aims to provide value to the learning community by offering an accessible, non-invasive, and flexible way to set up the computing and network infrastructure needed to develop hands-on skills used by professionals.
</details>


## Architecture and Design

This is just a bunch of general preaching and blabbering about things to keep in mind while developing `plex`.

### Overview

As you can imagine, `plex` runs as a core service bundled with all distributions of Portalab. Therefore, it is expected to pretty much always be running when using Portalab and should be built to be quite fault-tolerant. However, in the event of a failure or scheduled interruption of service, the state of the lab should always be safely determined and recovered. Basically, one of the most important jobs of `plex` is maintaining a sane sense of the lab's state to accurately represent for the user while simultaneously also providing a safe and powerful interface for that user to manipulate the lab state while not corrupting itself in the process. This is usually the same story for just about any other service but oh well, the author decided to reiterate that for some reason.

### Technologies

The web application side of `plex` is implemented using the **Nuxt framework**.

### Influential Forces of Truth and Concern in ~~no~~ _some_ particular order

1. Predefined tasks that must happen on startup and shutdown

2. FIFO queue of tasks to perform against the lab, making sure to drop new task requests that conflict with senior ones.

3. Environment Variables

4. Plaintext Configuration File Directives

5. Values set in Database Table

6. IPC with other core components

7. API Requests originating from Web Application


