FONTSOURCES = Khottabun.sfd

TTF_TARGETS = $(FONTSOURCES:.sfd=.ttf)
OTF_TARGETS = $(FONTSOURCES:.sfd=.otf)

CLEANFILES = *.ttf *.otf

EXTRA_DIST = $(FONTSOURCES)

if ENABLE_TTF
ttf_DATA = $(TTF_TARGETS)
endif

if ENABLE_OTF
otf_DATA = $(OTF_TARGETS)
endif

SUFFIXES: .sfd .ttf .otf

.sfd.ttf:
	$(FONTFORGE) -script $(top_srcdir)/scripts/gen-ttf.pe $<

.sfd.otf:
	$(FONTFORGE) -script $(top_srcdir)/scripts/gen-otf.pe $<

