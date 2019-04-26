---
title: 管理專案和方案屬性 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d727efc0-1096-4ede-84b6-31a65da22ac0
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dd20552a72775723c4ad006708ce1fb7f18d4181
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63424623"
---
# <a name="managing-project-and-solution-properties"></a>管理專案和方案屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

專案具有控管編譯、偵錯、測試和部署各個層面的屬性。 有些屬性是所有專案類型通用的，有些則是特定語言或平台特有的。 在方案總管的專案節點上按一下滑鼠右鍵並選擇 [屬性]，或在功能表列 [快速啟動] 的搜尋方塊中鍵入屬性，即可存取專案屬性。  
  
 ![專案操作功能表](../ide/media/vs2015-proj-prop-menu.gif "vs2015_proj_prop_menu")  
  
 在專案樹狀本身，.NET 專案也具有屬性節點。  
  
 ![方案總管樹狀結構中的 [屬性] 節點](../ide/media/vs2015-props-se.png "VS2015_Props_SE")  
  
> [!TIP]
> 方案有一些屬性，專案項目也有；您可以在 [[屬性視窗]](../ide/reference/properties-window.md) 中存取這些屬性，而非 [專案設計工具]。  
  
## <a name="project-properties"></a>專案屬性  
 [專案屬性] 會組織成群組，而且每個群組都具有其專屬屬性頁，並且頁面可能會因語言和專案類型不同而不同。  
  
### <a name="c-and-visual-basic-projects"></a>C# 和 Visual Basic 專案  
 C# 和 Visual Basic 專案的屬性是公開在 [專案設計工具] 中。 下圖顯示 C# 中 WPF 專案的 [建置] 屬性頁：  
  
 ![Visual Studio 專案設計工具](../ide/media/vs2015-proppage-build.png "VS2015_PropPage_Build")  
  
 如需 [專案設計工具] 中每個屬性頁的詳細資訊，請參閱[專案屬性參考](../ide/reference/project-properties-reference.md)。  
  
### <a name="c-and-javascript-projects"></a>C++ 和 JavaScript 專案  
 C++ 和 JavaScript 專案具有不同的使用者介面來管理專案屬性。 下圖顯示 C++ 專案屬性頁 (JavaScript 的專案屬性頁也很類似)：  
  
 ![Visual C&#43;&#43; 專案屬性](../ide/media/vs2015-projprops-cpp.png "VS2015_ProjProps_cpp")  
  
 如需 C++ 專案屬性的資訊，請參閱[使用專案屬性](http://msdn.microsoft.com/library/9b0d6f8b-7d4e-4e61-aa75-7d14944816cd)。 如需 JavaScript 屬性的詳細資訊，請參閱 [JavaScript、屬性頁](../ide/reference/property-pages-javascript.md)。  
  
## <a name="solution-properties"></a>方案屬性  
 若要存取方案上的屬性，請以滑鼠右鍵按一下方案總管中的方案節點，然後選擇 [屬性]。 在對話方塊中，您可以設定偵錯或發行組建的專案組態、在按 F5 時選擇哪些專案應該要當成啟始專案，以及設定程式碼分析選項。  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 中的方案和專案](../ide/solutions-and-projects-in-visual-studio.md)
