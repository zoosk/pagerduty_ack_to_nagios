NOTE THIS FORK IS NO LONGER MAINTAINED.  PLEASE REFER TO https://github.com/PagerDuty/pagerduty_ack_to_nagios WHICH IS THE NEW AUTHORITATIVE UPSTREAM
===============

pd_ack_to_nagios_ack_poller.pl
===============

to supplement https://github.com/PagerDuty/pagerduty-nagios-pl

pagerduty_nagios.pl does a good job of getting nagios events into
pagerduty... this script provides the reverse, for a more
round-trip-synced experience

more specifically, it polls pagerduty for new events since the last
poll, checks whether they are acks or resolves, and if so applies
those to their corresponding nagios alerts.  i.e., if you ack in
pagerduty, via sms or web ui or phone app, that ack will find it's way
back to your nagios instance.

set up a cron like so:

    * * * * * nagios /usr/local/bin/pd_ack_to_nagios_ack_poller.pl -p [my_pagerduty_token] -u [my_pagerduty_domain]

note this will generally need to be run as the nagios user so that it has write access to the nagios command pipe.
