include ../common.mk

# flags for building the gtk library
CFLAGS = $(CFLAGS_STD) \
	 $(CFLAGS_VX_GTK) \
         $(CFLAGS_IMAGESOURCE) \
	 $(CFLAGS_MATH) \
	 $(CFLAGS_COMMON) \
	 $(CFLAGS_LCMTYPES) \
	 -O2

LDFLAGS = $(LDFLAGS_STD) \
	  $(LDFLAGS_VX_GTK) \
	  $(LDFLAGS_IMAGESOURCE) \
	  $(LDFLAGS_MATH) \
	  $(LDFLAGS_COMMON) \
	  $(LDFLAGS_LCMTYPES)

LIBDEPS = $(call libdeps, $(LDFLAGS))

LIB_ROB550 = $(LIB_PATH)/librob550.a
LIBROB550_OBJS = rob550_util.o

BIN_ROB550_GUI_EXAMPLE = $(BIN_PATH)/rob550_gui_example
BIN_ROB550_REXARM_EXAMPLE = $(BIN_PATH)/rob550_rexarm_example
BIN_ROB550_MAEBOT_EXAMPLE = $(BIN_PATH)/rob550_maebot_example
BIN_ROB550_MAEBOT_VIDEO_TELOP = $(BIN_PATH)/rob550_maebot_video_telop

ALL = $(LIB_ROB550) $(BIN_ROB550_GUI_EXAMPLE) $(BIN_ROB550_REXARM_EXAMPLE) \
      $(BIN_ROB550_MAEBOT_EXAMPLE) $(BIN_ROB550_MAEBOT_VIDEO_TELOP)

all: $(ALL)

$(LIB_ROB550): $(LIBROB550_OBJS) $(LIBDEPS)
	@echo "\t$@"
	@ar rc $@ $(LIBROB550_OBJS)

$(BIN_ROB550_GUI_EXAMPLE): gui_example.o $(LIB_ROB550) $(LIBDEPS)
	@echo "\t$@"
	@$(CC) -o $@ $^ $(LDFLAGS) $(LIB_ROB550)

$(BIN_ROB550_REXARM_EXAMPLE): rexarm_example.o $(LIBDEPS)
	@echo "\t$@"
	@$(CC) -o $@ $^ $(LDFLAGS)

$(BIN_ROB550_MAEBOT_EXAMPLE): maebot_example.o $(LIBDEPS)
	@echo "\t$@"
	@$(CC) -o $@ $^ $(LDFLAGS)

$(BIN_ROB550_MAEBOT_VIDEO_TELOP): maebot_video_teleop.o $(LIBDEPS)
	@echo "\t$@"
	@$(CC) -o $@ $^ $(LDFLAGS)

clean:
	@rm -f *.o *~ *.a
	@rm -f $(ALL)
