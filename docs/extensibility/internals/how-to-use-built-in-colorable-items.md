---
title: 如何:使用內置的可著色物品 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34e07894c3306f544396e53001990f7b9a2df5a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707781"
---
# <a name="how-to-use-built-in-colorable-items"></a>如何:使用內建的可著色專案
在使用內置的可著色項之前,必須先向集成開發環境 (IDE) 發出信號,指出您沒有提供自己的自定義可著色項,在這種情況下,這些<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>項將是 物件。 為此,您可以為語言服務設置註冊表項。

## <a name="to-use-built-in-colorable-items"></a>使用內建的可著色項目

1. 在**HKEY_LOCAL_MACHINE_VisualStudio<\\ X.Y>_语言服务\\<语言名称\>** 下,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\<\<其中 X.Y> 是 語言名稱>是您的語言的名稱,請創建一個名為 **"RequestStockColors"** 的 DWORD 註冊表條目值。

2. 將 **「要求StockColors」** 註冊表項目值設定為*1*。

    創建註冊表項后,著色器<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>的方法可以使用枚舉的<xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS>成員 來填充顏色屬性陣列,供編輯器使用。

   > [!NOTE]
   > 如果要提供自定義可著色項,請不要設置此註冊表項。 有關詳細資訊,請參閱[自訂可著色項](../../extensibility/internals/custom-colorable-items.md)。

## <a name="see-also"></a>另請參閱
- [自訂編輯器中的語法著色](../../extensibility/syntax-coloring-in-custom-editors.md)
- [舊語言服務中的語法著色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [實現語法著色](../../extensibility/internals/implementing-syntax-coloring.md)
- [自訂可著色項目](../../extensibility/internals/custom-colorable-items.md)
- [註冊舊語言服務](../../extensibility/internals/registering-a-legacy-language-service2.md)
