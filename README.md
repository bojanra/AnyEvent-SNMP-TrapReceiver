[![Actions Status](https://github.com/bojanra/AnyEvent-SNMP-TrapReceiver/actions/workflows/test.yml/badge.svg)](https://github.com/bojanra/AnyEvent-SNMP-TrapReceiver/actions)
# NAME

AnyEvent::SNMP::TrapReceiver - SNMP trap receiver by help of AnyEvent

# SYNOPSIS

    use AnyEvent::SNMP::TrapReceiver;

    my $cond = AnyEvent->condvar;

    my $echo_server = AnyEvent::SNMP::TrapReceiver->new(
        bind => ['0.0.0.0', 162],
        cb => sub {
            my ( $trap) = @_;
        },
    );

    my $done = $cond->recv;

# DESCRIPTION

This is a wrapper for the AnyEvent::Handle::UDP with embedded SNMP trap decoder.

Currently only v1 and v2c traps are supported.

The trap decoder code was copied from Net::SNMPTrapd by Michael Vincent.

# ATTRIBUTES

## bind

The IP address and port to bind the UDP listener/handle.

## cb

The codeblock to be called when a trap is received.

# LICENSE

Copyright (C) Bojan Ramšak.

This library is free software; you can redistribute it and/or modify
it under the same terms as Perl itself.

# AUTHOR

Bojan Ramšak <bojanr@gmx.net>
