# バイナリビューアを使ってクラスファイルを読んでみよう！

* セッション資料
    * [バイナリビューアを使ってクラスファイルを読んでみよう #jjug_ccc](https://speakerdeck.com/yujisoftware/bainaribiyuawoshi-tutekurasuhuairuwodu-ndemiyou-number-jjug-ccc)
* ソースコード
    * [Main.java](./Main.java)
* クラスファイル
    * [Main.class](./Main.class)
* javap 出力
    * [Main.javap](./Main.javap)

## クラスファイルのバイナリー

```
00000000  ca fe ba be 00 00 00 41  00 26 0a 00 02 00 03 07  |.......A.&......|
00000010  00 04 0c 00 05 00 06 01  00 10 6a 61 76 61 2f 6c  |..........java/l|
00000020  61 6e 67 2f 4f 62 6a 65  63 74 01 00 06 3c 69 6e  |ang/Object...<in|
00000030  69 74 3e 01 00 03 28 29  56 09 00 08 00 09 07 00  |it>...()V.......|
00000040  0a 0c 00 0b 00 0c 01 00  10 6a 61 76 61 2f 6c 61  |.........java/la|
00000050  6e 67 2f 53 79 73 74 65  6d 01 00 03 6f 75 74 01  |ng/System...out.|
00000060  00 15 4c 6a 61 76 61 2f  69 6f 2f 50 72 69 6e 74  |..Ljava/io/Print|
00000070  53 74 72 65 61 6d 3b 08  00 0e 01 00 15 e9 a0 91  |Stream;.........|
00000080  e5 bc b5 e3 82 8a e3 81  be e3 81 99 ed a0 bd ed  |................|
00000090  b9 82 0a 00 10 00 11 07  00 12 0c 00 13 00 14 01  |................|
000000a0  00 13 6a 61 76 61 2f 69  6f 2f 50 72 69 6e 74 53  |..java/io/PrintS|
000000b0  74 72 65 61 6d 01 00 07  70 72 69 6e 74 6c 6e 01  |tream...println.|
000000c0  00 15 28 4c 6a 61 76 61  2f 6c 61 6e 67 2f 53 74  |..(Ljava/lang/St|
000000d0  72 69 6e 67 3b 29 56 07  00 16 01 00 04 4d 61 69  |ring;)V......Mai|
000000e0  6e 01 00 07 54 57 49 54  54 45 52 01 00 12 4c 6a  |n...TWITTER...Lj|
000000f0  61 76 61 2f 6c 61 6e 67  2f 53 74 72 69 6e 67 3b  |ava/lang/String;|
00000100  01 00 0d 43 6f 6e 73 74  61 6e 74 56 61 6c 75 65  |...ConstantValue|
00000110  08 00 1b 01 00 0d 40 59  75 6a 69 53 6f 66 74 77  |......@YujiSoftw|
00000120  61 72 65 01 00 03 41 47  45 01 00 01 4a 05 00 00  |are...AGE...J...|
00000130  00 00 00 00 00 26 01 00  04 43 6f 64 65 01 00 0f  |.....&...Code...|
00000140  4c 69 6e 65 4e 75 6d 62  65 72 54 61 62 6c 65 01  |LineNumberTable.|
00000150  00 04 6d 61 69 6e 01 00  16 28 5b 4c 6a 61 76 61  |..main...([Ljava|
00000160  2f 6c 61 6e 67 2f 53 74  72 69 6e 67 3b 29 56 01  |/lang/String;)V.|
00000170  00 0a 53 6f 75 72 63 65  46 69 6c 65 01 00 09 4d  |..SourceFile...M|
00000180  61 69 6e 2e 6a 61 76 61  00 21 00 15 00 02 00 00  |ain.java.!......|
00000190  00 02 00 19 00 17 00 18  00 01 00 19 00 00 00 02  |................|
000001a0  00 1a 00 19 00 1c 00 1d  00 01 00 19 00 00 00 02  |................|
000001b0  00 1e 00 02 00 01 00 05  00 06 00 01 00 20 00 00  |............. ..|
000001c0  00 1d 00 01 00 01 00 00  00 05 2a b7 00 01 b1 00  |..........*.....|
000001d0  00 00 01 00 21 00 00 00  06 00 01 00 00 00 01 00  |....!...........|
000001e0  09 00 22 00 23 00 01 00  20 00 00 00 25 00 02 00  |..".#... ...%...|
000001f0  01 00 00 00 09 b2 00 07  12 0d b6 00 0f b1 00 00  |................|
00000200  00 01 00 21 00 00 00 0a  00 02 00 00 00 06 00 08  |...!............|
00000210  00 07 00 01 00 24 00 00  00 02 00 25              |.....$.....%|
0000021c
```

## 解析データ

* magic: `ca fe ba be`
* minor_version: `00 00`
* major_version: `00 41`
* constant_pool_count: `00 26`
* constant_pool:
    * #0001:
        * tag: `0a` (CONSTANT_Methodref)
        * class_index: `00 02`
        * name_and_type_index: `00 03`
    * #0002:
        * tag: `07` (CONSTANT_Class)
        * name_index: `00 04`
    * #0003:
        * tag: `0c` (CONSTANT_NameAndType)
        * name_index: `00 05`
        * descriptor_index: `00 06`
    * #0004:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 10`
        * bytes: `6a 61 76 61 2f 6c 61 6e 67 2f 4f 62 6a 65 63 74` (java/lang/Object)
    * #0005:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 06`
        * bytes: `3c 69 6e 69 74 3e` (<init>)
    * #0006:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 03`
        * bytes: `28 29 56` (()V)
    * #0007:
        * tag: `09` (CONSTANT_Fieldref)
        * class_index: `00 08`
        * name_and_type_index: `00 09`
    * #0008:
        * tag: `07` (CONSTANT_Class)
        * name_index: `00 0a`
    * #0009:
        * tag: `0c` (CONSTANT_Fieldref)
        * class_index: `00 0b`
        * name_and_type_index: `00 0c`
    * #000A:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 10`
        * bytes: `6a 61 76 61 2f 6c 61 6e 67 2f 53 79 73 74 65 6d` (java/lang/System)
    * #000B:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 03`
        * bytes: `6f 75 74` (out)
    * #000C:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 15`
        * bytes: `4c 6a 61 76 61 2f 69 6f 2f 50 72 69 6e 74 53 74 72 65 61 6d 3b` (Ljava/io/PrintStream;)
    * #000D:
        * tag: `08` (CONSTANT_String)
        * string_index: `00 0e`
    * #000E:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 15`
        * bytes: `e9 a0 91 e5 bc b5 e3 82 8a e3 81 be e3 81 99 ed a0 bd ed b9 82` (頑張ります🙂)
    * #000F:
        * tag: `0a` (CONSTANT_NameAndType)
        * class_index: `00 10`
        * descriptor_index: `00 11`
    * #0010:
         * tag: `07` (CONSTANT_Class)
        * name_index: `00 12`
    * #0011:
        * tag: `0c` (CONSTANT_NameAndType)
        * name_index: `00 13`
        * descriptor_index: `00 14`
    * #0012:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 13`
        * bytes: `6a 61 76 61 2f 69 6f 2f 50 72 69 6e 74 53 74 72 65 61 6d` (java/io/PrintStream)
    * #0013:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 07`
        * bytes: `70 72 69 6e 74 6c 6e` (println)
    * #0014:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 15`
        * bytes: `28 4c 6a 61 76 61 2f 6c 61 6e 67 2f 53 74 72 69 6e 67 3b 29 56` ((Ljava/lang/String;)V)
    * #0015:
        * tag: `07` (CONSTANT_Class)
        * name_index: `00 16`
    * #0016:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 04`
        * bytes: `4d 61 69 6e` (Main)
    * #0017:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 07`
        * bytes: `54 57 49 54 54 45 52` (TWITTER)
    * #0018:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 12`
        * bytes: `4c 6a 61 76 61 2f 6c 61 6e 67 2f 53 74 72 69 6e 67 3b` (Ljava/lang/String;)
    * #0019:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 0d`
        * bytes: `43 6f 6e 73 74 61 6e 74 56 61 6c 75 65` (ConstantValue)
    * #001A:
        * tag: `08` (CONSTANT_String)
        * string_index: `00 1b`
    * #001B:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 0d`
        * bytes: `40 59 75 6a 69 53 6f 66 74 77 61 72 65` (@YujiSoftware)
    * #001C:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 03`
        * bytes: `41 47 45` (AGE)
    * #001D:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 01`
        * bytes: `4a` (J)
    * #001E:
        * tag: `05` (CONSTANT_Long)
        * high_bytes: `00 00 00 00`
        * low_bytes: `00 00 00 26`
    * #0020:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 04`
        * bytes: `43 6f 64 65` (Code)
    * #0021:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 0f`
        * bytes: `4c 69 6e 65 4e 75 6d 62 65 72 54 61 62 6c 65` (LineNumberTable)
    * #0022:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 04`
        * bytes: `6d 61 69 6e` (main)
    * #0023:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 16`
        * bytes: `28 5b 4c 6a 61 76 61 2f 6c 61 6e 67 2f 53 74 72 69 6e 67 3b 29 56` (([Ljava/lang/String;)V)
    * #0024:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 0a`
        * bytes: `53 6f 75 72 63 65 46 69 6c 65` (SourceFile)
    * #0025:
        * tag: `01` (CONSTANT_Utf8)
        * length: `00 09`
        * bytes: `4d 61 69 6e 2e 6a 61 76 61` (Main.java)
* access_flags: `00 21`
* this_class: `00 15`
* super_class: `00 02`
* interfaces_count: `00 00`
* interfaces:
* fields_count: `00 02`
* fields:
    * #0001:
        * access_flags: `00 19`
        * name_index: `00 17`
        * descriptor_index: `00 18`
        * attributes_count: `00 01`
        * attributes:
            * #0001:
                * attribute_name_index: `00 19` (ConstantValue)
                * attribute_length: `00 00 00 02`
                * constantvalue_index: `00 1a`
    * #0002:
        * access_flags: `00 19`
        * name_index: `00 1c`
        * descriptor_index: `00 1d`
        * attributes_count: `00 01`
        * attributes:
            * #0001:
                * attribute_name_index: `00 19` (ConstantValue)
                * attribute_length: `00 00 00 02`
                * constantvalue_index: `00 1e`
* methods_count: `00 02`
* methods:
    * #0001:
        * access_flags: `00 01`
        * name_index: `00 05`
        * descriptor_index: `00 06`
        * attributes_count: `00 01`
        * attributes:
            * #0001:
                * attribute_name_index: `00 20` (Code)
                * attribute_length: `00 00 00 1d`
                * max_stack: `00 01`
                * max_locals: `00 01`
                * code_length: `00 00 00 05`
                * code:
                    * #00000000:
                        * instruction: `2a` (aload_0)
                    * #00000001:
                        * instruction: `b7` (invokespecial)
                        * indexbyte1: `00`
                        * indexbyte2: `01`
                    * #00000004:
                        * instruction: `b1` (return)
                * exception_table_length: `00 00`
                * exception_table:
                * attributes_count: `00 01`
                * attributes:
                    * #0001:
                        * attribute_name_index: `00 21` (LineNumberTable)
                        * attribute_length: `00 00 00 06`
                        * line_number_table_length: `00 01`
                        * line_number_table:
                            * #0001:
                                * start_pc: `00 00`
                                * line_number: `00 01`
    * #0002:
        * access_flags: `00 09`
        * name_index: `00 22`
        * descriptor_index: `00 23`
        * attributes_count: `00 01`
        * attributes:
            * #0001:
                * attribute_name_index: `00 20` (Code)
                * attribute_length: `00 00 00 25`
                * max_stack: `00 02`
                * max_locals: `00 01`
                * code_length: `00 00 00 09`
                * code:
                    * #00000000:
                        * instruction: `b2` (getstatic)
                        * indexbyte1: `00`
                        * indexbyte2: `07`
                    * #00000003:
                        * instruction: `12` (ldc)
                        * index: `0d`
                    * #00000005:
                        * instruction: `b6` (invokevirtual)
                        * indexbyte1: `00`
                        * indexbyte2: `0f`
                    * #00000008:
                        * instruction: `b1` (return)
                * exception_table_length: `00 00`
                * exception_table:
                * attributes_count: `00 01`
                * attributes:
                    * #0001:
                        * attribute_name_index: `00 21` (LineNumberTable)
                        * attribute_length: `00 00 00 0a`
                        * line_number_table_length: `00 02`
                        * line_number_table:
                            * #0001:
                                * start_pc: `00 00`
                                * line_number: `00 06`
                            * #0002:
                                * start_pc: `00 08`
                                * line_number: `00 07`
* attributes_count: `00 01`
* attributes:
    * #0001:
        * attribute_name_index: `00 24` (SourceFile)
        * attribute_length: `00 00 00 02`
        * sourcefile_index: `00 25`
