########################################################################
# Copyright (c) 1988-2015 $organization$
#
# This software is provided by the author and contributors ``as is'' 
# and any express or implied warranties, including, but not limited to, 
# the implied warranties of merchantability and fitness for a particular 
# purpose are disclaimed. In no event shall the author or contributors 
# be liable for any direct, indirect, incidental, special, exemplary, 
# or consequential damages (including, but not limited to, procurement 
# of substitute goods or services; loss of use, data, or profits; or 
# business interruption) however caused and on any theory of liability, 
# whether in contract, strict liability, or tort (including negligence 
# or otherwise) arising in any way out of the use of this software, 
# even if advised of the possibility of such damage.
#
#   File: Makefile
#
# Author: $author$
#   Date: 12/7/2015
#
# Thirdpary Makefile for libpng
########################################################################

MAKEDIR=$(PWD)

########################################################################
#
# libpng defs
#
########################################################################
LIBPNG_VERSION_MAJOR = 1
LIBPNG_VERSION_MINOR = 6
LIBPNG_VERSION_RELEASE = 21

LIBPNG_VERSION_SEPARATOR = .
LIBPNG_VERSION_MAJOR_SEPARATOR = $(LIBPNG_VERSION_SEPARATOR)
LIBPNG_VERSION_MINOR_SEPARATOR = $(LIBPNG_VERSION_SEPARATOR)

LIBPNG_VERSION_SHORT = $(LIBPNG_VERSION_MAJOR)$(LIBPNG_VERSION_MINOR)$(LIBPNG_VERSION_RELEASE)
LIBPNG_VERSION = $(LIBPNG_VERSION_MAJOR)$(LIBPNG_VERSION_MAJOR_SEPARATOR)$(LIBPNG_VERSION_MINOR)$(LIBPNG_VERSION_MINOR_SEPARATOR)$(LIBPNG_VERSION_RELEASE)

LIBPNG_NAME_SEPARATOR = -
LIBPNG_NAME_BASE = libpng
LIBPNG_NAME = $(LIBPNG_NAME_BASE)$(LIBPNG_NAME_SEPARATOR)$(LIBPNG_VERSION)
LIBPNG_INSTALL_NAME_SEPARATOR = -
LIBPNG_INSTALL_NAME = $(LIBPNG_NAME_BASE)$(LIBPNG_INSTALL_NAME_SEPARATOR)$(LIBPNG_VERSION)

LIBPNG_ARCHIVED = tar
LIBPNG_COMPRESSED = gz
LIBPNG_ARCHIVE_SEPARATOR = .
LIBPNG_ARCHIVED_SEPARATOR = $(LIBPNG_ARCHIVE_SEPARATOR)
LIBPNG_COMPRESSED_SEPARATOR = $(LIBPNG_ARCHIVE_SEPARATOR)

LIBPNG_BUILD = $(HOME)/build
LIBPNG_PREFIX = $(LIBPNG_BUILD)/$(LIBPNG_INSTALL_NAME)
LIBPNG_EXEC_PREFIX = $(LIBPNG_PREFIX)
LIBPNG_CONF_PREFIX = $(LIBPNG_PREFIX)
LIBPNG_DOCS_PREFIX = $(LIBPNG_PREFIX)
LIBPNG_LINK_NAME = $(LIBPNG_BUILD)/$(LIBPNG_NAME_BASE)
LIBPNG_DIR = $(LIBPNG_NAME)
LIBPNG_EXTRACT_DIR = $(LIBPNG_NAME)
LIBPNG_TGZ_PREFIX = 
LIBPNG_TGZ = $(LIBPNG_NAME)$(LIBPNG_TGZ_PREFIX)$(LIBPNG_ARCHIVED_SEPARATOR)$(LIBPNG_ARCHIVED)$(LIBPNG_COMPRESSED_SEPARATOR)$(LIBPNG_COMPRESSED)
LIBPNG_PATCH_TGZ_PREFIX = $(LIBPNG_NAME_SEPARATOR)patch
LIBPNG_PATCH_TGZ = $(LIBPNG_NAME)$(LIBPNG_PATCH_TGZ_PREFIX)$(LIBPNG_ARCHIVED_SEPARATOR)$(LIBPNG_ARCHIVED)$(LIBPNG_COMPRESSED_SEPARATOR)$(LIBPNG_COMPRESSED)
LIBPNG_DOCS_TGZ_PREFIX = $(LIBPNG_NAME_SEPARATOR)docs
LIBPNG_DOCS_TGZ = $(LIBPNG_NAME)$(LIBPNG_DOCS_TGZ_PREFIX)$(LIBPNG_ARCHIVED_SEPARATOR)$(LIBPNG_ARCHIVED)$(LIBPNG_COMPRESSED_SEPARATOR)$(LIBPNG_COMPRESSED)

ifeq ($(LIBPNG_ARCHIVED),tar)
ifeq ($(LIBPNG_COMPRESSED),gz)
LIBPNG_TAR_UNCOMPRESS = z
LIBPNG_TAR_COMPRESS = z
else
ifeq ($(LIBPNG_COMPRESSED),bz2)
LIBPNG_TAR_UNCOMPRESS = j
LIBPNG_TAR_COMPRESS = j
else
endif
endif
LIBPNG_LIST = tar -tv$(LIBPNG_TAR_UNCOMPRESS)f
LIBPNG_EXTRACT = tar -x$(LIBPNG_TAR_UNCOMPRESS)f
LIBPNG_ARCHIVE = tar -cv$(LIBPNG_TAR_COMPRESS)f
else
ifeq ($(LIBPNG_ARCHIVED),zip)
LIBPNG_LIST = unzip -l
LIBPNG_EXTRACT = unzip
LIBPNG_ARCHIVE = zip
else
LIBPNG_LIST = echo unable to list
LIBPNG_EXTRACT = echo unable to extract
LIBPNG_ARCHIVE = echo unable to archive
endif
endif

LIBPNG_MKDIR = mkdir -p
LIBPNG_REMOVE = rm -r -f

LIBPNG_MAKE_DIR = $(LIBPNG_DIR)
LIBPNG_MAKE_PUSHD = pushd $(LIBPNG_MAKE_DIR)
LIBPNG_MAKE = make

LIBPNG_CONFIGURE_PUSHD = pushd $(LIBPNG_MAKE_DIR)

LIBPNG_CONFIGURE = \
./configure --prefix=$(LIBPNG_PREFIX) \
--exec_prefix=$(LIBPNG_EXEC_PREFIX) \

LIBPNG_HELP = ./configure --help

LIBPNG_LIST_TGZ = $(LIBPNG_LIST) $(LIBPNG_TGZ)
LIBPNG_EXTRACT_TGZ = $(LIBPNG_EXTRACT) $(LIBPNG_TGZ)
LIBPNG_TOUCH_EXTRACT = touch $(LIBPNG_DIR)
LIBPNG_REMOVE_DIR = $(LIBPNG_REMOVE) $(LIBPNG_DIR)

LIBPNG_LIST_PATCH = $(LIBPNG_LIST)
LIBPNG_EXTRACT_PATCH = $(LIBPNG_EXTRACT)
LIBPNG_LIST_PATCH_TGZ = $(LIBPNG_LIST_PATCH) $(LIBPNG_PATCH_TGZ)
LIBPNG_EXTRACT_PATCH_TGZ = $(LIBPNG_EXTRACT_PATCH) $(LIBPNG_PATCH_TGZ)

LIBPNG_LIST_DOCS = $(LIBPNG_LIST)
LIBPNG_EXTRACT_DOCS = $(LIBPNG_EXTRACT)
LIBPNG_LIST_DOCS_TGZ = $(LIBPNG_LIST_DOCS) $(LIBPNG_DOCS_TGZ)
LIBPNG_EXTRACT_DOCS_TGZ = $(LIBPNG_EXTRACT_DOCS) $(LIBPNG_DOCS_TGZ) -C$(LIBPNG_DOCS_PREFIX)

########################################################################
#
# rules
#
########################################################################

all:

test: test-libpng

install-links: install-libpng-links

install-docs: install-libpng-docs

install-prefix: install-libpng-prefix

install: install-libpng

build: build-libpng

clean: clean-libpng

configed: configed-$(LIBPNG_DIR)

config: config-$(LIBPNG_DIR)

help: help-libpng

list-docs: list-libpng-docs

list-patch: list-libpng-patch

extract-patch: extract-libpng-patch

list: list-libpng

extract: extract-libpng

unextract: unextract-libpng

archive: archive-libpng

linked: libpng-linked

prefixed: libpng-prefixed

archived: libpng-archived

extracted: libpng-extracted

########################################################################
#
# libpng rules
#
########################################################################

#
# Test libpng
#
test-libpng:
	@($(LIBPNG_MAKE_PUSHD);\
	  (($(LIBPNG_MAKE) test) || (exit 1));\
	  popd)

#
# Install libpng
#
install-libpng: configed-$(LIBPNG_DIR)
	@(echo Installing $(LIBPNG_DIR)...;\
	  $(LIBPNG_MAKE_PUSHD);\
	  (($(LIBPNG_MAKE) install) || (exit 1)) && \
	  ((touch $(MAKEDIR)/configed-$(LIBPNG_DIR)) || (exit 1));\
	  popd)
	  
#
# Build libpng
#
build-libpng: configed-$(LIBPNG_DIR)
	@(echo Building $(LIBPNG_DIR)...;\
	  $(LIBPNG_MAKE_PUSHD);\
	  (($(LIBPNG_MAKE)) || (exit 1)) && \
	  ((touch $(MAKEDIR)/configed-$(LIBPNG_DIR)) || (exit 1));\
	  popd)
	  
#
# Clean libpng
#
clean-libpng: configed-$(LIBPNG_DIR)
	@(echo Cleaning $(LIBPNG_DIR)...;\
	  $(LIBPNG_MAKE_PUSHD);\
	  (($(LIBPNG_MAKE) clean) || (exit 1)) && \
	  ((touch $(MAKEDIR)/configed-$(LIBPNG_DIR)) || (exit 1));\
	  popd)
	  
#
# Config libpng
#
config-$(LIBPNG_DIR): unconfig-$(LIBPNG_DIR) configed-$(LIBPNG_DIR)

unconfig-$(LIBPNG_DIR):
	@(rm -f configed-$(LIBPNG_DIR))

configed-$(LIBPNG_DIR): $(LIBPNG_DIR)
	@(echo Configing $(LIBPNG_DIR)...;\
	  $(LIBPNG_CONFIGURE_PUSHD);\
	  (($(LIBPNG_CONFIGURE)) || (exit 1)) && \
	  ((touch $(LIBPNG_DIR)) || (exit 1)) && \
	  ((touch $(MAKEDIR)/configed-$(LIBPNG_DIR)) || (exit 1));\
	  popd)

#
# Help libpng
#
help-libpng:
	@($(LIBPNG_CONFIGURE_PUSHD);\
	  (($(LIBPNG_HELP)) || (exit 1));\
	  popd)

#
# List libpng Docs
#
list-libpng-docs: $(LIBPNG_DOCS_TGZ)
	@(echo Listing $(LIBPNG_DOCS_TGZ)...;\
	  (($(LIBPNG_LIST_DOCS_TGZ)) || (exit 1)))

#
# Install libpng Docs
#
install-libpng-docs: $(LIBPNG_DOCS_PREFIX)
	@(echo Extracting $(LIBPNG_DOCS_TGZ)...;\
	  (($(LIBPNG_EXTRACT_DOCS_TGZ)) || (exit 1)))

#
# List libpng Patch
#
list-libpng-patch: $(LIBPNG_PATCH_TGZ)
	@(echo Listing $(LIBPNG_PATCH_TGZ)...;\
	  (($(LIBPNG_LIST_PATCH_TGZ)) || (exit 1)))

#
# Extract libpng patch
#
extract-libpng-patch: $(LIBPNG_DIR)
	@(echo Extracting $(LIBPNG_PATCH_TGZ)...;\
	  (($(LIBPNG_EXTRACT_PATCH_TGZ)) || (exit 1)))

#
# List libpng
#
list-libpng: 
	@(echo Listing $(LIBPNG_TGZ)...;\
	  (($(LIBPNG_LIST_TGZ)) || (exit 1)))

#
# Extract libpng
#
extract-libpng: unextract-libpng $(LIBPNG_DIR)

unextract-libpng: 
	@(echo Removing $(LIBPNG_DIR)...;\
	  (($(LIBPNG_REMOVE_DIR)) || (exit 1)))

$(LIBPNG_DIR): $(LIBPNG_TGZ)
	@(echo Extracting $(LIBPNG_TGZ)...;\
	  (($(LIBPNG_EXTRACT_TGZ)) || (exit 1)) && \
	  (($(LIBPNG_TOUCH_EXTRACT)) || (exit 1)))
	  
#
# Archive libpng
#
archive-libpng: 
	@(echo Archiving $(LIBPNG_DIR) to $(LIBPNG_TGZ)...;\
	  (($(LIBPNG_ARCHIVE) $(LIBPNG_TGZ) $(LIBPNG_DIR)) || (exit 1)))

#
# Install libpng links
#
install-libpng-links: 
	@((echo removing $(LIBPNG_LINK_NAME)) && \
	  ((rm -f $(LIBPNG_LINK_NAME)) || (exit 1)) && \
	  (echo Linking $(LIBPNG_LINK_NAME) "->" $(LIBPNG_PREFIX)) && \
	  ((ln -s $(LIBPNG_PREFIX) $(LIBPNG_LINK_NAME)) || (exit 1)))
	  
#
# libpng linked
#
libpng-linked: 
	@echo link is $(LIBPNG_LINK_NAME) "->" $(LIBPNG_PREFIX)
	  
#
# Install libpng prefix
#
install-libpng-prefix: 
	@((echo makeing $(LIBPNG_PREFIX)) && \
	  ((mkdir -p $(LIBPNG_PREFIX)) || (exit 1)) && \
	  (echo makeing $(LIBPNG_EXEC_PREFIX)) && \
	  ((mkdir -p $(LIBPNG_EXEC_PREFIX)) || (exit 1)))
	  
#
# libpng prefixed
#
libpng-prefixed: 
	@((echo prefix is $(LIBPNG_PREFIX)) && \
	  (echo exec prefix is $(LIBPNG_EXEC_PREFIX)) && \
	  (echo conf prefix is $(LIBPNG_CONF_PREFIX)) && \
	  (echo docs prefix is $(LIBPNG_DOCS_PREFIX)))
	  
$(LIBPNG_PREFIX):
	@(echo Makeing Directory $(LIBPNG_PREFIX)...;\
	  (($(LIBPNG_MKDIR) $(LIBPNG_PREFIX)) || (exit 1)))

$(LIBPNG_EXEC_PREFIX):
	@(echo Makeing Directory $(LIBPNG_EXEC_PREFIX)...;\
	  (($(LIBPNG_MKDIR) $(LIBPNG_EXEC_PREFIX)) || (exit 1)))

$(LIBPNG_CONF_PREFIX):
	@(echo Makeing Directory $(LIBPNG_CONF_PREFIX)...;\
	  (($(LIBPNG_MKDIR) $(LIBPNG_CONF_PREFIX)) || (exit 1)))

$(LIBPNG_DOCS_PREFIX):
	@(echo Makeing Directory $(LIBPNG_DOCS_PREFIX)...;\
	  (($(LIBPNG_MKDIR) $(LIBPNG_DOCS_PREFIX)) || (exit 1)))

#
# libpng archived
#
libpng-archived: 
	@(echo $(LIBPNG_TGZ))
	  
#
# libpng extracted
#
libpng-extracted: 
	@(echo $(LIBPNG_EXTRACT) $(LIBPNG_TGZ))



        

