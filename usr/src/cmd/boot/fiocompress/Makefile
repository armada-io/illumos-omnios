#
# CDDL HEADER START
#
# The contents of this file are subject to the terms of the
# Common Development and Distribution License (the "License").
# You may not use this file except in compliance with the License.
#
# You can obtain a copy of the license at usr/src/OPENSOLARIS.LICENSE
# or http://www.opensolaris.org/os/licensing.
# See the License for the specific language governing permissions
# and limitations under the License.
#
# When distributing Covered Code, include this CDDL HEADER in each
# file and include the License file at usr/src/OPENSOLARIS.LICENSE.
# If applicable, add the following below this CDDL HEADER, with the
# fields enclosed by brackets "[]" replaced with your own identifying
# information: Portions Copyright [yyyy] [name of copyright owner]
#
# CDDL HEADER END
#
#
# Copyright 2007 Sun Microsystems, Inc.  All rights reserved.
# Use is subject to license terms.
#

PROG= fiocompress

SBINLINKS= $(PROG)

OBJS= fiocompress.o
SRCS = $(OBJS:.o=.c)

include ../Makefile.com

.KEEP_STATE:

# There's no lint library for zlib, so only include this when building
$(PROG) := LDLIBS +=	-lz

CFLAGS +=	-I../../../uts/common
LINTFLAGS +=	-I../../../uts/common

# definitions for lint
# until libz is compiled against ON header files (uid/gid)
LINTFLAGS += -erroff=E_INCONS_ARG_DECL2
LINTFLAGS += -erroff=E_INCONS_VAL_TYPE_DECL2
LINTFLAGS += -erroff=E_NAME_USED_NOT_DEF2

all: $(PROG)

$(PROG): $(OBJS)
	$(LINK.c) -o $@ $(OBJS) $(LDLIBS)
	$(POST_PROCESS)

install: all $(ROOTSBINPROG) .WAIT $(ROOTUSRSBINLINKS)

clean:
	-$(RM) $(OBJS)

_msg:

lint:	lint_SRCS

include ../Makefile.targ
