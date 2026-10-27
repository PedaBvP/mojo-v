
LOCAL_CFLAGS= -std=c2x
LOCAL_LIBS=
LOCAL_OBJS=mojov-sectests.o ../common/simon.o ../target/mojov-utils.o

PROG=mojov-sectests

include ../Makefile

# Local branch labels avoid absolute-target JAL relocations with GNU as.


test: $(TARGET_EXE)
	rm -f FOO
	for i in $(shell seq 0 246); do \
	  echo "--- Test $$i ---" >> FOO; \
	  $(TARGET_SIM) --mojov-arg=$$i --mojov-verbose ./$(TARGET_EXE) >> FOO; \
	done
	$(TARGET_DIFF) FOO mojov-sectests.$(TARGET_REFEXT)
	rm -f FOO

