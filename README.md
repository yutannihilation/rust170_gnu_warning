```
cargo build --target=x86_64-pc-windows-gnu --lib --release

$env:R_HOME = "C:/Program Files/R/R-4.3.0"
$env:PATH = "${env:R_HOME}\bin\x64;C:\rtools43\usr\bin;C:\rtools43\x86_64-w64-mingw32.static.posix\bin;C:\msys64\mingw64\bin;${env:PATH}"

gcc -I"C:/R/include" -DNDEBUG -I"c:/rtools43/x86_64-w64-mingw32.static.posix/include" -O2 -Wall -gdwarf-2 -std=gnu99 -mfpmath=sse -msse2 -mstackrealign  -UNDEBUG -Wall -pedantic -g -O0 -c main.c -o main.o

gcc -shared -static-libgcc -o testpkgrust170_gnu_warning.dll main.o -L./target/x86_64-pc-windows-gnu/release -lrust170_gnu_warning -lws2_32 -ladvapi32 -luserenv -lbcrypt -lntdll -Lc:/rtools43/x86_64-w64-mingw32.static.posix/lib/x64 -Lc:/rtools43/x86_64-w64-mingw32.static.posix/lib -LC:/R/bin/x64

dumpbin.exe .\target\x86_64-pc-windows-gnu\release\librust170_gnu_warning.a
```

Result:
```
Microsoft (R) COFF/PE Dumper Version 14.29.30137.0
Copyright (C) Microsoft Corporation.  All rights reserved.


Dump of file .\target\x86_64-pc-windows-gnu\release\librust170_gnu_warning.a

File Type: LIBRARY

  Summary

           8 .CRT$XCT
           8 .CRT$XLB
         1F9 .bss
         190 .data
        8457 .debug_abbrev
        2300 .debug_aranges
         B50 .debug_frame
      10064C .debug_info
       718B4 .debug_line
        9DB9 .debug_loc
       93905 .debug_pubnames
         9C6 .debug_pubtypes
       8A8D0 .debug_ranges
      1725CC .debug_str
        EE44 .drectve
      80A0BC .llvmbc
           0 .llvmcmd
        6420 .pdata
           C .pdata$__absvdi2
           C .pdata$__absvsi2
           C .pdata$__absvti2
           C .pdata$__addvdi3
           C .pdata$__addvsi3
           C .pdata$__addvti3
           C .pdata$__clzdi2
           C .pdata$__clzsi2
           C .pdata$__clzti2
           C .pdata$__cmpdi2
           C .pdata$__cmpti2
           C .pdata$__ctzdi2
           C .pdata$__ctzsi2
           C .pdata$__ctzti2
           C .pdata$__divdc3
           C .pdata$__divsc3
           C .pdata$__divxc3
           C .pdata$__extendhfsf2
           C .pdata$__ffsti2
           C .pdata$__gnu_f2h_ieee
           C .pdata$__gnu_h2f_ieee
           C .pdata$__muldc3
           C .pdata$__mulsc3
           C .pdata$__mulvdi3
           C .pdata$__mulvsi3
           C .pdata$__mulvti3
           C .pdata$__mulxc3
           C .pdata$__negdf2
           C .pdata$__negdi2
           C .pdata$__negsf2
           C .pdata$__negti2
           C .pdata$__negvdi2
           C .pdata$__negvsi2
           C .pdata$__negvti2
           C .pdata$__paritydi2
           C .pdata$__paritysi2
           C .pdata$__parityti2
           C .pdata$__popcountdi2
           C .pdata$__popcountsi2
           C .pdata$__popcountti2
           C .pdata$__powixf2
           C .pdata$__subvdi3
           C .pdata$__subvsi3
           C .pdata$__subvti3
           C .pdata$__truncdfhf2
           C .pdata$__truncsfhf2
           C .pdata$__ucmpdi2
           C .pdata$__ucmpti2
           C .pdata.unlikely.__compilerrt_abort_impl
       2A6EB .rdata
          10 .rdata$.refptr.__rust_alloc_error_handler_should_panic
          F0 .rdata$__func__.0
         BC0 .rdata$zzz
       CBF4D .text
          50 .text$__absvdi2
          40 .text$__absvsi2
          60 .text$__absvti2
          60 .text$__addvdi3
          50 .text$__addvsi3
          90 .text$__addvti3
          30 .text$__clzdi2
          80 .text$__clzsi2
          40 .text$__clzti2
          30 .text$__cmpdi2
          30 .text$__cmpti2
          30 .text$__ctzdi2
          60 .text$__ctzsi2
          30 .text$__ctzti2
         930 .text$__divdc3
         770 .text$__divsc3
         3E0 .text$__divxc3
          A0 .text$__extendhfsf2
          30 .text$__ffsti2
          10 .text$__gnu_f2h_ieee
          10 .text$__gnu_h2f_ieee
         320 .text$__muldc3
         2F0 .text$__mulsc3
         120 .text$__mulvdi3
         110 .text$__mulvsi3
         270 .text$__mulvti3
         3C0 .text$__mulxc3
          10 .text$__negdf2
          10 .text$__negdi2
          10 .text$__negsf2
          30 .text$__negti2
          40 .text$__negvdi2
          30 .text$__negvsi2
          50 .text$__negvti2
          30 .text$__paritydi2
          30 .text$__paritysi2
          40 .text$__parityti2
          70 .text$__popcountdi2
          40 .text$__popcountsi2
          C0 .text$__popcountti2
          40 .text$__powixf2
          60 .text$__subvdi3
          50 .text$__subvsi3
          A0 .text$__subvti3
         150 .text$__truncdfhf2
         110 .text$__truncsfhf2
          30 .text$__ucmpdi2
          40 .text$__ucmpti2
          10 .text.unlikely.__compilerrt_abort_impl
        9970 .xdata
           8 .xdata$__absvdi2
           8 .xdata$__absvsi2
           8 .xdata$__absvti2
           8 .xdata$__addvdi3
           8 .xdata$__addvsi3
           8 .xdata$__addvti3
           4 .xdata$__clzdi2
           4 .xdata$__clzsi2
           4 .xdata$__clzti2
           4 .xdata$__cmpdi2
           4 .xdata$__cmpti2
           4 .xdata$__ctzdi2
           4 .xdata$__ctzsi2
           4 .xdata$__ctzti2
          20 .xdata$__divdc3
          20 .xdata$__divsc3
          10 .xdata$__divxc3
           4 .xdata$__extendhfsf2
           4 .xdata$__ffsti2
           4 .xdata$__gnu_f2h_ieee
           4 .xdata$__gnu_h2f_ieee
          30 .xdata$__muldc3
          2C .xdata$__mulsc3
           8 .xdata$__mulvdi3
           8 .xdata$__mulvsi3
          18 .xdata$__mulvti3
           8 .xdata$__mulxc3
           4 .xdata$__negdf2
           4 .xdata$__negdi2
           4 .xdata$__negsf2
           8 .xdata$__negti2
           8 .xdata$__negvdi2
           8 .xdata$__negvsi2
           8 .xdata$__negvti2
           4 .xdata$__paritydi2
           4 .xdata$__paritysi2
           4 .xdata$__parityti2
           4 .xdata$__popcountdi2
           4 .xdata$__popcountsi2
           8 .xdata$__popcountti2
           4 .xdata$__powixf2
           8 .xdata$__subvdi3
           8 .xdata$__subvsi3
           8 .xdata$__subvti3
           4 .xdata$__truncdfhf2
           4 .xdata$__truncsfhf2
           4 .xdata$__ucmpdi2
           4 .xdata$__ucmpti2
           4 .xdata.unlikely.__compilerrt_abort_impl
```