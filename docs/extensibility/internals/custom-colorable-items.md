---
title: 自定義可著色物品 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: feecd9e8f8178045f66999b775e2d0792f50b288
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708988"
---
# <a name="custom-colorable-items"></a>自訂可著色項目
您可以透過在語言服務中實現自訂可著色項來覆蓋著色類型清單,例如關鍵字和註釋。

## <a name="user-settings-of-colorable-items"></a>以色項目的使用者設定
 您可以通過在 **「工具」** 選單上選擇 **「選項**」,然後在 **「環境**」下選擇 **「字型和顏色**」對話框來顯示「**字型和顏色**」對話框。 當您選擇顯示(如**文字編輯器**或**命令視窗**)時,「**顯示專案」** 清單框顯示該顯示的所有可著色項。 您可以查看和更改每個可著色項的字型、大小、前景顏色和背景顏色。 您的選擇存儲在註冊表中的緩存中,並由可著色的項目名稱訪問。

## <a name="presentation-of-colorable-items"></a>提供可著色物品
 由於 IDE 處理 **「 字型和顏色」** 對話框中可著色項的使用者覆蓋,因此只需為每個自定義可著色項提供名稱。 此名稱是 **「顯示項目**」清單中顯示的內容。 可著色項按字母順序顯示。 要對語言服務的自定義可著色項目進行分組,可以使用語言名稱開始每個名稱,例如 **「新建語言 -註釋**」和 **「新建語言 - 關鍵字**」。

> [!CAUTION]
> 應在可著色項名稱中包含語言名稱,以避免與現有可著色項名稱發生衝突。 如果在開發期間更改了其中一個可著色項的名稱,則必須重置首次訪問可著色項時創建的緩存。 您可以使用**CreateExpA 工具**重新設定實驗快取,該工具通常安裝在 Visual Studio SDK 中, 通常位於目錄中:
>
> *C:\程式檔 (x86)\微軟視覺工作室 14.0_VSSDK_視覺工作室集成\工具\Bin*
>
> 要重置快取,請輸入 **「創建實例/重置**」。 有關**CreateExp 實體的詳細**資訊,請參閱[建立說明實用程式](../../extensibility/internals/createexpinstance-utility.md)。

 永遠不會引用可著色項清單中的第一項。 第一個項對應於可著色項索引 0,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]並且 始終提供該專案的預設文本顏色和屬性。 處理此未引用項的最簡單方法是將清單中的占位符可著色項作為第一項提供。

## <a name="implement-custom-colorable-items"></a>實現自訂可著色項目

1. 定義語言中必須著色的內容,例如關鍵字、運算元和標識碼。

2. 創建這些可著色項的枚舉。

3. 將從解析器或掃描器返回的權杖類型與枚舉值相關聯。

    例如,表示令牌類型的值可以是自定義可著色項枚舉中相同的值。

4. 在<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A><xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>物件中方法的實現中,使用自定義可著色項中的值填充屬性清單,枚舉與從解析器或掃描器返回的標記類型對應。

5. 在實現<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>介面的同一類中,<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>實現介面及其兩種方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>,<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>和 。

6. 實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 介面。

7. 如果要支援 24 位元或高顏色值<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>,還要實現介面。

8. 在語言服務物件中,創建一個包含物件<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>的清單,該清單針對解析器或掃描器可以標識的每個可著色項創建一個清單。

    您可以使用自定義可著色項枚舉中的相應值訪問清單中的每個項。 將枚舉值用作清單中的索引。 清單中的第一項永遠不會被訪問,因為它對應於[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]始終處理自身的預設文本樣式。 您可以通過在清單的開頭插入占位符可著色項來補償這一點。

9. 在實現 方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>時 ,返回自定義可著色項清單中的項目數。

10. 在實現 方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>時 ,從清單中返回請求的可著色項。

    有關如何實現<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem><xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>和介面的示例,請參閱<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>。

## <a name="see-also"></a>另請參閱
- [傳統語言服務的模型](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [自訂編輯器中的語法著色](../../extensibility/syntax-coloring-in-custom-editors.md)
- [舊語言服務中的語法著色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [實現語法著色](../../extensibility/internals/implementing-syntax-coloring.md)
- [如何:使用內建的可著色專案](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
