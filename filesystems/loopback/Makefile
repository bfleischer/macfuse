TARGETS = loopback

CC = gcc
CFLAGS_MACFUSE = -D__DARWIN_64_BIT_INO_T=0 -D__FreeBSD__=10 -D_FILE_OFFSET_BITS=64 -I/usr/local/include/fuse
CFLAGS_EXTRA = -Wall -g
ARCHS = -arch i386 -arch x86_64
LIBS = -lfuse

.c:
	$(CC) $(CFLAGS_MACFUSE) $(CFLAGS_EXTRA) $(ARCHS) -o $@ $< $(LIBS)

all: info

loopback: loopback.c

info: $(TARGETS)
	@echo
	@echo Compiled. The following is a typical way to run the loopback file system. In
	@echo this example, /tmp/dir is an existing directory whose contents will become
	@echo available in the existing mount point /Volumes/loop:
	@echo
	@echo "sudo ./loopback /Volumes/loop -omodules=threadid:subdir,subdir=/tmp/dir -oallow_other,native_xattr,volname=LoopbackFS"
	@echo

clean:
	rm -f $(TARGETS) *.o
