# Greenbank Lab Environment: Intro and Etiquette

The Greenbank Lab Environment has been established for the purpose of creating a space for the as- Oops, wrong document. It's been established for the purpose of giving SAD members an always-on, remotely-accessible environment to practice Linux administration, virtualization, basic networking, identity management technologies, web hosting, and so on. And just to have fun with.

**It's here for YOU, so please, make use of it!** Don't be afraid of using up resources or breaking something. The beauty of virtualization is that it allows us to back up everything anyways. If you use too many resources, we'll let you know. It's been built for you guys, so have fun with it.

That said, it is a shared computing environment running on our own physical hardware, so we have to set some reasonable restrictions. This document will explain how to make use of the environment and how to be a good "SAD citizen".

## Da Rules

### Rule One: Don't break other people's stuff

Don't *intentionally* break the infrastructure or other people's VMs.

So don't spam the shutdown buttons or screw up the proxy or whatever just because you feel like it. We trust all of you to not do that, and I really doubt anyone will ever break something intentionally, but it had to be said.
- Note: Breaking your *own* VMs is allowed; encouraged, even. Do whatever you want to your own stuff, as long as you're reasonably certain nobody else is using it.
- Security "recon" is allowed, think `nmap` and similar tools... again, encouraged, even. You can *find* security holes, just don't exploit them to harm stuff. There's various personal info on here, if you manage to access it, don't snoop around in it too much.

### Rule Two: Don't let the bad guys in

Don't create security holes.

Basically that means be careful with the **firewall** and the **VPN**. Don't create port-forwards without getting approval. Don't work around the firewall (reverse shells and other such tunnels). Don't give out your VPN cert. If your VPN cert is compromised, you must inform us *immediately* so that we can revoke the certificate. We have an internal security system but it's best not to rely on it.

It also means don't test **malware** on Greenbank systems. Malware is cool and fun, but it's more the domain of the Cyberdawgs and Malware Research Group, not us. If you'd really like to try it, let the board know and we'll make a specially-secured VM for that purpose.

## Getting Started: VPN Access and Changing your Password

Now that that's over with - we'll explain how to actually get logged in!

You should have been given a username and a default password.

You should have also been given an `ovpn` file with your VPN certificate. This file (plus your password) is what grants you access to the internal network. Guard it closely. Again, if this file gets compromised (say your machine is stolen or you find out you have a bad malware infection) tell us ASAP and we'll revoke your cert and give you a fresh one.

If you weren't given all this stuff then contact the board to get access!

Anyways, you'll need to install OpenVPN...

### Installing and Connecting

- **Windows**: Go here https://openvpn.net/community-downloads/ and grab the Windows 64-bit MSI installer and install it. You should see OpenVPN GUI in your start menu now; open it. It should pop up a little screen with a lock on it in your notifications tray, like [this](https://i.imgur.com/6TB126q.png). Right-click on it, and click `Import File...`. Find the `.ovpn` file you were given (it should be something like `sadgreenbank-yourname-2021-02-06.ovpn`) and import it. Then hit Connect. Log in with the username and password we gave you. If there's a failure/error you might need to reboot your machine (or restart the Service, but reboot is easier).
- **Mac**: Go here https://openvpn.net/vpn-server-resources/connecting-to-access-server-with-macos/ and scroll to `OpenVPN Connect v3` and grab the `OpenVPN Connect v3 for macOS` installer. Install it and use the GUI to import the `.ovpn` file and connect. Log in with the username and password we gave you.
- **Linux**: Instructions are available here https://openvpn.net/vpn-server-resources/connecting-to-access-server-with-linux/. Generally you should probably install the OpenVPN Client using the package manager for your particular distro. Follow the instructions and run the appropriate command to connect, probably `openvpn --config [yourfilegoeshere].ovpn`. Log in with the username and password we gave you.
- **BSD**: IDK google it
- **Plan 9**: wha- 👀

### Testing VPN Connectivity

If the connection window disappears and now you have a green status icon, or a checkmark, or something similar, then you should be connected.

Try, in the terminal, `ping 192.168.1.50` and `ping 192.168.1.1`. If both of these work, then you should be good to go. Try visiting http://192.168.1.1 in your web browser (you'll need to clear the self-signed-cert warning; in Firefox hit `Advanced...` then `Accept the Risk and Continue`, for example). You should see the pfSense login page. You should be able to log in with your username and password, though it'll probably just give you an error screen as you have no pfSense perms by default. If any of these steps failed, let us know.

Now we should test the DNS. Try going to https://pfsense.greenbank.lan in your browser. This should take you to the same page you were on before. If it doesn't work, let us know.

Basically, if you can go to https://pfsense.greenbank.lan in your browser and see the pfSense login screen, then the VPN is working. Cool!

### Changing Your Password

Please change your password (and remember it; or even better, put it in a password manager) before you disconnect. We'd really like everyone to not be using the default passwords.

Note: Passwords are hashed, salted, and stored securely in FreeIPA... but this is nevertheless a shared lab environment, potentially vulnerable to data breaches or MITM attacks. *Please* don't use, like, the same password that you've used for your bank accounts and UMBC accounts here. Please make a unique password.

Go to https://ipa.greenbank.lan in your browser and log in using your default username and password. It should succeed, then say `Your password has expired. Please enter a new password.` and immediately prompt you to make a password change. Enter your current password (the default one we provided you) and then your desired new password. Leave the OTP field blank. Submit the form.

This should bring you to your user account page. Feel free to customize it and give yourself a job title or phone number or something, I guess. (Don't add your address unless you want the entirety of SAD visiting your house.)
