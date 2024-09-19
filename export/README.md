# [RectLabel](https://rectlabel.com)
How to use? Read our [Help page](https://rectlabel.com/help/).

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

# Export menus
- [Export Create ML JSON file](https://rectlabel.com/export#export-create-ml-json-file)
- [Import Create ML JSON file](https://rectlabel.com/export#import-create-ml-json-file)
- [Export images for classification](https://rectlabel.com/export#export-images-for-classification)
- [Export COCO JSON file](https://rectlabel.com/export#export-coco-json-file)
- [Import COCO JSON file](https://rectlabel.com/export#import-coco-json-file)
- [Import COCO JSON per image files](https://rectlabel.com/export#import-coco-json-per-image-files)
- [Export Labelme JSON files](https://rectlabel.com/export#export-labelme-json-files)
- [Import Labelme JSON files](https://rectlabel.com/export#import-labelme-json-files)
- [Export YOLO txt files](https://rectlabel.com/export#export-yolo-txt-files)
- [Import YOLO txt files](https://rectlabel.com/export#import-yolo-txt-files)
- [Export DOTA txt files](https://rectlabel.com/export#export-dota-txt-files)
- [Import DOTA txt files](https://rectlabel.com/export#import-dota-txt-files)
- [Export train/val/test folders](https://rectlabel.com/export#export-trainvaltest-folders)
- [Export object names file](https://rectlabel.com/export#export-object-names-file)
- [Import object names file](https://rectlabel.com/export#import-object-names-file)
- [Export mask images](https://rectlabel.com/export#export-mask-images)
- [Export screenshots](https://rectlabel.com/export#export-screenshots)
- [Export augmented images](https://rectlabel.com/export#export-augmented-images)
- [Export sliced images](https://rectlabel.com/export#export-sliced-images)
- [Export objects and attributes stats](https://rectlabel.com/export#export-objects-and-attributes-stats)

# Export Create ML JSON file
Annotation files are exported as an [Create ML JSON file](https://developer.apple.com/videos/play/wwdc2019/424/).

- Specify the split ratio "80/10/10" so that images are split into train, validation, and test sets.
- For "Image size", images are resized, if "Image size" is empty, images are not resized.
- If you encouter errors, read [Empty table from specified data source](https://stackoverflow.com/questions/65314564/empty-table-from-specified-data-source-error-in-create-ml).

![createml](https://github.com/user-attachments/assets/4976010d-f835-4125-af5c-0a3d7c225fbd)

```
[{
    "image": "sneakers-1.jpg",
    "annotations": [
    {
        "label": "sneakers",
        "coordinates":
        {
            "y": 838,
            "x": 393,
            "width": 62,
            "height": 118
        }
    },
    {
        "label": "sneakers",
        "coordinates":
        {
            "y": 881,
            "x": 392,
            "width": 51,
            "height": 102
        }
    }]
}]
```

# Import Create ML JSON file
- The Create ML JSON file is imported to annotation files in the current folder.
- Before importing, be sure that you opened images folder and annotations folder.
- RectLabel can import from "imagefilename" and "annotation" keys, too.

# Export images for classification
All images are exported into object-named subfolders.
- Specify the split ratio "80/10/10" so that images are split into train, validation, and test sets.
- For "Image size", images are resized, if "Image size" is empty, images are not resized.
- You can change the image type to whole image or cropped image.
- [Creating an Image Classifier Model on Create ML](https://developer.apple.com/documentation/createml/creating-an-image-classifier-model).

![classification](https://github.com/user-attachments/assets/d68fd4ef-2fae-4de4-b32f-563e523fcd7e)

```
└── saved_folder
    ├── object_name0
    ├── object_name1
    └── object_name2
```

# Export COCO JSON file
Annotation files are exported as an [COCO JSON file](http://cocodataset.org/#format-data). This format is for [Detectron2](https://github.com/facebookresearch/detectron2).
- Specify the split ratio "80/10/10" so that images are split into train, validation, and test sets.
- For "Image size", images are resized, if "Image size" is empty, images are not resized.
- For "Export only used names", if checked on, all annotation files are scanned and the new objects table is created, based on the objects table, each object index is written in the COCO JSON file.

![coco_export](https://github.com/user-attachments/assets/df5c22db-d72a-433b-ae9b-8240f5b1accd)

For a box object, "segmentation" is exported as empty.

```
"annotations": [
{
    "area": 254521,
    "bbox": [2150, 419, 595, 428],
    "category_id": 14,
    "id": 1,
    "image_id": 1,
    "iscrowd": 0,
    "segmentation": []
},
```

For a rotated box/polygon/line/point object, "segmentation" is exported as polygons.

```
"annotations": [
{
    "area": 164608,
    "bbox": [132, 417, 594, 432],
    "category_id": 14,
    "id": 1,
    "image_id": 1,
    "iscrowd": 0,
    "segmentation": [
        [136, 557, 152, 532, 191, 509, 266, 482, 367, 456, 375, 428, 427, 417, 486, 443, 516, 481, 518, 499, 564, 522, 611, 518, 661, 536, 701, 557, 724, 574, 719, 597, 691, 645, 723, 654, 715, 678, 695, 719, 681, 759, 681, 791, 670, 801, 659, 789, 656, 765, 627, 756, 644, 778, 629, 832, 591, 842, 553, 834, 514, 809, 494, 781, 491, 767, 433, 769, 403, 761, 405, 794, 387, 823, 369, 840, 344, 847, 309, 837, 295, 810, 286, 776, 290, 755, 297, 741, 259, 723, 216, 693, 179, 658, 147, 629, 132, 601, 132, 577]
    ]
},
```

For a pixels object, "segmentation" is exported as RLE. RLE is encoding the mask image using the [COCO API](https://github.com/cocodataset/cocoapi/tree/master/PythonAPI/pycocotools).

```
"annotations": [
{
    "area": 1022954,
    "bbox": [212, 0, 4204, 2960],
    "category_id": 26,
    "id": 1,
    "image_id": 1,
    "iscrowd": 0,
    "segmentation":
    {
        "counts": "ie_e03cW3O100O1000_knT30QmmjL2MOUW3?K3I]OViLg0iV35D`0FdNoiL]1lU39RjLZNfU3n1M2O2LSOejLGXU3;hjLkNMf0YU3?QkL_OoT3a0VkL[OiT3f0ZkLhNA9UU3o0`kLjNYO1WU3V1Q110O01O001O1O1N2O1L3O2O001O100M120N2N1O2O1O1O1O1O010O1O1O001O001O00100N101O1O1O0O2O001N10001O1O1N20000O1O1O1O00100O1O00101N1000O101O001OO10000O10O010O02N1M201L5L2K6L4N2N2O010O1O1O1O1O100O1O10O01O2OO0101N0010000O10000O1O1O011O000O1O100O1O1O010O100O0010000O1O100O10O01N200O2OO01O2N10O01N3M2O1O1O10O01O1O1O010O101N0O20O100000N1100O1OO200O01O10gaMQKki1o4VVNQKhi1Q5YVNnJgi1R5XVNPKgi1o4ZVNQKei1o4\\VNQKbi1Q5^VNoJbi1Q5^VNPK`i1Q5`VNoJ`i1P5bVNoJ]i1Q5dVNQKYi1P5gVNPKWi1S5hVNmJXi1S5hVNmJVi1T5kVNlJUi1T5kVNlJSi1V5mVNjJRi1X5mVNgJSi1Z5mVNfJQi1\\5nVNeJPi1]5PWNcJPi1]5oVNdJQi1]5nVNcJRi1^5mVNbJPi1a5PWN_JQi1`5nVN`Joh1e5oVN\\JQi1d5oVN\\JPi1e5oVN\\JQi1e5nVN[JQi1f5oVNYJPi1i5oVNXJPi1j5nVNWJQi1k5nVNUJQi1n5mVNQJSi1P6lVNQJRi1T6kVNkIUi1W6iVNjIVi1Y6gVNhIXi1[6eVNfIYi1^6eVNbIZi1_6eVNbIYi1b6eVN\\I\\i1g6aVNZI]i1h6bVNYI]i1h6bVNYI\\i1j6cVNTI]i1o6aVNRI^i1o6aVNPIj\\OFd\\2[7bVNoH^i1S7aVNnH]i1T7cVNlH\\i1U7cVNjH^i1W7aVNjH_i1V7`VNkH_i1V7`VNkH_i1V7`VNiH`i1Y7_VNhH`i1V7bVNkH]i1V7cVNjH\\i1V7dVNjH\\i1W7dVNhH[i1Z7dVNfH]i1Z7cVNeH\\i1\\7dVNdH\\i1\\7dVNeH[i1\\7dVNdH\\i1\\7eVNdHZi1]7eVNbH[i1`7eVN`HYi1b7fVN^H[i1a7eVN`HYi1b7fVN^HYi1d7gVN\\HWi1e7iVNZHWi1h7hVNYHVi1h7jVNWHXi1i7hVNWHUi1k7kVNVHSi1l7lVNTHTi1m7lVNRHSi1o7mVNQHRi1Q8mVNoGSi1R8lVNoGQi1S8oVNmGQi1T8oVNkGPi1V8oVNkGPi1W8oVNiGQi1X8nVNhGQi1Z8oVNfGoh1\\8oVNdGQi1^8oVNaGnh1b8QWN`Gnh1a8QWN^Gmh1f8RWN[Glh1g8SWNXGlh1k8SWNVGlh1j8TWNWGih1l8mmMnFI5\\R2m8kmMnFH5ZR2Q9hmMRGKM\\R2S9imMPGJM]R2T9emMSGMH]R2X9fmMPGLImP2M_gM[9d7QG1GiP23^gMW9g7PG0FmP25WgMW9l7mF1GjP2:_fMYOe0i9Q8mFOHlP2>QgMP9o7lF4GlP2`0ofMl8R8mF2GmP2d0hfMl8U8kF7DmP2i0_fMl8^8gF6DlP2Q;lnM]E6BoP2R;knMZE7EnP2Q;dnM`E=_OPQ2R;anM`E?]OQQ2S;^nMaEa0^OPQ2Q;\\nMdEd0[OPQ2R;YnMeEd0\\OTQ2n:VnMgEg0ZOTQ2P;QnMhEk0YOUQ2o:jmMmER1SOTQ2P;hmMoEQ1SOYQ2n:dmMQFQ1SO[Q2l:_mMTFT1RO^Q2k:\\mMUFU1QO_Q2i:YmMYFT1QOeQ2f:SmM]FV1oNgQ2d:nlMaFT1QOPR2^:glMfFW1nNRR2[:clMlFU1nNXR2W:\\lMQG[1iNZR2V:nkM^Gd1_N^R2T:hkMbGh1]N`R2Q:bjM]DaKW4Z7[MfR2P:XjMPIR3QMeR2P:RjMUIV3lLkR2P:kiMVIZ3jLkR2Q:fiMZI]3fLnR2P:biM]I^3dLPS2Q:ZiMbIc3`LSS2o9XiMbId3^LVS2P:SiMeIkNfJa2e1aU2R:PiMdIoNgJ\\2d1fU2Q:lhMgIROmJYN=e0YO=g1gX2P:ihMhIUOZLkMWN5K2b0U1[1kX2P:dhMkI[OaMROeNPY2o9ahMmI]O`MoNeNTY2o9\\hMPJ_O^MnNdNWY2P:ZhMoIA]MkNgNZY2o9VhMoID\\MjNgN]Y2n9ShMQJE\\MjNdN_Y2P:ogMRJG\\MfNfNcY2n9ngMQJI[MfNeNdY2Q:igMRJK]M`NcNmY2o9fgMSJJ]M`NdNoY2o9cgMTJL3aX2j5`gMVJM0dX2n5XgMVJ3KfX2o5hfMfJ>^OiX2Q6jeM^K[1`NlX2]>SgMdAmX2\\>RgMdAnX2^>PgMcAPY2\\>PgMeAPY2\\>ofMcARY2a>ifM_AWY2h>bfMYA^Y2k>]fMUAdY2k>ZfMWAfY2i>XfMXAiY2j>TfMWAlY2k>QfMVAoY2l>neMUARZ2P?geMRAYZ2o>aeMUA_Z2Pf0100000O100000O0100O0100000O0100O10O0100O100O01000O01000O10O00100000N2000000O1O0100O010000O10O10O1O1000O10000O10O1O0100000000O10000000000O100000WO\\eMaTOdZ2_k0\\eMaTOdZ2Xl000O100O02O00O100000000O2O000O10000O10000O100000000O0100O10O100000O0010000O0010OO11000O1O10OO20O10O1O10O0100O010O0010O10N1100O10N1100O00001OO11N2N2OO02O001O001O0O2N101O1N2N11OO20ON300N2O10O01N2O1O10O01O001000000O1O10N11O100O10O1O01O100O011NO11O1O1OO1100O1O100O100O1O10000O100O1O100O1O2O0N3OOO3N1M300N200J6N2N2M3cNXQOjiMkn0UV2ZQOeiMhn0ZV2\\QO^iMin0`V2\\QO\\iMen0dV2X1M1O100O100O10002M100O102M2O3L3N:F000O01O10000N1100OO200L310N110L40ON3O1N1O2K4O2N2N101N1N3O0N3O0O2O1N1O2N200M210N200M3OO0200N102L3O0N300N110M3O1N200N20OO200N101O1O1M300N200N1100000N200N200N200N20OO200N200N20OO20001OOO200N200N1011O00N200N200N2000000N200N200N3O0N200N201K400N200N200L401M2N1O201K4O1O2M2N200N200L400N200L400L400L40NN40L040NN4OO1100N2O2N2M2O102N002N0M5M102N000N2O3M1O10002N002L3N2N10001N3M2N2N2O1O1O1O1K4O2O1O1O1L4O0O2O1N100N3O1M201M220L201M201O1M2N3O001O1M202L202N002L202N002L202N002L201O1O00002N0000002N002L211NO11O010O1N1001O00010O01O002OO011M12OO001O02OO1O001000O000100O010O1O0011OO011N01O011OO003NO10O020N10OO21N04NN000022L01O1O1O22MO2N0020N03N0O11O00O1O12N00O1O20OO20OO4NN05MN14OL04NN130MO31MN31NO20NO04L1O5K1O3M2N2N3L4M1O3M3L5L2N4L2N4L2M4M1O3L2O1O1N3N1O1N2N3N1OO02NoVOhbMig0X]2TXOlbMkg0R]2VXOobMjg0P]2UXORcMkg0k\\2WXOVcMig0h\\2WXOZcMig0e\\2VXO^cMig0a\\2WXO`cMig0^\\2WXOdcMig0[\\2WXOfcMig0Y\\2UXOjcMkg0U\\2VXOlcMig0R\\2WXOPdMig0o[2WXORdMig0l[2WXOVdMig0i[2WXOYdMhg0f[2WXO\\dMkg0a[2UXO`dMkg0^[2UXOddMkg0[[2TXOgdMlg0W[2TXOkdMlg0T[2UXOmdMjg0Q[2UXOReMkg0mZ2UXOTeMkg0jZ2UXOWeMng0fZ2RXO[eMng0cZ2QXO`eMog0_Z2QXObeMog0\\Z2PXOgeMRh0UZ2PXOkeMPh0SZ2RXOmeMng0RZ2SXOneMmg0QZ2RXOQfMPh0lY2QXOTfMog0jY2QXOXfMog0gY2RXOYfMng0dY2SXO\\fMQh0aY2oWO`fMQh0^Y2nWOefMRh0YY2oWOhfMQh0VY2PXOlfMQh0PY2oWORgMQh0mX2nWOUgMRh0iX2oWOXgMQh0gX2mWO\\gMSh0cX2nWO\\gMSh0aX2nWOagMTh0\\X2lWOegMTh0XX2lWOlgMUh0QX2kWOPhMUh0oW2kWOQhMVh0nW2iWOThMWh0jW2jWOWhMXh0fW2hWO[hMXh0cW2hWO_hMZh0^W2eWOdhM[h0ZW2eWOhhM[h0WW2eWOjhM[h0RW2fWOPiM]h0nV2cWORiM]h0lV2bWOWiM^h0gV2cWOYiM_h0dV2aWO^iM`h0aV2_WO`iMah0^V2^WOeiMdh0WV2]WOjiMch0TV2^WOmiMbh0RV2]WOPjMch0mU2^WOUjMdh0hU2\\WOYjMdh0eU2[WO]jMhh0`U2XWOajMhh0^U2XWOcjMjh0ZU2UWOgjMlh0VU2UWOljMlh0RU2SWOPkMmh0nT2TWOSkMmh0kT2RWOWkMoh0gT2PWOZkMQi0dT2PWO]kMRi0_T2nVOckMRi0\\T2oVOckMSi0YT2mVOjkMTi0UT2kVOlkMVi0QT2fVOQhMoNQ4]j0kS2eVOXlM\\i0fS2cVO\\lM^i0aS2cVO`lM^i0]S2aVOflM`i0XS2aVOhlMai0TS2]VOPmMdi0nR2]VORmMdi0kR2\\VOWmMfi0fR2[VOZmMei0dR2YVO`mMii0]R2XVOcmMhi0[R2YVOgmMgi0WR2ZVOimMgi0SR2ZVOomMgi0PR2XVOQnMii0lQ2YVOTnMhi0iQ2YVOYnMfi0eQ2YVO^nMhi0`Q2XVOanMii0\\Q2VVOgnMki0WQ2UVOjnMli0SQ2TVOonMoi0lP2RVOUoMni0jP2PVOZoMQj0cP2oUO^oMQj0`P2oUOboMRj0\\P2oUOdoMRj0e1nTOZg1Q1SWNRj0a1oTOZg1n0WWNTj0]1PUOZg1k0\\WNTj0Y1QUOZg1m0]WNSj0W1QUOZg1l0aWNTj0S1QUOZg1l0dWNTj0P1QUOZg1k0hWNUj0m0PUOZg1k0jWNUj0k0QUOXg1j0PXNWj0e0oTO[g1j0QXNXj0b0oTO\\g1h0UXNXj0=QUO]g1g0WXNYj0;QUO\\g1g0[XNXj07QUO]g1i0\\XNVj06RUO\\g1g0aXNXj01QUO^g1f0cXNZj0MPUO_g1g0eXNYj0JQUOag1e0gXNZj0GRUO`g1e0kXNYj0BSUObg1d0nXNXj0@TUOag1d0QYNYj0ZOVUOdg1`0TYNZj0VOWUOeg1?WYN[j0ROUUOhg1?XYN[j0nNXUOhg1?[YNZj0jNXUOjg1?]YNYj0hNXUOjg1?aYNXj0cN[UOkg1nQ2RCm[NU5QCP8PQ2lBT\\Nn4oBR8lP2QCX\\Ni4UCo7dP2WCY\\Ni4UCo7_P2XC_\\Ng4TCQ8[P2XCf\\Nc4SCPJ`Nh=hQ2fCi\\N_4RCk7XP2dCi\\N`4QCk7QP2fCR]N_4PCh7mo1iCT]N]4QCf7ko1oCX]NY4PC]7PP2YDQ]NY4PC^7jo1\\DX]NU4TCY7do1bDY]NU4SCY7`o1aDd]NR4SCe6lo1VET]NU4PCc6jo1YEY]NS4nBc6ho1\\EZ]NQ4nBc6fo1ZEb]NP4iBW6QP2kEW]Nn3hBU6QP2lE\\]Nm3cBW6no1mEa]Nl3aBW6lo1lEh]Ni3fBe5no1aFZmM_NS`0[5eBe5ko1bFf]Nf3`Be5lo1dFe]Nh3_Bd5ho1fFn]Nc3ZBg5fo1eFS^Nd3`BS5fo1YGn]Nb3\\Bn4lo1^Gk]Nd3YBn4ho1`GU^N^3SBR5go1^GY^N]3hBQ4Zo1dHR^NY3dBm3_o1hHP^N[3aBm3\\o1iHY^NV3[BQ4Yo1jH^^NU3XCf2en1TJ[^Nn2RCc2ln1^JS^NQ3QC`2jn1`J[^Nl2kBb2kn1`J]^Nn2YCc1dn1`KZ^Ni2RC[1on1mKo]Nh2RC[1ln1lKZ^Nd2kB`1jn1iK_^Nf2hBa1fn1jKe^Nd2VCj0[n1aLa^Ne2TCg0[n1eLc^Ne2QCd0fk1ZKoPN^1[`0d2PCb0fk1_KkPN\\1f`0^2VC6\\k1QLgPNZ1i`0\\2WC9Xk1RLdPN[1Qa0X2SC5^k1XL\\PNZ1Va0Y2PC3^k1]LXPNX1`a0U2RCHZk1lLRPNW1da0U2PCGZk1nLooMX1ja0o1oBF\\k1TMhoMX1oa0o1lBC^k1WMfoMV1Rb0P2jBC\\k1YMdoMU1Yb0m1P\\O_LT7c2Uk1lMomMFm0a1lb0j1VCQOSk1oMlmMHk0_1Rc0i1TCQORk1PNkmMIl0\\1Uc0k1QCPOSk1PNjmMKh0\\1bc0c1mBnNRk1kN]nMd0gc0`1kBPOQk1nN\\nMa0ic0`1kBQOoj1oNYnM`0Qd0`1gBQOnj1QOWnM`0Vd0\\1nBhNfj1]OTnM>]d0[1iBjNej1^OSnM>`d0Z1hBjNdj1@nmM?id0T1gBkNdj1CjmM?kd0S1gBkNcj1GgmM9Ue0R1aBnN_j1h1QcNZO`BmN_j1h1TcNXO_BoNZj1l1XcNVO]BnN[j1h1acNTObBfNmi1W2acNSObBfNhi1Z2kcNmN]BhNfi1]2ncNkN\\BhNei1\\2VdNgN]BeN\\i1e2WdNfN]BdN[i1g2]dNaNXBhNZi1h2^dN`NXBhNYi1h2`dN_NXBiNWi1g2gdNXLcYOR2g8gNnh1o2mdNXNUBjNlh1n2PeNXNTBjNkh1m2TeNXNRBjNjh1n2WeNUNSBkNch1n2^eNVNSBhN^h1Q3aeNWNQBhN]h1P3deNXNoAhN\\h1P3ieNUNmAiNYh1Q3meNUNoAdNUh1V3meNVNoAcNSh1V3PfNWNdc1h1]\\NXNcc1f1d\\NUN[c1k1f\\NUNZc1j1g\\NVNYc1h1i\\NXNWc1f1Q]NTNob1k1R]NUNnb1i1V]NUNib1k1X]NTNib1j1]]NRNcb1m1^]NSNcb1j1`]NUN`b1j1a]NVN_b1h1c]NYN]b1e1g]NXNYb1g1i]NYNVb1f1k]NZNUb1e1l]N[NTb1c1S^NXNma1g1V^NXNia1g1X^NYNha1f1[^NYNda1f1]^NZNda1c1`^N[N`a1e1`^N[N`a1c1c^N^N[a1a1g^N^NYa1a1j^N^NUa1a1l^N`NRa1`1Q_N^No`1_1T_NaNk`1\\1[_NdNb`1S1^eMYNSj0d0_`1n0o_NPOQ`1n0Q`NSOn_1l0U`NSOj_1n0U`NROj_1o0X`NQOe_1Q1Z`NoNe_1o0``NPO__1l0e`NTOQ_1_ORfM\\1Qk0TOk^1BSfMZ1Rk0TOj^1CSfMZ1Yk0nNb^1]1^aNcNa^1\\1gaN^NX^1b1iaN^NV^1b1maN[NS^1f1maNZNR^1g1mk01ON2001OO1O11OO1MZjLYNeU3h14OO11O00O2000O00000010O10O00100O1O00100O10RjL[NlU3g100O100000O100O100O00100000O00001O2N1O2N101O1OO1001O1N01O10000O10O10O001O1O010O00100000OO21N10MYjLWNhU3g131O101N01O0100O01O00001O010O1O0FUjLlNjU3T1VjLkNlU3U1TjLjNlU3W1TjLgNnU3X18O0001O10O1O01O0010O1O0001O01O0010O10OO1100O00O20N20M30NliLcNTV3]11001O0100N20O010N1011N1O0eNiiLY1WV3210O01O10O1M3001N00010O100ON30O1O01O10N11O010N110000O0001O10O1N11O010O01O0100O01O0010O0010O0O110O01O10N2O010O001O100O01000O000010O100O0001OO20O0010O0100O01O00001O001O10O00O1100O10O1OO1010O010O1QjLdNdU3]1XjLiNdU3f1IVN`jLk1_U36O1N2O1N21NO2N2N2O00010kjLcMPU3b2O2M2O10000O1O1001N00002O000ON3OO2000O0100O0O111O000M3O1N2M300N1O2O0O2N200O2N1000O0O21N10O1N1001O1O01O10N1O2N0011OO110N2O1N20ON030O10O0100N20OO11O011NO3ON2000N2N1O11M[NWjLd1iU322N200O01O0010N200N020000O0O20O01O2O0000O00O2O2O00O2N1N11N110O01N1101N2NOXjLYNeU3f151N20ON31O11NI_jLZN^U3h1cjLXN]U3g1djLZNZU3g1fjLYNYU3i19M3O000100O1O1000NVjLYNjU3g1NYNYjLh1gU3XNXjLi1hU3N401ON1O10O201ON2001O00O1O1OO2ON12000OO1010OO02NLWjL`NiU3`1XjL_NhU3`17O01N1O20OO[NUjLf1hU3[NXjLe1hU3401O0O2N1O02OO3N1MNajLRN^U3P232M1O1ON3LajLRN^U3P22N_jLRNaU3m110^jLRNcU3n120N21N1OO200O00010O010M2100O10J51N0200M201M21O000100O0O10O2000O011ON200O1O1O010O1000OM40O11ON200000O10N3O0O1O10000N2O11O0O2OL5O0000000LdMojL\\2QU35O0O02M20N11O1O001N3K1hMhjLY2WU33O02O00O002LcMmjL[2VU312NO0021N2O0N10100000O00NejLkM\\U3T220010N20N11O100O1O1O00O21M2O0012K1200O10O01O1OO2O01O1OO20O10NQN^jLo1bU320O00001O0000100000N1O1010O1O1000OO20M120001NNSN^jLl1cU330O11N1OO_jLPN`U3Q221ON100O20O1O00O20000O0O11N20O0O20M210O0000010O001O10J53M1O11OO000N3M30O3M1O10O0010N2O101O000O1001OM21O10OO01101O0O1NN40OO[jLTNeU3k1\\jLUNdU3j1]jLWNaU3k131O1O010O10N200NZjLUNeU3l11100O000O20000ONO301000O2NNRN_jLn1_U350O2L12000O01O01O01M30O01O12N0M2010L31O100NO30N3O001OO01O0UN[jLh1eU33O12O00N110NO300O1000M2100ON1200O01O0N210000M111000001NNTN]jLk1dU3210O010N20N2O1N20N110000000O1O00001000OO20O01O001O0010O10N3N0001O1O1O0001O1000N21N010M21O1O0002O0OL`jLUN_U3l1ajLTN_U3k152MN40O1O10N20M111OO3N100OO1011NO11O010000O000010000O01O1N10010O0000O20O1O01O10O0010O01O10N0011O010O1O01N2000O000000100OMUN\\jLm1cU322N10O10O00O2O01OLTN`jLl1aU342OMO3OO2O2N01O4K11N2OO2000O01000O00O110O001O1O010O0010000O10OO0110O010O0ZlLUNcQ3k1ZnLUNRN50K^S3k1_nLbN_Q3Z1dlLYNo1>[Q3Z1enLjNXQ3V1hnLPOSQ3o0lnLUOPQ3m0onLUOoP3k0PoLXOoP3g0RoL\\OiP3f0ToL]OlP3c0ToL^OjP3b0VoL@hP3a0XoL_OhP3b0VoL_OiP3b0WoL^OhP3c0WoL^OiP3a0WoL@iP3?XoLAeP3b0[oL[OhP3d0XoL]OgP3c0ZoL]OdP3e0[oL[OfP3e0ZoLZOfP3g0PoLPNhNZ1WR3f0jnLoMiNl1ZR34mnLNUQ32jnLOVQ30jnL1VQ3OinL2WQ3NhnL3WQ3NgnL4XQ3LhnL5TQ3NmnL2SQ3LmnL6SQ3JmnL5TQ3KknL7SQ3JlnL7SQ3GPoL9nP3IQoL7QQ3GPoL9oP3GQoL:nP3FRoL9PQ3GPoL8PQ3IPoL6QQ3JlnLPNoNT2WR3JknL9SQ3InnL7RQ3HnnL7UQ3HjnL9UQ3HjnL7WQ3IinL8VQ3HhnL9YQ3HdnLoMTOX2ZR3HbnL8aQ3G_nL2gQ30XnL0iQ30UnL2kQ3NSnL3mQ3LUnL3iQ3OUnL2mQ3NQnL2QR3NkmLnM@S2gR3OimL2WR30hmLJ_R33QmLoM`0l1bR35^mLKcR36\\mLGeR3;ZmLCiR3>TmLEiR3=WmLBkR3>SmLCnR3;RmLDQS3;llLlMKi1VS3b20OO1NeKmlLZ4TS3gKklLY4US33000O2L300O2N11OMdlLnK]S3R430000L4M3O10O02K300O2N2OOO3O00001N2M0eLlkL[3TT322N0001N11N2N2O1O1N2N10001N002O0O02O03N0NO3O01O1N2N1O101O10O02NO02N2O00010N2N1O002O0O3L21O1O1NcMljL[2VU311N101O1O10O10NfjLiMYU3W221MhMijLX2WU321N20N011O0001L4000O1O01O1O10O0N30N11000O1OO1001000O0001ON22OO1O00010O0O11O3NO0001OO1O110OM4N20O1ON12O1O1O10O1000N2000O01N11O0010O01N2O02M1100O00001OO2O10O0O200O000100O00O020N20N20O0010OO200OO2N11000O1ON3O1O0100O0O2OO2O10O00O10O20O2ON200O01O00O2OO3N01O0O21O0O1NO2100N2ON300O010O0100O00O1100O0010N02O01M120001NN201OO20000O001ON210000O00001OO2N01100000O000O110O01O010LmMdjLT2]U321N1OO12OO0O10O200N11O1O10N20N2O0001O001L`jLSN^U3n150O02OM121OO01O1O10N1001000O01N200O1OO110O1O01M1200O000000001000O0001000ON201OO2O000100N20N11O011ON0200ON30O1O01O01O1O01N20O1N1100MoMajLQ2`U311O10O10NO31NNoMajLR2^U32100N110O0010N11O1O1ONPN`jLQ2^U33101ON0200OO2O01O1N11O100OOajLnM^U3S211OO101O0010N20O1OO11O100OO2N11OO020000N`jLoM_U3R220N11O011N01L31M40OO1ON30N20L40N20O02OO001O00010MnMcjLR2]U321ON21O1N20O02ON1O20N2000N110O0002NN12O1OO20000O000O11O01ON3O10M120N2000N11O1O10O1O10M3O01N2OO20000O00O10100O01N11O00100OO20NOnMcjLS2\\U31djLkM\\U3U2012N100O0O11O1O00O1100O01OO20O1OOmMbjLS2]U32001O10N100010O1O010O01N10N4N10O10OO1001O1O100ONQN`jLn1aU3121M110O1N1100M12N20O1O1O10NO21O1O001O0001000O1O010O1O2MO30010OOO0101O3OOM30N2OM40OOLnjLhMSU3X25L4N2O01N11000O1ON30O001OO20NmMbjLQ20oM]U3T211N2002MO11O10OOO30O0000100O00010O1ON2010O00010OO13M10NmMbjLR2^U3210NO21O02OO0O20O002N01O01ON30ONmMdjLR2\\U31211ON2O0010OO1O12N1O1O1O0001O11N0OO21O00O1101N2ON2NmMbjLQ2^U342OKnMejLQ2\\U322O2OL301OO11001OOO20N2O10NOjMfjLV2[U311N20O00010L22O101NL500M2O2OOJfMQkL^2oT33100ON3NO3OO20O010O001O1OM_MUkL`2kT333O2MO101O10O1O1O100O100O1O1001OMkjLeMVU3[220000N20000000000O100O12NO1O10000N2N2O13M1O1O1OO100O1O1O1O100M3000000O1000000000000001O00000000000000N2N2K5M3N2N21O0000000000001O000000IQjLgNPV3Y16DiiLZOWV3`0PjLZOKMUV3i0XjLWOhU3i0b0N2O100O1O1O1O1N2001OMnhLBSW3>200O100LkhLGVW393N2N200N200000000000000",
        "size": [3317, 4417]
    }
},
```

For a keypoints object, "keypoints" and "num_keypoints" are exported. 
- You can export a keypoints object combined with a polygon object when you aligned the keypoints object at the row and the polygon object at the row + 1 on the labels table.

```
"annotations": [
{
    "area": 555429,
    "bbox": [732, 1446, 864, 1309],
    "category_id": 1,
    "id": 1,
    "image_id": 1,
    "iscrowd": 0,
    "keypoints": [1108, 1633, 2, 1104, 1603, 2, 1112, 1596, 1, 1149, 1593, 2, 1146, 1582, 1, 1108, 1730, 2, 1334, 1687, 2, 1061, 1890, 2, 1387, 1936, 2, 1017, 1665, 2, 1458, 2106, 2, 1160, 2060, 2, 1299, 2053, 2, 1174, 2291, 2, 1196, 2291, 2, 1321, 2609, 2, 1196, 2590, 2],
    "num_keypoints": 17,
    "segmentation": [
        [986, 1654, 1030, 1613, 1087, 1596, 1105, 1511, 1168, 1485, 1183, 1449, 1216, 1446, 1239, 1496, 1260, 1557, 1236, 1619, 1267, 1662, 1359, 1678, 1411, 1864, 1477, 2065, 1494, 2157, 1594, 2367, 1454, 2488, 1330, 2578, 1359, 2618, 1409, 2659, 1384, 2695, 1319, 2754, 1303, 2741, 1300, 2710, 1250, 2702, 1099, 2720, 1048, 2705, 1042, 2673, 1105, 2655, 1159, 2601, 1165, 2485, 1054, 2414, 895, 2340, 789, 2304, 732, 2278, 794, 2135, 889, 2013, 970, 1913, 968, 1714]
    ]
},
```

- You can export a keypoints object combined with a pixels object when you aligned the keypoints object at the row and the pixels object at the row + 1 on the labels table.

```
"annotations": [
{
    "area": 2977340,
    "bbox": [1435, 1125, 1105, 3708],
    "category_id": 1,
    "id": 1,
    "image_id": 1,
    "iscrowd": 0,
    "keypoints": [1904, 1495, 2, 1970, 1417, 2, 1822, 1433, 2, 2068, 1481, 2, 1730, 1533, 2, 2308, 1951, 2, 1595, 2075, 2, 2369, 2555, 2, 1561, 2614, 2, 2371, 3076, 2, 1508, 3136, 2, 2172, 3035, 2, 1753, 3101, 2, 2280, 4034, 2, 1806, 4124, 2, 2367, 4833, 1, 1842, 4833, 1],
    "num_keypoints": 17,
    "segmentation":
    {
        "counts": "ZUhc6a0af4b0]Oc0^Oa0^Oc0]Ob0_Ob0]Oc0]Ob0_Ob0]Oc0nnKjJS_3h5T`LkKa^3g4d`LmLP^3f3VaLmM_]3d2haLoNl\\3d1YbLi8bS3jGdkLg8ST3iGTkLi8bT3gGgjLj8oT3gGYjLj8^U3eGjiLm8lU3dG\\iLm8[V3fGihLl8mV3oGQhLb8eW3YHXgLZ8^X3aH_fLP8WY3kHgeLf7oY3UIndL]7iZ3]IUdLT7a[3`b0G9F:F9H1N2N2O1N2O1N2N2O1N2N2O1N2O1N2N2O1N2N2K5J6J6J6K5J6J6J6J6J6J6J6J5K6J6J6J6J6J6J6J6J6J6J6J6J6PgMn]Nd[1]c1WdNh\\NVZ1kd1eeNY[NoY1Te1leNP[NSZ1Re1heNS[NVZ1od1eeNU[NZZ1md1aeNW[N^Z1kd1]eNY[NbZ1id1YeN\\[NeZ1fd1VeN^[NiZ1dd1ReN`[NlZ1cd1odNb[NoZ1`d1ldNd[NS[1^d1hdNf[NW[1\\d1ddNh[N[[1Zd1bdNi[N[[1Zd1bdNh[N\\[1[d1`dNh[N^[1[d1_dNh[N_[1Zd1^dNh[N`[1[d1]dNg[Na[1\\d1\\dNg[Na[1\\d1\\dNf[Nc[1\\d1ZdNf[Nd[1]d1YdNe[Ne[1^d1XdNe[Nf[1]d1VdNf[Nh[1]d1UdNe[Ni[1]d1UdNf[Nh[1]d1UdNe[Nj[1]d1SdNe[Nk[1^d1RdNd[N^[1md1_dNV[NlZ1_e1QeNcZNZZ1Sf1ceNoYNTZ1[f1heNiYNTZ1[f1ieNgYNUZ1\\f1heNfYNUZ1^f1heNeYNUZ1^f1heNdYNUZ1`f1heNbYNVZ1af1geNaYNVZ1bf1heNaYNTZ1cf1ieN_YNUZ1cf1heN`YNUZ1cf1ieN`YNTZ1cf1ieN_YNTZ1df1jeN^YNTZ1ef1ieN]YNTZ1ff1jeN]YNSZ1ef1keN]YNRZ1gf1keN[YNSZ1gf1jeN]YNoV1ji1nhNXVNPW1ji1nhNXVNoV1ki1ohNWVNnV1mi1ohNVVNmV1mi1QiNUVNlV1ni1RiNTVNkV1Pj1RiNSVNjV1Pj1TiNRVNjV1Qj1RiNRVNkV1Qj1SiNRVNiV1Qj1UiNQVNhV1ej1chN]UNZW1[k1ogNgTNnW1Pl1\\gNSTNaX1dl1hfN^SNUY1Ym1UfNiRNhY1mm1ceNVRNYZ1Xn1XeNlQNeZ1an1mdNcQNP[1jn1cdNYQN`CdIWd1aU2jgNPQNkCcIXd1iU2_gNhPNVDbIXd1TV2SgN^PNbDaIXd1^V2ifNUPNlD`IWd1iV2^fNkoMXE_IWd1SW2SfNboMcE^IWd1]W2heNZoMmE]IXd1fW2\\eNQoMZF[IWd1QX2ReNgnMdF[IWd1\\X2fdN]nMPG[IVd1eX2\\dNUnMZGYIWd1oX2QdNlmMeGXIWd1ZY2fcNamMQHXIUd1gY2YcNVmM^HVIWd1RZ2kbNllMkHUIWd1_Z2]bN`lMYIUIVd1jZ2RbNTlMfITIUd1W[2eaNjkMRJRIVd1d[2WaN^kM`JRIUd1o[2k`NSkMmJQIVd1[\\2\\`NijM[KnHVd1h\\2l_NajMkKkHUd1T]2S_NajMeL^H?mMfa1c_2Y`NcjM_MPH=oMha1m_2`_NejMXNbG:QNka1X`2f^NejMROUG7UNma1``2n]NfjMKhF5WNPb1j`2R]NijMe0ZF3XNSb1]m2h]N]TM0[NUb1[m2h]N]TMM^NXb1Ym2g]N]TMK_N[b1Wm2g]N]TMIaN]b1Um2h]N\\TMFdN`b1Rm2g]N[VMVb1ii2f]NZVMWb1ii2f]N[VMVb1hi2h]NZVMUb1[o2M3M3N2O1O100O1O1O2M2O1O1O1O1O1O1O1O1O2N1O1N2O1O1O1O1O1O1O1O2N1O1O1N2O1O1O1O1O1O1O2N1O1O1O1N200O1O1O1O2N1O100O1O1O1O1O1O100O2N1O1O1O1O1O100O1O1O2N1O1O100O1O1O1O1O1O101N1O1O1O1O1O100O1O1O9G?A>B?A>C=B?A>B?A>B>B?B4K5K5K4L5L4K5K5K5K5L4K5K4L5K5L4K5K5K5L4K4L5K5K5L4K5K5K5K4M4K1O1O100O1O1O1O100O1O1O1O100O1O1O100O1O1O1O100O10000O100O10000O10000O100O10000O10000O100O10000O10000O100O10000O100O10000O10000O100O10000O10000O100O10000O10000O100O10000O100O10000O10000O100O10000O100O1O100O1O1O100O100O100O100O100O100O100O100O100O100O10000O100O100O100O100O100O100O100O100O100O100O100O1000000001O00001O0000001O0000001O0000001O0000001O00000`N`1UMl2UOj0ZOf0ZOf0YOh0YOf0ZOg0N2O1O001O1O1O0O2O1O1O001O1O1O0O2O1O00001O00001N10001O0000001O0O101O1O1O1O1O1O1N2O1O1O1O1O1O1O1N2O1O1O1O1O1O001N2O1O1O1O1O1O1O1jhL\\bNkT3f]1TkL[bNkT3f]1TkLZbNlT3g]1SkLZbNlT3g]1SkLYbNmT3h]1RkLYbNmT3h]1RkLXbNnT3i]1QkLXbNnT3i]1QkLWbNnT3k]1QkLVbNnT3k]1QkLUbNoT3l]1PkLUbNoT3l]1PkLTbNPU3m]1ojLTbNPU3l]1ojLUbNQU3l]1mjLUbNSU3l]1kjLVbNSU3l]1ljLTbNTU3m]1jjLUbNUU3l]1ijLUbNWU3l]1gjLVbNXU3k]1fjLVbNZU3k]1ejLVbNZU3k]1djLWbN[U3j]1cjLYbNZU3i]1djLYbN[U3h]1cjLZbN\\U3g]1bjL[bN\\U3g]1cjL[bN[U3f]1cjL\\bN\\U3e]1\\jLcbNbU3_]1RjLmbNmU3V_1N1N2O2N1N2O1N3N1O1N2O2N2M3N3L3N2N2N2O2M2N2N2N2N3M2O1N2N2N3M2N2N2O1N3M2N2N2N2N3N1N2N2N2N2N1O2O1N2N2N2N2N1O2O1N2N2N2N2N5K4M4K4L5K4L5K4L5K4L5K4L5K4L5K>B?A?A?A?A`0@5K1N3N2N1O2N1O2N1O2N2N1O2N1O2N2N1O2M4M3M2N3M3M2N3M3M2N3M3M2N3M2N3M2M4L4L3M4kYMjSNXa2Xl1d^MkSNZa2Yl1a^MiSN^a2Zl1^^MhSNaa2\\l1Y^MhSNea2[l1W^MgSNia2\\l1R^MfSNma2]l1o]MeSNPb2_l1k]MdSNSb2_l1h]MdSNWb2`l1d]MbSN[b2bl1`]MaSN_b2fl1X]M\\SNgb2kl1Q]MWSNnb2Qm1i\\MRSNUc2Um1b\\MnRN]c2Zm1Z\\MhRNfc2_m1Q\\MdRNmc2cm1k[M_RNTd2im1c[MYRN\\d2om1Z[MURNed2Qn1S[MQRNmd2Vn1jZMlQNVe2QP2O00001O0000001O00001O00001O00001O00001O0003N1N3M2O2M2N3M2O2M2N2O2M2N3N1N3M2O2M2N2O2M2N3N1N3M2O2M2ZWNTYMRa1of2e^NWYM[a1kf2]^N[YMda1ff2Z^NZYMfa1if2W^NWYMia1kf2T^NVYMma1lf2P^NTYMPb1nf2m]NSYMSb1Pg2j]NPYMWb1Qg2g]NoXMYb1Tg2c]NmXM]b1Ug2a]NkXM`b1Wg2\\]NjXMdb1Xg2Z]NhXMfb1\\g2U]NeXMlb1]g2Q]NcXMob1`g2n\\N`XMRc1cg2W[NlWMcMb0Wg1dg2Q[NmWMgM?Xg1gg2lZNnWMiM<[g1ig2hZNmWMlM:]g1kg2bZNnWMoM8_g1mg2^ZNnWMQN5ag1Qh2XZNmWMVN2bg1Th2SZNmWMYN0eg1Uh2nYNnWM[NMgg1Xh2iYNnWM^NKig1Zh2eYNmWMaNIkg1\\h2_YNoWMdNEmg1_h2[YNnWMfNDog1ah2VYNnWMjNAQh1ch2PYNPXMlN^OTh1fh2kXNnWMPO\\OUh1ih2fXNnWMSOZOXh1jh2aXNoWMUOWOZh1mh2\\XNoWMYOTO[h1Pi2WXNoWM\\ORO^h1Ri2QXNoWM_OoN`h1Ui2lWNoWMBmNbh1Xi2gWNmWMFkNdh1Zi2aWNoWMIgNfh1^i2[WNnWMLfNih1_i2WWNnWMLeNnh1_i2QWNQYMoh1aj200001O000000000000001O000000000000001O000000000000001O000000000000001O0000000000001O000000000000001O001O001O001O001O001O001O001O001O001O001O001O001O001O1O001O001O001O001O001O001O001O001O001O001O001O001O001O001O001O001O001O001O001O001O001O2N3M2N2N3M2N3M2N2N3M2N3M2N3M2N2N3M2N3UC]TNQnMek1mQ2dTNjmM_k1SR2kTNcmMWk1[R2SUN[mMoj1VX1TTN\\VOW1TAhj1RX1nTNXVOd0\\A`j1oW1hUNTVO2cAZj1jW1`VNRVO@jAWj1bW1UWNSVOnNQBSj1[W1lWNRVO[NYBPj1RW1bXNTVOhM`Bmi1jV1WYNPgNZJU7l2gJii1[ObSNjm0\\6cmNWLa:k1nHWh1KiTN\\n0j5PkNUNk=l0RGcf1S1[UNoLUN^l0V>]^O\\I^ETe1V2lUN^LlN_l0U=^_OQI]EYe1e1]VNnK[Ogl0Z]1M4L4L4LlXZS5",
        "size": [4834, 3648]
    }
},
```

In "categories", "keypoints" and "skeleton" are exported.

```
"categories": [
{
    "id": 1,
    "keypoints": ["nose", "leftEye", "rightEye", "leftEar", "rightEar", "leftShoulder", "rightShoulder", "leftElbow", "rightElbow", "leftWrist", "rightWrist", "leftHip", "rightHip", "leftKnee", "rightKnee", "leftAnkle", "rightAnkle"],
    "name": "person",
    "skeleton": [
        [9, 11],
        [6, 12],
        [14, 16],
        [7, 13],
        [15, 17],
        [12, 13],
        [14, 12],
        [8, 6],
        [10, 8],
        [6, 7],
        [9, 7],
        [15, 13],
        [5, 3],
        [3, 1],
        [1, 2],
        [2, 4]
    ]
},
```

# Import COCO JSON file
- The COCO JSON file is imported to annotation files in the current folder.
- Before importing, be sure that you opened images folder and annotations folder.

# Import COCO JSON per image files
You can import the COCO RLE JSON files of the [SA-1B dataset](https://github.com/facebookresearch/segment-anything).
- This COCO format does not include the "category_id" so that each label name is set to the recently used label name.
- Before importing, be sure that you opened images folder and annotations folder.

```
{
    "image":
    {
        "image_id": 1,
        "width": 1500,
        "height": 2060,
        "file_name": "sa_1.jpg"
    },
    "annotations": [
    {
        "bbox": [866.0, 946.0, 132.0, 199.0],
        "area": 14773,
        "segmentation":
        {
            "size": [2060, 1500],
            "counts": "TS_f15SP27K3N2iTNHWf1:bYN0Yf12cYN1\\f11mWN7SNKni11PVNS2OmMPj15aUN\\2;aMSj1m3`UNVL_j1m4N1O1O1O10000O10O10O100000000O10000O100O1O100O101O000000000O10O101N1N2N2O1O100O100\\KhUNT3Wj1jLnUNS3Tj1kLoUNR3Rj1mLTVNW3ci1hL`VNW3_i1hLdVNV3\\i1iLfVNV3Zi1jLgVNU3Yi1jLiVNV3Vi1jLlVNT3Ti1kLnVNT3Ri1lLoVNS3Qi1lLQWNS3oh1mLRWNR3nh1nLSWNQ3mh1nLVWNP3jh1PMWWNo2ih1QMXWNl2jh1TMWWNg2mh1XMUWNV1gNlN_j1NkVNS1jNkN]j12jVNQ1lNiN\\j16jVNm0mNjN[j19iVNk0nNjNZj1;iVNh0QOkNVj1=jVNe0TOjNTj1a0jVN3EXObi1e0YYNVOjf1j0\\4001O00001O00001O00001O10O01O001O1O1O1O1O2N1O1O1O1O1O1O100O101N10000O00100O1O1O100O1O1O0000lNRRNGQn17S1O2N1O101M4Mom^o0"
        },
        "predicted_iou": 0.9523417353630066,
        "point_coords": [
            [940.9375, 1034.5625]
        ],
        "crop_box": [622.0, 902.0, 567.0, 707.0],
        "id": 523353737,
        "stability_score": 0.9742233753204346
    },
    ...
}
```

# Export Labelme JSON files
Annotation files are exported as [Labelme JSON files](https://github.com/wkentaro/labelme).

```
{
    "flags":
    {},
    "imageData": null,
    "imageHeight": 3022,
    "imagePath": "wembley-S3Vq97p3gSk-unsplash.jpg",
    "imageWidth": 4666,
    "shapes": [
    {
        "flags":
        {},
        "group_id": null,
        "label": "anemonefish",
        "points": [
            [2152.53857421875, 556.815673828125],
            [2149.539306640625, 586.8057861328125],
            [2156.53759765625, 613.79681396484375],
            [2245.5185546875, 698.7686767578125],
            [2314.50390625, 737.75579833984375],
            [2308.505126953125, 782.74090576171875],
            [2315.503662109375, 814.73028564453125],
            [2331.500244140625, 835.723388671875],
            [2383.489013671875, 836.7230224609375],
            [2420.481201171875, 800.73492431640625],
            [2427.479736328125, 785.73992919921875],
            [2424.480224609375, 764.746826171875],
            [2511.461669921875, 775.74322509765625],
            [2524.458740234375, 795.736572265625],
            [2580.44677734375, 830.72503662109375],
            [2647.432373046875, 827.72601318359375],
            [2661.429443359375, 795.736572265625],
            [2661.429443359375, 772.74420166015625],
            [2653.43115234375, 757.7491455078125],
            [2675.426513671875, 762.74749755859375],
            [2681.42529296875, 800.73492431640625],
            [2692.4228515625, 797.7359619140625],
            [2701.4208984375, 737.75579833984375],
            [2723.416259765625, 687.7723388671875],
            [2744.41162109375, 662.78057861328125],
            [2735.41357421875, 647.78558349609375],
            [2722.41650390625, 650.78460693359375],
            [2697.421875, 641.78753662109375],
            [2737.4130859375, 599.80145263671875],
            [2737.4130859375, 569.8114013671875],
            [2668.427978515625, 529.82464599609375],
            [2580.44677734375, 522.82696533203125],
            [2535.45654296875, 494.83621215820312],
            [2533.45703125, 482.84017944335938],
            [2508.46240234375, 447.85174560546875],
            [2452.474365234375, 422.86001586914062],
            [2432.478515625, 420.86068725585938],
            [2393.48681640625, 430.85739135742188],
            [2375.49072265625, 457.84844970703125],
            [2284.51025390625, 479.84115600585938],
            [2215.525146484375, 506.83224487304688],
            [2160.536865234375, 543.82000732421875]
        ],
        "shape_type": "polygon"
    }],
    "version": "4.0.0"
}
```

# Import Labelme JSON files
- The Labelme JSON files are imported to annotation files in the current folder.
- Before importing, be sure that you opened images folder and annotations folder.

# Export YOLO txt files
Annotation files are exported as YOLO text files. A YOLO text file is saved per an image.

- Specify the split ratio "80/10/10" so that images are split into train, validation, and test sets.
- For "Image size", images are resized, if "Image size" is empty, images are not resized.
- For "Names file", there are "yaml file as dictionary", "yaml file as array", and "names file".
- For "Export only used names", if checked on, all annotation files are scanned and the new objects table is created, based on the objects table, each object index is written in each YOLO text file. If you are using attributes, check on "Export only used names".

![yolo_export](https://github.com/user-attachments/assets/da7b521d-fff8-4b03-9c19-a2276d41b6e6)

```
├── datasets
│   └── sneakers
│       ├── images
│       └── labels
└── yolov5
    └── data
        └── sneakers.yaml
```

For a box object, the bounding box is saved. center_x, center_y, width, and height are float values relative to width and height of the image.

```
class_index center_x center_y width height
0 0.464615 0.594724 0.680000 0.769784
```

For a rotated box/polygon/cubic bezier/line/point/pixels object, the points coordinates are saved. This format is for [YOLOv5](https://github.com/ultralytics/yolov5) and [YOLOv8](https://github.com/ultralytics/ultralytics) Instance Segmentation.

```
class_index x1 y1 x2 y2 x3 y3 ...
0 0.180027 0.287930 0.181324 0.280698 0.183726 0.270573 ...
```

For a keypoints object, the bounding box and the points coordinates are saved. This format is for [YOLOv8](https://github.com/ultralytics/ultralytics).

```
class_index center_x center_y width height x1 y1 v1 x2 y2 v2 x3 y3 v3 ...
0 0.545230 0.616880 0.298794 0.766239 0.522073 0.309332 2 0.540170 0.293193 2 0.499589 0.296503 2 ...
```

# Import YOLO txt files
- The YOLO text files are imported to annotation files in the current folder.
- Before importing, be sure that you opened images folder and annotations folder.

# Export DOTA txt files
Annotation files are exported as [DOTA text files](https://captain-whu.github.io/DOTA/dataset.html). This format is for [MMRotate](https://github.com/open-mmlab/mmrotate).

- Specify the split ratio "80/10/10" so that images are split into train, validation, and test sets.
- For "Image size", images are resized, if "Image size" is empty, images are not resized.

![dota_export](https://github.com/user-attachments/assets/429c91f3-9a45-415f-954b-cc1c43f04e54)

Settings menu.
- “Use truncated, occluded, and difficult tags” is to show truncated, occluded, and difficult checkboxes on the label dialog.

```
x1 y1 x2 y2 x3 y3 x4 y4 category difficult
1300.536987 1413.503784 1192.848755 1535.568848 530.876038 951.562073 638.564270 829.497009 truck 0
```

# Import DOTA txt files
- The DOTA text files are imported to annotation files in the current folder.
- Before importing, be sure that you opened images folder and annotations folder.

# Export train/val/test folders
- Specify the split ratio "80/10/10" so that images are split into train, validation, and test sets.
- You can export train/val/test folders and the yaml file at once in the YOLO format.

# Export object names file
Export a yaml file as dictionary for [YOLOv5](https://github.com/ultralytics/yolov5) and [YOLOv8](https://github.com/ultralytics/ultralytics).
- For "Export only used names", if checked on, all annotation files are scanned and the new objects table is created.
- The "flip_idx" array is to flip the "left" included keypoint position and the "right" included keypoint position.

```
path: ../datasets/keypoints
train: images
val: images

kpt_shape: [17, 3]
flip_idx: [0, 2, 1, 4, 3, 6, 5, 8, 7, 10, 9, 12, 11, 14, 13, 16, 15]

names:
  0: person
```

Export a yaml file as array for [YOLOv5](https://github.com/ultralytics/yolov5).

```
path: ../datasets/sneakers
train: images
val: images

nc: 2
names: ['sneakers', 'ignore']
```

Export an object names text file.

```
sneakers
ignore
```

# Import object names file
You can import an object names file or import object names from xml files.

# Export mask images
You can specify which mask image to export.
- Export an image includes all objects: An indexed color image which includes all objects is saved as {image_file_name}_all_objects.png.
- Export an image per object class: A grayscale image per object class is saved as {image_file_name}_class_{class_name}.png.
- Export an image per object: A grayscale image per object is saved as {image_file_name}_object{object_idx}.png.

For the indexed color image.
- The indexed color table is created from object colors on the objects table.
- Overlaps of objects are based on the layer order on the labels table.

![mask](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/7b9a30a2-3bff-486f-873d-cf650a402662)

# Export screenshots
You can export images and annotations as jpg images.

View menus.
- “Show labels on boxes” to show labels on boxes.
- “Show coordinates on boxes” to show (x, y) coordinates on boxes.

# Export augmented images
You can augment images and annotations using "Flip", "Crop", "Contrast", and "Rotate".
- For "Flip", each image is flipped horizontally with 0.5 probability.
- For "Crop", each image is cropped to [100% - value, 100%] of the original size.
- For "Contrast", each image contrast is changed to [100% - value, 100% + value].
- For "Rotate", each image is rotated to [-value, value] degrees.
- For "Number of augmented images", it means the number of augmented images from an image.
- If the object is cut out so that the bounding box size is less than 0.01 of the original size, the object is removed.
- To flip keypoints horizontally, use "left" and "right" in each keypoint name.

Settings menu.
- “Rotate boxes as rotated boxes when augment” is to rotate boxes as rotated boxes when augment.

![augment](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/4b128657-363c-4b3f-9a6e-4f1bb15bd5ef)

# Export sliced images
You can slice images and annotations horizontally and vertically.
- For "Horizontal slices", each image is sliced horizontally by the number of horizontal slices.
- For "Vertical slices", each image is sliced vertically by the number of vertical slices.

![slice](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/7d12d7ef-c858-4e0e-9241-a2a90f5fcec9)

# Export objects and attributes stats
- The number of used objects and attributes are exported.










































