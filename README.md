# rtpengine-systemd
Runing Sipwise RTPEngine under systemd control.

Follow these steps:

	# git clone https://github.com/Binan/rtpengine-systemd.git

	# cd rtpengine-systemd

Edit the configuration file " rtpengine-conf " to reflect your configuration. Then install the files in your system:

	# cp rtpengine-conf /etc/default/rtpengine-conf

	# cp rtpengine.service /usr/lib/systemd/system/rtpengine.service

	#  cp rtpengine-start /usr/bin/rtpengine/rtpengine-start
	#  cp rtpengine-stop-post /usr/bin/rtpengine/rtpengine-stop-post

	# chmod +x /usr/bin/rtpengine/rtpengine-start

	# chmod +x /usr/bin/rtpengine/rtpengine-stop-post

In the systemd unit file, the option "ExecStopPost" is used to clean the system after the RTPEngine daemon is stopped. This incolves: deleting the forwarding table, the iptables related rules, and unload the kernel module (xt_RTPENGINE).

Now you can enable/start/stop/status of the rtpengine service as following:
	# systemctl enable rtpengine.service
	# systemctl start rtpengine.service
	# systemctl status rtpengine.service
	# systemctl stop rtpengine.service
iRestart your system. Check if RTPEngine is working under systemd control.
