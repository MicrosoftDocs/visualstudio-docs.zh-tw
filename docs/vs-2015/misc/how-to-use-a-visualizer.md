---
title: 如何：使用視覺化檢視 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
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
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f981b76d471658fe82e874901ad784a17841891
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "64778371"
---
# <a name="how-to-use-a-visualizer"></a>如何：使用視覺化檢視
您可以使用視覺化檢視，以對資料類型有意義的方式，顯示變數或物件的內容。 您可以從 [ **資料提示**]、 **[監看** 式] 視窗 **、[** 自動 **變數** ] 視窗或 [區域變數] 視窗使用視覺化檢視。  
  
 Compact Framework 上不支援視覺化檢視。  
  
> [!NOTE]
> 在 **Store** 應用程式中，只支援標準文字、HTML、XML 和 JSON 視覺化檢視。 不支援自訂 (使用者建立的) 視覺化檢視。  
  
### <a name="to-open-a-visualizer"></a>若要開啟視覺化檢視  
  
1. 按一下 [ **資料提示**]、[ **監看** 式] 視窗 **、[自動**變數]、[ **區域變數**] 或 [ **快速監看** 式] 視窗中，出現在變數名稱旁邊的放大鏡圖示。  
  
     視覺化檢視的清單隨即顯示。  
  
2. 按一下要使用的視覺化檢視。  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>若要在遠端偵錯期間使用 Managed 程式碼的視覺化檢視  
  
- 在啟動偵錯工作階段之前，將視覺化檢視 DLL 複製到遠端電腦上。  
  
     在遠端和本機電腦上，這個 DLL 的路徑必須相同。 這個路徑可以是下列其中一個位置：  
  
     *Visual Studio 安裝路徑* `\Common7\Packages\Debugger\Visualizers`  
  
     -或-  
  
     `My Documents\Visual Studio 2010\Visualizers`*Visual Studio 版本*`\Visualizers`  
  
## <a name="see-also"></a>另請參閱  
 [建立自訂的視覺化檢視](../debugger/create-custom-visualizers-of-data.md)   
 [如何：安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)   
 [How to：撰寫視覺化](../debugger/how-to-write-a-visualizer.md)   
 [在資料提示中檢視資料值](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)