======================
Flowcharts
======================

Flowchart library
====================================
ILAO is using the `Mermaid.js <https://mermaid-js.github.io/mermaid/#/>`_ library to build and integrate Flowcharts and other diagrams into the website.

There is a `live editor <https://mermaid-js.github.io/mermaid-live-editor/#>`_ that can be used to build diagrams. 

.. code-block:: html

    <div class="mermaid">
    graph TB
      A[Hard edge] -->|Link text| B(Round edge)
      B --> C{Decision}
      C -->|One| D[Result one] 
      C -->|Two| E[fa:fa-car Result two]
      click D "https://www.illinoislegalaid.org" "Home"
    </div>

.. image:: ../assets/cms-flowchart.png

In the above image:
    
    * the flowchart is set to be top to bottom (graph TB)
    * A, B, C, D, E are the ids of the 5 blocks
    * Text within | | are text between pathways, for example One between C & D
    * Both hard edge and round edge use the rectangle, but the round edge class has rounded edges.
    * Result one includes a hyperlink to our website with a tooltip of Home
    * Result two includes the car font-awesome icon.
    


Configuration
===============
Flowcharts must be created using the text format "Diagrams." This ensures that characters are not escaped in a way that breaks the image.

To create a flowchart, use the `flowchart syntax <https://mermaid-js.github.io/mermaid/#/flowchart>`_ documentation. 

Theming
========
ILAO will design a standard visual design for flowcharts. Staff can use other themes as appropriate, or switch to the base theme and set custom theme variables.

See `theming documentation <https://mermaid-js.github.io/mermaid/#/theming>`_.

Icon support
=============

Mermaid supports the use of basic `font-awesome <https://fontawesome.com/icons?d=gallery>`_ icons.  While ILAO has a pro account, only the basic class is currently supported. 

.. todo:: determine if ILAO just needs to add support for fal/fas clases in font awesome to support the additional icon set.

Content format
================
Pages with a flowchart should be set to a content format of Flowchart.  This will cause the flowchart label and icon to display.







