# ===========================================================================
#
#                            PUBLIC DOMAIN NOTICE
#               National Center for Biotechnology Information
#
#  This software/database is a "United States Government Work" under the
#  terms of the United States Copyright Act.  It was written as part of
#  the author's official duties as a United States Government employee and
#  thus cannot be copyrighted.  This software/database is freely available
#  to the public for use. The National Library of Medicine and the U.S.
#  Government have not placed any restriction on its use or reproduction.
#
#  Although all reasonable efforts have been taken to ensure the accuracy
#  and reliability of the software and data, the NLM and the U.S.
#  Government do not and cannot warrant the performance or results that
#  may be obtained by using this software or data. The NLM and the U.S.
#  Government disclaim all warranties, express or implied, including
#  warranties of performance, merchantability or fitness for any particular
#  purpose.
#
#  Please cite the author in any work or product based on this material.
#
# ===========================================================================

default: runtests

TOP ?= $(abspath ../..)
MODULE = test/vdb-config

TEST_TOOLS = \
	test-vdb-config-model

include $(TOP)/build/Makefile.env # BINDIR

$(TEST_TOOLS): makedirs
	@ $(MAKE_CMD) $(TEST_BINDIR)/$@

.PHONY: $(TEST_TOOLS)

clean: stdclean

#-------------------------------------------------------------------------------
# test-vdb-config
#

runtests: test-vdb-config

test-vdb-config:
	@ printf "Testing exit code vdb-config of vdb-config... "
	@ PATH=$(BINDIR):"$(PATH)" ; ./test-vdb-config.pl
	@ echo OK

#-------------------------------------------------------------------------------
# test-vdb-config-model
#

STRIDES_SRC = \
	test-vdb-config-model

STRIDES_OBJ = \
	$(addsuffix .$(OBJX),$(STRIDES_SRC))

STRIDES_LIB = \
	-skapp \
	-sktst \
	-sncbi-vdb \

$(TEST_BINDIR)/test-vdb-config-model: $(STRIDES_OBJ)
	$(LP) --exe -o $@ $^ $(STRIDES_LIB)

model: test-vdb-config-model
	$(TEST_BINDIR)/test-vdb-config-model  2>&1


