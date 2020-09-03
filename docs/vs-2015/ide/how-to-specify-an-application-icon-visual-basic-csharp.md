---
title: 如何：指定應用程式圖示 (Visual Basic、C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 136fd00bea736af0f0c589c28eae597ff8fd558e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670696"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>如何：指定應用程式圖示 (Visual Basic、C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

專案的 `Icon` 屬性指定已編譯的應用程式將會顯示在檔案總管和 Windows 工作列的圖示檔 (.ico)。

 透過 [專案設計工具]**** 的 [應用程式]**** 窗格，即可存取 `Icon` 屬性；該屬性包含圖示清單，其中的圖示都已經用資源或內容檔案的形式新增至專案。

> [!NOTE]
> 設定應用程式的 Icon 屬性之後，您也可以設定應用程式中每個 [視窗]**** 或 [表單]**** 的 `Icon` 屬性。 如需 Windows Presentation Foundation (WPF) 獨立應用程式之視窗圖示的詳細資訊，請參閱 <xref:System.Windows.Window.Icon%2A> 屬性。

### <a name="to-specify-an-application-icon"></a>指定應用程式圖示

1. 在方案總管**** 中，選擇專案節點 (而不是 [方案]**** 節點)。

2. 在功能表列上，依序選擇 [專案]**** 和 [屬性]****。

3. 當 [專案設計工具]**** 出現時，請選擇 [應用程式]**** 索引標籤。

4. **(Visual Basic)** 在 [圖示]**** 清單中，選擇圖示檔 (.ico)。

     **C #** 在 **圖示** 清單附近，選擇該 **\<Browse...>** 按鈕，然後流覽至您想要的圖示檔位置。

## <a name="see-also"></a>另請參閱
 專案設計工具[、應用程式頁面、專案設計工具 (Visual Basic) ](../ide/reference/application-page-project-designer-visual-basic.md) [應用程式頁面、專案設計工具 (c # ) ](../ide/reference/application-page-project-designer-csharp.md) [管理應用程式屬性](../ide/application-properties.md)[如何：新增或移除資源](https://msdn.microsoft.com/7b77bc06-3952-4799-b029-def3f8f7f88d)
