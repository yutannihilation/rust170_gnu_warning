# A Minimal Reproducible Example To Show "Warning: corrupt .drectve at end of def file" Warning

``` console
$ cargo build --target=x86_64-pc-windows-gnu --lib --release

$ gcc -c main.c -o main.o

$ gcc -o testpkgrust170_gnu_warning.dll main.o -L./target/x86_64-pc-windows-gnu/release -lrust170_gnu_warning -lws2_32 -ladvapi32 -luserenv -lbcrypt -lntdll 
```

And we'll see this warning:

```
Warning: corrupt .drectve at end of def file
Warning: corrupt .drectve at end of def file
```

### Dumpbin result

```
dumpbin.exe /directives .\target\x86_64-pc-windows-gnu\release\librust170_gnu_warning.a
```

```
Microsoft (R) COFF/PE Dumper Version 14.29.30137.0
Copyright (C) Microsoft Corporation.  All rights reserved.


Dump of file .\target\x86_64-pc-windows-gnu\release\librust170_gnu_warning.a

File Type: LIBRARY

   Linker Directives
   -----------------
   -exclude-symbols:__subdf3

   Linker Directives
   -----------------
   -exclude-symbols:__eqsf2

   Linker Directives
   -----------------
   -exclude-symbols:__extendsfdf2

   Linker Directives
   -----------------
   -exclude-symbols:__truncdfsf2

   Linker Directives
   -----------------
   -exclude-symbols:__llvm_memset_element_unordered_atomic_8

   Linker Directives
   -----------------
   -exclude-symbols:_ZN17compiler_builtins5float3cmp7__gesf217h68e72b219b26de82E
   -exclude-symbols:_ZN17compiler_builtins5float3cmp10__unordsf217hf082cad0a6b47908E
   -exclude-symbols:_ZN17compiler_builtins5float3cmp7__eqsf217ha5d3b4b43657456eE
   -exclude-symbols:_ZN17compiler_builtins5float3cmp7__gedf217h710e2b8efd359e91E
   -exclude-symbols:_ZN17compiler_builtins5float3cmp10__unorddf217h425420c7d2e69592E
   -exclude-symbols:_ZN17compiler_builtins5float3cmp7__eqdf217hbff7b17233876731E
   -exclude-symbols:_ZN17compiler_builtins5float3cmp7__lesf217h33a8623ba150f268E
   -exclude-symbols:_ZN17compiler_builtins5float3cmp7__ltsf217h0fd30427de26b7d2E
   -exclude-symbols:_ZN17compiler_builtins5float3cmp7__nesf217h0432284a63214109E
   -exclude-symbols:_ZN17compiler_builtins5float3cmp7__gtsf217hb528ff38409d15cdE
   -exclude-symbols:_ZN17compiler_builtins5float3cmp7__ledf217h8083c0ffe2edf728E
   -exclude-symbols:_ZN17compiler_builtins5float3cmp7__ltdf217h205e1c5fc186f15aE
   -exclude-symbols:_ZN17compiler_builtins5float3cmp7__nedf217hfb2f75ec1f354858E
   -exclude-symbols:_ZN17compiler_builtins5float3cmp7__gtdf217h739ed4c6e0c6e462E

   Linker Directives
   -----------------
   -exclude-symbols:___chkstk_ms

   Linker Directives
   -----------------
   -exclude-symbols:_ZN55_$LT$f32$u20$as$u20$compiler_builtins..float..Float$GT$11signed_repr17h3f0c732047945a48E
   -exclude-symbols:_ZN55_$LT$f32$u20$as$u20$compiler_builtins..float..Float$GT$7eq_repr17h59ad6e910082f4f5E
   -exclude-symbols:_ZN55_$LT$f32$u20$as$u20$compiler_builtins..float..Float$GT$4sign17hbf05434dee717bb2E
   -exclude-symbols:_ZN55_$LT$f32$u20$as$u20$compiler_builtins..float..Float$GT$3exp17h4b8c64890a5bacfeE
   -exclude-symbols:_ZN55_$LT$f32$u20$as$u20$compiler_builtins..float..Float$GT$4frac17h8b8ec8798d65c9e0E
   -exclude-symbols:_ZN55_$LT$f32$u20$as$u20$compiler_builtins..float..Float$GT$8imp_frac17hf5e2d2a517e8a23bE
   -exclude-symbols:_ZN55_$LT$f32$u20$as$u20$compiler_builtins..float..Float$GT$9from_repr17h1e2ed409daa67e84E
   -exclude-symbols:_ZN55_$LT$f32$u20$as$u20$compiler_builtins..float..Float$GT$10from_parts17hff12e10e02305ad4E
   -exclude-symbols:_ZN55_$LT$f32$u20$as$u20$compiler_builtins..float..Float$GT$9normalize17h467f4e9931d9cf6fE
   -exclude-symbols:_ZN55_$LT$f32$u20$as$u20$compiler_builtins..float..Float$GT$12is_subnormal17h50cb0ec90a02f9e6E
   -exclude-symbols:_ZN55_$LT$f64$u20$as$u20$compiler_builtins..float..Float$GT$11signed_repr17h88cbb0d0e5f6d8fbE
   -exclude-symbols:_ZN55_$LT$f64$u20$as$u20$compiler_builtins..float..Float$GT$7eq_repr17h5c5cf60dfca4bb17E
   -exclude-symbols:_ZN55_$LT$f64$u20$as$u20$compiler_builtins..float..Float$GT$4sign17he43845e51475cdb6E
   -exclude-symbols:_ZN55_$LT$f64$u20$as$u20$compiler_builtins..float..Float$GT$3exp17h4218ef0b85e74141E
   -exclude-symbols:_ZN55_$LT$f64$u20$as$u20$compiler_builtins..float..Float$GT$4frac17hf15eb410c3436048E
   -exclude-symbols:_ZN55_$LT$f64$u20$as$u20$compiler_builtins..float..Float$GT$8imp_frac17he9744724b2a6c514E
   -exclude-symbols:_ZN55_$LT$f64$u20$as$u20$compiler_builtins..float..Float$GT$9from_repr17h99daa4091ba27317E
   -exclude-symbols:_ZN55_$LT$f64$u20$as$u20$compiler_builtins..float..Float$GT$10from_parts17h36e754f8a01fa13eE
   -exclude-symbols:_ZN55_$LT$f64$u20$as$u20$compiler_builtins..float..Float$GT$9normalize17h3657b7755d6ff9d2E
   -exclude-symbols:_ZN55_$LT$f64$u20$as$u20$compiler_builtins..float..Float$GT$12is_subnormal17hd3a2db15664aa3f7E
   -exclude-symbols:_ZN55_$LT$f32$u20$as$u20$compiler_builtins..float..Float$GT$4repr17hc09c061d3ff27edaE
   -exclude-symbols:_ZN55_$LT$f64$u20$as$u20$compiler_builtins..float..Float$GT$4repr17h72265156e9ab1123E

   Linker Directives
   -----------------
   -exclude-symbols:__nedf2

   Linker Directives
   -----------------
   -exclude-symbols:_ZN17compiler_builtins3int13leading_zeros8__clzsi217hdab486aba7f2b459E

   Linker Directives
   -----------------
   -exclude-symbols:__divsf3

   Linker Directives
   -----------------
   -exclude-symbols:__ashrti3

   Linker Directives
   -----------------
   -exclude-symbols:__llvm_memset_element_unordered_atomic_1

   Linker Directives
   -----------------
   -exclude-symbols:__alloca

   Linker Directives
   -----------------
   -exclude-symbols:__rust_u128_add

   Linker Directives
   -----------------
   -exclude-symbols:__eqdf2

   Linker Directives
   -----------------
   -exclude-symbols:__floatunsidf

   Linker Directives
   -----------------
   -exclude-symbols:__fixunsdfti

   Linker Directives
   -----------------
   -exclude-symbols:__llvm_memmove_element_unordered_atomic_1

   Linker Directives
   -----------------
   -exclude-symbols:__rust_u128_subo

   Linker Directives
   -----------------
   -exclude-symbols:__floatdisf

   Linker Directives
   -----------------
   -exclude-symbols:_ZN17compiler_builtins5float3add8__addsf317he967b96fc8afa1e0E
   -exclude-symbols:_ZN17compiler_builtins5float3add8__adddf317h028183ef3336737dE

   Linker Directives
   -----------------
   -exclude-symbols:_ZN17compiler_builtins5float4conv12int_to_float15u32_to_f32_bits17hd7e0ef3a1706f9dfE
   -exclude-symbols:_ZN17compiler_builtins5float4conv12int_to_float15u32_to_f64_bits17he516dbc5995556edE
   -exclude-symbols:_ZN17compiler_builtins5float4conv12int_to_float15u64_to_f32_bits17h22c67102ebf46836E
   -exclude-symbols:_ZN17compiler_builtins5float4conv12int_to_float15u64_to_f64_bits17h7d3db884ea9d4ce2E
   -exclude-symbols:_ZN17compiler_builtins5float4conv12int_to_float16u128_to_f32_bits17h493a661b754e6a1eE
   -exclude-symbols:_ZN17compiler_builtins5float4conv12int_to_float16u128_to_f64_bits17h5cc85ebe7b144fcfE

   Linker Directives
   -----------------
   -exclude-symbols:_ZN17compiler_builtins5float5trunc12__truncdfsf217h19dca9b0cffddc42E

   Linker Directives
   -----------------
   -exclude-symbols:__rust_i128_subo

   Linker Directives
   -----------------
   -exclude-symbols:__ledf2

   Linker Directives
   -----------------
   -exclude-symbols:__lshrsi3

   Linker Directives
   -----------------
   -exclude-symbols:__unorddf2

   Linker Directives
   -----------------
   -exclude-symbols:__rust_i128_mulo

   Linker Directives
   -----------------
   -exclude-symbols:__subsf3

   Linker Directives
   -----------------
   -exclude-symbols:__llvm_memmove_element_unordered_atomic_4

   Linker Directives
   -----------------
   -exclude-symbols:__ashlsi3

   Linker Directives
   -----------------
   -exclude-symbols:__divmodti4

   Linker Directives
   -----------------
   -exclude-symbols:__addsf3

   Linker Directives
   -----------------
   -exclude-symbols:__floattisf

   Linker Directives
   -----------------
   -exclude-symbols:__fixunsdfsi

   Linker Directives
   -----------------
   -exclude-symbols:__divdi3

   Linker Directives
   -----------------
   -exclude-symbols:_ZN17compiler_builtins5float3mul8__mulsf317hb9c978303f45e0adE
   -exclude-symbols:_ZN17compiler_builtins5float3mul8__muldf317h065fe933b76446eaE

   Linker Directives
   -----------------
   -exclude-symbols:_ZN17compiler_builtins3int5shift9__ashlsi317hf62866b0559cb9cdE
   -exclude-symbols:_ZN17compiler_builtins3int5shift9__ashldi317he264547ad527514dE
   -exclude-symbols:_ZN17compiler_builtins3int5shift9__ashlti317h122228c4b964bde2E
   -exclude-symbols:_ZN17compiler_builtins3int5shift9__ashrsi317haa25e7e7ef8d1bdbE
   -exclude-symbols:_ZN17compiler_builtins3int5shift9__ashrdi317h6b2f9270cee9f3b1E
   -exclude-symbols:_ZN17compiler_builtins3int5shift9__ashrti317hefc5efcdf8159c64E
   -exclude-symbols:_ZN17compiler_builtins3int5shift9__lshrsi317hb1947b2cdac615edE
   -exclude-symbols:_ZN17compiler_builtins3int5shift9__lshrdi317hca0ce2f4d570e81dE
   -exclude-symbols:_ZN17compiler_builtins3int5shift9__lshrti317hda8cabc49202ac9aE

   Linker Directives
   -----------------
   -exclude-symbols:__fixdfsi

   Linker Directives
   -----------------
   -exclude-symbols:__mulodi4

   Linker Directives
   -----------------
   -exclude-symbols:___chkstk

   Linker Directives
   -----------------
   -exclude-symbols:__divmodsi4

   Linker Directives
   -----------------
   -exclude-symbols:__fixunsdfdi

   Linker Directives
   -----------------
   -exclude-symbols:__fixdfti

   Linker Directives
   -----------------
   -exclude-symbols:__umodti3

   Linker Directives
   -----------------
   -exclude-symbols:__floatunsisf

   Linker Directives
   -----------------
   -exclude-symbols:_ZN17compiler_builtins3int4udiv9__udivsi317h3effbcf9978d6ed3E
   -exclude-symbols:_ZN17compiler_builtins3int4udiv9__umodsi317hdea937f0a84ca94dE
   -exclude-symbols:_ZN17compiler_builtins3int4udiv12__udivmodsi417h12db59bda3103d1cE
   -exclude-symbols:_ZN17compiler_builtins3int4udiv9__udivdi317h4dae608c861fbf4fE
   -exclude-symbols:_ZN17compiler_builtins3int4udiv9__umoddi317hc3c005a4eb10152dE
   -exclude-symbols:_ZN17compiler_builtins3int4udiv12__udivmoddi417h4a4eb7d716ca33d5E
   -exclude-symbols:_ZN17compiler_builtins3int4udiv9__udivti317h70d062ad1aa5d841E
   -exclude-symbols:_ZN17compiler_builtins3int4udiv9__umodti317hd9931b5b9532f6cfE
   -exclude-symbols:_ZN17compiler_builtins3int4udiv12__udivmodti417h68053bb03860fb6cE

   Linker Directives
   -----------------
   -exclude-symbols:__udivsi3

   Linker Directives
   -----------------
   -exclude-symbols:__llvm_memmove_element_unordered_atomic_2

   Linker Directives
   -----------------
   -exclude-symbols:__unordsf2

   Linker Directives
   -----------------
   -exclude-symbols:__ltsf2

   Linker Directives
   -----------------
   -exclude-symbols:__powidf2

   Linker Directives
   -----------------
   -exclude-symbols:__gtdf2

   Linker Directives
   -----------------
   -exclude-symbols:__llvm_memmove_element_unordered_atomic_8

   Linker Directives
   -----------------
   -exclude-symbols:__llvm_memset_element_unordered_atomic_2

   Linker Directives
   -----------------
   -exclude-symbols:__udivti3

   Linker Directives
   -----------------
   -exclude-symbols:__moddi3

   Linker Directives
   -----------------
   -exclude-symbols:_ZN17compiler_builtins5float3div8__divsf317h20a751ea589f4415E
   -exclude-symbols:_ZN17compiler_builtins5float3div8__divdf317h9b40c1bfc7176228E

   Linker Directives
   -----------------
   -exclude-symbols:__divmoddi4

   Linker Directives
   -----------------
   -exclude-symbols:_ZN50_$LT$u8$u20$as$u20$compiler_builtins..int..Int$GT$8abs_diff17hdc0ab99ea3d21788E
   -exclude-symbols:_ZN50_$LT$i8$u20$as$u20$compiler_builtins..int..Int$GT$13from_unsigned17h526a15aa12014ffaE
   -exclude-symbols:_ZN50_$LT$i8$u20$as$u20$compiler_builtins..int..Int$GT$8abs_diff17h784825c3b0d8ddfdE
   -exclude-symbols:_ZN50_$LT$u8$u20$as$u20$compiler_builtins..int..Int$GT$15overflowing_add17h871c3ae358a26cc9E
   -exclude-symbols:_ZN50_$LT$i8$u20$as$u20$compiler_builtins..int..Int$GT$9from_bool17h016b430ac937b91dE
   -exclude-symbols:_ZN50_$LT$i8$u20$as$u20$compiler_builtins..int..Int$GT$11logical_shr17h76f7eab313a35863E
   -exclude-symbols:_ZN50_$LT$i8$u20$as$u20$compiler_builtins..int..Int$GT$7is_zero17he4f012dfcb13bb91E
   -exclude-symbols:_ZN50_$LT$i8$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_neg17h4cdacde6f0f03de7E
   -exclude-symbols:_ZN50_$LT$i8$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_add17h31d1d7e57a8b1278E
   -exclude-symbols:_ZN50_$LT$i8$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_mul17h3ec53ddb634cbe19E
   -exclude-symbols:_ZN50_$LT$i8$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_sub17h2a77c1c8aa64f83eE
   -exclude-symbols:_ZN50_$LT$i8$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shl17hf3a61d4592c1ae93E
   -exclude-symbols:_ZN50_$LT$i8$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shr17h10fdbf286efd02ceE
   -exclude-symbols:_ZN50_$LT$i8$u20$as$u20$compiler_builtins..int..Int$GT$11rotate_left17hd216766d6c9f4f9fE
   -exclude-symbols:_ZN50_$LT$i8$u20$as$u20$compiler_builtins..int..Int$GT$15overflowing_add17h4a7be594277f4b67E
   -exclude-symbols:_ZN50_$LT$i8$u20$as$u20$compiler_builtins..int..Int$GT$13leading_zeros17hea0b26c4cae03cdbE
   -exclude-symbols:_ZN51_$LT$u16$u20$as$u20$compiler_builtins..int..Int$GT$8abs_diff17h2b57c120e0f04433E
   -exclude-symbols:_ZN51_$LT$i16$u20$as$u20$compiler_builtins..int..Int$GT$13from_unsigned17h813bc60d630f8e64E
   -exclude-symbols:_ZN51_$LT$i16$u20$as$u20$compiler_builtins..int..Int$GT$8abs_diff17h3e8a36a6352a8b3aE
   -exclude-symbols:_ZN51_$LT$u16$u20$as$u20$compiler_builtins..int..Int$GT$15overflowing_add17hb05fc8247172bd43E
   -exclude-symbols:_ZN51_$LT$i16$u20$as$u20$compiler_builtins..int..Int$GT$9from_bool17he206c62e856d23f1E
   -exclude-symbols:_ZN51_$LT$i16$u20$as$u20$compiler_builtins..int..Int$GT$11logical_shr17h137abfc796adbe2eE
   -exclude-symbols:_ZN51_$LT$i16$u20$as$u20$compiler_builtins..int..Int$GT$7is_zero17h5312835312a9ec66E
   -exclude-symbols:_ZN51_$LT$i16$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_neg17h1cfa6e3474c21568E
   -exclude-symbols:_ZN51_$LT$i16$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_add17hd7b9257016161703E
   -exclude-symbols:_ZN51_$LT$i16$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_mul17h733e03dd3e0358e0E
   -exclude-symbols:_ZN51_$LT$i16$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_sub17ha3603bc1f9a30121E
   -exclude-symbols:_ZN51_$LT$i16$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shl17hfdbfb2ca3be28c71E
   -exclude-symbols:_ZN51_$LT$i16$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shr17h4cdd9a4a43a6d5b8E
   -exclude-symbols:_ZN51_$LT$i16$u20$as$u20$compiler_builtins..int..Int$GT$11rotate_left17ha681c62231e670fcE
   -exclude-symbols:_ZN51_$LT$i16$u20$as$u20$compiler_builtins..int..Int$GT$15overflowing_add17he908986f68b27cb5E
   -exclude-symbols:_ZN51_$LT$i16$u20$as$u20$compiler_builtins..int..Int$GT$13leading_zeros17h9e8b1db391b1d6f7E
   -exclude-symbols:_ZN51_$LT$u32$u20$as$u20$compiler_builtins..int..Int$GT$8abs_diff17he107eb4d7bbc1d06E
   -exclude-symbols:_ZN51_$LT$i32$u20$as$u20$compiler_builtins..int..Int$GT$13from_unsigned17hc97368a693697f96E
   -exclude-symbols:_ZN51_$LT$i32$u20$as$u20$compiler_builtins..int..Int$GT$8abs_diff17hf0152d0f8211af8fE
   -exclude-symbols:_ZN51_$LT$u32$u20$as$u20$compiler_builtins..int..Int$GT$15overflowing_add17h2fd8c25eff886715E
   -exclude-symbols:_ZN51_$LT$i32$u20$as$u20$compiler_builtins..int..Int$GT$9from_bool17h2abd75c9db829c32E
   -exclude-symbols:_ZN51_$LT$i32$u20$as$u20$compiler_builtins..int..Int$GT$11logical_shr17h2b4370919c5c7572E
   -exclude-symbols:_ZN51_$LT$i32$u20$as$u20$compiler_builtins..int..Int$GT$7is_zero17h9310daaec6b71f36E
   -exclude-symbols:_ZN51_$LT$i32$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_neg17h327eb4be09fb6c19E
   -exclude-symbols:_ZN51_$LT$i32$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_add17hcf7642b78429f953E
   -exclude-symbols:_ZN51_$LT$i32$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_mul17h3f2850e5b0eaf3c2E
   -exclude-symbols:_ZN51_$LT$i32$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_sub17hb1f8c9babd27f9f7E
   -exclude-symbols:_ZN51_$LT$i32$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shl17h9cbd5d210a50e5e6E
   -exclude-symbols:_ZN51_$LT$i32$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shr17h082aebc2752e8247E
   -exclude-symbols:_ZN51_$LT$i32$u20$as$u20$compiler_builtins..int..Int$GT$11rotate_left17h2fb2c6760153fe0cE
   -exclude-symbols:_ZN51_$LT$i32$u20$as$u20$compiler_builtins..int..Int$GT$15overflowing_add17hfe6ba551d49fd5eeE
   -exclude-symbols:_ZN51_$LT$i32$u20$as$u20$compiler_builtins..int..Int$GT$13leading_zeros17h467a47be29b7aff8E
   -exclude-symbols:_ZN51_$LT$u64$u20$as$u20$compiler_builtins..int..Int$GT$8abs_diff17h863d2ecc80e59741E
   -exclude-symbols:_ZN51_$LT$i64$u20$as$u20$compiler_builtins..int..Int$GT$13from_unsigned17h5be3759e05f0ca94E
   -exclude-symbols:_ZN51_$LT$i64$u20$as$u20$compiler_builtins..int..Int$GT$8abs_diff17ha6c4109871c54c03E
   -exclude-symbols:_ZN51_$LT$u64$u20$as$u20$compiler_builtins..int..Int$GT$15overflowing_add17h9a76eb44c75002aeE
   -exclude-symbols:_ZN51_$LT$i64$u20$as$u20$compiler_builtins..int..Int$GT$9from_bool17h2096aa42f5231bd6E
   -exclude-symbols:_ZN51_$LT$i64$u20$as$u20$compiler_builtins..int..Int$GT$11logical_shr17h193fc49334a2b3ccE
   -exclude-symbols:_ZN51_$LT$i64$u20$as$u20$compiler_builtins..int..Int$GT$7is_zero17h71db7a6801bf1cddE
   -exclude-symbols:_ZN51_$LT$i64$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_neg17h758eb33588a9fd97E
   -exclude-symbols:_ZN51_$LT$i64$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_add17hcc1f4a05338365eaE
   -exclude-symbols:_ZN51_$LT$i64$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_mul17h6835d041081457c6E
   -exclude-symbols:_ZN51_$LT$i64$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_sub17h007d0c214958c247E
   -exclude-symbols:_ZN51_$LT$i64$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shl17hc0a8a1d36541d183E
   -exclude-symbols:_ZN51_$LT$i64$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shr17h84a24b5766e43206E
   -exclude-symbols:_ZN51_$LT$i64$u20$as$u20$compiler_builtins..int..Int$GT$11rotate_left17h85fe775b7129436bE
   -exclude-symbols:_ZN51_$LT$i64$u20$as$u20$compiler_builtins..int..Int$GT$15overflowing_add17h8194d533c6f4e22dE
   -exclude-symbols:_ZN51_$LT$i64$u20$as$u20$compiler_builtins..int..Int$GT$13leading_zeros17ha9b8d3b14e32f64eE
   -exclude-symbols:_ZN52_$LT$u128$u20$as$u20$compiler_builtins..int..Int$GT$8abs_diff17h9317a48b3c7149ddE
   -exclude-symbols:_ZN52_$LT$i128$u20$as$u20$compiler_builtins..int..Int$GT$13from_unsigned17h556fc4d147af7105E
   -exclude-symbols:_ZN52_$LT$i128$u20$as$u20$compiler_builtins..int..Int$GT$8abs_diff17hc509963ca6de412bE
   -exclude-symbols:_ZN52_$LT$u128$u20$as$u20$compiler_builtins..int..Int$GT$15overflowing_add17hca535adcb8fc3fc0E
   -exclude-symbols:_ZN52_$LT$i128$u20$as$u20$compiler_builtins..int..Int$GT$9from_bool17h8d8cf9be57f9368fE
   -exclude-symbols:_ZN52_$LT$i128$u20$as$u20$compiler_builtins..int..Int$GT$11logical_shr17h55937a8e2ad56efaE
   -exclude-symbols:_ZN52_$LT$i128$u20$as$u20$compiler_builtins..int..Int$GT$7is_zero17h78469102d3927493E
   -exclude-symbols:_ZN52_$LT$i128$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_neg17h68f99ac7386ede30E
   -exclude-symbols:_ZN52_$LT$i128$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_add17ha8fc925f98b8cd5fE
   -exclude-symbols:_ZN52_$LT$i128$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_mul17hf413703519c0692bE
   -exclude-symbols:_ZN52_$LT$i128$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_sub17h8b42df0f1a5657adE
   -exclude-symbols:_ZN52_$LT$i128$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shl17h2d5e441f057b0157E
   -exclude-symbols:_ZN52_$LT$i128$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shr17hd2e16371d65b8240E
   -exclude-symbols:_ZN52_$LT$i128$u20$as$u20$compiler_builtins..int..Int$GT$11rotate_left17h10f2b4d49bb210f1E
   -exclude-symbols:_ZN52_$LT$i128$u20$as$u20$compiler_builtins..int..Int$GT$15overflowing_add17h8890364ab1c49ce5E
   -exclude-symbols:_ZN52_$LT$i128$u20$as$u20$compiler_builtins..int..Int$GT$13leading_zeros17h476983dc847ef0d1E
   -exclude-symbols:_ZN52_$LT$i16$u20$as$u20$compiler_builtins..int..DInt$GT$2lo17hf5e50fbf567c8fdfE
   -exclude-symbols:_ZN52_$LT$i16$u20$as$u20$compiler_builtins..int..DInt$GT$2hi17had90caed3cf496f1E
   -exclude-symbols:_ZN52_$LT$i16$u20$as$u20$compiler_builtins..int..DInt$GT$5lo_hi17h2145641d5f57b892E
   -exclude-symbols:_ZN52_$LT$i16$u20$as$u20$compiler_builtins..int..DInt$GT$10from_lo_hi17h2939c02d72c9b63bE
   -exclude-symbols:_ZN52_$LT$i32$u20$as$u20$compiler_builtins..int..DInt$GT$2lo17hfc3a3c1c3e95ecbcE
   -exclude-symbols:_ZN52_$LT$i32$u20$as$u20$compiler_builtins..int..DInt$GT$2hi17heafa76766836d302E
   -exclude-symbols:_ZN52_$LT$i32$u20$as$u20$compiler_builtins..int..DInt$GT$5lo_hi17he1bc0f988e1e4bb4E
   -exclude-symbols:_ZN52_$LT$i32$u20$as$u20$compiler_builtins..int..DInt$GT$10from_lo_hi17h1b8079f3ba9e4a1bE
   -exclude-symbols:_ZN52_$LT$i64$u20$as$u20$compiler_builtins..int..DInt$GT$2lo17hd3d49db528584a87E
   -exclude-symbols:_ZN52_$LT$i64$u20$as$u20$compiler_builtins..int..DInt$GT$2hi17hfc12768339769488E
   -exclude-symbols:_ZN52_$LT$i64$u20$as$u20$compiler_builtins..int..DInt$GT$5lo_hi17h6bd02443e91b07b2E
   -exclude-symbols:_ZN52_$LT$i64$u20$as$u20$compiler_builtins..int..DInt$GT$10from_lo_hi17h5aaa812fcc5cbea8E
   -exclude-symbols:_ZN53_$LT$i128$u20$as$u20$compiler_builtins..int..DInt$GT$2lo17hc7c873632d10a180E
   -exclude-symbols:_ZN53_$LT$i128$u20$as$u20$compiler_builtins..int..DInt$GT$2hi17hfe3a0672c81287e5E
   -exclude-symbols:_ZN53_$LT$i128$u20$as$u20$compiler_builtins..int..DInt$GT$5lo_hi17hf361ce3ddedf1466E
   -exclude-symbols:_ZN53_$LT$i128$u20$as$u20$compiler_builtins..int..DInt$GT$10from_lo_hi17hf23ba5393773fd02E
   -exclude-symbols:_ZN51_$LT$i8$u20$as$u20$compiler_builtins..int..HInt$GT$5widen17he3b7ac145f319463E
   -exclude-symbols:_ZN51_$LT$i8$u20$as$u20$compiler_builtins..int..HInt$GT$10zero_widen17h88bf5ffda6ab6498E
   -exclude-symbols:_ZN51_$LT$i8$u20$as$u20$compiler_builtins..int..HInt$GT$8widen_hi17h93ee82e6df54b148E
   -exclude-symbols:_ZN51_$LT$i8$u20$as$u20$compiler_builtins..int..HInt$GT$14zero_widen_mul17h934fe88f421d34f9E
   -exclude-symbols:_ZN51_$LT$i8$u20$as$u20$compiler_builtins..int..HInt$GT$9widen_mul17h1d93f6d08ad73214E
   -exclude-symbols:_ZN52_$LT$i16$u20$as$u20$compiler_builtins..int..HInt$GT$5widen17h05dd4be08a08cdb9E
   -exclude-symbols:_ZN52_$LT$i16$u20$as$u20$compiler_builtins..int..HInt$GT$10zero_widen17h40b7e3ad8d7fc0c1E
   -exclude-symbols:_ZN52_$LT$i16$u20$as$u20$compiler_builtins..int..HInt$GT$8widen_hi17h0b8002fdb4f5d98fE
   -exclude-symbols:_ZN52_$LT$i16$u20$as$u20$compiler_builtins..int..HInt$GT$14zero_widen_mul17h688f13fdb4915f8fE
   -exclude-symbols:_ZN52_$LT$i16$u20$as$u20$compiler_builtins..int..HInt$GT$9widen_mul17h4f835d3df8a9951eE
   -exclude-symbols:_ZN52_$LT$i32$u20$as$u20$compiler_builtins..int..HInt$GT$5widen17h37c742dc786370ccE
   -exclude-symbols:_ZN52_$LT$i32$u20$as$u20$compiler_builtins..int..HInt$GT$10zero_widen17hcc85f7a940bcd2b0E
   -exclude-symbols:_ZN52_$LT$i32$u20$as$u20$compiler_builtins..int..HInt$GT$8widen_hi17h8100a95216128b72E
   -exclude-symbols:_ZN52_$LT$i32$u20$as$u20$compiler_builtins..int..HInt$GT$14zero_widen_mul17h304692ecf2913b8bE
   -exclude-symbols:_ZN52_$LT$i32$u20$as$u20$compiler_builtins..int..HInt$GT$9widen_mul17h26a55cdb90fcac4bE
   -exclude-symbols:_ZN52_$LT$i64$u20$as$u20$compiler_builtins..int..HInt$GT$5widen17h7f2701232a911858E
   -exclude-symbols:_ZN52_$LT$i64$u20$as$u20$compiler_builtins..int..HInt$GT$10zero_widen17h8771f885053f1b99E
   -exclude-symbols:_ZN52_$LT$i64$u20$as$u20$compiler_builtins..int..HInt$GT$8widen_hi17h7991d552f8aff83aE
   -exclude-symbols:_ZN52_$LT$i64$u20$as$u20$compiler_builtins..int..HInt$GT$14zero_widen_mul17ha9ccadde28602c53E
   -exclude-symbols:_ZN52_$LT$i64$u20$as$u20$compiler_builtins..int..HInt$GT$9widen_mul17h9e8945b5d40247aaE
   -exclude-symbols:_ZN66_$LT$u8$u20$as$u20$compiler_builtins..int..CastInto$LT$i32$GT$$GT$4cast17h366adca4d22f9d7aE
   -exclude-symbols:_ZN66_$LT$u8$u20$as$u20$compiler_builtins..int..CastInto$LT$i64$GT$$GT$4cast17h929b3bcb4a39ccd4E
   -exclude-symbols:_ZN67_$LT$u8$u20$as$u20$compiler_builtins..int..CastInto$LT$i128$GT$$GT$4cast17h6b29ae338e2536e1E
   -exclude-symbols:_ZN66_$LT$i8$u20$as$u20$compiler_builtins..int..CastInto$LT$i32$GT$$GT$4cast17hcfd2ccfe9d8905faE
   -exclude-symbols:_ZN66_$LT$i8$u20$as$u20$compiler_builtins..int..CastInto$LT$i64$GT$$GT$4cast17hefbcc8b530152b50E
   -exclude-symbols:_ZN67_$LT$i8$u20$as$u20$compiler_builtins..int..CastInto$LT$i128$GT$$GT$4cast17h9344e23155e02011E
   -exclude-symbols:_ZN67_$LT$u16$u20$as$u20$compiler_builtins..int..CastInto$LT$i64$GT$$GT$4cast17hdad507498fb673cfE
   -exclude-symbols:_ZN68_$LT$u16$u20$as$u20$compiler_builtins..int..CastInto$LT$i128$GT$$GT$4cast17hfd4f209f64877372E
   -exclude-symbols:_ZN67_$LT$i16$u20$as$u20$compiler_builtins..int..CastInto$LT$i64$GT$$GT$4cast17hc3ed810317db418bE
   -exclude-symbols:_ZN68_$LT$i16$u20$as$u20$compiler_builtins..int..CastInto$LT$i128$GT$$GT$4cast17hb538717d6cb4e43cE
   -exclude-symbols:_ZN68_$LT$u32$u20$as$u20$compiler_builtins..int..CastInto$LT$i128$GT$$GT$4cast17h5530f9ebd826a59eE
   -exclude-symbols:_ZN66_$LT$i32$u20$as$u20$compiler_builtins..int..CastInto$LT$i8$GT$$GT$4cast17he151cbac77f4c554E
   -exclude-symbols:_ZN68_$LT$i32$u20$as$u20$compiler_builtins..int..CastInto$LT$i128$GT$$GT$4cast17h438a299d9412de00E
   -exclude-symbols:_ZN66_$LT$i64$u20$as$u20$compiler_builtins..int..CastInto$LT$i8$GT$$GT$4cast17h1315036537633eb3E
   -exclude-symbols:_ZN67_$LT$i64$u20$as$u20$compiler_builtins..int..CastInto$LT$i16$GT$$GT$4cast17haf3694de5b360f62E
   -exclude-symbols:_ZN67_$LT$i128$u20$as$u20$compiler_builtins..int..CastInto$LT$i8$GT$$GT$4cast17h7335bd7ac2baf223E
   -exclude-symbols:_ZN68_$LT$i128$u20$as$u20$compiler_builtins..int..CastInto$LT$i16$GT$$GT$4cast17h68a0703e79b61c23E
   -exclude-symbols:_ZN68_$LT$i128$u20$as$u20$compiler_builtins..int..CastInto$LT$i32$GT$$GT$4cast17h4d1084ec74bb3a70E
   -exclude-symbols:_ZN53_$LT$usize$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_neg17h8c74360a1ecf2576E
   -exclude-symbols:_ZN50_$LT$u8$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_neg17h416bbb347de91aeeE
   -exclude-symbols:_ZN51_$LT$u16$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_neg17h9f8c950086231d01E
   -exclude-symbols:_ZN51_$LT$u32$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_neg17heeeb3429f1e8ce84E
   -exclude-symbols:_ZN53_$LT$isize$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_neg17h166ef341992a0a18E
   -exclude-symbols:_ZN51_$LT$u64$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_neg17h43321c87b75277bcE
   -exclude-symbols:_ZN52_$LT$u128$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_neg17hbddf57a11394e212E
   -exclude-symbols:_ZN50_$LT$u8$u20$as$u20$compiler_builtins..int..Int$GT$11rotate_left17he3c978e0617f93c4E
   -exclude-symbols:_ZN51_$LT$u16$u20$as$u20$compiler_builtins..int..Int$GT$11rotate_left17hd835be19186ff2bbE
   -exclude-symbols:_ZN51_$LT$u32$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shr17h56f6dbda1f981298E
   -exclude-symbols:_ZN51_$LT$u32$u20$as$u20$compiler_builtins..int..Int$GT$11logical_shr17h14c6b10bc3c3a26fE
   -exclude-symbols:_ZN53_$LT$usize$u20$as$u20$compiler_builtins..int..Int$GT$13leading_zeros17h0be402b58bf62561E
   -exclude-symbols:_ZN53_$LT$isize$u20$as$u20$compiler_builtins..int..Int$GT$13leading_zeros17h4736da4201fd26e0E
   -exclude-symbols:_ZN51_$LT$u64$u20$as$u20$compiler_builtins..int..Int$GT$13leading_zeros17h7919faa999e0b653E
   -exclude-symbols:_ZN52_$LT$u128$u20$as$u20$compiler_builtins..int..Int$GT$13leading_zeros17h58529a1dd97a6644E
   -exclude-symbols:_ZN50_$LT$u8$u20$as$u20$compiler_builtins..int..Int$GT$13leading_zeros17h5a66bb85d8cc6dffE
   -exclude-symbols:_ZN51_$LT$u16$u20$as$u20$compiler_builtins..int..Int$GT$13leading_zeros17h60fc5d3b2a6401b9E
   -exclude-symbols:_ZN51_$LT$u32$u20$as$u20$compiler_builtins..int..Int$GT$13leading_zeros17hfabdad5f763a5491E
   -exclude-symbols:_ZN51_$LT$u8$u20$as$u20$compiler_builtins..int..HInt$GT$9widen_mul17hc9d97187b6448604E
   -exclude-symbols:_ZN52_$LT$u16$u20$as$u20$compiler_builtins..int..HInt$GT$9widen_mul17hf061a142a25e0dc1E
   -exclude-symbols:_ZN52_$LT$u32$u20$as$u20$compiler_builtins..int..HInt$GT$9widen_mul17h0c059ced3ac48453E
   -exclude-symbols:_ZN52_$LT$u64$u20$as$u20$compiler_builtins..int..HInt$GT$9widen_mul17h6fdfa0eb28639fcaE
   -exclude-symbols:_ZN51_$LT$u8$u20$as$u20$compiler_builtins..int..HInt$GT$14zero_widen_mul17h1255a6550e8c854fE
   -exclude-symbols:_ZN52_$LT$u16$u20$as$u20$compiler_builtins..int..HInt$GT$14zero_widen_mul17ha3d24bd42a0dd36dE
   -exclude-symbols:_ZN52_$LT$u32$u20$as$u20$compiler_builtins..int..HInt$GT$14zero_widen_mul17h25db5eff332c65adE
   -exclude-symbols:_ZN52_$LT$u64$u20$as$u20$compiler_builtins..int..HInt$GT$14zero_widen_mul17h3da030049697eaa3E
   -exclude-symbols:_ZN53_$LT$usize$u20$as$u20$compiler_builtins..int..Int$GT$8unsigned17he932e42e62833e2dE
   -exclude-symbols:_ZN53_$LT$usize$u20$as$u20$compiler_builtins..int..Int$GT$13from_unsigned17h558e1c49e69a9d16E
   -exclude-symbols:_ZN53_$LT$isize$u20$as$u20$compiler_builtins..int..Int$GT$8unsigned17h1dd92824f5cd0834E
   -exclude-symbols:_ZN50_$LT$u8$u20$as$u20$compiler_builtins..int..Int$GT$8unsigned17hd038365269f7cd75E
   -exclude-symbols:_ZN50_$LT$u8$u20$as$u20$compiler_builtins..int..Int$GT$13from_unsigned17he2e93e90b03c9ff7E
   -exclude-symbols:_ZN50_$LT$i8$u20$as$u20$compiler_builtins..int..Int$GT$8unsigned17h2f8b8e3b3b34c84aE
   -exclude-symbols:_ZN51_$LT$u16$u20$as$u20$compiler_builtins..int..Int$GT$8unsigned17h34b1d0fb681e57b9E
   -exclude-symbols:_ZN51_$LT$u16$u20$as$u20$compiler_builtins..int..Int$GT$13from_unsigned17h592fbdb44c01c098E
   -exclude-symbols:_ZN51_$LT$i16$u20$as$u20$compiler_builtins..int..Int$GT$8unsigned17he3da6cb0dddaa40dE
   -exclude-symbols:_ZN51_$LT$u32$u20$as$u20$compiler_builtins..int..Int$GT$8unsigned17h0be9fc3e8c5fd2acE
   -exclude-symbols:_ZN51_$LT$u32$u20$as$u20$compiler_builtins..int..Int$GT$13from_unsigned17hb2bd0b43ac604e30E
   -exclude-symbols:_ZN51_$LT$i32$u20$as$u20$compiler_builtins..int..Int$GT$8unsigned17h5bf23f9f959ad178E
   -exclude-symbols:_ZN53_$LT$isize$u20$as$u20$compiler_builtins..int..Int$GT$13from_unsigned17hcb68b6c10dea8fa1E
   -exclude-symbols:_ZN51_$LT$u64$u20$as$u20$compiler_builtins..int..Int$GT$8unsigned17haffe8507dbaaf6d1E
   -exclude-symbols:_ZN51_$LT$u64$u20$as$u20$compiler_builtins..int..Int$GT$13from_unsigned17h9bcd773ac0c079c7E
   -exclude-symbols:_ZN51_$LT$i64$u20$as$u20$compiler_builtins..int..Int$GT$8unsigned17h93bc51858a4c94b6E
   -exclude-symbols:_ZN52_$LT$u128$u20$as$u20$compiler_builtins..int..Int$GT$8unsigned17hbe3094e6ee999f7aE
   -exclude-symbols:_ZN52_$LT$u128$u20$as$u20$compiler_builtins..int..Int$GT$13from_unsigned17h71a514603a9fc15aE
   -exclude-symbols:_ZN52_$LT$i128$u20$as$u20$compiler_builtins..int..Int$GT$8unsigned17h892f49d5bb1ca98bE
   -exclude-symbols:_ZN71_$LT$usize$u20$as$u20$compiler_builtins..int..CastInto$LT$usize$GT$$GT$4cast17hdf7d63955b459a2aE
   -exclude-symbols:_ZN71_$LT$usize$u20$as$u20$compiler_builtins..int..CastInto$LT$isize$GT$$GT$4cast17hcdec203a6ff1f868E
   -exclude-symbols:_ZN69_$LT$usize$u20$as$u20$compiler_builtins..int..CastInto$LT$u64$GT$$GT$4cast17h8c94a9adbc17fefcE
   -exclude-symbols:_ZN69_$LT$usize$u20$as$u20$compiler_builtins..int..CastInto$LT$i64$GT$$GT$4cast17hcdde1bbe11861acdE
   -exclude-symbols:_ZN71_$LT$isize$u20$as$u20$compiler_builtins..int..CastInto$LT$usize$GT$$GT$4cast17h4fb49edd829a7659E
   -exclude-symbols:_ZN71_$LT$isize$u20$as$u20$compiler_builtins..int..CastInto$LT$isize$GT$$GT$4cast17h2b32f0cd04cb0be9E
   -exclude-symbols:_ZN69_$LT$isize$u20$as$u20$compiler_builtins..int..CastInto$LT$u64$GT$$GT$4cast17h4fb5784bf93e4f6dE
   -exclude-symbols:_ZN69_$LT$isize$u20$as$u20$compiler_builtins..int..CastInto$LT$i64$GT$$GT$4cast17hfe0dcc2256a89943E
   -exclude-symbols:_ZN65_$LT$u8$u20$as$u20$compiler_builtins..int..CastInto$LT$u8$GT$$GT$4cast17hccfa7e0529a42dd2E
   -exclude-symbols:_ZN65_$LT$u8$u20$as$u20$compiler_builtins..int..CastInto$LT$i8$GT$$GT$4cast17hcbadfc7924457f68E
   -exclude-symbols:_ZN65_$LT$i8$u20$as$u20$compiler_builtins..int..CastInto$LT$u8$GT$$GT$4cast17h4dfb958a1cfb076fE
   -exclude-symbols:_ZN65_$LT$i8$u20$as$u20$compiler_builtins..int..CastInto$LT$i8$GT$$GT$4cast17ha1bd696a20bb6aefE
   -exclude-symbols:_ZN67_$LT$u16$u20$as$u20$compiler_builtins..int..CastInto$LT$u16$GT$$GT$4cast17he5324b5406e1faa0E
   -exclude-symbols:_ZN67_$LT$u16$u20$as$u20$compiler_builtins..int..CastInto$LT$i16$GT$$GT$4cast17h1ec70a067496b0b3E
   -exclude-symbols:_ZN67_$LT$i16$u20$as$u20$compiler_builtins..int..CastInto$LT$u16$GT$$GT$4cast17h8c65afff302b85beE
   -exclude-symbols:_ZN67_$LT$i16$u20$as$u20$compiler_builtins..int..CastInto$LT$i16$GT$$GT$4cast17h89a7d94f1da26e40E
   -exclude-symbols:_ZN67_$LT$u32$u20$as$u20$compiler_builtins..int..CastInto$LT$u32$GT$$GT$4cast17h252c6a54bbb9863dE
   -exclude-symbols:_ZN67_$LT$u32$u20$as$u20$compiler_builtins..int..CastInto$LT$i32$GT$$GT$4cast17h99d45bb23f738437E
   -exclude-symbols:_ZN67_$LT$i32$u20$as$u20$compiler_builtins..int..CastInto$LT$u32$GT$$GT$4cast17hecea83e71dce9bdcE
   -exclude-symbols:_ZN67_$LT$i32$u20$as$u20$compiler_builtins..int..CastInto$LT$i32$GT$$GT$4cast17h171837a86cb40445E
   -exclude-symbols:_ZN69_$LT$u64$u20$as$u20$compiler_builtins..int..CastInto$LT$usize$GT$$GT$4cast17h844ca7ef82df568cE
   -exclude-symbols:_ZN69_$LT$u64$u20$as$u20$compiler_builtins..int..CastInto$LT$isize$GT$$GT$4cast17h077cfde7ee29020dE
   -exclude-symbols:_ZN67_$LT$u64$u20$as$u20$compiler_builtins..int..CastInto$LT$u64$GT$$GT$4cast17ha4a9dfbc5358de8bE
   -exclude-symbols:_ZN67_$LT$u64$u20$as$u20$compiler_builtins..int..CastInto$LT$i64$GT$$GT$4cast17h088bc06d880d9cbfE
   -exclude-symbols:_ZN69_$LT$i64$u20$as$u20$compiler_builtins..int..CastInto$LT$usize$GT$$GT$4cast17h7bffc41f60b66c69E
   -exclude-symbols:_ZN69_$LT$i64$u20$as$u20$compiler_builtins..int..CastInto$LT$isize$GT$$GT$4cast17h179739a1ca04ec83E
   -exclude-symbols:_ZN67_$LT$i64$u20$as$u20$compiler_builtins..int..CastInto$LT$u64$GT$$GT$4cast17h4ed4f80dab55d38fE
   -exclude-symbols:_ZN67_$LT$i64$u20$as$u20$compiler_builtins..int..CastInto$LT$i64$GT$$GT$4cast17h888376d77456c3e1E
   -exclude-symbols:_ZN69_$LT$u128$u20$as$u20$compiler_builtins..int..CastInto$LT$u128$GT$$GT$4cast17h2201f579b6efd70cE
   -exclude-symbols:_ZN69_$LT$u128$u20$as$u20$compiler_builtins..int..CastInto$LT$i128$GT$$GT$4cast17hd3130a705e876cbeE
   -exclude-symbols:_ZN69_$LT$i128$u20$as$u20$compiler_builtins..int..CastInto$LT$u128$GT$$GT$4cast17h43b75f02471171d2E
   -exclude-symbols:_ZN69_$LT$i128$u20$as$u20$compiler_builtins..int..CastInto$LT$i128$GT$$GT$4cast17h64aa8d763cceb237E
   -exclude-symbols:_ZN52_$LT$u16$u20$as$u20$compiler_builtins..int..DInt$GT$5lo_hi17h700aa589d4770d78E
   -exclude-symbols:_ZN52_$LT$u32$u20$as$u20$compiler_builtins..int..DInt$GT$5lo_hi17hbd96ffba703f336fE
   -exclude-symbols:_ZN52_$LT$u64$u20$as$u20$compiler_builtins..int..DInt$GT$5lo_hi17h15028a0de5e46e9cE
   -exclude-symbols:_ZN53_$LT$u128$u20$as$u20$compiler_builtins..int..DInt$GT$5lo_hi17hc85cadb38aa246f2E
   -exclude-symbols:_ZN52_$LT$u16$u20$as$u20$compiler_builtins..int..DInt$GT$2hi17h76a34ce344a79b25E
   -exclude-symbols:_ZN52_$LT$u32$u20$as$u20$compiler_builtins..int..DInt$GT$2hi17h7622e885d68336d7E
   -exclude-symbols:_ZN52_$LT$u64$u20$as$u20$compiler_builtins..int..DInt$GT$2hi17h2033574c1ef03ebfE
   -exclude-symbols:_ZN53_$LT$u128$u20$as$u20$compiler_builtins..int..DInt$GT$2hi17h471959247635ce75E
   -exclude-symbols:_ZN53_$LT$usize$u20$as$u20$compiler_builtins..int..Int$GT$9from_bool17h4be57c12060403bcE
   -exclude-symbols:_ZN50_$LT$u8$u20$as$u20$compiler_builtins..int..Int$GT$9from_bool17h6087f81581770779E
   -exclude-symbols:_ZN51_$LT$u16$u20$as$u20$compiler_builtins..int..Int$GT$9from_bool17h626c0ed22eec0297E
   -exclude-symbols:_ZN51_$LT$u32$u20$as$u20$compiler_builtins..int..Int$GT$9from_bool17hd9da887ec1ab584bE
   -exclude-symbols:_ZN53_$LT$isize$u20$as$u20$compiler_builtins..int..Int$GT$9from_bool17hc8b11177464cfb05E
   -exclude-symbols:_ZN51_$LT$u64$u20$as$u20$compiler_builtins..int..Int$GT$9from_bool17hcd28b5a191170190E
   -exclude-symbols:_ZN52_$LT$u128$u20$as$u20$compiler_builtins..int..Int$GT$9from_bool17h0f2a609f22150971E
   -exclude-symbols:_ZN51_$LT$u8$u20$as$u20$compiler_builtins..int..HInt$GT$5widen17hbb342593ef78c64fE
   -exclude-symbols:_ZN52_$LT$u16$u20$as$u20$compiler_builtins..int..HInt$GT$5widen17hd9bc9641c344a2a2E
   -exclude-symbols:_ZN52_$LT$u32$u20$as$u20$compiler_builtins..int..HInt$GT$5widen17hb5a1af8d530b99efE
   -exclude-symbols:_ZN52_$LT$u64$u20$as$u20$compiler_builtins..int..HInt$GT$5widen17h82f1cbfeb1d6f27bE
   -exclude-symbols:_ZN51_$LT$u8$u20$as$u20$compiler_builtins..int..HInt$GT$10zero_widen17h18e28c05e41896e3E
   -exclude-symbols:_ZN52_$LT$u16$u20$as$u20$compiler_builtins..int..HInt$GT$10zero_widen17h40b647a857097661E
   -exclude-symbols:_ZN52_$LT$u32$u20$as$u20$compiler_builtins..int..HInt$GT$10zero_widen17hcb534cca04955c70E
   -exclude-symbols:_ZN52_$LT$u64$u20$as$u20$compiler_builtins..int..HInt$GT$10zero_widen17h02b6e9619a55b936E
   -exclude-symbols:_ZN70_$LT$usize$u20$as$u20$compiler_builtins..int..CastInto$LT$u128$GT$$GT$4cast17h46cd469a246003ffE
   -exclude-symbols:_ZN70_$LT$usize$u20$as$u20$compiler_builtins..int..CastInto$LT$i128$GT$$GT$4cast17h89ad489ad75cd0a7E
   -exclude-symbols:_ZN68_$LT$u8$u20$as$u20$compiler_builtins..int..CastInto$LT$usize$GT$$GT$4cast17h33682ce4c5b4f33eE
   -exclude-symbols:_ZN66_$LT$u8$u20$as$u20$compiler_builtins..int..CastInto$LT$u16$GT$$GT$4cast17hb283ec52f80f4c64E
   -exclude-symbols:_ZN66_$LT$u8$u20$as$u20$compiler_builtins..int..CastInto$LT$i16$GT$$GT$4cast17h3b2c198635619357E
   -exclude-symbols:_ZN66_$LT$u8$u20$as$u20$compiler_builtins..int..CastInto$LT$u32$GT$$GT$4cast17h1af4f3e9f8294068E
   -exclude-symbols:_ZN68_$LT$u8$u20$as$u20$compiler_builtins..int..CastInto$LT$isize$GT$$GT$4cast17h3025f2b921d2b833E
   -exclude-symbols:_ZN66_$LT$u8$u20$as$u20$compiler_builtins..int..CastInto$LT$u64$GT$$GT$4cast17h02258db6005bb03dE
   -exclude-symbols:_ZN67_$LT$u8$u20$as$u20$compiler_builtins..int..CastInto$LT$u128$GT$$GT$4cast17h200263b12712d1d4E
   -exclude-symbols:_ZN69_$LT$u16$u20$as$u20$compiler_builtins..int..CastInto$LT$usize$GT$$GT$4cast17hf2e588e07a5fde43E
   -exclude-symbols:_ZN67_$LT$u16$u20$as$u20$compiler_builtins..int..CastInto$LT$u32$GT$$GT$4cast17h76b38d8514505f65E
   -exclude-symbols:_ZN67_$LT$u16$u20$as$u20$compiler_builtins..int..CastInto$LT$i32$GT$$GT$4cast17h594cb828138a6c86E
   -exclude-symbols:_ZN69_$LT$u16$u20$as$u20$compiler_builtins..int..CastInto$LT$isize$GT$$GT$4cast17h6ed2be4f70777b8dE
   -exclude-symbols:_ZN67_$LT$u16$u20$as$u20$compiler_builtins..int..CastInto$LT$u64$GT$$GT$4cast17hffba01b983632d2eE
   -exclude-symbols:_ZN68_$LT$u16$u20$as$u20$compiler_builtins..int..CastInto$LT$u128$GT$$GT$4cast17heaf3df998960b29bE
   -exclude-symbols:_ZN69_$LT$u32$u20$as$u20$compiler_builtins..int..CastInto$LT$usize$GT$$GT$4cast17ha36319d90c8111f0E
   -exclude-symbols:_ZN69_$LT$u32$u20$as$u20$compiler_builtins..int..CastInto$LT$isize$GT$$GT$4cast17h7e195c852b5284f9E
   -exclude-symbols:_ZN67_$LT$u32$u20$as$u20$compiler_builtins..int..CastInto$LT$u64$GT$$GT$4cast17h87cc80ee32ae215bE
   -exclude-symbols:_ZN67_$LT$u32$u20$as$u20$compiler_builtins..int..CastInto$LT$i64$GT$$GT$4cast17hf3562228d527bff1E
   -exclude-symbols:_ZN68_$LT$u32$u20$as$u20$compiler_builtins..int..CastInto$LT$u128$GT$$GT$4cast17he048ad411b44f587E
   -exclude-symbols:_ZN68_$LT$u64$u20$as$u20$compiler_builtins..int..CastInto$LT$u128$GT$$GT$4cast17h3ae929c0d2f8613aE
   -exclude-symbols:_ZN68_$LT$u64$u20$as$u20$compiler_builtins..int..CastInto$LT$i128$GT$$GT$4cast17h73c1b981e1ba2a64E
   -exclude-symbols:_ZN53_$LT$usize$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shr17ha73d1175d499875dE
   -exclude-symbols:_ZN53_$LT$usize$u20$as$u20$compiler_builtins..int..Int$GT$11logical_shr17h3dab0862afd4e5eaE
   -exclude-symbols:_ZN53_$LT$isize$u20$as$u20$compiler_builtins..int..Int$GT$11logical_shr17h7887de1ae41d2721E
   -exclude-symbols:_ZN51_$LT$u64$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shr17h5ea9f96c5bbeb46fE
   -exclude-symbols:_ZN51_$LT$u64$u20$as$u20$compiler_builtins..int..Int$GT$11logical_shr17ha1afd2d4b1809666E
   -exclude-symbols:_ZN52_$LT$u128$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shr17heb3d28b73aa21cceE
   -exclude-symbols:_ZN52_$LT$u128$u20$as$u20$compiler_builtins..int..Int$GT$11logical_shr17h379f5cc101e94189E
   -exclude-symbols:_ZN53_$LT$isize$u20$as$u20$compiler_builtins..int..Int$GT$8abs_diff17h54c69fde3cfd099aE
   -exclude-symbols:_ZN70_$LT$isize$u20$as$u20$compiler_builtins..int..CastInto$LT$u128$GT$$GT$4cast17h014a3f7e6104ccceE
   -exclude-symbols:_ZN70_$LT$isize$u20$as$u20$compiler_builtins..int..CastInto$LT$i128$GT$$GT$4cast17h97cb812a8d82ff60E
   -exclude-symbols:_ZN68_$LT$i8$u20$as$u20$compiler_builtins..int..CastInto$LT$usize$GT$$GT$4cast17h11c49f451c3dcfc0E
   -exclude-symbols:_ZN66_$LT$i8$u20$as$u20$compiler_builtins..int..CastInto$LT$u16$GT$$GT$4cast17h9fd754b6b7975d1fE
   -exclude-symbols:_ZN66_$LT$i8$u20$as$u20$compiler_builtins..int..CastInto$LT$i16$GT$$GT$4cast17h1d9268761a0afbc9E
   -exclude-symbols:_ZN66_$LT$i8$u20$as$u20$compiler_builtins..int..CastInto$LT$u32$GT$$GT$4cast17h5ef9a8982c76438fE
   -exclude-symbols:_ZN68_$LT$i8$u20$as$u20$compiler_builtins..int..CastInto$LT$isize$GT$$GT$4cast17he80569622d4aa863E
   -exclude-symbols:_ZN66_$LT$i8$u20$as$u20$compiler_builtins..int..CastInto$LT$u64$GT$$GT$4cast17hd9f58a4fb8398845E
   -exclude-symbols:_ZN67_$LT$i8$u20$as$u20$compiler_builtins..int..CastInto$LT$u128$GT$$GT$4cast17h13db7a4e05d051d7E
   -exclude-symbols:_ZN69_$LT$i16$u20$as$u20$compiler_builtins..int..CastInto$LT$usize$GT$$GT$4cast17hfeaa853d3ae16e8eE
   -exclude-symbols:_ZN67_$LT$i16$u20$as$u20$compiler_builtins..int..CastInto$LT$u32$GT$$GT$4cast17hce788e278961ecfeE
   -exclude-symbols:_ZN67_$LT$i16$u20$as$u20$compiler_builtins..int..CastInto$LT$i32$GT$$GT$4cast17haed2bd875533d838E
   -exclude-symbols:_ZN69_$LT$i16$u20$as$u20$compiler_builtins..int..CastInto$LT$isize$GT$$GT$4cast17he310e89caf18c770E
   -exclude-symbols:_ZN67_$LT$i16$u20$as$u20$compiler_builtins..int..CastInto$LT$u64$GT$$GT$4cast17h6c3e65164a805eb2E
   -exclude-symbols:_ZN68_$LT$i16$u20$as$u20$compiler_builtins..int..CastInto$LT$u128$GT$$GT$4cast17h005e7a35ea118aa8E
   -exclude-symbols:_ZN69_$LT$i32$u20$as$u20$compiler_builtins..int..CastInto$LT$usize$GT$$GT$4cast17hb01ee84cf4fd3551E
   -exclude-symbols:_ZN69_$LT$i32$u20$as$u20$compiler_builtins..int..CastInto$LT$isize$GT$$GT$4cast17hdd9f9fecb3caaf48E
   -exclude-symbols:_ZN67_$LT$i32$u20$as$u20$compiler_builtins..int..CastInto$LT$u64$GT$$GT$4cast17h7a13e665c7b3fd70E
   -exclude-symbols:_ZN67_$LT$i32$u20$as$u20$compiler_builtins..int..CastInto$LT$i64$GT$$GT$4cast17h52df25662bafa311E
   -exclude-symbols:_ZN68_$LT$i32$u20$as$u20$compiler_builtins..int..CastInto$LT$u128$GT$$GT$4cast17hdafd7e1320702238E
   -exclude-symbols:_ZN68_$LT$i64$u20$as$u20$compiler_builtins..int..CastInto$LT$u128$GT$$GT$4cast17hefbd6e93c14aa2a3E
   -exclude-symbols:_ZN68_$LT$i64$u20$as$u20$compiler_builtins..int..CastInto$LT$i128$GT$$GT$4cast17h7f6d09a9bb04cd70E
   -exclude-symbols:_ZN53_$LT$usize$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shl17hd3eee012f9fcf548E
   -exclude-symbols:_ZN53_$LT$isize$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shl17h609275623f433d3bE
   -exclude-symbols:_ZN51_$LT$u64$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shl17h392dc7e35dc91371E
   -exclude-symbols:_ZN52_$LT$u128$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shl17ha60a86f224c456a1E
   -exclude-symbols:_ZN52_$LT$u16$u20$as$u20$compiler_builtins..int..DInt$GT$2lo17h7fa7c647867417b8E
   -exclude-symbols:_ZN52_$LT$u32$u20$as$u20$compiler_builtins..int..DInt$GT$2lo17h7a5bdf3fa755868dE
   -exclude-symbols:_ZN52_$LT$u64$u20$as$u20$compiler_builtins..int..DInt$GT$2lo17h50c0ccfcca1b17e9E
   -exclude-symbols:_ZN53_$LT$u128$u20$as$u20$compiler_builtins..int..DInt$GT$2lo17hed38b10ec9c788a3E
   -exclude-symbols:_ZN68_$LT$usize$u20$as$u20$compiler_builtins..int..CastInto$LT$u8$GT$$GT$4cast17hf2b77e17d8010131E
   -exclude-symbols:_ZN69_$LT$usize$u20$as$u20$compiler_builtins..int..CastInto$LT$u16$GT$$GT$4cast17h556b80f2f67c6b5cE
   -exclude-symbols:_ZN69_$LT$usize$u20$as$u20$compiler_builtins..int..CastInto$LT$u32$GT$$GT$4cast17ha03c8c9d24255facE
   -exclude-symbols:_ZN69_$LT$usize$u20$as$u20$compiler_builtins..int..CastInto$LT$i32$GT$$GT$4cast17h5299f7215c90f584E
   -exclude-symbols:_ZN68_$LT$usize$u20$as$u20$compiler_builtins..int..CastInto$LT$i8$GT$$GT$4cast17hf105a94486dac951E
   -exclude-symbols:_ZN68_$LT$isize$u20$as$u20$compiler_builtins..int..CastInto$LT$u8$GT$$GT$4cast17h4fe4013bf0d35df1E
   -exclude-symbols:_ZN69_$LT$usize$u20$as$u20$compiler_builtins..int..CastInto$LT$i16$GT$$GT$4cast17hfd5af1d06bfb4a50E
   -exclude-symbols:_ZN69_$LT$isize$u20$as$u20$compiler_builtins..int..CastInto$LT$u16$GT$$GT$4cast17h43253c42efd32441E
   -exclude-symbols:_ZN69_$LT$isize$u20$as$u20$compiler_builtins..int..CastInto$LT$u32$GT$$GT$4cast17hffa570566c4307feE
   -exclude-symbols:_ZN69_$LT$isize$u20$as$u20$compiler_builtins..int..CastInto$LT$i32$GT$$GT$4cast17h1a4e9d1d09d1b676E
   -exclude-symbols:_ZN66_$LT$u16$u20$as$u20$compiler_builtins..int..CastInto$LT$u8$GT$$GT$4cast17hc7a589554693e5a3E
   -exclude-symbols:_ZN66_$LT$u16$u20$as$u20$compiler_builtins..int..CastInto$LT$i8$GT$$GT$4cast17ha0559fc0ffd187a0E
   -exclude-symbols:_ZN66_$LT$i16$u20$as$u20$compiler_builtins..int..CastInto$LT$u8$GT$$GT$4cast17hb54f7a277d718584E
   -exclude-symbols:_ZN66_$LT$i16$u20$as$u20$compiler_builtins..int..CastInto$LT$i8$GT$$GT$4cast17hac6093995b373011E
   -exclude-symbols:_ZN66_$LT$u32$u20$as$u20$compiler_builtins..int..CastInto$LT$u8$GT$$GT$4cast17hb7bf0a9dbff21557E
   -exclude-symbols:_ZN67_$LT$u32$u20$as$u20$compiler_builtins..int..CastInto$LT$u16$GT$$GT$4cast17h119e0971cbbc977dE
   -exclude-symbols:_ZN67_$LT$u32$u20$as$u20$compiler_builtins..int..CastInto$LT$i16$GT$$GT$4cast17h4eb5a64f40b1f2ebE
   -exclude-symbols:_ZN66_$LT$u32$u20$as$u20$compiler_builtins..int..CastInto$LT$i8$GT$$GT$4cast17h746ad1d50ffd0dc4E
   -exclude-symbols:_ZN66_$LT$i32$u20$as$u20$compiler_builtins..int..CastInto$LT$u8$GT$$GT$4cast17heeb30d28b2dd270dE
   -exclude-symbols:_ZN67_$LT$i32$u20$as$u20$compiler_builtins..int..CastInto$LT$u16$GT$$GT$4cast17ha6fedad86295a517E
   -exclude-symbols:_ZN67_$LT$i32$u20$as$u20$compiler_builtins..int..CastInto$LT$i16$GT$$GT$4cast17h0d6f40fe410319e7E
   -exclude-symbols:_ZN68_$LT$isize$u20$as$u20$compiler_builtins..int..CastInto$LT$i8$GT$$GT$4cast17h53aeaed04dbe1b9dE
   -exclude-symbols:_ZN66_$LT$u64$u20$as$u20$compiler_builtins..int..CastInto$LT$u8$GT$$GT$4cast17h76a1329cf944422dE
   -exclude-symbols:_ZN69_$LT$isize$u20$as$u20$compiler_builtins..int..CastInto$LT$i16$GT$$GT$4cast17hcfd442bc144f9574E
   -exclude-symbols:_ZN67_$LT$u64$u20$as$u20$compiler_builtins..int..CastInto$LT$u16$GT$$GT$4cast17h362a4d86d21e941bE
   -exclude-symbols:_ZN67_$LT$u64$u20$as$u20$compiler_builtins..int..CastInto$LT$u32$GT$$GT$4cast17hb87f88331dc92a04E
   -exclude-symbols:_ZN67_$LT$u64$u20$as$u20$compiler_builtins..int..CastInto$LT$i32$GT$$GT$4cast17hc47ca379b09d7fe0E
   -exclude-symbols:_ZN66_$LT$u64$u20$as$u20$compiler_builtins..int..CastInto$LT$i8$GT$$GT$4cast17h4e4e03092addaa5eE
   -exclude-symbols:_ZN66_$LT$i64$u20$as$u20$compiler_builtins..int..CastInto$LT$u8$GT$$GT$4cast17hb4ccd95e8362ea65E
   -exclude-symbols:_ZN67_$LT$u64$u20$as$u20$compiler_builtins..int..CastInto$LT$i16$GT$$GT$4cast17h2bc02f926154037bE
   -exclude-symbols:_ZN67_$LT$i64$u20$as$u20$compiler_builtins..int..CastInto$LT$u16$GT$$GT$4cast17h1fd68aa975116f37E
   -exclude-symbols:_ZN67_$LT$i64$u20$as$u20$compiler_builtins..int..CastInto$LT$u32$GT$$GT$4cast17h8683eb95c457bfa9E
   -exclude-symbols:_ZN67_$LT$i64$u20$as$u20$compiler_builtins..int..CastInto$LT$i32$GT$$GT$4cast17h564d4707278e4a42E
   -exclude-symbols:_ZN70_$LT$u128$u20$as$u20$compiler_builtins..int..CastInto$LT$usize$GT$$GT$4cast17hda1f975b82aad89aE
   -exclude-symbols:_ZN70_$LT$u128$u20$as$u20$compiler_builtins..int..CastInto$LT$isize$GT$$GT$4cast17h3cd8f421e176b2c2E
   -exclude-symbols:_ZN67_$LT$u128$u20$as$u20$compiler_builtins..int..CastInto$LT$u8$GT$$GT$4cast17hf53472482bb3a527E
   -exclude-symbols:_ZN68_$LT$u128$u20$as$u20$compiler_builtins..int..CastInto$LT$u16$GT$$GT$4cast17h8b3cfe62bc660270E
   -exclude-symbols:_ZN68_$LT$u128$u20$as$u20$compiler_builtins..int..CastInto$LT$u32$GT$$GT$4cast17h14e8696f9c183f3fE
   -exclude-symbols:_ZN68_$LT$u128$u20$as$u20$compiler_builtins..int..CastInto$LT$u64$GT$$GT$4cast17he73e3e810ef1b90cE
   -exclude-symbols:_ZN68_$LT$u128$u20$as$u20$compiler_builtins..int..CastInto$LT$i64$GT$$GT$4cast17h29df009acd8c7016E
   -exclude-symbols:_ZN70_$LT$i128$u20$as$u20$compiler_builtins..int..CastInto$LT$usize$GT$$GT$4cast17h9905e74197f553ffE
   -exclude-symbols:_ZN70_$LT$i128$u20$as$u20$compiler_builtins..int..CastInto$LT$isize$GT$$GT$4cast17h7061d86a2ecd96b0E
   -exclude-symbols:_ZN67_$LT$u128$u20$as$u20$compiler_builtins..int..CastInto$LT$i8$GT$$GT$4cast17h83ae9b9b0eeefb53E
   -exclude-symbols:_ZN67_$LT$i128$u20$as$u20$compiler_builtins..int..CastInto$LT$u8$GT$$GT$4cast17hf4cc2d6d58c71427E
   -exclude-symbols:_ZN68_$LT$u128$u20$as$u20$compiler_builtins..int..CastInto$LT$i16$GT$$GT$4cast17hf6eff9f382891692E
   -exclude-symbols:_ZN68_$LT$i128$u20$as$u20$compiler_builtins..int..CastInto$LT$u16$GT$$GT$4cast17h463b870254bcea43E
   -exclude-symbols:_ZN68_$LT$u128$u20$as$u20$compiler_builtins..int..CastInto$LT$i32$GT$$GT$4cast17h8f234714323f11b9E
   -exclude-symbols:_ZN68_$LT$i128$u20$as$u20$compiler_builtins..int..CastInto$LT$u32$GT$$GT$4cast17hcc154d2aaa16d0cdE
   -exclude-symbols:_ZN68_$LT$i128$u20$as$u20$compiler_builtins..int..CastInto$LT$u64$GT$$GT$4cast17h5ad7d4f317fdebf4E
   -exclude-symbols:_ZN68_$LT$i128$u20$as$u20$compiler_builtins..int..CastInto$LT$i64$GT$$GT$4cast17h38f4b39004cadd3dE
   -exclude-symbols:_ZN53_$LT$usize$u20$as$u20$compiler_builtins..int..Int$GT$11rotate_left17h8da51dbd3de3d450E
   -exclude-symbols:_ZN53_$LT$isize$u20$as$u20$compiler_builtins..int..Int$GT$11rotate_left17hd3b6b628fd7a596cE
   -exclude-symbols:_ZN51_$LT$u64$u20$as$u20$compiler_builtins..int..Int$GT$11rotate_left17h39b8fdd8a00a3dc7E
   -exclude-symbols:_ZN52_$LT$u128$u20$as$u20$compiler_builtins..int..Int$GT$11rotate_left17hb2cee8b22867a931E
   -exclude-symbols:_ZN53_$LT$usize$u20$as$u20$compiler_builtins..int..Int$GT$15overflowing_add17hf8c33d663e357949E
   -exclude-symbols:_ZN53_$LT$isize$u20$as$u20$compiler_builtins..int..Int$GT$15overflowing_add17h147567346d40cebcE
   -exclude-symbols:_ZN51_$LT$u32$u20$as$u20$compiler_builtins..int..Int$GT$11rotate_left17h1045780f8e4c8072E
   -exclude-symbols:_ZN53_$LT$usize$u20$as$u20$compiler_builtins..int..Int$GT$7is_zero17hcfc1e08f28ff1093E
   -exclude-symbols:_ZN50_$LT$u8$u20$as$u20$compiler_builtins..int..Int$GT$7is_zero17h839b802e74facdc2E
   -exclude-symbols:_ZN51_$LT$u16$u20$as$u20$compiler_builtins..int..Int$GT$7is_zero17he9838b0e14b87124E
   -exclude-symbols:_ZN51_$LT$u32$u20$as$u20$compiler_builtins..int..Int$GT$7is_zero17h54f3b881603d25d8E
   -exclude-symbols:_ZN53_$LT$isize$u20$as$u20$compiler_builtins..int..Int$GT$7is_zero17he0d86483f0bce9f7E
   -exclude-symbols:_ZN51_$LT$u64$u20$as$u20$compiler_builtins..int..Int$GT$7is_zero17hd9b0fca03912606dE
   -exclude-symbols:_ZN52_$LT$u128$u20$as$u20$compiler_builtins..int..Int$GT$7is_zero17h3ebb2d38a06ef320E
   -exclude-symbols:_ZN50_$LT$u8$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shr17h06b9cce4b9083005E
   -exclude-symbols:_ZN50_$LT$u8$u20$as$u20$compiler_builtins..int..Int$GT$11logical_shr17hc2442dd102ece759E
   -exclude-symbols:_ZN51_$LT$u16$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shr17h3ccd46897563e4adE
   -exclude-symbols:_ZN51_$LT$u16$u20$as$u20$compiler_builtins..int..Int$GT$11logical_shr17h9668282d5eee43ceE
   -exclude-symbols:_ZN53_$LT$isize$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shr17h412589d53290e62dE
   -exclude-symbols:_ZN53_$LT$usize$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_sub17ha46286e11ef56c93E
   -exclude-symbols:_ZN50_$LT$u8$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_sub17h64ce9c38896ae41fE
   -exclude-symbols:_ZN51_$LT$u16$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_sub17h4f9aa91d93e41cbeE
   -exclude-symbols:_ZN51_$LT$u32$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_sub17h75948d2cf546f8b1E
   -exclude-symbols:_ZN53_$LT$isize$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_sub17ha076ca6d2b7845adE
   -exclude-symbols:_ZN51_$LT$u64$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_sub17h94d3d4f45aba4b20E
   -exclude-symbols:_ZN52_$LT$u128$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_sub17h15f43809b4a0a4daE
   -exclude-symbols:_ZN51_$LT$u32$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shl17hacdd319c9a12214cE
   -exclude-symbols:_ZN50_$LT$u8$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shl17hb328cff2bf51530bE
   -exclude-symbols:_ZN51_$LT$u16$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_shl17h422edd4e4bb7169bE
   -exclude-symbols:_ZN53_$LT$usize$u20$as$u20$compiler_builtins..int..Int$GT$8abs_diff17h461a56f55041ac27E
   -exclude-symbols:_ZN51_$LT$u8$u20$as$u20$compiler_builtins..int..HInt$GT$8widen_hi17h257e5b4c4bd8e980E
   -exclude-symbols:_ZN52_$LT$u16$u20$as$u20$compiler_builtins..int..HInt$GT$8widen_hi17h3e9e5f8b39f89e3bE
   -exclude-symbols:_ZN52_$LT$u32$u20$as$u20$compiler_builtins..int..HInt$GT$8widen_hi17h71caefd2f78d64ddE
   -exclude-symbols:_ZN52_$LT$u64$u20$as$u20$compiler_builtins..int..HInt$GT$8widen_hi17h72f543609ba76392E
   -exclude-symbols:_ZN53_$LT$usize$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_mul17he81b7571c860fdfaE
   -exclude-symbols:_ZN50_$LT$u8$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_mul17h8a9dccab71d3e9cdE
   -exclude-symbols:_ZN51_$LT$u16$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_mul17hadff955a65b54c0cE
   -exclude-symbols:_ZN51_$LT$u32$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_mul17h4806e3272c7e403fE
   -exclude-symbols:_ZN53_$LT$isize$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_mul17h2b1bd909e2c0800bE
   -exclude-symbols:_ZN51_$LT$u64$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_mul17hf885afd90bacfb2bE
   -exclude-symbols:_ZN52_$LT$u128$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_mul17h716a30df9521d50aE
   -exclude-symbols:_ZN53_$LT$usize$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_add17h72f3e85318d51fe9E
   -exclude-symbols:_ZN50_$LT$u8$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_add17hbf81172cd1d522a7E
   -exclude-symbols:_ZN51_$LT$u16$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_add17h99e2bde87a126858E
   -exclude-symbols:_ZN51_$LT$u32$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_add17h3b0a00323dab879fE
   -exclude-symbols:_ZN53_$LT$isize$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_add17h3b4fa11f2476d70eE
   -exclude-symbols:_ZN51_$LT$u64$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_add17hf1afb75cf35a3d40E
   -exclude-symbols:_ZN52_$LT$u128$u20$as$u20$compiler_builtins..int..Int$GT$12wrapping_add17h68e126353fbb1c3aE
   -exclude-symbols:_ZN52_$LT$u16$u20$as$u20$compiler_builtins..int..DInt$GT$10from_lo_hi17h83b0f9dcea673819E
   -exclude-symbols:_ZN52_$LT$u32$u20$as$u20$compiler_builtins..int..DInt$GT$10from_lo_hi17hd3cc7080dec5b72bE
   -exclude-symbols:_ZN52_$LT$u64$u20$as$u20$compiler_builtins..int..DInt$GT$10from_lo_hi17h4a1846c9d413e5e2E
   -exclude-symbols:_ZN53_$LT$u128$u20$as$u20$compiler_builtins..int..DInt$GT$10from_lo_hi17hfacd8e7f21f67010E

   Linker Directives
   -----------------
   -exclude-symbols:_ZN17compiler_builtins3int4sdiv11__divmodsi417hf38fe17d49b7637eE
   -exclude-symbols:_ZN17compiler_builtins3int4sdiv8__divsi317h3d3ce4a8412273e8E
   -exclude-symbols:_ZN17compiler_builtins3int4sdiv8__modsi317h2dec38a4a53bfc58E
   -exclude-symbols:_ZN17compiler_builtins3int4sdiv11__divmoddi417hfe0ccc901ab1dfd6E
   -exclude-symbols:_ZN17compiler_builtins3int4sdiv8__divdi317h1901a83ef0d39bf8E
   -exclude-symbols:_ZN17compiler_builtins3int4sdiv8__moddi317h96c8681b2daca6f3E
   -exclude-symbols:_ZN17compiler_builtins3int4sdiv11__divmodti417hd3d528c12e3be196E
   -exclude-symbols:_ZN17compiler_builtins3int4sdiv8__divti317h333c518a828889d1E
   -exclude-symbols:_ZN17compiler_builtins3int4sdiv8__modti317hacb8f0df0b47157eE

   Linker Directives
   -----------------
   -exclude-symbols:__floatdidf

   Linker Directives
   -----------------
   -exclude-symbols:__ltdf2

   Linker Directives
   -----------------
   -exclude-symbols:__muldf3

   Linker Directives
   -----------------
   -exclude-symbols:__lshrdi3

   Linker Directives
   -----------------
   -exclude-symbols:__fixunssfti

   Linker Directives
   -----------------
   -exclude-symbols:_ZN17compiler_builtins3int3mul5UMulo4mulo17he1cf3bcf1c3f82aeE.llvm.12294291525361866871
   -exclude-symbols:_ZN17compiler_builtins3int3mul8__muldi317h149af4e3c6e6760aE
   -exclude-symbols:_ZN17compiler_builtins3int3mul8__multi317h2dfdcd8123025966E
   -exclude-symbols:_ZN17compiler_builtins3int3mul9__mulosi417h3a053544f8c8b33aE
   -exclude-symbols:_ZN17compiler_builtins3int3mul9__mulodi417hd5998607c7312647E
   -exclude-symbols:_ZN17compiler_builtins3int3mul9__muloti417h969cdcf3ff67bf71E
   -exclude-symbols:_ZN17compiler_builtins3int3mul16__rust_i128_mulo17h58a0dc02754f245bE
   -exclude-symbols:_ZN17compiler_builtins3int3mul16__rust_u128_mulo17h43dde3ca56d78155E

   Linker Directives
   -----------------
   -exclude-symbols:__udivmodti4

   Linker Directives
   -----------------
   -exclude-symbols:_ZN17compiler_builtins3mem5impls9rep_param17h8b40b5af50b1eac5E

   Linker Directives
   -----------------
   -exclude-symbols:__fixdfdi

   Linker Directives
   -----------------
   -exclude-symbols:__divti3

   Linker Directives
   -----------------
   -exclude-symbols:__ashldi3

   Linker Directives
   -----------------
   -exclude-symbols:__muldi3

   Linker Directives
   -----------------
   -exclude-symbols:__fixsfdi

   Linker Directives
   -----------------
   -exclude-symbols:_ZN17compiler_builtins3mem6memcpy17h8b9af081503470dcE
   -exclude-symbols:_ZN17compiler_builtins3mem7memmove17h092b1207c3a7c7a8E
   -exclude-symbols:_ZN17compiler_builtins3mem6memset17h0b2e88e3c285ece5E
   -exclude-symbols:_ZN17compiler_builtins3mem6memcmp17hb62f03aed894126dE
   -exclude-symbols:_ZN17compiler_builtins3mem4bcmp17hac4cd6ff040ca104E
   -exclude-symbols:_ZN17compiler_builtins3mem6strlen17h314f7d47a0f666f6E
   -exclude-symbols:_ZN17compiler_builtins3mem40__llvm_memcpy_element_unordered_atomic_117h421b0bd173b92466E
   -exclude-symbols:_ZN17compiler_builtins3mem40__llvm_memcpy_element_unordered_atomic_217hfd16645532c48e09E
   -exclude-symbols:_ZN17compiler_builtins3mem40__llvm_memcpy_element_unordered_atomic_417h7137363db575006dE
   -exclude-symbols:_ZN17compiler_builtins3mem40__llvm_memcpy_element_unordered_atomic_817h1bea3c14475a5f05E
   -exclude-symbols:_ZN17compiler_builtins3mem41__llvm_memmove_element_unordered_atomic_117hf1b988265eab6d22E
   -exclude-symbols:_ZN17compiler_builtins3mem41__llvm_memmove_element_unordered_atomic_217hbcd7e9062bd1b722E
   -exclude-symbols:_ZN17compiler_builtins3mem41__llvm_memmove_element_unordered_atomic_417h21ead8447a320b3cE
   -exclude-symbols:_ZN17compiler_builtins3mem41__llvm_memmove_element_unordered_atomic_817hf798ade4d366e9f1E
   -exclude-symbols:_ZN17compiler_builtins3mem40__llvm_memset_element_unordered_atomic_117hd60dcb7c780dddedE
   -exclude-symbols:_ZN17compiler_builtins3mem40__llvm_memset_element_unordered_atomic_217h7453034f964b853cE
   -exclude-symbols:_ZN17compiler_builtins3mem40__llvm_memset_element_unordered_atomic_417h1c776efd0396498bE
   -exclude-symbols:_ZN17compiler_builtins3mem40__llvm_memset_element_unordered_atomic_817ha2ebc07cc59a189bE

   Linker Directives
   -----------------
   -exclude-symbols:_ZN17compiler_builtins5float4conv13__floatunsisf17h40d628b4257fd865E
   -exclude-symbols:_ZN17compiler_builtins5float4conv13__floatunsidf17h6df9a784a3ca7366E
   -exclude-symbols:_ZN17compiler_builtins5float4conv13__floatundisf17hde99c827a80a3b95E
   -exclude-symbols:_ZN17compiler_builtins5float4conv13__floatundidf17hd4bf199e078d8180E
   -exclude-symbols:_ZN17compiler_builtins5float4conv13__floatuntisf17h147217ceb7a01522E
   -exclude-symbols:_ZN17compiler_builtins5float4conv13__floatuntidf17h394e14bba301ce0fE
   -exclude-symbols:_ZN17compiler_builtins5float4conv11__floatsisf17he880276807739803E
   -exclude-symbols:_ZN17compiler_builtins5float4conv11__floatsidf17heb081f45d0dfafd0E
   -exclude-symbols:_ZN17compiler_builtins5float4conv11__floatdisf17h48f2098f805b0fe4E
   -exclude-symbols:_ZN17compiler_builtins5float4conv11__floatdidf17h4094213afb084875E
   -exclude-symbols:_ZN17compiler_builtins5float4conv11__floattisf17h2286fe0aefdc1fd6E
   -exclude-symbols:_ZN17compiler_builtins5float4conv11__floattidf17h6f1524d504ae7b16E
   -exclude-symbols:_ZN17compiler_builtins5float4conv12__fixunssfsi17hd9dc2dd00317bb9dE
   -exclude-symbols:_ZN17compiler_builtins5float4conv12__fixunssfdi17h039ed174c55b5717E
   -exclude-symbols:_ZN17compiler_builtins5float4conv12__fixunssfti17h32a27a90426c3967E
   -exclude-symbols:_ZN17compiler_builtins5float4conv12__fixunsdfsi17hd3460f44544992f2E
   -exclude-symbols:_ZN17compiler_builtins5float4conv12__fixunsdfdi17h25047e266f9c1481E
   -exclude-symbols:_ZN17compiler_builtins5float4conv12__fixunsdfti17h5072c6bb37227cd6E
   -exclude-symbols:_ZN17compiler_builtins5float4conv9__fixsfsi17h2562541c008cbef6E
   -exclude-symbols:_ZN17compiler_builtins5float4conv9__fixsfdi17h5d1aff09c0db79e2E
   -exclude-symbols:_ZN17compiler_builtins5float4conv9__fixsfti17h76ab5132778e8062E
   -exclude-symbols:_ZN17compiler_builtins5float4conv9__fixdfsi17hb9d1164ae7afc0dcE
   -exclude-symbols:_ZN17compiler_builtins5float4conv9__fixdfdi17h42f84fc024ce3c7bE
   -exclude-symbols:_ZN17compiler_builtins5float4conv9__fixdfti17h4a60abfebf04f288E

   Linker Directives
   -----------------
   -exclude-symbols:__ashrdi3

   Linker Directives
   -----------------
   -exclude-symbols:__mulsf3

   Linker Directives
   -----------------
   -exclude-symbols:_ZN17compiler_builtins5float6extend13__extendsfdf217h571e693fe8eaa4f4E

   Linker Directives
   -----------------
   -exclude-symbols:_ZN17compiler_builtins3int6addsub7UAddSub4usub17h3b9d6a7fefd1c2ecE.llvm.3664432139947906414
   -exclude-symbols:_ZN17compiler_builtins3int6addsub6AddSub3add17h215cbbba6a431904E.llvm.3664432139947906414
   -exclude-symbols:_ZN17compiler_builtins3int6addsub15__rust_i128_add17h9b78bb5888d2e972E
   -exclude-symbols:_ZN17compiler_builtins3int6addsub16__rust_i128_addo17h8f62f7ee4e231ef8E
   -exclude-symbols:_ZN17compiler_builtins3int6addsub16__rust_u128_addo17hba84145d68aa5878E
   -exclude-symbols:_ZN17compiler_builtins3int6addsub15__rust_i128_sub17hd431236030684e3aE
   -exclude-symbols:_ZN17compiler_builtins3int6addsub16__rust_i128_subo17h76e0ac843e1e1a0aE
   -exclude-symbols:_ZN17compiler_builtins3int6addsub16__rust_u128_subo17h71fade3682912d49E
   -exclude-symbols:_ZN17compiler_builtins3int6addsub15__rust_u128_sub17h1811b2f9db66a07fE
   -exclude-symbols:_ZN17compiler_builtins3int6addsub6AddSub3add17h608b7f1815cfe9d9E.llvm.3664432139947906414
   -exclude-symbols:_ZN17compiler_builtins3int6addsub15__rust_u128_add17ha41bfae2eed943bdE

   Linker Directives
   -----------------
   -exclude-symbols:__fixunssfsi

   Linker Directives
   -----------------
   -exclude-symbols:__udivmodsi4

   Linker Directives
   -----------------
   -exclude-symbols:_ZN17compiler_builtins5float3sub8__subsf317h058514f4ad6ce136E
   -exclude-symbols:_ZN17compiler_builtins5float3sub8__subdf317h33d98f9e6f21b699E

   Linker Directives
   -----------------
   -exclude-symbols:__udivmoddi4

   Linker Directives
   -----------------
   -exclude-symbols:__udivdi3

   Linker Directives
   -----------------
   -exclude-symbols:__floatsisf

   Linker Directives
   -----------------
   -exclude-symbols:__lesf2

   Linker Directives
   -----------------
   -exclude-symbols:__ashlti3

   Linker Directives
   -----------------
   -exclude-symbols:__modti3

   Linker Directives
   -----------------
   -exclude-symbols:__rust_i128_sub

   Linker Directives
   -----------------
   -exclude-symbols:__gesf2

   Linker Directives
   -----------------
   -exclude-symbols:__mulosi4

   Linker Directives
   -----------------
   -exclude-symbols:__rust_i128_add

   Linker Directives
   -----------------
   -exclude-symbols:__llvm_memcpy_element_unordered_atomic_2

   Linker Directives
   -----------------
   -exclude-symbols:__floattidf

   Linker Directives
   -----------------
   -exclude-symbols:__rust_u128_addo

   Linker Directives
   -----------------
   -exclude-symbols:__rust_i128_addo

   Linker Directives
   -----------------
   -exclude-symbols:__divdf3

   Linker Directives
   -----------------
   -exclude-symbols:__rust_u128_mulo

   Linker Directives
   -----------------
   -exclude-symbols:_ZN107_$LT$compiler_builtins..macros..win64_128bit_abi_hack..U64x2$u20$as$u20$core..convert..From$LT$i128$GT$$GT$4from17h61dba8575ebe2327E
   -exclude-symbols:_ZN107_$LT$compiler_builtins..macros..win64_128bit_abi_hack..U64x2$u20$as$u20$core..convert..From$LT$u128$GT$$GT$4from17h3a680de0439f2955E

   Linker Directives
   -----------------
   -exclude-symbols:__powisf2

   Linker Directives
   -----------------
   -exclude-symbols:__llvm_memset_element_unordered_atomic_4

   Linker Directives
   -----------------
   -exclude-symbols:__multi3

   Linker Directives
   -----------------
   -exclude-symbols:__rust_u128_sub

   Linker Directives
   -----------------
   -exclude-symbols:__floatuntidf

   Linker Directives
   -----------------
   -exclude-symbols:__llvm_memcpy_element_unordered_atomic_4

   Linker Directives
   -----------------
   -exclude-symbols:_ZN17compiler_builtins5float3pow9__powisf217hc3d5111d5e534594E
   -exclude-symbols:_ZN17compiler_builtins5float3pow9__powidf217he4f5e8b1f3bb582fE

   Linker Directives
   -----------------
   -exclude-symbols:__ashrsi3

   Linker Directives
   -----------------
   -exclude-symbols:__divsi3

   Linker Directives
   -----------------
   -exclude-symbols:__llvm_memcpy_element_unordered_atomic_1

   Linker Directives
   -----------------
   -exclude-symbols:__nesf2

   Linker Directives
   -----------------
   -exclude-symbols:_ZN17compiler_builtins3int19specialized_div_rem12u128_div_rem17hdcf30e1742f4330dE
   -exclude-symbols:_ZN17compiler_builtins3int19specialized_div_rem11u64_div_rem17h40075ad64ab213dbE
   -exclude-symbols:_ZN17compiler_builtins3int19specialized_div_rem11u32_div_rem17h5f1e7a70b2e81cf1E

   Linker Directives
   -----------------
   -exclude-symbols:__gtsf2

   Linker Directives
   -----------------
   -exclude-symbols:__fixsfsi

   Linker Directives
   -----------------
   -exclude-symbols:__umodsi3

   Linker Directives
   -----------------
   -exclude-symbols:__fixunssfdi

   Linker Directives
   -----------------
   -exclude-symbols:__gedf2

   Linker Directives
   -----------------
   -exclude-symbols:__fixsfti

   Linker Directives
   -----------------
   -exclude-symbols:__muloti4

   Linker Directives
   -----------------
   -exclude-symbols:__floatundisf

   Linker Directives
   -----------------
   -exclude-symbols:__llvm_memcpy_element_unordered_atomic_8

   Linker Directives
   -----------------
   -exclude-symbols:__floatundidf

   Linker Directives
   -----------------
   -exclude-symbols:__adddf3

   Linker Directives
   -----------------
   -exclude-symbols:__modsi3

   Linker Directives
   -----------------
   -exclude-symbols:__floatsidf

   Linker Directives
   -----------------
   -exclude-symbols:__umoddi3

   Linker Directives
   -----------------
   -exclude-symbols:__floatuntisf

   Linker Directives
   -----------------
   -exclude-symbols:__lshrti3

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