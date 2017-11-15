---
title: "如何：指定應用程式圖示 (Visual Basic、C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 17cce04dd94829225823de676e286b7d0158abec
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>如何：指定應用程式圖示 (Visual Basic、C#)
專案的 `Icon` 屬性指定已編譯的應用程式將會顯示在檔案總管和 Windows 工作列的圖示檔 (.ico)。  
  
 透過 [專案設計工具] 的 [應用程式] 窗格，即可存取 `Icon` 屬性；該屬性包含圖示清單，其中的圖示都已經用資源或內容檔案的形式新增至專案。  
  
> [!NOTE]
>  設定應用程式的 Icon 屬性之後，您也可以設定應用程式中每個 [視窗] 或 [表單] 的 `Icon` 屬性。 如需 Windows Presentation Foundation (WPF) 獨立應用程式之視窗圖示的詳細資訊，請參閱 <xref:System.Windows.Window.Icon%2A> 屬性。  
  
### <a name="to-specify-an-application-icon"></a>指定應用程式圖示  
  
1.  在方案總管中，選擇專案節點 (而不是 [方案] 節點)。  
  
2.  在功能表列上，依序選擇 [專案] 和 [屬性]。  
  
3.  當 [專案設計工具] 出現時，請選擇 [應用程式] 索引標籤。  
  
4.  **(Visual Basic)** 在 [圖示] 清單中，選擇圖示檔 (.ico)。  
  
     **C#** 選擇 [圖示] 清單附近的 [\<瀏覽...>] 按鈕，然後瀏覽至您想要之圖示檔的位置。  
  
## <a name="see-also"></a>另請參閱  
 [專案設計工具、應用程式頁面 (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [專案設計工具，應用程式頁面 (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [管理應用程式屬性](../ide/application-properties.md)  
 [如何：新增或移除資源](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)