[TOC]
# Awesome Software Development

[Ruby Warrior - Learn Ruby Programming with Bloc](https://www.bloc.io/ruby-warrior#/)

## Rails 4.2 + Puma + IPv6 enabled OS = feel the pain

Since Rails 4.2, the `rails s` command no longer listens at *0.0.0.0* (means listen on all interfaces) by default, its default is now *localhost* instead.

For IPv4 only OS *localhost* is **always** *127.0.0.1*. For IPv6 enabled OS *localhost* may be either *127.0.0.1* or *::1*, so everything works if client, server and domain name system agree to use the same IP version.

Rails 4.2 with Puma web server on Mac OS X listens at *::1*. For me, it breaks *http://lvh.me* (the domain name is IPv4 only), *http://pow.cx* (it doesn’t cover IPv6 by design), gem "em-eventsource" and even Google Chrome (try to add `::1 subdomain.localhost` to */etc/hosts*; although it's not a problem for Safari, you'll fail to open *http://subdomain.localhost:3000* powered by Puma).

My Mac OS X "Network Service" name is *Ethernet (en0)*, so I turned off IPv6 support for ethernet:
		
	networksetup -setv6off "Ethernet (en0)"

Your mileage may vary.
