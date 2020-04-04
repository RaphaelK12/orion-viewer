# Orion Viewer: Android Pdf and Djvu reader

Orion Viewer is pdf, djvu, xps, cbz and tiff file viewer for Android
devices based on
[mupdf](http://mupdf.com/) and
[DjVuLibre](https://sourceforge.net/p/djvu/djvulibre-git/ci/master/tree/)
libraries

To build Orion Viewer you will need:

 * android-sdk-r27+
 * gradle 5.6.4+
 * android-ndk-r20+
 * make + python2 for mupdf
 * git

 * downloaded Native Libs [mupdf, djvu]:

    `./gradlew -b  thirdparty_build.gradle downloadAndPatchDjvu downloadAndMakeMupdf`

    They are defined in gradle scripts via 'externalNativeBuild' section
    (for details see 'djvuModule/build.gradle' and 'mupdfModule/build.gradle').
    Native libs are checked out into 'nativeLibs/djvu' and 'nativeLibs/mupdf' folders.

 * specify path to android-sdk, android-ndk in 'local.properties' (use 'local.properties.sample' as example).

 * By default sources for native libs are excluded from build because otherwise IDE becomes too slow,
 so you need to prebuild them once:

    ``./gradlew -b  thirdparty_build.gradle buildDjvu buildMupdf`
    or
    run `ndk-build` command within `nativeLibs/djvuModule' and `nativeLibs/mupdfModule'

   To include native sources specify `orion.include_native_libs_source=true` in `local.properties` file.