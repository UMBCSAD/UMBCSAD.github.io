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
