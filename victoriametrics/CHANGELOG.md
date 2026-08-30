- Use a fixed Ingress port

The app does not run on the host network, so there is no host port to
avoid clashing with and the Ingress port does not need to be randomized.
