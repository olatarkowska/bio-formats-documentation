.. _source-obtain-and-build:

Obtaining and building Bio-Formats
==================================

.. note:: Bio-Formats requires Java 8 or above

.. _source-code:

Source code
-----------

The source code for this Bio-Formats release is available from the
:downloads:`downloads site <>`.
This release and the latest
Bio-Formats source code are also available from the Git repository.
This may be accessed using the repository path::

    git@github.com:openmicroscopy/bioformats.git

More information about Git and client downloads are available from the
`Git project website <https://git-scm.com/>`_.  You can also browse the
`Bio-Formats source on GitHub
<https://github.com/openmicroscopy/bioformats>`_

.. note::

    Windows users must set git to use ``core.autocrlf=input`` to
    ensure that Bio-Formats uses LF rather than CRLF line endings,
    otherwise the build will fail (Genshi can't process code templates
    with CRLF line endings, leading to broken sources being
    generated).  This can be set globally in the registry when
    installing :program:`msysgit` or by editing :file:`etc/gitconfig`
    in the git installation directory.  Annoyingly, these settings
    appear to override per-user and per-repository configuration
    values, requiring these to be set globally.

Lastly, you can browse the :javadoc:`Bio-Formats Javadocs online <>`,
or generate them yourself using the "docs" Ant target.


Source code structure
---------------------

The Bio-Formats code is divided into several projects. Core components
are located in subfolders of the :sourcedir:`components <components/>` folder,
with some components further classified into :sourcedir:`components/forks
<components/forks/>`, depending on the nature of the project. See the
:doc:`components` for more information, including associated build targets
for each component.

Each project has a corresponding Maven POM file, which can be used to
work with the project in your favorite IDE, or from the command line,
once you have cloned the source.

.. _source-building:

Building from source
--------------------

Instructions for several popular options follow.  In all cases, make
sure that the prerequisites are installed before you begin.

If you are interested in working on the Bio-Formats source code itself,
you can load it into your favorite IDE, or develop with your favorite
text editor.

NetBeans
^^^^^^^^

NetBeans comes with Maven support built in. To import the Bio-Formats
source, perform the following steps:

#. Select :menuselection:`File --> Open Project` from the menu - choose the
   top-level path to bioformats.git and click :menuselection:`Open Project`
#. In the 'Projects' tab on the left-hand side, expand the 'Bio-Formats
   projects' entry - you should now have a series of folders including 'Other
   Sources', 'Modules' and 'Dependencies.
#. Expand the 'Modules' folder to give a list of components and then
   double-click the desired project(s) to work with them.

.. figure:: /images/netbeans.png
    :align: center
    :alt: Opening Bio-Formats in Netbeans

Alternately, you can clone the source directly from NetBeans into a
project by selecting :menuselection:`Team --> Git --> Clone Other...` from
the menu.

Eclipse
^^^^^^^

Eclipse uses the "Maven Integration for Eclipse" (m2e) plugin to work with
Maven projects. It is more flexible than Eclipse's built-in project
management because m2e transparently converts between project dependencies
and JAR dependencies (stored in the Maven repository in
:file:`~/.m2/repository`) on the build path, depending on which projects are
currently open.

We recommend using Eclipse 4.3 (Kepler) or later, specifically -
"Eclipse IDE for Java developers". It comes with m2e installed
(http://eclipse.org/downloads/compare.php?release=kepler).

You can import the Bio-Formats source by choosing
:menuselection:`File --> Import --> Existing Maven Projects` from the menu
and browsing to the top-level folder of your Bio-Formats working copy.
Alternatively, run the Eclipse Maven target with :command:`mvn
eclipse:eclipse` to create the Eclipse project files, then use
:menuselection:`File --> Import --> Existing Maven Projects`.

Command line
^^^^^^^^^^^^

If you prefer developing code with a text editor such as vim or emacs,
you can use the Ant or Maven command line tools to compile Bio-Formats.
The Bio-Formats source tree provides parallel build systems for both Ant
and Maven, so you can use either one to build the code.

For a list of Ant targets, run::

    ant -p

In general, ``ant jars`` or ``ant tools`` is the correct command.

When using Maven, Bio-Formats is configured to run the "install" target
by default, so all JARs will be copied into your local Maven repository
in :file:`~/.m2/repository`. Simply run::

    mvn

With either Ant or Maven, you can use similar commands in any subproject
folder to build just that component.
