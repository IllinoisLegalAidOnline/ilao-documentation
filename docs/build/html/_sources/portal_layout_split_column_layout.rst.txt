==================================
Portal layout split column layout
==================================

The portal layout split column is used to show two side-by-side (desktop) or stacked text blocks (mobile)

.. image:: ../assets/portal-split-column-edit.png

The portal split column layout should contain 2 blocks fo portal text. A portal text component consists of:

* a portal icon (not required; not displayed to users).
* a title (required)
* a summary (required)
* optionally a button/link. 

.. note::  The portal icon field will be removed in a future release

What users see
================

.. image:: ../assets/portal-split-column-desktop.png
   :scale: 50%

.. image:: ../assets/portal-split-column-mobile.png
   :scale: 50%

Placement
============

Portal split column layouts  are always placed in the left column (desktop) and beneath any sidebar items on mobile.

Portal split column layouts are rendered in the order they are placed in the main column, except that timelines always render last.

Portal text within a layout are rendered in the order in which they are placed.