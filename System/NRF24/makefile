INCFLAG =\
-I. \
-Iinc \
-I../STM32/inc \
-I../CMSIS/inc 


CFLAGS  += $(INCFLAG)

SRCOBJS =\
$(patsubst %.c, %.o, $(wildcard ./src/*.c)) 

OBJS = $(subst /src/,/obj/, $(SRCOBJS))

all: $(OBJS)

$(OBJDIR)/%.o: src/%.c | $(OBJDIR)
	@echo "bulid file: $<"
	$(CC) $(CFLAGS) -MMD -MF$(@:%.o=%.d) -o $@ $<\
        && echo $(NOW) INFO Objecting System/NRF24/$< success. >> ../../build.log \
        || echo $(NOW) ERROR Objecting System/NRF24/$< failed, stop building. >> ../../build.log | exit 

$(OBJDIR):
	@echo $(NOW) INFO Make new folder System/NRF24/$(OBJDIR). >> ../../build.log
	mkdir -p $(OBJDIR)

clean:
	-rm -rf $(OBJDIR)/*.o 
	-rm -rf $(OBJDIR)/*.d
