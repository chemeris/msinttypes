## msinttypes ##

This project fills the absence of `stdint.h` and `inttypes.h` in Microsoft Visual Studio. This files were standartized by ISO/IEC as a part of [C99](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1124.pdf) standard library. If you want to compile or use C99 compliant project with Microsoft Visual Studio, you will likely find that you're missing these headers. Note though, that just adding these header does not make Visual Studio compiler fully C99 compliant.

[FFMpeg](http://ffmpeg.mplayerhq.hu/) is a good example of library that requires `inttypes.h` even if you just want to link your program with it.

More portable version of `stdint.h` can be find [here](http://www.azillionmonkeys.com/qed/pstdint.h) but it does not implement `inttypes.h` features, such as printf and scanf format specifiers.


## Changes history ##

```
------------------------------------------------------------------------
r29 | 2013-05-25 02:36:43 +0400 | 2 lines

Fix Issue 9: Surround (U)INTMAX_C with #ifndef's to prevent compiler warnings.

------------------------------------------------------------------------
r28 | 2013-05-25 02:32:18 +0400 | 2 lines

Fix Issue 10: Use system <stdint.h> for Visual Studio 2010 and later.

------------------------------------------------------------------------
r27 | 2013-05-25 02:24:11 +0400 | 2 lines

Fix license bug - the name of the product and the names of contributors
must not be used for promotion.

------------------------------------------------------------------------
r26 | 2009-10-02 13:36:47 +0400 | 2 lines

[Issue 5] Change <stdint.h> to "stdint.h" to let compiler search for it in local directory.

------------------------------------------------------------------------
r25 | 2009-09-17 23:46:49 +0400 | 2 lines

[Issue 4] Fix incorrect int8_t behaviour if compiled with /J flag.

------------------------------------------------------------------------
r24 | 2009-05-13 14:53:48 +0400 | 2 lines

Forgot about #ifdef __cplusplus guard around 'extern "C"', so inclusion to C files has been broken.

------------------------------------------------------------------------
r23 | 2009-05-12 01:27:45 +0400 | 3 lines

[Issue 2] Always wrap <wchar.h> with 'extern "C" {}'.
It turns out that not only Visual Studio 6 requires this, but also newer versions when compiling for ARM.

------------------------------------------------------------------------
r22 | 2009-05-11 22:22:15 +0400 | 3 lines

[Issue 3] Visual Studio 6 and Embedded Visual C++ 4 doesn't realize that, e.g. char has the same size as
__int8 so we give up on __intX for them.
This should close Issue 3 in issue tracker.

------------------------------------------------------------------------
r21 | 2008-07-17 09:47:22 +0400 | 4 lines

Get rid of these compiler warnings when compiling for 32-bit:
  warning C4311: 'type cast' : pointer truncation from 'void *' to 'uintptr_t'
  warning C4312: 'type cast' : conversion from 'uintptr_t' to 'const void *' of greater size

------------------------------------------------------------------------
r20 | 2007-10-09 16:54:27 +0400 | 2 lines

Better C99 conformance: macros for format specifiers should only be included in C++ implementations
if __STDC_FORMAT_MACROS is defined before <inttypes.h> is included.

------------------------------------------------------------------------
r19 | 2007-07-04 02:14:40 +0400 | 3 lines

Explicitly cast to appropriate type INT8_MIN, INT16_MIN, INT32_MIN and INT64_MIN constants.
Due to their unusual definition in Visual Studio headers (-_Ix_MAX-1) they are propagated to int and thus
do not have expected type, causing VS6 strict compiler to claim about type inconsistency.

------------------------------------------------------------------------
r18 | 2007-06-26 16:53:23 +0400 | 2 lines

Better handling of (U)INTx_C macros - now they generate constants of exact width.

------------------------------------------------------------------------
r17 | 2007-03-29 20:16:14 +0400 | 2 lines

Fix typo: Miscrosoft -> Microsoft.

------------------------------------------------------------------------
r16 | 2007-02-24 17:32:58 +0300 | 4 lines

Remove `<BaseTsd.h>` include, as it is not present in Visual Studio 2005 Epxress Edition and
required only for INT_PTR and UINT_PTR types.

'intptr_t' and 'uintptr_t' types now defined explicitly with #ifdef _WIN64.

------------------------------------------------------------------------
r15 | 2007-02-11 20:53:05 +0300 | 2 lines

Initial public release.
```