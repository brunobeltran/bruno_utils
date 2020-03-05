.. _plots:

Plotting utilities
==================

While :mod:`matplotlib`'s API often isn't very "discoverable", so there are
several topics that tend to trip up me and colleagues over and over.

Here, we document the proper ways to make :ref:`a line with varying colors
<colored_line>`, :ref:`colorbars for non-scatter plots <colorbar>`, as well as
(TODO), `how to use seaborn's "FacetGrid" intuitively`.

First, a quick overview about how colors as a whole work in :mod:`matplotlib`.

Colors in :mod:`matplotlib`
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Colors in :mod:`matplotlib` are typically specified by defining a map from data
values to color space. There are two parts to this map.

.. math::

    \text{data} \overset{\texttt{norm}}{\mapsto}
    [0, 1] \overset{\texttt{cmap}}{\mapsto} \texttt{RGB(a)}

TODO: finish documenting how to get norms, cmaps.

.. _colorbar:

Colorbars in :mod:`matplotlib`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

TODO: finish documenting scalarmappable/set_array stuff

.. _colored_line:

Lines with color gradients
^^^^^^^^^^^^^^^^^^^^^^^^^^

You would want

    >>> plt.plot(x, y, c)

to allow `c.shape == x.shape`, in analogy to `plt.scatter`. However, this is not
the case.

In order to work around this, we provide the function :func:`plot_colored_lines`
that takes parameters `t`, `x`, `y`, and plots line :math:`(x(t), y(t))`,
colored by :math:`t`.

Publication Quality
===================

While there are many write ups online that try to walk you through how to make
your plots publication quality in Matplotlib. However, I have yet to find one
that let's you accomplish what (I think) should be the typical requirements for
making a plot for publication:

1) Entire figure (including annotations, etc.) must match the column width of
the Journal
2) Actual axes themselves should have consistent aspect ratio or height (either
of which requires adjustment depending on how bulky the
ticks/labels/annotations are)
3) Font sizes requested should be reproduced exactly when the figure is placed
in the paper itself

Unfortunatley, Matplotlib does not make it easy to express these requirements,
and you have to dig much farther into the internal representation of how plots
are arranged than most users should ever have to in order to actually make it
work.

Let's walk through a typical, seemingly simple figure together.



