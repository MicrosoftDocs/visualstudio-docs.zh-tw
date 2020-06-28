---
title: IDiaSymbol：： get_undecoratedNameEx |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25942c76d8e568d6354c9a6a2b2c69c806cde352
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461599"
---
# <a name="idiasymbolget_undecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
抓取 c + + 裝飾（連結）名稱的部分或全部未裝飾名稱稱。

## <a name="syntax"></a>語法

```C++
HRESULT get_undecoratedNameEx( 
   DWORD undecorateOptions,
   BSTR* pRetval
);
```

#### <a name="parameters"></a>參數
 `undecoratedOptions`

在指定可控制傳回內容的旗標組合。 請參閱「備註」一節中的特定值和動作。

 `pRetVal`

脫銷傳回 c + + 裝飾名稱的未裝飾名稱稱。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="remarks"></a>備註
 `undecorateOptions`可以是下列旗標的組合。

> [!NOTE]
> 旗標名稱不會在 DIA SDK 中定義，因此您必須將宣告新增至您的程式碼，或使用原始值。

|旗標|值|描述|
|----------|-----------|-----------------|
|UNDNAME_COMPLETE|0x0000|啟用完整 undecoration。|
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|移除 Microsoft 擴充關鍵字的前置底線。|
|UNDNAME_NO_MS_KEYWORDS|0x0002|停用 Microsoft 擴充關鍵字的擴充。|
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|停用主要宣告的傳回類型擴充。|
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|停用宣告模型的擴充。|
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|停用宣告語言規範的擴充。|
|UNDNAME_RESERVED1|0x0020|保留。|
|UNDNAME_RESERVED2|0x0040|保留。|
|UNDNAME_NO_THISTYPE|0x0060|停用類型上的所有修飾詞 `this` 。|
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|停用成員的存取規範擴充。|
|UNDNAME_NO_THROW_SIGNATURES|0x0100|停用擴充函式和函式指標的「擲回簽章」。|
|UNDNAME_NO_MEMBER_TYPE|0x0200|停用 `static` 或成員的展開 `virtual` 。|
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|停用針對 UDT 傳回的 Microsoft 模型展開。|
|UNDNAME_32_BIT_DECODE|0x0800|Undecorates 32 位裝飾名稱。|
|UNDNAME_NAME_ONLY|0x1000|只取得主要宣告的名稱;只傳回 [scope：：] 名稱。  展開範本參數。|
|UNDNAME_TYPE_ONLY|0x2000|輸入只是一種類型編碼;撰寫抽象宣告子。|
|UNDNAME_HAVE_PARAMETERS|0x4000|真正的範本參數可供使用。|
|UNDNAME_NO_ECSU|0x8000|抑制列舉/類別/結構/等位。|
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|隱藏檢查是否有有效的識別碼字元。|
|UNDNAME_NO_PTR64|0x20000|不包含輸出中的 ptr64。|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)