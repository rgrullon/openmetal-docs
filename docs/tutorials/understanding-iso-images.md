# Understanding ISO images in the world of OpenStack  

## Background

In OpenStack, ISO images serve a similar purpose to CD-ROMs in traditional
computing environments. Let's explore this comparison:

- CD-ROMs in Traditional Computing:

- In traditional computing, CD-ROMs are physical discs used to store data,
software, and operating system installation files. Users insert these discs into
 CD-ROM drives on their computers to access or install software.

- ISO Images in OpenStack:

- In OpenStack, ISO images are digital files that serve the same purpose as
CD-ROMs. Instead of physical discs, ISO images are files that contain all the
necessary files and data required to install an operating system or software on
a virtual machine (VM).

## Content of ISO Images

- Just like CD-ROMs contain installation files, operating system images,
and other data, ISO images in OpenStack include the necessary files to install
an operating system on a VM. This includes the operating system itself, drivers,
configuration files, and any additional software.

## Attaching ISO Images to Virtual Machines

- In OpenStack, users attach ISO images to virtual machines during the VM
creation or configuration process. This is similar to inserting a CD-ROM into a
CD-ROM drive on a physical computer.

## Installation Process

- When a user attaches an ISO image to a VM in OpenStack, the VM boots from the
 ISO image, just like a computer boots from a CD-ROM. The installation process
 then begins, allowing the user to install the operating system onto the VM.

In summary, ISO images in OpenStack function similarly to CD-ROMs in traditional
computing environments. They contain installation files and data for operating
systems and software, and users attach them to virtual machines to install the
desired software or operating system. This comparison helps illustrate the role
of ISO images in OpenStack's virtualized environment.

To use an ISO image in OpenStack to create an instance with an operating system,
 you'll typically follow these steps:

- Upload the ISO Image to OpenStack:

- First, you need to upload the ISO image containing the operating system to
OpenStack. You can do this using the OpenStack dashboard (Horizon) or the
command-line interface (CLI). Here's an example CLI command to upload an ISO
image named fedora.iso:

```bash
openstack image create --container-format bare --disk-format iso --file fedora.iso fedora-iso
```

- Choose Flavor and Networking:

- Decide on the instance flavor (specifications like CPU, RAM, and disk size)
and networking settings (network and subnet) for your instance.

- Launch an Instance:

- Use the OpenStack dashboard or CLI to launch a new instance. When launching
the instance, select the uploaded ISO image as the boot source. Here's an example
CLI command to launch an instance named my-instance with the uploaded ISO image
as the boot source:

```bash
openstack server create --flavor FLAVOR_ID --image fedora-iso --nic net-id=NETWORK_ID my-instance
```

- Replace FLAVOR_ID with the ID of the flavor you want to use and NETWORK_ID
with the ID of the network you want to attach the instance to.

- Access the Instance Console:

- Once the instance is launched, you can access its console to interact with
the operating system installation process. This console allows you to see the
boot process and perform any necessary configuration. You can access the console
through the OpenStack dashboard or CLI.

## Complete Installation

- Follow the prompts in the instance console to complete the operating system
installation process. This typically involves selecting installation options,
configuring the network, setting up users, and so on.

- Eject ISO Image and Reboot:

- After the operating system installation is complete, eject the ISO image from
the instance. You can do this through the OpenStack dashboard or CLI. Then,
reboot the instance to boot from the installed operating system.

- Access the Instance:

- Once the instance has rebooted, you can access it using SSH
(for Linux instances) or Remote Desktop Protocol (RDP) (for Windows instances).
Use the instance's IP address and login credentials to access and manage it.

By following these steps, you can create an instance in OpenStack using an ISO
image as the boot source and install the desired operating system on the
instance. Adjust the commands and options based on your specific requirements and
environment.

## References

- <https://docs.openstack.org/image-guide/fedora-image.html>
