# Points to Remember
---
## Main Components of Snort

  - Packet Decoder - Packet collector component of Snort. It collects and prepares the packets for pre-processing. 
  - Pre-processors - A component that arranges and modifies the packets for the detection engine.
  - Detection Engine - The primary component that process, dissect and analyse the packets by applying the rules. 
  - Logging and Alerting - Log and alert generation component.
  - Outputs and Plugins - Output integration modules (i.e. alerts to syslog/mysql) and additional plugin (rule management detection plugins) support is done with this component. 
  - There are three types of rules available for snort
---
  - Community Rules - Free ruleset under the GPLv2. Publicly accessible, no need for registration.
  - Registered Rules - Free ruleset (requires registration). This ruleset contains subscriber rules with 30 days delay.
  - Subscriber Rules (Paid) - Paid ruleset (requires subscription). This ruleset is the main ruleset and is updated twice a week (Tuesdays and Thursdays).

Note: Once you install Snort2, it automatically creates the required directories and files. However, if you want to use the community or the paid rules, you need to indicate each rule in the snort.conf file.

Since it is a long, all-in-one configuration file, editing it without causing misconfiguration is troublesome for some users. That is why Snort has several rule updating modules and integration tools. To sum up, never replace your configured Snort configuration files; you must edit your configuration files manually or update your rules with additional tools and modules to not face any fail/crash or lack of feature.

snort.conf: Main configuration file.
local.rules: User-generated rules file.
Let's start with overviewing the main configuration file (snort.conf) sudo gedit /etc/snort/snort.conf

Navigate to the "Step #1: Set the network variables." section.

This section manages the scope of the detection and rule paths.

TAG NAME	INFO	EXAMPLE
HOME_NET That is where we are protecting.  'any' OR '192.168.1.1/24'
EXTERNAL_NET This field is the external network, so we need to keep it as 'any' or '!$HOME_NET'. 'any' OR '!$HOME_NET'
RULE_PATH Hardcoded rule path. /etc/snort/rules
SO_RULE_PATH These rules come with registered and subscriber rules. $RULE_PATH/so_rules
PREPROC_RULE_PATH These rules come with registered and subscriber rules. $RULE_PATH/plugin_rules

Navigate to the "Step #2: Configure the decoder." section.

In this section, you manage the IPS mode of snort. The single-node installation model IPS model works best with "afpacket" mode. You can enable this mode and run Snort in IPS.

TAG NAME	INFO	EXAMPLE
#config daq:	IPS mode selection.	afpacket
#config daq_mode:	Activating the inline mode	inline
#config logdir:	Hardcoded default log path.	/var/logs/snort
Data Acquisition Modules (DAQ) are specific libraries used for packet I/O, bringing flexibility to process packets. It is possible to select DAQ type and mode for different purposes.

There are six DAQ modules available in Snort;

Pcap: Default mode, known as Sniffer mode.
Afpacket: Inline mode, known as IPS mode.
Ipq: Inline mode on Linux by using Netfilter. It replaces the snort_inline patch.  
Nfq: Inline mode on Linux.
Ipfw: Inline on OpenBSD and FreeBSD by using divert sockets, with the pf and ipfw firewalls.
Dump: Testing mode of inline and normalisation.
The most popular modes are the default (pcap) and inline/IPS (Afpacket).

Navigate to the "Step #6: Configure output plugins" section.

This section manages the outputs of the IDS/IPS actions, such as logging and alerting format details. The default action prompts everything in the console application, so configuring this part will help you use the Snort more efficiently. 

Navigate to the "Step #7: Customise your ruleset" section.

TAG NAME	INFO	EXAMPLE
# site specific rules
Hardcoded local and user-generated rules path.	include $RULE_PATH/local.rules
#include $RULE_PATH/
Hardcoded default/downloaded rules path.
include $RULE_PATH/rulename
Note that "#" is commenting operator. You should uncomment a line to activate it.
