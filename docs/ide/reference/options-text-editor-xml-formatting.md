---
title: 選項、文字編輯器、XML、格式化
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1af8ff6f085d744cb58cb3844fced18d3e484494
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673206"
---
# <a name="options-text-editor-xml-formatting"></a>選項、文字編輯器、XML、格式化
使用 [格式化] 屬性頁來指定如何格式化您 XML 文件中的項目和屬性。 若要開啟 [選項] 對話方塊，請按一下 [工具] 功能表，然後按一下 [選項]。 若要存取 [格式化] 屬性頁，請展開 [文字編輯器] > [XML] > [格式化] 節點。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)。

## <a name="attributes"></a>屬性  
**保留手動屬性的格式**  
不要將屬性重新格式化。 此設定為預設。  
  
> [!NOTE]  
>  如果屬性跨多行，則編輯器會將屬性的每一行縮排，以符合父項目的縮排。  
  
**對齊位於各行上的屬性**  
垂直對齊第二個屬性及後續屬性，使其符合第一個屬性的縮排。 下列 XML 文字為如何對齊屬性的範例。  
  
```xml
<item id = "123-A"  
      name = "hammer"  
      price = "9.95"  
</item>  
```  
  
## <a name="auto-reformat"></a>自動重新格式化  
**從剪貼簿貼上**  
重新格式化從剪貼簿貼上的 XML 文字。  
  
**結束標記完成**  
結束標記完成時將項目重新格式化。  
  
## <a name="mixed-content"></a>混合內容  
**根據預設，會將混合內容重新設定。**  
會嘗試將混合內容重新格式化，但內容在 `xml:space="preserve"` 範圍中時除外。 此設定為預設。  
  
如果項目包含文字與標記的混合，則將內容視為混合內容。 下列是具有混合內容的項目範例。  
  
```xml
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
\</dir>  
```  
## <a name="see-also"></a>另請參閱
- [如何：建立 XML 文件 (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [程式碼產生](../code-generation-in-visual-studio.md)
  
