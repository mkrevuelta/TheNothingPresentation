cmake_minimum_required (VERSION 2.8.12)

project (PresentationProject NONE)

if (NOT EXISTS ./UseLATEX.cmake)
    message (FATAL_ERROR "\nCan't find UseLATEX.cmake\nPlease, download it from:\n\thttps://cmake.org/Wiki/images/8/80/UseLATEX.cmake\nor:\n\thttps://github.com/kmorel/UseLATEX\nand save a copy together with this CMakeLists.txt")
endif ()

include (UseLATEX.cmake)

# Temporary files and output will be saved in this directory
set (LATEX_OUTPUT_PATH build)

# Name of the main TEX file
set (PRESENTATION_NAME Presentation)

# Sections and other stuff
set (PRESENTATION_SUBDOCUMENTS
    src/latex/TitlePageData.tex
    src/latex/PackagesAndCustomCommands.tex
    src/latex/Colors.tex
    src/latex/1_Intro.tex
    src/latex/2_SomeStuff.tex
    src/latex/3_SomeMoreStuff.tex
    )

add_latex_document (src/latex/${PRESENTATION_NAME}_169_handout.tex
    INPUTS src/latex/${PRESENTATION_NAME}.tex
           src/latex/Header_169.tex
           ${PRESENTATION_SUBDOCUMENTS}
    IMAGE_DIRS src/figs
    )

add_latex_document (src/latex/${PRESENTATION_NAME}_43_handout.tex
    INPUTS src/latex/${PRESENTATION_NAME}.tex
           src/latex/Header_43.tex
           ${PRESENTATION_SUBDOCUMENTS}
    IMAGE_DIRS src/figs
    EXCLUDE_FROM_DEFAULTS
    )

add_latex_document (src/latex/${PRESENTATION_NAME}_169.tex
    INPUTS src/latex/${PRESENTATION_NAME}.tex
           src/latex/Header_169.tex
           ${PRESENTATION_SUBDOCUMENTS}
    IMAGE_DIRS src/figs
    EXCLUDE_FROM_DEFAULTS
    )

add_latex_document (src/latex/${PRESENTATION_NAME}_43.tex
    INPUTS src/latex/${PRESENTATION_NAME}.tex
           src/latex/Header_43.tex
           ${PRESENTATION_SUBDOCUMENTS}
    IMAGE_DIRS src/figs
    EXCLUDE_FROM_DEFAULTS
    )

