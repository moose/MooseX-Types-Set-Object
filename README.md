# NAME

MooseX::Types::Set::Object - Set::Object type with coercions and stuff.

# VERSION

version 0.04

# SYNOPSIS

    package Foo;
    use Moose;

    use MooseX::Types::Set::Object;

    has children => (
        isa      => "Set::Object",
        accessor => "transition_set",
        coerce   => 1, # also accept array refs
        handles  => {
            children     => "members",
            add_child    => "insert",
            remove_child => "remove",
            # See Set::Object for all the methods you could delegate
        },
    );

    # ...

    my $foo = Foo->new( children => [ @objects ] );

    $foo->add_child( $obj );

# DESCRIPTION

This module provides a Moose type constraint (see
[Moose::Util::TypeConstraints](https://metacpan.org/pod/Moose::Util::TypeConstraints), [MooseX::Types](https://metacpan.org/pod/MooseX::Types)).
Note that this constraint and its coercions are __global__, not simply limited to the scope that
imported it -- in this way it acts like a regular [Moose](https://metacpan.org/pod/Moose) type constraint,
rather than one from [MooseX::Types](https://metacpan.org/pod/MooseX::Types).

# TYPES

- Set::Object

    A subtype of `Object` that isa [Set::Object](https://metacpan.org/pod/Set::Object) with coercions to and from the
    `ArrayRef` type.

# SEE ALSO

[Set::Object](https://metacpan.org/pod/Set::Object), [MooseX::AttributeHandlers](https://metacpan.org/pod/MooseX::AttributeHandlers), [MooseX::Types](https://metacpan.org/pod/MooseX::Types),
[Moose::Util::TypeConstraints](https://metacpan.org/pod/Moose::Util::TypeConstraints)

# AUTHOR

יובל קוג'מן (Yuval Kogman) <nothingmuch@woobling.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2008 by Yuval Kogman.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.

# CONTRIBUTORS

- Florian Ragwitz <rafl@debian.org>
- Karen Etheridge <ether@cpan.org>
- Yuval Kogman <nothingmuch@woobling.org>
