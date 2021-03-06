Changes for April 2010
======================


List of key changes for April 2010 major release of the ome-xml data
model.

The new major release of the schema has a new namespace and all version
numbers are reset to 1. As a major release, any file that validated
correctly using the last major release will probably not validate
correctly using this new release. Some files that failed to validate
before will now be valid. It is important to update any file readers and
writers to understand the changes.


The version number of all schema files is now 1.

This schema uses the new namespace

::

    http://www.openmicroscopy.org/Schemas/[NameSpaceTitle]/2010-04/

For the OME schema

::

    http://www.openmicroscopy.org/Schemas/OME/2010-04/

and the schema file is located at

::

    http://www.openmicroscopy.org/Schemas/OME/2010-04/ome.xsd

Overview of components changed
------------------------------

-  schema cleanup
-  units
-  ROI changes
-  SPW changes
-  Filter changes


Schema cleanup
^^^^^^^^^^^^^^

The following legacy objects have been removed:

-  :file:`AnalysisChain.xsd`
-  :file:`AnalysisModule.xsd`
-  :file:`CA.xsd`
-  :file:`CLI.xsd`
-  :file:`DataHistory.xsd`
-  :file:`MLI.xsd`
-  :file:`STD.xsd`

This required the removal of references to them from ``ome.xsd``; the removal 
of ``CustomAttributes`` from OME, Image and Dataset nodes; and the removal of 
``SemanticTypeDefinitions`` from the OME Node. 

Units
^^^^^

-  Units were defined for everything in

   -  :file:`ome.xsd`
   -  :file:`ROI.xsd`
   -  :file:`SPW.xsd`

Follow some examples:

::

    Physical size of a pixel in microns[um]
    The Z-section this plane is for. [units:none]
    This is the name of the fluorophore used to produce this channel [plain text string]

ROI changes
^^^^^^^^^^^

-  ROI now has:

   -  an optional ``Description`` element
   -  an optional ``Name`` attribute
   -  an optional ``Namespace``

-  Shape now has:

   -  an abstract marker in an appinfo
   -  an optional ``Name`` attribute
   -  ``ChannelRef [0..\*]`` removed
   -  ``TheC`` added linked to ``Channel [0..1]``
   -  all the attributes previously on the dropped ``ShapeDisplayOptions`` 
      e.g. ``Fill``, ``Stroke``, ``FontFamily``, etc.

-  The ``Text`` element has been renamed to ``Label``.

SPW changes
^^^^^^^^^^^

-  ``Plate`` now has:

   -  ``PlateAcquisition [0..\*]`` added
   -  an attribute ``Rows``
   -  an attribute ``Columns``
   -  a unique key ``WellSampleIndex`` added for the attribute ``Index`` in
      ``SPW:Well/SPW:WellSample``
   -  ``DefaultSample`` removed

-  ``ScreenAcquisition`` has become ``PlateAcquisition``.

-  ``PlateAcquisition`` now has:

   -  an optional ``Description`` element added
   -  an optional ``Name`` attribute added
   -  an optional ``MaximumFieldCount`` attribute added

-  ``Screen`` now has ``ScreenAcquisition`` removed.

-  ``WellSample`` now has ``Index`` added.

Filter changes
^^^^^^^^^^^^^^

-  Filter now has type 'Dichroic'.
-  There is a new ``LightPath`` object (this provides much more flexibility 
   than ``SecondaryEmissionFilter`` and ``SecondaryExcitationFilter``).

Other
^^^^^

-  There have been changes and additions made to ``Detector``.
-  The lack of LED attributes was explained in documentation.

