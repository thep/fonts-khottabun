#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.71])
AC_INIT([fonts-khottabun],[0.1.0],[theppitak@gmail.com])

FONTFORGE_MIN_VER=20190801

AM_INIT_AUTOMAKE

# Configure options

dnl Enable TTF
AC_ARG_ENABLE(ttf,
  [AS_HELP_STRING([--disable-ttf],
                  [disable TTF generation])],
                  , enable_ttf="yes")
if test "x$enable_ttf" = "xyes"; then
  AC_ARG_WITH(ttfdir,
    [AS_HELP_STRING([--with-ttfdir=DIR],
                    [font directory in DIR [PREFIX/share/fonts/truetype/khottabun]])],
    [ttfdir="$withval"], [ttfdir=\$\{prefix\}/share/fonts/truetype/khottabun])
  AC_MSG_CHECKING(--with-ttfdir)
  AC_MSG_RESULT("$ttfdir")

  AC_SUBST(ttfdir)
fi

AM_CONDITIONAL(ENABLE_TTF,test $enable_ttf = "yes")

dnl Enable OTF
AC_ARG_ENABLE(otf,
  [AS_HELP_STRING([--enable-otf],
                  [enable OTF generation])],
                  , enable_otf="no")
if test "x$enable_otf" = "xyes"; then
  AC_ARG_WITH(otfdir,
    [AS_HELP_STRING([--with-otfdir=DIR],
                    [font directory in DIR [PREFIX/share/fonts/opentype/khottabun]])],
    [otfdir="$withval"], [otfdir=\$\{prefix\}/share/fonts/opentype/khottabun])
  AC_MSG_CHECKING(--with-otfdir)
  AC_MSG_RESULT("$otfdir")

  AC_SUBST(otfdir)
fi

AM_CONDITIONAL(ENABLE_OTF,test $enable_otf = "yes")

dnl Enable WOFF
AC_ARG_ENABLE(woff,
  [AS_HELP_STRING([--enable-woff],
                  [enable WOFF generation])],
                  , enable_woff="no")
if test "x$enable_woff" = "xyes"; then
  AC_ARG_WITH(woffdir,
    [AS_HELP_STRING([--with-woffdir=DIR],
                    [font directory in DIR [PREFIX/share/fonts/woff/khottabun]])],
    [woffdir="$withval"], [woffdir=\$\{prefix\}/share/fonts/woff/khottabun])
  AC_MSG_CHECKING(--with-woffdir)
  AC_MSG_RESULT("$woffdir")

  AC_SUBST(woffdir)
fi

AM_CONDITIONAL(ENABLE_WOFF,test $enable_woff = "yes")

# Checks for programs.
AC_PROG_INSTALL
AC_PROG_LN_S

AC_CHECK_PROGS(FONTFORGE,fontforge,no)

if test "x$FONTFORGE" = "xno"; then
  AC_MSG_ERROR([You need fontforge to generate fonts.])
else
  AC_MSG_CHECKING([for Fontforge >= $FONTFORGE_MIN_VER])
  FONTFORGE_VER=$($FONTFORGE --version 2>/dev/null | grep '^fontforge' | cut -d' ' -f2)
  if test $FONTFORGE_VER -lt $FONTFORGE_MIN_VER; then
    AC_MSG_ERROR([Requires Fontforge >= $FONTFORGE_MIN_VER but $FONTFORGE_VER was found)])
  fi
  AC_MSG_RESULT([$FONTFORGE_VER found, ok])
fi

AC_CONFIG_FILES([Makefile
                 fonts/Makefile
                 scripts/Makefile])
AC_OUTPUT
