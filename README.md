# DNS-over-HTTPS Utilities for OpenWrt

This repository contains two essential utilities for managing and verifying DNS-over-HTTPS (DoH) services on OpenWrt systems. These utilities include a DNS resolver script (`dns-resolver`) to ensure your DoH service is correctly configured and operational, and a DoH verification tool (`doh-verification`) to test the functionality of your DoH setup.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
  - [DNS Resolver](#dns-resolver)
  - [DoH Verification](#doh-verification)
- [Troubleshooting](#troubleshooting)
- [License](#license)

## Installation

1. Clone this repository to your OpenWrt system:

```bash
git clone https://github.com/inabakumori/dns-over-https-utilities-openwrt.git
```

2. Change to the cloned directory:

```bash
cd dns-over-https-utilities-openwrt
```

3. Make the scripts executable:

```bash
chmod +x dns-resolver doh-verification
```

4. Move the scripts to the appropriate directory:

```bash
mv dns-resolver /etc/init.d/
mv doh-verification /usr/local/bin/
```

## Usage

### DNS Resolver

The `dns-resolver` script is designed to ensure that your DoH service (v2raya and https-dns-proxy) is running and properly configured. It will attempt to start the services if they are not running and restart dnsmasq to apply changes.

To enable the DNS resolver:

```bash
/etc/init.d/dns-resolver enable
```

To start the DNS resolver:

```bash
/etc/init.d/dns-resolver start
```

To stop the DNS resolver:

```bash
/etc/init.d/dns-resolver stop
```

The script will log its actions and any errors to `/var/log/dns-resolver.log`.

### DoH Verification

The `doh-verification` script is a tool to verify the functionality of your DoH setup by performing DNS resolution tests for a list of domains.

To run the DoH verification:

```bash
/usr/local/bin/doh-verification
```

The script will log its actions and any errors to `/var/log/doh-verification.log`.

## Troubleshooting

If you encounter any issues with the DNS resolver or DoH verification, please check the respective log files (`/var/log/dns-resolver.log` and `/var/log/doh-verification.log`) for more information.

Common issues and their solutions:

- If the DNS resolver fails to start v2raya or https-dns-proxy, ensure that these services are installed and configured correctly on your OpenWrt system.
- If the DoH verification fails for any of the test domains, double-check your DoH setup, including the resolver IP and port in the `doh-verification` script.

Note: These utilities have been successfully tested on OpenWrt systems.

## License

This project is licensed under the GNU General Public License v3.0. See the [LICENSE](LICENSE) file for details.

---
