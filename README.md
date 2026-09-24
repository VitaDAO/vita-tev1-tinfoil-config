# Vita Tev1 CPU test enclave

Attested deployment configuration for the private VitaDAO/vita-tev1-enclave serving image. Test deployment only: CPU accuracy and latency are measured separately from attestation. No database credentials or patient data are included. Clients use Tinfoil verification before sending private requests. No caller API key or manually supplied release version is required.

## Client connection

After deployment, run `tinfoil container connect vita-tev1-cpu --port 8770`. The proxy binds to loopback and verifies the enclave against this repository before forwarding requests. Use `http://127.0.0.1:8770/decide` or `/select` through that proxy. A generic HTTPS request is not evidence that attestation passed.

CPU test allocation: 8 vCPUs and 32768 MB, no GPU, no debug SSH, confidential computing enabled. The server allows one active inference and returns 429 while busy. No runtime outbound network is declared. The endpoint has no application API-key requirement and is publicly callable; enclave confidentiality does not restrict who can call it.
