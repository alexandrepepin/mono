thisdir = class/System.Data
SUBDIRS = 
include ../../build/rules.make

LIBRARY = System.Data.dll

LIB_REFS = System System.Xml System.Core
LIB_MCS_FLAGS = \
	-nowarn:649 \
	-unsafe

MOBILE := $(filter monotouch monodroid xammac mobile mobile_static, $(PROFILE))
ifdef MOBILE
LIB_REFS += Mono.Data.Tds System.Transactions
else
LIB_REFS += System.EnterpriseServices Mono.Data.Tds System.Configuration System.Transactions
endif

RESOURCE_STRINGS = ../../../external/referencesource/System.Data/system.data.txt

TEST_MCS_FLAGS = $(LIB_MCS_FLAGS) -r:System.Core.dll -r:Mono.Data.Sqlite.dll -nowarn:618,169,612,219,168

TEST_MONO_PATH = .

EXTRA_DISTFILES = \
	TODO					\
	$(wildcard Test/System.Data/*.xml)		\
	$(wildcard Test/System.Data/*.xsd)		\
	$(wildcard Test/System.Xml/*.xml)		\
	$(wildcard Test/System.Xml/*.xsd)		\
	Test/System.Data/schemas/ChangeLog	\
	$(wildcard Test/System.Data/schemas/*.xsd)		\
	Mono.Data.SqlExpressions/Parser.jay	\
	app_test_net_2_0.config			\
	app_test_net_4_5.config			\
	Test/System.Data/binserialize/*.bin	\
	SqliteTest.db

BUILT_SOURCES = Mono.Data.SqlExpressions/Parser.cs

Mono.Data.SqlExpressions/Parser.cs: Mono.Data.SqlExpressions/Parser.jay $(topdir)/jay/skeleton.cs
	$(topdir)/jay/jay -vct < $(topdir)/jay/skeleton.cs $(CURDIR)/$< >$@
	rm -f y.output

include ../../build/library.make

$(test_lib): $(test_lib).config

$(test_lib).config: app_test_$(PROFILE).config
	cp $< $@
