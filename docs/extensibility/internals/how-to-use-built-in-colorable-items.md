---
title: 如何：使用內建的可設定色彩專案 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 762d1e53f7aafa11ed345859e68fc98766eec77d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905218"
---
# <a name="how-to-use-built-in-colorable-items"></a>如何：使用內建的可設定色彩專案
使用內建的可設定色彩專案之前，您必須先向整合式開發環境發出 (IDE) 您未提供自己的自訂可設定色彩專案，在此情況下會是 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 物件。 做法是設定語言服務的登錄專案。

## <a name="to-use-built-in-colorable-items"></a>使用內建的可設定色彩專案

1. 在**HKEY_LOCAL_MACHINE \visualstudio \\<X. Y> \languages\language Services \\<語言名稱 \> **，其中 \<X.Y> 是的版本， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 而 \<Language Name> 是您的語言名稱，請建立名為**RequestStockColors**的 DWORD 登錄專案值。

2. 將 **RequestStockColors** 登錄專案值設定為 *1*。

    在您建立登錄專案之後，著色器的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 方法可以使用列舉的成員 <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> 來填入色彩屬性的陣列，以供編輯器使用。

   > [!NOTE]
   > 如果您要提供自訂可設定色彩專案，請不要設定此登錄專案。 如需詳細資訊，請參閱 [自訂可設定色彩專案](../../extensibility/internals/custom-colorable-items.md)。

## <a name="see-also"></a>另請參閱
- [自訂編輯器中的語法著色](../../extensibility/syntax-coloring-in-custom-editors.md)
- [舊版語言服務中的語法著色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [執行語法著色](../../extensibility/internals/implementing-syntax-coloring.md)
- [自訂可設定色彩專案](../../extensibility/internals/custom-colorable-items.md)
- [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service2.md)
