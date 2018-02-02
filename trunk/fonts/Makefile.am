FONTSOURCES = Khottabun.sfd

TTF_TARGETS = $(FONTSOURCES:.sfd=.ttf)
OTF_TARGETS = $(FONTSOURCES:.sfd=.otf)
WOFF_TARGETS = $(FONTSOURCES:.sfd=.woff)

CLEANFILES = *.ttf *.otf *.woff

EXTRA_DIST = $(FONTSOURCES)

if ENABLE_TTF
ttf_DATA = $(TTF_TARGETS)
endif

if ENABLE_OTF
otf_DATA = $(OTF_TARGETS)
endif

if ENABLE_WOFF
woff_DATA = $(WOFF_TARGETS)
endif

SUFFIXES: .sfd .ttf .otf .woff

.sfd.ttf:
	$(FONTFORGE) -script $(top_srcdir)/scripts/gen-ttf.pe $<

.sfd.otf:
	$(FONTFORGE) -script $(top_srcdir)/scripts/gen-otf.pe $<

.sfd.woff:
	$(FONTFORGE) -script $(top_srcdir)/scripts/gen-woff.pe $<

