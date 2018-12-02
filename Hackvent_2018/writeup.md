# HACKvent 2018

The annual advent calender from Hacking-lab

![](writeupfiles/xmas.jpg)

## Overview


Title                                         | Category    | Points | Flag
--------------------------------------------- | ----------- | ------ | ------------------------------
[Teaser     ](#teaser)                        |             |        | `Multiple, see below`
[December 1 ](#day-01-just-another-bar-code)  | Easy        | 2/1    | `HV18-L3ts-5t4r-7Th3-Phun-G33k`
[December 2 ](#day-02-me)                     | Easy        | 2/1    | `HL18-7QTH-JZ1K-JKSD-GPEB-GJPU`
[December 3 ](#day-03-)                       | Easy        | 2/1    | `HV18-`
[December 4 ](#day-04-)                       | Easy        | 2/1    | `HV18-`
[December 5 ](#day-05-)                       | Easy        | 2/1    | `HV18-`
[December 6 ](#day-06-)                       | Easy        | 2/1    | `HV18-`
[December 7 ](#day-07-)                       | Easy        | 2/1    | `HV18-`
[December 8 ](#day-08-)                       | Medium      | 3/2    | `HV18-`
[December 9 ](#day-09-)                       | Medium      | 3/2    | `HV18-`
[December 10](#day-10-)                       | Medium      | 3/2    | `HV18-`
[December 11](#day-11-)                       | Medium      | 3/2    | `HV18-`
[December 12](#day-12-)                       | Medium      | 3/2    | `HV18-`
[December 13](#day-13-)                       | Medium      | 3/2    | `HV18-`
[December 14](#day-14-)                       | Medium      | 3/2    | `HV18-`
[December 15](#day-15-)                       | Hard        | 4/3    | `HV18-`
[December 16](#day-16-)                       | Hard        | 4/3    | `HV18-`
[December 17](#day-17-)                       | Hard        | 4/3    | `HV18-`
[December 18](#day-18-)                       | Hard        | 4/3    | `HV18-`
[December 19](#day-19-)                       | Hard        | 4/3    | `HV18-`
[December 20](#day-20-)                       | Hard        | 4/3    | `HV18-`
[December 21](#day-21-)                       | Hard        | 4/3    | `HV18-`
[December 22](#day-22-)                       | Expert      | 5/4    | `HV18-`
[December 23](#day-23-)                       | Expert      | 5/4    | `HV18-`
[December 24](#day-24-)                       | Expert      | 5/4    | `HV18-`
[December 25](#day-25-)                       | Expert      | 5/4    | `HV18-`

## Teaser

**Challenge**

![](writeupfiles/Teaser.png)

**Solution**

*Stage 1*

The image contains braille code. We translate it to http://bit.ly/2TJvxHt

This gets us the following image:

![](writeupfiles/teaser/Flag_Stage_1.png)

this QR decodes to `Rushed by ..`

Turns out the bit.ly link actually translated to https://hackvent.hacking-lab.com/T34s3r_MMXVIII/index.php?flag=UI18-GAUa-lXhq-htyV-w2Wr-0yiV

and the `flag` parameter when ROT13'd gives us the first flag: `HV18-TNHn-yKud-uglI-j2Je-0lvI
`

when we fill in the correct flag in the url, we get to the next stage:

https://hackvent.hacking-lab.com/T34s3r_MMXVIII/index.php?flag=HV18-TNHn-yKud-uglI-j2Je-0lvI


*Stage 2*

Next stage is https://hackvent.hacking-lab.com/T34s3r_MMXVIII/ZOoxjUSe1OVB7OPoVrsX.pdf

Which is this [pdf file](writeupfiles/teaser/stage2.pdf)

Ok, there is lots here, lets get all the elements of the pdf with http://extractpdf.com

we get some images:

![](writeupfiles/teaser/stage2-banner.jpeg)
![](writeupfiles/teaser/stage2-balll.jpeg)
![](writeupfiles/teaser/stage2-stereogram.jpeg)

And some Morse code text:

```
HACKvent 2018

.... ...- .---- ---.. -....- --. --- .-. .. -....- --.. .-. ... -... -....- ..- ..-. .- . -....- - ... -.... -.-. -....- -.-. ...- - -

```

this decodes to: `HV18-GORI-ZRSB-UFAE-TS6C-CVTT`

Next, we try binwalk:

```bash
$ binwalk stage2.pdf
DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PDF document, version: "1.7"
404           0x194           Unix path: /PDF/Text/ImageB/ImageC/ImageI] >>/MediaBox[ 0 0 595.32 841.92] /Contents 4 0 R/Group<</Type/Group/S/Transparency/CS/DeviceRGB>>
621           0x26D           Zlib compressed data, default compression
1751          0x6D7           Unix path: /Type/XObject/Subtype/Image/Width 1000/Height 340/ColorSpace/DeviceRGB/BitsPerComponent 8/Filter/DCTDecode/Interpolate true/Leng
1899          0x76B           JPEG image data, JFIF standard 1.01
1929          0x789           TIFF image data, big-endian, offset of first image directory: 8
51778         0xCA42          Unix path: /Type/ExtGState/BM/Normal/ca 1>>
51831         0xCA77          Unix path: /Type/Font/Subtype/TrueType/Name/F1/BaseFont/BCDEEE+Calibri/Encoding/WinAnsiEncoding/FontDescriptor 8 0 R/FirstChar 32/LastChar
51998         0xCB1E          Unix path: /Type/FontDescriptor/FontName/BCDEEE+Calibri/Flags 32/ItalicAngle 0/Ascent 750/Descent -250/CapHeight 750/AvgWidth 521/MaxWidth
52237         0xCC0D          Unix path: /Type/ExtGState/BM/Normal/CA 1>>
52291         0xCC43          Unix path: /Type/XObject/Subtype/Image/Width 781/Height 781/ColorSpace/DeviceRGB/BitsPerComponent 8/Interpolate false/Filter/FlateDecode/Le
52442         0xCCDA          Zlib compressed data, default compression
187860        0x2DDD4         Unix path: /Type/Font/Subtype/TrueType/Name/F2/BaseFont/BCDFEE+Arial-Black/Encoding/WinAnsiEncoding/FontDescriptor 12 0 R/FirstChar 32/Last
188034        0x2DE82         Unix path: /Type/FontDescriptor/FontName/BCDFEE+Arial-Black/Flags 32/ItalicAngle 0/Ascent 1101/Descent -212/CapHeight 716/AvgWidth 552/MaxW
188279        0x2DF77         Unix path: /Type/Font/Subtype/TrueType/Name/F3/BaseFont/TimesNewRomanPS-BoldMT/Encoding/WinAnsiEncoding/FontDescriptor 14 0 R/FirstChar 32/
188456        0x2E028         Unix path: /Type/FontDescriptor/FontName/TimesNewRomanPS-BoldMT/Flags 32/ItalicAngle 0/Ascent 891/Descent -216/CapHeight 677/AvgWidth 427/M
188698        0x2E11A         Unix path: /Type/XObject/Subtype/Image/Width 200/Height 200/ColorSpace/DeviceRGB/BitsPerComponent 8/Filter/DCTDecode/Interpolate true/Lengt
188844        0x2E1AC         JPEG image data, JFIF standard 1.01
188874        0x2E1CA         TIFF image data, big-endian, offset of first image directory: 8
195577        0x2FBF9         Zlib compressed data, default compression
196145        0x2FE31         Zlib compressed data, default compression
215877        0x34B45         Zlib compressed data, default compression
231310        0x3878E         Unix path: /Type/Metadata/Subtype/XML/Length 3075>>
231494        0x38846         Unix path: /www.w3.org/1999/02/22-rdf-syntax-ns#">
231734        0x38936         Unix path: /purl.org/dc/elements/1.1/">
232171        0x38AEB         Unix path: /ns.adobe.com/xap/1.0/mm/">
234681        0x394B9         Zlib compressed data, default compression
236069        0x39A25         RAR archive data, first volume type: MAIN_HEAD
236135        0x39A67         Zip archive data, encrypted at least v2.0 to extract, compressed size: 210390, uncompressed size: 210378, name: z.zip
446647        0x6D0B7         End of Zip archive

# we see there are files appended, we extract with:
$ binwalk -e stage2.pdf
```

Reveals an [encrypted zip file](writeupfiles/teaser/_stage2.pdf.extracted/final.zip)

and an image:

![](writeupfiles/teaser/_stage2.pdf.extracted/QR3C.png)

and a [Santa.txt](writeupfiles/teaser/_stage2.pdf.extracted/Santa.txt) file:

```
MOPEN TLRHAHB TDTT CDRT ANOEO NFROA NHSYALHET ORAIT AD ONSAH AE RSUTL GI17-OICV-NTNL-EHNE-YIPN-ILBM
```

**Flag**
```
1: HV18-TNHn-yKud-uglI-j2Je-0lvI
2: HV18-GORI-ZRSB-UFAE-TS6C-CVTT
3:
```

## Day 01: Just Another Bar Code

**Challenge**

After a decade of monochromity, Santa has finally updated his infrastructure with color displays.

![](writeupfiles/HV18_Ball_Day1_color.png)

**Solution**

After some Googling, we find JAB Code (Just Another Bar Code) which is a high-capacity 2D color bar code,
which can encode more data than traditional black/white (QR) codes.


- [GitHub repo](https://github.com/jabcode/jabcode)
- [Online Decoder](https://jabcode.org/scan)

Their online decoder gives us the flag

**Flag**
```
HV18-L3ts-5t4r-7Th3-Phun-G33k
```

## Day 02: Me

**Challenge**


Can you help Santa decoding these numbers?

```
115 112 122 127 113 132 124 110 107 106 124 124 105 111 104 105 115 126 124 103 101 131
124 104 116 111 121 107 103 131 124 104 115 122 123 127 115 132 132 122 115 64 132 103
101 132 132 122 115 64 132 103 101 131 114 113 116 121 121 107 103 131 124 104 115 122
123 127 115 63 112 101 115 106 125 127 131 111 104 103 115 116 123 127 115 132 132 122
115 64 132 103 101 132 132 122 115 64 132 103 101 131 114 103 115 116 123 107 113 111
104 102 115 122 126 107 127 111 104 103 115 116 126 103 101 132 114 107 115 64 131 127
125 63 112 101 115 64 131 127 117 115 122 101 115 106 122 107 107 132 104 106 105 102
123 127 115 132 132 122 116 112 127 123 101 131 114 104 115 122 124 124 105 62 102 101
115 106 122 107 107 132 104 112 116 121 121 107 117 115 114 110 107 111 121 107 103 131
63 105 115 126 124 107 117 115 122 101 115 106 122 107 113 132 124 110 107 106 124 124
105 111 104 102 115 122 123 127 115 132 132 122 115 64 132 103 101 131 114 103 115 116
123 107 117 115 124 112 116 121 121 107 117 115 114 110 107 111 121 107 103 131 63 105
115 126 124 107 117 115 122 101 115 106 122 107 107 132 104 106 105 102 121 127 105 132
114 107 115 64 131 127 117 115 122 101 115 112 122 127 111 132 114 107 105 101 75 75
75 75 75 75
```

**Solution**

A series of decodings
  - Octal
  - Base32
  - 14-segment display

Decoding script [day02.py](writeupfiles/day02.py):

```python
import base64

input= "115 112 122 127 113 132 124 110 107 106 124 124 105 111 104 105 115 126 124 103 101 131 124 104 116 111 121 107 103 131 124 104 115 122 123 127 115 132 132 122 115 64 132 103 101 132 132 122 115 64 132 103 101 131 114 113 116 121 121 107 103 131 124 104 115 122 123 127 115 63 112 101 115 106 125 127 131 111 104 103 115 116 123 127 115 132 132 122 115 64 132 103 101 132 132 122 115 64 132 103 101 131 114 103 115 116 123 107 113 111 104 102 115 122 126 107 127 111 104 103 115 116 126 103 101 132 114 107 115 64 131 127 125 63 112 101 115 64 131 127 117 115 122 101 115 106 122 107 107 132 104 106 105 102 123 127 115 132 132 122 116 112 127 123 101 131 114 104 115 122 124 124 105 62 102 101 115 106 122 107 107 132 104 112 116 121 121 107 117 115 114 110 107 111 121 107 103 131 63 105 115 126 124 107 117 115 122 101 115 106 122 107 113 132 124 110 107 106 124 124 105 111 104 102 115 122 123 127 115 132 132 122 115 64 132 103 101 131 114 103 115 116 123 107 117 115 124 112 116 121 121 107 117 115 114 110 107 111 121 107 103 131 63 105 115 126 124 107 117 115 122 101 115 106 122 107 107 132 104 106 105 102 121 127 105 132 114 107 115 64 131 127 117 115 122 101 115 112 122 127 111 132 114 107 105 101 75 75 75 75 75 75"

# looks like ascii encoded in octal

output1 = ""
for i in input.split(' '):
    output1 += chr(int(i, 8))

print('output1: ', output1)

# looks like base32

output2 = base64.b32decode(output1)
print('output2: ', output2.upper())

# now what..?
```

This outputs:

```
output1:  MJRWKZTHGFTTEIDEMVTCAYTDNIQGCYTDMRSWMZZRM4ZCAZZRM4ZCAYLKNQQGCYTDMRSWM3JAMFUWYIDCMNSWMZZRM4ZCAZZRM4ZCAYLCMNSGKIDBMRVGWIDCMNVCAZLGM4YWU3JAM4YWOMRAMFRGGZDFEBSWMZZRNJWSAYLDMRTTE2BAMFRGGZDJNQQGOMLHGIQGCY3EMVTGOMRAMFRGKZTHGFTTEIDBMRSWMZZRM4ZCAYLCMNSGOMTJNQQGOMLHGIQGCY3EMVTGOMRAMFRGGZDFEBQWEZLGM4YWOMRAMJRWIZLGEA======
output2:  b'BCEFG1G2 DEF BCJ ABCDEFG1G2 G1G2 AJL ABCDEFM AIL BCEFG1G2 G1G2 ABCDE ADJK BCJ EFG1JM G1G2 ABCDE EFG1JM ACDG2H ABCDIL G1G2 ACDEFG2 ABEFG1G2 ADEFG1G2 ABCDG2IL G1G2 ACDEFG2 ABCDE ABEFG1G2 BCDEF '
```

This last bit seems to be 14-segment display code, which can be solved with [this tool](https://www.geocachingtoolbox.com/index.php?lang=en&page=segmentDisplay) from the geocaching toolbox:

![](writeupfiles/day02-14segment-decode.jpg)

And [this site](http://kryptografie.de/kryptografie/chiffre/14-segment.htm) decodes to text directly, giving us the flag:

```
HL18-7QTH-JZ1K-JKSD-GPEB-GJPU
```

(The `HL18` at the start seems to just have been a mistake, and the flag is accepted like this)

**Flag**
```
HL18-7QTH-JZ1K-JKSD-GPEB-GJPU
```

## Day 03:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 04:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 05:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 06:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 07:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 08:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 09:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 10:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 11:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 12:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 13:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 14:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 15:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 16:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 17:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 18:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 19:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 20:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 21:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 22:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 23:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 24:

**Challenge**

**Solution**

**Flag**
```
HV18-
```

## Day 25:

**Challenge**

**Solution**

**Flag**
```
HV18-
```