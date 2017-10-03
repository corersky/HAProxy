# HAProxy
Running HTTPS, SSH and VPN on port 443

<p>A port can only be bound to one service at a time, which makes perfect sense since the OS cannot possibly know which application to route the packet to. However, protocols often have distinct signatures, for example the first few bytes of SSH is always <code>SSH-2.0</code> while HTTP packets always start with <code>{HEAD|GET|PUT|POST|DELETE|OPTIONS}</code>. So technically, it should be possible for a proxy application to perform Deep Packet Inspection (DPI) and route it to the correct service if the signatures are provided. </p>
<p><a href="http://www.haproxy.org">HAProxy</a> is one such application, with the capability to redirect packets at both TCP as well as HTTP (application) layer. A word of warning though, the documentation is a tad lengthy, 110,000 words over 15,000 lines. After a few weeks of messing around with the settings, I finally got it to work and now have HTTPS, SSH and VPN listening on port 443.</p>
<p>This is not purely an academic exercise, there are some real world benefits. Firstly, if you are connecting from behind a restrictive firewall, say one that only allows port 80 and 443, you will now be able to SSH/VPN out of that network, unless of course that restrictive firewall itself performs DPI, in which case, you might have to consider tunnelling SSH through SSL, which incidentally is also supported by HAProxy. Secondly, you can "cloak" your services. Someone performing a port scan would only see the default service, thus adding another layer of security to your server.</p> 

Information source: https://limbenjamin.com/articles/running-https-ssh-vpn-on-port-443.html
