# Makefile_preset

A versatile Makefile Preset for C/C++ projects.

Feel free to use the preset for any projects, if it helps. The repository is published under a permissive Apache 2.0 License.

The file is still subject to change, and will be updated if any issues or missing features are reported. For bugs, feature requests and recommendations, use this repository's git issues.

Includes some features not provided by simple GCC or implicit make rules, or even simple Makefiles. Expects at least very basic knowledge of make and Makefile syntax.

__Features:__
 - split compilation and linking process
 - recompilation based on automatic header file dependencies
 - a recursively searched source file path
 - option to turn on address sanitizer
 - code documentation generation (e.g. using doxygen)
 - simple configuration for reasonably complex projects

## Usage

To use this in your project, simply copy the file 'Makefile_preset' to the project folder *(rename it to just 'Makefile' if make should use the file by default)* and configure the file. 

Afterwards, calling `make help` displays the available options and commands. Based on user configuration, the compilation, linking and other targets will be displayed. At that point, the Makefile can be used normally within the project.

## Configuration

The Makefile is configured using Make variables, all declared at the start of the file. The user can edit said variables, which modifies the behavior of the file to match the needs of a given project.

Most of the options can be kept to their default values, however, they are modifiable, in case it is necessary for a specific use-case.

The configurable variables are as follows:

### General project settings
 - __PROJECT_NAME__ ... The name of the project, to be displayed in the help target - **needs to be configured**
 - __OUTFILE__ ... The name of the output executable file - **needs to be configured**

### Compiler and linker programs
 - __CC__ ... The C/C++ compiler program; the default is *gcc*
 - __LD__ ... The C/C++ linker program; the default is *gcc*

### C/C++ Language settings
 - __SOURCE_EXT__ ... The file extension of source files - **should be changed if C++ (or other language) used**; the default is *c*
 - __OBJECT_EXT__ ... The file extension of compiled object files; the default is *o*
 - __DEPENDENCY_EXT__ ... The file extension of files describing additional generated dependencies on included header files; the default is *dep*

### C/C++ Compiler and linker settings
 - __COMPILE_FLAG__ ... The compiler flag to specify an input source file to be compiled; the default is *-c*
 - __OUTPUT_FLAG__ ... The compiler/linker flag to specify an output file; the default is *-o*
 - __DEPENDENCY_FLAG__ ... The compiler flag to generate dependencies for source files derived from included header files; the default is *-MM*
 - __DEP_TARGET_FLAG__ ... The compiler flag specifying the format of the generated dependency target; the default is *-MT*

### Directories
 - __BUILD_DIR__ ... The directory to output compiled object files into; the default is *build*
 - __SOURCE_DIR__ ... The directory containing your project source files - **needs to be configured**
 - __DEPS_DIR__ ... The directory to output generated dependency data into; the default is *.dependencies*
 - __DOCS_DIR__ ... The directory to output generated documentation into; the default is *doxygen_doc*

### Additional compiler/linker flags
 - __CFLAGS__ ... Any additional flags to pass to the compiler
 - __LDFLAGS__ ... Any additional flags to pass to the linker

### Documentation
 - __DOCS_SW__ ... The program used to generate code documentation; the default is *doxygen*
 - __DOCS_CONF__ ... The configuration file for the program used to generate documentation; the default is *Doxyfile*

### Makefile shell configuration
 - __SHELL__ ... The shell program to be used; the default is *sh*
 - __MKDIR_COMMAND__ ... The shell command used to create new directories - **should be changed if non-unix shell used**; the default is *mkdir -p*
 - __RM_COMMAND__ ... The shell command used to remove files and directories - **should be changed if non-unix shell used**; the default is *rm -r*
 - __ECHO_COMMAND__ ... The shell command used to output text on the command line - **should be changed if non-unix shell used**; the default is *echo*

### Makefile meta configuration
 - __DIR_TARGET__ ... The name of the make target to create required directories; the default is *dirs*
 - __COMPILE_TARGET__ ... The name of the make target to compile source files; the default is *compile*
 - __LINK_TARGET__ ... The name of the make target to link compiled object files; the default is *link*
 - __RUN_TARGET__ ... The name of the make target to run the compiled executable (rebuilding it if necessary); the default is *run*
 - __DOCS_TARGET__ ... The name of the make target to generate code documentation; the default is *doc*
 - __CLEAN_TARGET__ ... The name of the make target to clean build output (compiled files, linked executable, dependency information, documentation); the default is *clean*
 - __HELP_TARGET__ ... The name of the make target to display project help information; the default is *help*
 - __ALL_TARGET__ ... The make targets to be called by the PHONY *all* target; the default is *$(DIR_TARGET) $(COMPILE_TARGET) $(LINK_TARGET)*

### Additional help information
 - __USER_HELP__ ... Any additional information to be displayed when calling the help target (variable directly passed to the echo command, so quotes are user-managed)

