---
title: 如何： 使用視覺化檢視 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.dataviewer
- vs.debug.stringviewer
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, about visualizers
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
ms.author: susanno
manager: douge
ms.openlocfilehash: cc158e0d84db56bc26262d60acd0fb8e92e47188
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47492032"
---
# <a name="how-to-use-a-visualizer"></a>如何：使用視覺化檢視
您可以使用視覺化檢視，以對資料類型有意義的方式，顯示變數或物件的內容。 您可以使用從視覺化檢視**DataTips**，則**監看式** 視窗中，**自動變數** 視窗中，或**區域變數**視窗。  
  
 Compact Framework 上不支援視覺化檢視。  
  
> [!NOTE]
>  在 **存放區**應用程式，僅限標準的文字，支援 HTML、 XML 及 JSON 視覺化檢視。 不支援自訂 (使用者建立的) 視覺化檢視。  
  
### <a name="to-open-a-visualizer"></a>若要開啟視覺化檢視  
  
1.  按一下中的變數名稱旁邊出現放大鏡圖示**DataTips**，則**監看式** 視窗中，或**自動變數**，**區域變數**，或**快速監看式**視窗。  
  
     視覺化檢視的清單隨即顯示。  
  
2.  按一下要使用的視覺化檢視。  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>若要在遠端偵錯期間使用 Managed 程式碼的視覺化檢視  
  
-   在啟動偵錯工作階段之前，將視覺化檢視 DLL 複製到遠端電腦上。  
  
     在遠端和本機電腦上，這個 DLL 的路徑必須相同。 這個路徑可以是下列其中一個位置：  
  
     *Visual Studio 安裝路徑* `\Common7\Packages\Debugger\Visualizers`  
  
     -或-  
  
     `My Documents\Visual Studio 2010\Visualizers` *Visual Studio 版本* `\Visualizers`  
  
## <a name="see-also"></a>另請參閱  
 [建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)   
 [如何： 安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)   
 [如何： 撰寫視覺化檢視](../debugger/how-to-write-a-visualizer.md)   
 [在資料提示中檢視資料值](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)