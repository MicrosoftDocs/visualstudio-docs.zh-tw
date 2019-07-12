---
title: 'Idiasymbol:: Get_undecoratednameex |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f9c50f5d352d8a52b0eb8b125992b2c325e48234
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "64811858"
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取部分或全部的未裝飾名稱的C++裝飾 （連結） 的名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>參數  
 `undecoratedOptions`  
 [in]指定旗標的組合傳回該控制項。 請參閱 < 備註 > 一節的特定值，以及他們如何。  
  
 `pRetVal`  
 [out]傳回的未裝飾的名稱C++裝飾名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
> 傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 `undecorateOptions`可以是下列旗標的組合。  
  
> [!NOTE]
> 旗標名稱未定義在 DIA SDK 中，因此您需要將宣告新增至您的程式碼，或使用原始值。  
  
|旗標|值|描述|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|啟用完整 undecoration。|  
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|移除 Microsoft 擴充關鍵字前置底線。|  
|UNDNAME_NO_MS_KEYWORDS|0x0002|停用 Microsoft 擴充關鍵字的擴充。|  
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|停用擴充的主要宣告的傳回型別。|  
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|停用擴充的宣告模型。|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|停用擴充的宣告語言規範。|  
|UNDNAME_RESERVED1|0x0020|保留。|  
|UNDNAME_RESERVED2|0x0040|保留。|  
|UNDNAME_NO_THISTYPE|0x0060|停用上的所有修飾詞`this`型別。|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|停用擴充成員的存取規範。|  
|UNDNAME_NO_THROW_SIGNATURES|0x0100|停用擴充 」 throw-簽章 」 函式和函式的指標。|  
|UNDNAME_NO_MEMBER_TYPE|0x0200|停用的擴充`static`或`virtual`成員。|  
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|針對 UDT 傳回，會停用擴充 Microsoft 模型。|  
|UNDNAME_32_BIT_DECODE|0x0800|Undecorates 32 位元的裝飾的名稱。|  
|UNDNAME_NAME_ONLY|0x1000|取得主要宣告; 的名稱只傳回 [範圍::] 名稱。  展開 範本參數。|  
|UNDNAME_TYPE_ONLY|0x2000|輸入是只要型別支援的編碼。撰寫抽象宣告子。|  
|UNDNAME_HAVE_PARAMETERS|0x4000|使用真實的樣板參數。|  
|UNDNAME_NO_ECSU|0x8000|會隱藏列舉/類別/結構/等位。|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|隱藏有效的識別項字元檢查。|  
|UNDNAME_NO_PTR64|0x20000|不包含 ptr64 輸出中。|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
