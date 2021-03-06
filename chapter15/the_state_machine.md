## The VM Provisioning State Machine

The VM Provisioning State Machine (VMProvision_VM) schema contains a number of States, as shown (illustrated is the _template_ Instance of this State Machine)...
<br>

![screenshot](images/screenshot11.png)

<br>

Several of these States (such as _RegisterCMDB_ ) contain no out-of-the-box values, but we are free to copy the State Machine into our own Domain, and add Instance URIs to the States as required. A common addition is to add a method at the _AcquireIPAddress_ step to retrieve an IP address from a corporate IPAM solution such as an Infoblox Appliance. Once retrieved, the IP address is inserted into the _Task's_ options hash using the ```.set_option``` method, e.g.

```ruby
$evm.root['miq_provision'].set_option(:ip_addr, allocated_ip_address)
```