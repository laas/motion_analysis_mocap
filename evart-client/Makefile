VERSION=2.2
TARBALL=evart-client-$(VERSION).tar.gz
TARBALL_URL=http://softs.laas.fr/openrobots/distfiles/evart/${TARBALL}

SOURCE_DIR=build/evart-client-$(VERSION)
UNPACK_CMD=tar xzf
MD5SUM_FILE=evart-client-$(VERSION).tar.gz.md5sum

INSTALL_DIR=$(shell rospack find evart-client)/install

CONFIGURE_FLAGS=--prefix=$(INSTALL_DIR)

all: $(SOURCE_DIR)/configured
ifneq ($(MAKE),)
	cd $(SOURCE_DIR) && $(MAKE) install $(ROS_PARALLEL_JOBS)
else
	cd $(SOURCE_DIR) && make install $(ROS_PARALLEL_JOBS)
endif

$(SOURCE_DIR)/configured: $(SOURCE_DIR)/unpacked
	cd $(SOURCE_DIR) && \
	CPPFLAGS="-DNDEBUG" CXXFLAGS="-02 -g" ./configure $(CONFIGURE_FLAGS)
	touch $(SOURCE_DIR)/configured

include $(shell rospack find mk)/download_unpack_build.mk

clean:
	-rm -rf build install

.PHONY: all clean
