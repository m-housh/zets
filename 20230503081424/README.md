# Hydronic Infloor

1. Do I need a buffer tank?

A buffer tank is generally used to control the cycling of the boilers (especially at part load conditions),
so it will depend on if the boilers are modulating and what the turn-down ratio is on the boilers.  In your
scenario with (2) Weil McLain Ultra's a buffer tank is probably not required.

2.  What controls should I use?

I'm not real familiar with the Weil McLain's control setup, on Lochinvar (the brand I generally use), they
have built-in controls that can handle most of my needs (handles lead / lag and staging themselves) they
also handle outdoor reset with the on-board controls. I would imagine that Ultra's would have similar
capabilities.

3. What should control my water temperature?

This will partially depend on what is decided for question (2).  I would generally run the outdoor reset
curve on the boiler to control the water temperature, but once again I'm more familiar with the Lochinvar
family of boilers.

4.  How can I have indirect water heater supplied from both boilers?

I'm not sure that I've ever had to do an indirect that is supplied by (2) boilers, but in theory it should
just be piped together with an aquastat that sends a signal to each boiler to tell it that it's in DHW mode.
I would probably consult the documents for the Ultra boilers on this one.  That said, aside from redundancy I'm
not sure there's a ton of benefit as one of the boilers ought to have plenty of output to handle DHW needs.

5.  Can I run 3/4 pex to my manifolds?

This is not an easy to answer question without knowing the flow rate, btu's, and fitting / tubing lengths
required for each manifold / circuit... I'm going to go with most likely yes, but it ultimately depends.

6. Can I use taco 0018e to supply water to manifolds?

My answer to this question is basically the same as my answer to question (5)... "It depends".

7. What should I use to control the water flow, actuators on the manifold or pump for each zone?

This is also an "it depends" answer, either way is valid and will depend on how the loops / zones are
setup.  Personally I like to try and use actuators where possible to cut down on the number of accessory
pumps (as you generally need a few pumps for near boiler piping arrangements and pumps are fairly pricey).
Actuators often allow you to use the same manifold to supply multiple zones, so it sorta depends on your
needs and you may have to mix and match.

8. Is 8" spacing good for aluminum plates?

I would consult the docs for this one, the spacing generally influences the BTU/ft^2 that is output to the space.
So the space BTU's required vs. the square footage you have to work with for a given space determines the spacing.
And this also influences the water temeratures required to maintain the space temperature, so the closer the spacing
the lower the supply water temperature, but it's obviously a balancing act between material cost and efficiency.

Here is an example of upward heat output vs. tubing spacing.

![Upward Heat Output](https://github.com/m-housh/zets/blob/main/20230503081424/assets/Screenshot%202023-05-03%20at%208.12.43%20AM.png)

9. What pipe spacing should I do for basement and garage?

See answer (8).

